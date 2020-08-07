---
title: Репликация данных в зашифрованных столбцах (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e1528d81faa352fdcdf37abe9ad93fda190445c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732566"
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a>Репликация данных в зашифрованные столбцы (среда SQL Server Management Studio)
  Репликация позволяет публиковать данные зашифрованных столбцов. Для расшифровки и использования этих данных на подписчике ключ, который был использован при шифровании данных на издателе, должен также располагаться и на подписчике. Репликация не предоставляет безопасного механизма для передачи ключей шифрования. Необходимо вручную повторно создать ключ шифрования на подписчике. В данном разделе показано, как зашифровать столбец на издателе и убедиться в том, что ключ шифрования доступен на подписчике.  
  
 Основными шагами являются следующие:  
  
1.  Создание симметричного ключа на издателе.  
  
2.  Шифрование данных столбца с помощью симметричного ключа.  
  
3.  Публикация таблицы с зашифрованным столбцом.  
  
4.  Подписка на эту публикацию.  
  
5.  Инициализация подписки.  
  
6.  Повторное создание симметричного ключа на подписчике с использованием тех же самых значений для ALGORITHM, KEY_SOURCE и IDENTITY_VALUE, что и в первом шаге.  
  
7.  Получение доступа к данным зашифрованного столбца.  
  
> [!NOTE]  
>  Для шифрования данных столбца следует использовать симметричный ключ. Симметричный ключ сам по себе может быть защищен на издателе и подписчике различными способами.  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a>Создание и репликация данных зашифрованного столбца  
  
1.  На издателе выполните инструкцию [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql).  
  
    > [!IMPORTANT]  
    >  Значение KEY_SOURCE является важным значением, которое может быть использовано для повторного создания симметричного ключа и расшифровки данных. Значение KEY_SOURCE должно всегда храниться и передаваться с соблюдением всех мер предосторожности.  
  
2.  Чтобы открыть новый ключ, выполните инструкцию [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) .  
  
3.  Для шифрования данных столбца на издателе используйте функцию [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) .  
  
4.  Чтобы закрыть ключ, выполните инструкцию [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) .  
  
5.  Опубликуйте таблицу, которая содержит зашифрованный столбец. Дополнительные сведения см. в разделе [Create a Publication](../publish/create-a-publication.md).  
  
6.  Подписка на эту публикацию. Дополнительные сведения см. в статьях [Создание подписки по запросу](../create-a-pull-subscription.md) и [Создание принудительной подписки](../create-a-push-subscription.md).  
  
7.  Инициализация подписки. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
8.  На подписчике выполните инструкцию [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) , используя те же самые значения для ALGORITHM, KEY_SOURCE и IDENTITY_VALUE, что и в первом шаге. При этом можно задать иное значение в предложении ENCRYPTION BY.  
  
    > [!IMPORTANT]  
    >  Значение KEY_SOURCE является важным значением, которое может быть использовано для повторного создания симметричного ключа и расшифровки данных. Значение KEY_SOURCE должно всегда храниться и передаваться с соблюдением всех мер предосторожности.  
  
9. Чтобы открыть новый ключ, выполните инструкцию [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) .  
  
10. Для расшифровки реплицируемых данных на подписчике используйте функцию [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) .  
  
11. Чтобы закрыть ключ, выполните инструкцию [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) .  
  
## <a name="example"></a>Пример  
 В этом примере создается симметричный ключ, сертификат, который используется для обеспечения безопасности симметричного ключа, и главный ключ. Эти ключи создаются в базе данных публикации. В последующем они используются для создания зашифрованного столбца EncryptedCreditCardApprovalCode в таблице `SalesOrderHeader` . Этот столбец опубликован в публикации AdvWorksSalesOrdersMerge вместо незашифрованного столбца CreditCardApprovalCode. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/publishencryptedcolumn.sql#sp_publishencryptedcolumn)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="example"></a>Пример  
 В этом примере повторно создается тот же самый симметричный ключ в базе данных подписки с помощью тех же самых значений для ALGORITHM, KEY_SOURCE и IDENTITY_VALUE, что и в первом шаге. В этом примере предполагается, что уже имеется инициализированная подписка на публикацию AdvWorksSalesOrdersMerge для репликации зашифрованного столбца. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные в файле скрипта, следует защитить этот файл во время хранения и передачи, чтобы предотвратить несанкционированный доступ к нему.  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/subscriberencryptedcolumn.sql#sp_subscriberencryptedcolumn)]  
  
## <a name="see-also"></a>См. также:  
 [Безопасность Репликация SQL Server](view-and-modify-replication-security-settings.md)   
 [Создание идентичных симметричных ключей на двух серверах](../../security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
