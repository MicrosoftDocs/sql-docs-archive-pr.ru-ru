---
title: Репликация изменений схемы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bec2f363cd8c4f7dea45935568a88722b19323fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664870"
---
# <a name="replicate-schema-changes"></a>Репликация изменений схемы
  В этом разделе описывается процесс репликации изменений схемы в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Если в опубликованную статью внести следующие изменения схемы, они по умолчанию распространяются на подписчики [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для репликации изменений схемы используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Инструкция ALTER TABLE ... DROP COLUMN всегда реплицируется для всех подписчиков, чьи подписки содержат удаляемые столбцы, даже при отключенной репликации изменений схемы.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Если реплицировать изменения схемы для публикации не требуется, отключите репликацию изменений схемы в диалоговом окне **Свойства публикации — \<Publication>** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
#### <a name="to-disable-replication-of-schema-changes"></a>Отключение репликации изменений схемы  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<Publication>** установите для свойства **Реплицировать изменения схемы** значение **False**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Для распространения только определенных изменений схемы перед изменением схемы установите свойство в **True** , а после выполнения изменений установите его в **False** . И наоборот, для распространения всех изменений схемы, за исключением данного изменения, перед изменением схемы установите свойство в **False** , а после выполнения изменений установите его в **True** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно использовать хранимые процедуры репликации для указания, следует ли реплицировать эти изменения схемы. Используемая хранимая процедура зависит от типа публикации.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a>Создание публикации моментальных снимков или публикации транзакций без репликации изменений схемы  
  
1.  На издателе в базе данных публикации выполните [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), указав значение **0** для ** \@ replicate_ddl**. Дополнительные сведения см. в разделе [Create a Publication](create-a-publication.md).  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a>Создание публикации слиянием без репликации изменений схемы  
  
1.  На издателе в базе данных публикации выполните [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), указав значение **0** для ** \@ replicate_ddl**. Дополнительные сведения см. в разделе [Create a Publication](create-a-publication.md).  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a>Временное отключение репликации изменений схемы для публикации моментальных снимков или публикации транзакций  
  
1.  Для публикации с репликацией изменений схемы выполните [sp_changepublication &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав значение **replicate_ddl** для ** \@ Свойства** и значение **0** в качестве ** \@ значения**.  
  
2.  Выполните команду DDL на опубликованном объекте.  
  
3.  Используемых Повторно включите репликацию изменений схемы, выполнив [sp_changepublication &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав значение **replicate_ddl** для ** \@ Свойства** и значение **1** в качестве ** \@ значения**.  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a>Временное отключение репликации изменений схемы для публикации слиянием  
  
1.  Для публикации с репликацией изменений схемы выполните [sp_changemergepublication &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), указав значение **replicate_ddl** для ** \@ Свойства** и значение **0** в качестве ** \@ значения**.  
  
2.  Выполните команду DDL на опубликованном объекте.  
  
3.  Используемых Повторно включите репликацию изменений схемы, выполнив [sp_changemergepublication &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), указав значение **replicate_ddl** для ** \@ Свойства** и значение **1** в качестве ** \@ значения**.  
  
## <a name="see-also"></a>См. также:  
 [Внесение изменений в схемы баз данных публикации](make-schema-changes-on-publication-databases.md)   
 [Внесение изменений в схемы баз данных публикации](make-schema-changes-on-publication-databases.md)  
  
  
