---
title: Измерение задержки и проверка правильности соединений для репликации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, performance
- tracer tokens [SQL Server replication]
- latency [SQL Server replication]
- transactional replication, tracer tokens
- monitoring performance [SQL Server replication], tracer tokens
ms.assetid: 4addd426-7523-4067-8d7d-ca6bae4c9e34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba1e5eddfdcffa5fbefdea323f110ba9d15ca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657653"
---
# <a name="measure-latency-and-validate-connections-for-transactional-replication"></a>Измерение задержки и проверка правильности соединений для репликации транзакций
  В данном разделе описывается измерение задержки и проверка соединений для репликации транзакций в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью монитора репликации, [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO. Репликация транзакций предоставляет функцию трассировочных токенов, которая обеспечивает удобный способ измерения длительности задержки в топологиях репликации транзакций и помогает проверять соединения между издателем, распространителем и подписчиками. Токен (небольшой объем данных) записывается в журнал транзакций базы данных публикации и помечается так, как если бы он был обычной реплицируемой транзакцией, а затем проходит по системе, позволяя вычислить следующие характеристики:  
  
-   Время, прошедшее между фиксацией транзакции на издателе и вставкой соответствующей команды в базу данных распространителя на распространителе.  
  
-   Время, прошедшее между вставкой команды в базу данных распространителя и соответствующей транзакцией, зафиксированной у подписчика.  
  
 Из этих вычислений можно получить ответы на следующие вопросы:  
  
-   Какой подписчик позднее всех получает изменения от издателя?  
  
-   Какие подписчики, ожидающие получение трассировочного токена, его не получили (если таковые имеются)?  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для измерения задержки и проверки соединений используется:**  
  
     [Монитор репликации SQL Server](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Объекты RMO](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Трассировочные токены также могут быть полезны при «замораживании» системы, когда останавливаются все действия и проверяется получение всеми узлами всех необработанных изменений. Дополнительные сведения см. в разделе [Замораживание топологии репликации (программирование репликации на языке Transact-SQL)](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
 Чтобы использовать трассировочные токены, необходимо использовать определенные версии [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   Распространитель должен быть [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии.  
  
-   Издатель должен быть [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии, либо издателем Oracle.  
  
-   Для принудительных подписок статистика трассировочного токена собирается от издателя, распространителя и подписчиков, если подписчик равен [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7,0 или более поздней версии.  
  
-   Для подписок по запросу статистика по трассировочным токенам собирается с подписчиков, только если это подписчик [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Если подписчик равен [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7,0 или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , статистика собирается только от издателя и распространителя.  
  
 Следует также учитывать ряд других вопросов и ограничений:  
  
-   Подписки должны быть активными, чтобы получать трассировочный токен. Подписка является активной, если она инициализирована.  
  
-   При повторной инициализации удаляются все отложенные трассировочные токены для соответствующих подписок.  
  
-   Подписчики получают только трассировочные токены, созданные после их исходной синхронизации.  
  
-   Трассировочные токены не пересылаются переиздающими подписчиками.  
  
-   После отработки отказа на вторичной реплике монитор репликации не сможет изменить имя экземпляра публикации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и будет продолжать отображать сведения о репликации по имени исходного первичного экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. После отработки отказа нельзя ввести трассировочный токен с помощью монитора репликации, но трассировочный токен, введенный в новый издатель с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)], отображается в мониторе репликации.  
  
##  <a name="using-sql-server-replication-monitor"></a><a name="SSMSProcedure"></a>Использование монитора Репликация SQL Server  
 Сведения о запуске монитора репликации см. в [этой статье](start-the-replication-monitor.md).  
  
#### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>Вставка трассировочного токена и просмотр сведений о токене  
  
1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
2.  Щелкните вкладку **Трассировочные токены** .  
  
3.  Выберите команду **Вставить трассировочный маркер**.  
  
4.  Просмотрите затраченное время для трассировочного маркера в следующих столбцах: **От издателя к распространителю**, **От распространителя к подписчику**, **Общая задержка**. Значение **Pending** указывает, что маркер не достиг данной точки.  
  
#### <a name="to-view-information-on-a-tracer-token-inserted-previously"></a>Просмотр сведений о трассировочном токене, вставленном ранее  
  
1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
2.  Щелкните вкладку **Трассировочные токены** .  
  
3.  Выберите время в раскрывающемся списке **Время вставки** .  
  
4.  Просмотрите затраченное время для трассировочного маркера в следующих столбцах: **От издателя к распространителю**, **От распространителя к подписчику**, **Общая задержка**. Значение **Pending** указывает, что маркер не достиг данной точки.  
  
    > [!NOTE]  
    >  Данные трассировочных токенов хранятся в течение того же периода времени, что и другие данные предыстории; этот период определяется сроком хранения журнала в базе данных распространителя. Дополнительные сведения о доступе к этим диалоговым окнам см. в статье [Просмотр и изменение свойств издателя и распространителя](../view-and-modify-distributor-and-publisher-properties.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a>Отправка трассировочного токена в публикацию транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helppublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) (необязательно). Удостоверьтесь в том, что публикация существует и находится в активном состоянии.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) (необязательно). Удостоверьтесь в том, что подписка существует и находится в активном состоянии.  
  
3.  На издателе в базе данных издателя выполните процедуру [sp_posttracertoken (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql), указав параметр **@publication**. Запишите значение **@tracer_token_id** параметра OUTPUT.  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a>Измерение задержки и проверка соединений для публикации транзакций  
  
1.  Передайте трассировочный токен в публикацию при помощи описанной выше процедуры.  
  
2.  На издателе в базе данных издателя выполните процедуру [sp_helptracertokens (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), указав параметр **@publication**. Будет возвращен список всех трассировочных токенов, опубликованных для публикации. Запомните нужное значение **tracer_id** в результирующем наборе.  
  
3.  На издателе в базе данных издателя выполните процедуру [sp_helptracertokenhistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql), указав параметр **@publication** и идентификатор трассировочного маркера, полученного на шаге 2, в параметре **@tracer_id**. В результате этого будут возвращены сведения о задержке для выделенного трассировочного токена.  
  
#### <a name="to-remove-tracer-tokens"></a>Удаление трассировочных токенов  
  
1.  На издателе в базе данных издателя выполните процедуру [sp_helptracertokens (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), указав параметр **@publication**. Будет возвращен список всех трассировочных токенов, опубликованных для публикации. Запомните нужное значение **tracer_id** в результирующем наборе для удаляемого трассировочного токена.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_deletetracertokenhistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql), указав параметр **@publication**, а также идентификатор удаляемого трассировочного маркера, полученного на шаге 2, в параметре **@tracer_id**.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере продемонстрирована отправка трассировочного токена, и просмотр сведений о задержке по возвращенному идентификатору отправленного трассировочного токена.  
  
 [!code-sql[HowTo#sp_tracertokens](../../../snippets/tsql/SQL15/replication/howto/tsql/createtracertokens.sql#sp_tracertokens)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a>Отправка трассировочного токена в публикацию транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication>.  
  
3.  Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства.  
  
4.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает `false`, то либо на шаге 3 были неверно определены свойства публикации, либо публикация не существует.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> . Этот метод обеспечивает вставку трассировочного токена в журнал транзакций публикации.  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a>Измерение задержки и проверка соединений для публикации транзакций  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.PublicationMonitor>.  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>и <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> , а в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> установите созданное на шаге 1 соединение.  
  
4.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает `false`, то либо на шаге 3 были неверно определены свойства монитора публикации, либо публикация не существует.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> . Приведите возвращенный объект <xref:System.Collections.ArrayList> к типу массива объектов <xref:Microsoft.SqlServer.Replication.TracerToken> .  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> . Передайте значение <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> для трассировочного токена, полученного на шаге 5. В результате будут возвращены сведения о задержке для выделенного трассировочного токена в виде объекта <xref:System.Data.DataSet> . Если возвращены все сведения о трассировочном токене, то существует соединение между издателем и распространителем, а также соединение между распространителем и подписчиком, и топология репликации работоспособна.  
  
#### <a name="to-remove-tracer-tokens"></a>Удаление трассировочных токенов  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.PublicationMonitor>.  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>и <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> , а в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> установите созданное на шаге 1 соединение.  
  
4.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает `false`, то либо на шаге 3 были неверно определены свойства монитора публикации, либо публикация не существует.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> . Приведите возвращенный объект <xref:System.Collections.ArrayList> к типу массива объектов <xref:Microsoft.SqlServer.Replication.TracerToken> .  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> . Передайте одно из следующих значений.  
  
    -   Значение <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> для трассировочного токена, полученного на шаге 5. В результате этого сведения для выделенного токена будут удалены.  
  
    -   Объект <xref:System.DateTime>. В результате этого будут удалены сведения обо всех токенах, созданных до наступления указанного момента времени.  
  
###  <a name="PShellExample"></a>  
