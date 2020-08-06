---
title: Включение обновляемых подписок для публикации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, enabling
- subscriptions [SQL Server replication], updatable
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f432b1e402c51646efba54ed4aacba3287b0c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656324"
---
# <a name="enable-updating-subscriptions-for-transactional-publications"></a>Включение обновляемых подписок для публикаций транзакций
  В этом разделе описывается включение обновляемых подписок для публикаций транзакций в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Включение обновляемых подписок для публикаций транзакций производится на странице **Тип публикации** мастера создания публикаций. Дополнительные сведения об использовании мастера см. в статье [Создание публикации](create-a-publication.md). После того как публикация создана, обновляемые подписки невозможно включить.  
  
 Для использования обновляемых подписок необходимо также настроить параметры в мастере создания подписки. Дополнительные сведения см. в разделе [Создание обновляемых подписок для публикаций транзакций](../publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
#### <a name="to-enable-updating-subscriptions"></a>Включение обновляемых подписок  
  
1.  На странице **Тип публикации** мастера создания публикаций выберите **Публикация транзакций с обновляемыми подписками**.  
  
2.  На странице **Безопасность агентов** укажите настройки безопасности агента чтения очереди в дополнение к агенту моментальных снимков и агенту чтения журнала. Дополнительные сведения о разрешениях, необходимых для учетной записи, под которой запускается агент чтения очереди, см. в разделе [Replication Agent Security Model](../security/replication-agent-security-model.md).  
  
    > [!NOTE]  
    >  Настройка агента чтения очереди осуществляется даже при использовании только подписок, обновляемых немедленно.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 При создании публикации транзакций программным путем при помощи хранимых процедур репликации подписки на нее могут быть настроены как на немедленное обновление, так и на обновление посредством очередей.  
  
#### <a name="to-create-a-publication-that-supports-immediate-updating-subscriptions"></a>Создание публикации с поддержкой немедленно обновляемых подписок  
  
1.  В случае необходимости создайте задание агента чтения журнала для базы данных публикации.  
  
    -   Если задание агента чтения журнала для базы данных публикации уже существует, переходите к шагу 2.  
  
    -   Если неизвестно, существует ли задание агента чтения журнала для публикуемой базы данных, выполните процедуру [sp_helplogreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql) на издателе в базе данных издателя. Если результирующий набор пуст, то необходимо создать задание агента чтения журнала.  
  
    -   На издателе выполните [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql). Укажите [!INCLUDE[msCoName](../../../includes/msconame-md.md)] учетные данные Windows, с которыми запускается агент, для **@job_name** и **@password** . Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **@publisher_security_mode** и данные входа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** @password **@publisher_password**.  
  
2.  Выполните [sp_addpublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), указав значение **true** для параметра **@allow_sync_tran**.  
  
3.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql). Укажите имя публикации, используемое в шаге 2 **@publication** , и учетные данные Windows, с которыми будет выполняться агент моментальных снимков **@job_name** , для и **@password** . Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** @password **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
4.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
5.  Создайте на подписчике обновляемую подписку на эту публикацию. Дополнительные сведения см. в разделе [Создание обновляемых подписок для публикаций транзакций](../publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
#### <a name="to-create-a-publication-that-supports-queued-updating-subscriptions"></a>Создание публикации с поддержкой обновления подписок посредством очередей  
  
1.  В случае необходимости создайте задание агента чтения журнала для базы данных публикации.  
  
    -   Если задание агента чтения журнала для базы данных публикации уже существует, переходите к шагу 2.  
  
    -   Если неизвестно, существует ли задание агента чтения журнала для публикуемой базы данных, выполните процедуру [sp_helplogreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql) на издателе в базе данных издателя. Если результирующий набор пуст, необходимо создать задание агента чтения журнала.  
  
    -   На издателе выполните [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql). Укажите учетные данные Windows, с которыми запускается агент, для **@job_name** и **@password** . Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** @password **@publisher_password**.  
  
2.  Если необходимо, создайте на распространителе задание агента чтения очереди.  
  
    -   Если он уже существует для указанной базы данных распространителя, то перейдите к шагу 3.  
  
    -   Чтобы выяснить, существует ли в базе данных распространителя задание агента чтения очереди, запустите в ней хранимую процедуру [sp_helpqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql). Если результирующий набор пуст, то задание агента чтения очереди необходимо создать.  
  
    -   В распространителе выполните хранимую процедуру [sp_helpqreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql). Укажите учетные данные Windows, с которыми запускается агент, для **@job_name** и **@password** . Указанные учетные данные используются при подключении агента чтения очереди к издателю или подписчику. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../security/replication-agent-security-model.md).  
  
3.  Выполните хранимую процедуру [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), указав значение **true** в параметре **@allow_queued_tran** и значение **pub wins**, **sub reinit** или **sub wins** в параметре **@conflict_policy**.  
  
4.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql). Укажите имя публикации, используемое на шаге 3 **@publication** , и учетные данные Windows, с которыми будет выполняться агент моментальных снимков **@snapshot_job_name** , для и **@password** . Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** @password **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
5.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
6.  Создайте на подписчике обновляемую подписку на эту публикацию. Дополнительные сведения см. в разделе [Создание обновляемых подписок для публикаций транзакций](../publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
#### <a name="to-change-the-conflict-policy-for-a-publication-that-allows-queued-updating-subscriptions"></a>Изменение политики разрешения конфликтов для публикации с поддержкой обновления подписок посредством очередей  
  
1.  В издателе в базе данных публикации выполните процедуру [sp_changepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql). Укажите значение **conflict_policy** в параметре **@property** и задайте режим политики конфликтов, передав значение **pub wins**, **sub reinit**или **sub wins** в параметре **@value**.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается публикация, поддерживающая оба режима обновления подписок по запросу: немедленное и посредством очередей.  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpubupdate.sql#sp_createtranupdatingpub)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка параметров разрешения конфликтов обновления посредством очередей &#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Типы публикаций для репликации транзакций](../transactional/transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Create a Publication](create-a-publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Использование программы sqlcmd с переменными скрипта](../../scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
