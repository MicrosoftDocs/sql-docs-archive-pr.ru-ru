---
title: MSSQL_ENG021797 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021797 error
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d33ade7e7eea9fa9e95453a5b232447f7b222b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730494"
---
# <a name="mssql_eng021797"></a>MSSQL_ENG021797
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21797|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|"%s" должно быть допустимым именем входа Windows, представленным в следующем виде: "КОМПЬЮТЕР\имя_входа" или "ДОМЕН\имя_входа". См. документацию по "%s".»|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка возникает в следующих хранимых процедурах репликации, если значение, указанное для **@job_login** параметра, равно null или недопустимо. Эта ошибка может возникнуть, если член предопределенной роли базы данных **db_owner** запускает скрипты из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Модель безопасности в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]изменилась, поэтому эти скрипты необходимо обновить.  
  
-   [sp_addlogreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)  
  
-   [sp_addqreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql)  
  
-   [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql)  
  
-   [sp_addpushsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)  
  
-   [sp_addpullsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)  
  
-   [sp_addmergepushsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)  
  
-   [sp_addmergepullsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)  
  
 Эти хранимые процедуры могут запускаться членом предопределенной роли сервера **sysadmin** на соответствующем сервере или членом предопределенной роли базы данных **db_owner** в соответствующей базе данных. Каждая из этих хранимых процедур создает задание для агента и позволяет задать учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается агент. Для пользователей в роли **sysadmin** задания агентов создаются неявно, даже если не задана учетная запись Windows (если учетная запись задана, то она должна быть допустимой); агенты запускаются в контексте учетной записи службы агентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на соответствующем сервере. Несмотря на то, что учетная запись не требуется, в целях безопасности рекомендуется задать отдельную учетную запись для каждого агента. Дополнительные сведения см. в статье [Модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что для параметра каждой процедуры указана допустимая учетная запись Windows **@job_login** . При наличии скриптов репликации из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]обновите эти скрипты для включения хранимых процедур и параметров, требуемых [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения см. в статье [Обновление скриптов репликации (программирование репликации на языке Transact-SQL)](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
