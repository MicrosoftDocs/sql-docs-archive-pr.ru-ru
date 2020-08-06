---
title: Обновление скриптов репликации (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server replication], upgrading
- upgrading SQL Server, replicated databases
- upgrading replication applications
- replication [SQL Server], scripting
- replication [SQL Server], upgrading
- upgrading replicated databases
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c47101c76ca2c585accd493b74f0e59c56bf009e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657679"
---
# <a name="upgrade-replication-scripts-replication-transact-sql-programming"></a>обновить скрипты репликации (программирование репликации на языке Transact-SQL)
  Настройка топологии репликации программным способом возможна при помощи файлов скриптов на языке[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Дополнительные сведения см. в статье [Основные понятия системных хранимых процедур репликации](../concepts/replication-system-stored-procedures-concepts.md).  
  
> [!IMPORTANT]  
>  Хотя обновление скриптов, выполняемых членами роли `sysadmin`, не является обязательным, рекомендуется внести в существующие скрипты изменения, описанные в настоящем разделе. Для всех агентов репликации следует указывать учетные записи, наделенные минимальным числом разрешений, как это описано в подразделе «Разрешения, необходимые для агентов» раздела [Replication Agent Security Model](../security/replication-agent-security-model.md).  
  
 Улучшения в области безопасности, повышающие управляемость разрешений за счет предоставления пользователю возможности явно задавать учетные записи [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, от которых выполняются задания агента репликации, затронут следующие хранимые процедуры в существующих скриптов.  
  
-   **sp_addpublication_snapshot**:  
  
     Теперь учетные данные Windows следует указывать как **@job_login** и **@job_password** при выполнении [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) для создания задания, при котором агент моментальных снимков выполняется на распространителе.  
  
-   **sp_addpushsubscription_agent**:  
  
     Теперь пользователь должен выполнять хранимую процедуру [sp_addpushsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql), чтобы явным образом добавить задание и передать учетные данные Windows(в параметрах **@job_login** и **@job_password**), с которыми задание агента распространителя будет выполняться на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это выполнялось автоматически при создании принудительной подписки.  
  
-   **sp_addmergepushsubscription_agent**:  
  
     Теперь пользователь должен выполнить процедуру [sp_addpushsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql), чтобы явным образом добавить задание и передать учетные данные Windows (в параметрах **@job_login** и **@job_password**), с использованием которых задание агента слияния будет выполняться на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это выполнялось автоматически при создании принудительной подписки.  
  
-   **sp_addpullsubscription_agent**:  
  
     Теперь учетные данные Windows следует указывать как **@job_login** и **@job_password** при выполнении [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) для создания задания, при котором агент распространения выполняется на подписчике.  
  
-   **sp_addmergepullsubscription_agent**:  
  
     Теперь учетные данные Windows следует указывать как **@job_login** и **@job_password** при выполнении [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) для создания задания, при котором агент слияния выполняется на подписчике.  
  
-   **sp_addlogreader_agent**:  
  
     Теперь пользователь должен вызвать хранимую процедуру [sp_addlogreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql), чтобы вручную добавить задание и передать учетные данные Windows, с использованием которых агент чтения журнала будет выполняться на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это делалось автоматически при создании публикации транзакций.  
  
-   **sp_addqreader_agent**:  
  
     Теперь пользователь должен вызвать хранимую процедуру [sp_addlogreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql), чтобы вручную добавить задание и передать учетные данные Windows, с использованием которых агент чтения очереди будет выполняться на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это производилось автоматически при создании публикации транзакций, поддерживающей обновление посредством очередей.  
  
 В модели безопасности, представленной в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] , агенты репликации всегда выполняют соединения с локальным экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с проверкой подлинности Windows, используя учетные данные, указанные в **@job_name** и **@job_password** . Сведения о требованиях к учетным записям Windows, которые предназначены для выполнения заданий агента репликации, см. в разделе [Replication Agent Security Model](../security/replication-agent-security-model.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если учетные данные сохраняются в файле скрипта, то должна быть обеспечена защита этого файла.  
  
### <a name="to-upgrade-scripts-that-configure-a-snapshot-or-transactional-publication"></a>Обновление скриптов настройки репликации моментальными снимками и публикацией транзакций  
  
1.  В существующем скрипте перед [sp_addpublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) выполните хранимую процедуру [sp_addlogreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) в издателе в базе данных публикации. Укажите учетные данные Windows, с которыми будет выполняться агент чтения журнала, для **@job_name** и **@job_password** . Если агент будет использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверку подлинности при соединении с издателем, необходимо также указать значение **0** в параметре **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа для **@publisher_login** и **@publisher_password** . Таким образом будет сформировано задание агента чтения журнала для базы данных публикации.  
  
    > [!NOTE]  
    >  Этот шаг предназначен только для публикаций транзакций и не обязателен для публикаций моментальных снимков.  
  
2.  (Необязательно.) Перед [sp_addpublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) выполните [sp_addlogreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) в издателе в базе данных публикации. Укажите учетные данные Windows, с которыми будет выполняться агент чтения очереди, для **@job_name** и **@job_password** . В результате этого будет сформировано задание агента чтения очереди для распространителя.  
  
    > [!NOTE]  
    >  Этот шаг обязателен только для публикаций транзакций, которые поддерживают подписчиков, обновляемых посредством очередей.  
  
3.  Чтобы установить для параметров, реализующих новые функции репликации, значения отличные от принятых по умолчанию, обновите код вызова процедуры [sp_addpublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) (необязательно).  
  
4.  После [sp_addpublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) выполните [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) в издателе в базе данных публикации. Укажите **@publication** учетные данные Windows, с которыми будет запускаться агент моментальных снимков, и **@job_name** **@job_password** . Если агент будет использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверку подлинности при соединении с издателем, необходимо также указать значение **0** в параметре **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа для **@publisher_login** и **@publisher_password** . Будет создано задание агента моментальных снимков для публикации.  
  
5.  Чтобы установить для параметров, реализующих новые функции репликации, значения, отличные от принятых по умолчанию, обновите код вызова процедуры [sp_addarticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) (необязательно).  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-snapshot-or-transactional-publication"></a>Обновление скриптов, которые добавляют подписки к публикациям моментальных снимков или публикациям транзакций  
  
1.  После вызова хранимой процедуры, которая создает подписку, обязательно выполните хранимую процедуру, формирующую задание агента распространителя для синхронизации подписки. Используемая хранимая процедура зависит от типа подписки.  
  
    -   Для подписки по запросу обновите вызов процедуры [sp_addpullsubscription_agent (Transact-SQL) ](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql), указав в параметрах **@job_name** и **@job_password** учетные данные Windows, с использованием которых агент распространителя будет запускаться на подписчике. Это необходимо сделать после вызова хранимой процедуры [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Дополнительные сведения см. в статье [Создание подписки по запросу](../create-a-pull-subscription.md).  
  
    -   Для принудительной подписки выполните процедуру [sp_addpushsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) на издателе. Укажите **@subscriber** , **@subscriber_db** , **@publication** , учетные данные Windows, с которыми агент распространения выполняется на распространителе для **@job_name** и **@job_password** , и расписание для этого задания агента. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../specify-synchronization-schedules.md). Это необходимо сделать после вызова процедуры [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Дополнительные сведения см. в статье [Создание принудительной подписки](../create-a-push-subscription.md).  
  
### <a name="to-upgrade-scripts-that-configure-a-merge-publication"></a>Обновление скриптов настройки публикации слиянием  
  
1.  В существующем скрипте обновите вызов процедуры [sp_addmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), указав для новых параметров, реализующих новые функции репликации, значения, отличные от заданных по умолчанию (необязательно).  
  
2.  После [sp_addmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) выполните [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) в издателе в базе данных публикации. Укажите **@publication** учетные данные Windows, с которыми будет запускаться агент моментальных снимков, и **@job_name** **@job_password** . Если агент будет использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверку подлинности при соединении с издателем, необходимо также указать значение **0** в параметре **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа для **@publisher_login** и **@publisher_password** . Будет создано задание агента моментальных снимков для публикации.  
  
3.  (Необязательно.) Чтобы установить для параметров, реализующих новые функции репликации, значения, отличные от принятых по умолчанию, обновите код вызова процедуры [sp_addmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-merge-publication"></a>Обновление скриптов, добавляющих подписки к публикации слиянием  
  
1.  После вызова хранимой процедуры, которая создает подписку, обязательно выполните хранимую процедуру, формирующую задание агента слияния для синхронизации подписки. Используемая хранимая процедура зависит от типа подписки.  
  
    -   Для подписки по запросу обновите вызов процедуры [sp_addmergepullsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql), указав в параметрах **@job_name** и **@job_password** учетные данные Windows, с использованием которых агент слияния будет запускаться на подписчике. Это необходимо сделать после вызова процедуры [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql). Дополнительные сведения см. в статье [Создание подписки по запросу](../create-a-pull-subscription.md).  
  
    -   Для принудительной подписки, выполните процедуру [sp_addmergepushsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql) на издателе. Укажите **@subscriber** , **@subscriber_db** , **@publication** , учетные данные Windows, с которыми будет запускаться агент слияния на распространителе **@job_name** **@job_password** , и расписание для этого задания агента. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../specify-synchronization-schedules.md). Это необходимо сделать после вызова хранимой процедуры [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql). Дополнительные сведения см. в статье [Создание принудительной подписки](../create-a-push-subscription.md).  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает публикацию транзакций для таблицы Product. Эта публикация поддерживает немедленное обновление с переключением на обновление отработки отказа. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpub80.sql#sp_createtranpub_nwpreupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведено обновление предыдущего примера скрипта, который создает публикацию транзакций для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Эта публикация поддерживает немедленное обновление с переключением на обновление отработки отказа. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>   Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpublication.sql#sp_createtranpub_nwpostupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает публикацию слиянием для таблицы Customers. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepub80.sql#sp_createmergepub_nwpreupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта для создания публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>   Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepublication.sql#sp_createmergepub_nwpostupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает принудительную подписку для публикации транзакций. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpushsub80.sql#sp_createtranpushsub_nwpreupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта для создания принудительной подписки для публикации транзакций, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>   Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpushsub.sql#sp_createtranpushsub_nwpostupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает принудительную подписку для публикации слиянием. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepushsub80.sql#sp_createmergepushsub_nwpreupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта, создающий принудительную подписку для публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>   Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpushsub.sql#sp_createmergepushsub_nwpostupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает подписку по запросу для публикации транзакций. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepushsub80.sql#sp_createmergepushsub_nwpreupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта для создания подписки по запросу для публикации транзакций, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>   Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpullsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpullsub.sql#sp_createtranpullsub_nwpostupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает подписку по запросу для публикации слиянием. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepullsub80.sql#sp_createmergepullsub_nwpreupgrade)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта, создающий подписку по запросу для публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>   Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpullsub.sql#sp_createmergepullsub_nwpostupgrade)]  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../publish/create-a-publication.md)   
 [Create a Push Subscription](../create-a-push-subscription.md)   
 [Create a Pull Subscription](../create-a-pull-subscription.md)   
 [Просмотр и изменение параметров безопасности репликации](../security/view-and-modify-replication-security-settings.md)   
 [MSSQL_ENG021797](../mssql-eng021797.md)   
 [MSSQL_ENG021798](../mssql-eng021798.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Обновление реплицируемых баз данных](../../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
