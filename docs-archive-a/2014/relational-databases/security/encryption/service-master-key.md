---
title: Главный ключ службы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: baeeffd49ac89ce85cf64932fbfd4982d7243887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752059"
---
# <a name="service-master-key"></a>главный ключ службы
  Главный ключ службы является корнем иерархии шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Он создается автоматически, как только он впервые понадобится для шифрования другого ключа. По умолчанию главный ключ службы шифруется с помощью API-интерфейса защиты данных Windows и ключа локального компьютера. Главный ключ службы может быть открыт только учетной записью службы Windows, под которой он был создан, либо участником, имеющим доступ к имени и паролю учетной записи службы.  
  
 Для повторного создания или восстановления из копии главного ключа службы необходимо дешифровать и снова зашифровать всю иерархию шифрования. Если только ключ не был похищен, данную ресурсоемкую операцию следует планировать на то время, когда количество обращений к серверу минимальное.  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] использует для защиты главного ключа службы и главного ключа базы данных алгоритм шифрования AES. AES - это новый алгоритм шифрования, отличный от алгоритма 3DES, используемого в более ранних версиях. После обновления экземпляра компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] до [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] необходимо заново сформировать главный ключ службы и главный ключ базы данных, чтобы обновить главные ключи до алгоритма AES. Дополнительные сведения о повторном создании главного ключа базы данных см. в статьях [ALTER SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-service-master-key-transact-sql) и [ALTER MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-master-key-transact-sql).  
  
## <a name="best-practice"></a>Рекомендации  
 Создайте резервную копию главного ключа службы и храните ее на безопасном автономном компьютере.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [BACKUP SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/backup-service-master-key-transact-sql)  
  
 [RESTORE SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/restore-service-master-key-transact-sql)  
  
 [ALTER SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-service-master-key-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [Иерархия средств шифрования](encryption-hierarchy.md)  
  
  
