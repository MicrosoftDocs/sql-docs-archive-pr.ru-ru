---
title: Пример. Создание оповещения агент SQL Server с помощью поставщика WMI для событий сервера | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SQL Server Agent [WMI]
- WMI Provider for Server Events, samples
- sample applications [WMI]
ms.assetid: d44811c7-cd46-4017-b284-c863ca088e8f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f23a3a8738435dc6a27a230f4521300a3ee2470f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733682"
---
# <a name="sample-creating-a-sql-server-agent-alert-by-using-the-wmi-provider-for-server-events"></a>Образец. Создание предупреждения агента SQL Server с помощью поставщика WMI для событий сервера
  Один из общепринятых способов использования поставщика событий WMI состоит в создании предупреждений агента SQL Server, которые отвечают на конкретные события. В следующем образце представлено простое предупреждение, которое сохраняет события графа взаимоблокировок XML в таблице для последующего анализа. Агент SQL Server отправляет запрос WQL, получает события WMI и запускает задание в ответ на событие. Обратите внимание, что в обработке сообщения уведомления участвуют несколько объектов компонента Service Broker, но детальные операции создания и управления этими объектами возлагаются на поставщика событий WMI.  
  
## <a name="example"></a>Пример  
 Прежде всего в базе данных `AdventureWorks` создается таблица для хранения событий графа взаимоблокировок. Таблица содержит два столбца: `AlertTime` столбец содержит время запуска оповещения, а `DeadlockGraph` столбец содержит XML-документ, содержащий граф взаимоблокировок.  
  
 Затем создается предупреждение. Скрипт сначала создает задание, которое запускается предупреждением, добавляет шаг задания к заданию и направляет задание в текущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После этого скрипт создает предупреждение.  
  
 Шаг задания извлекает свойство **TextData** экземпляра события WMI и вставляет это значение в столбец **DeadlockGraph** таблицы **DeadlockGraph** . Обратите внимание, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неявно преобразует строку в формат XML. Поскольку в шагах задания используется подсистема [!INCLUDE[tsql](../../includes/tsql-md.md)], шаг задания не задает учетной записи-посредника.  
  
 Предупреждение запускает задание каждый раз, когда регистрируется событие трассировки графа взаимоблокировок. Для предупреждения WMI агент SQL Server создает запрос уведомления с использованием пространства имен и указанной инструкции WQL. Применительно к этому предупреждению агент SQL Server наблюдает за экземпляром по умолчанию на локальном компьютере. Инструкция WQL запрашивает любое событие `DEADLOCK_GRAPH` в экземпляре по умолчанию. Чтобы изменить экземпляр, за которым ведется наблюдение с помощью предупреждения, измените имя экземпляра на `MSSQLSERVER` в `@wmi_namespace` для события.  
  
> [!NOTE]  
>  Для агент SQL Server получения событий WMI [!INCLUDE[ssSB](../../includes/sssb-md.md)] необходимо включить в **msdb** и [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
USE AdventureWorks ;  
GO  
  
IF OBJECT_ID('DeadlockEvents', 'U') IS NOT NULL  
BEGIN  
    DROP TABLE DeadlockEvents ;  
END ;  
GO  
  
CREATE TABLE DeadlockEvents  
    (AlertTime DATETIME, DeadlockGraph XML) ;  
GO  
-- Add a job for the alert to run.  
  
EXEC  msdb.dbo.sp_add_job @job_name=N'Capture Deadlock Graph',   
    @enabled=1,   
    @description=N'Job for responding to DEADLOCK_GRAPH events' ;  
GO  
  
-- Add a jobstep that inserts the current time and the deadlock graph into  
-- the DeadlockEvents table.  
  
EXEC msdb.dbo.sp_add_jobstep  
    @job_name = N'Capture Deadlock Graph',  
    @step_name=N'Insert graph into LogEvents',  
    @step_id=1,   
    @on_success_action=1,   
    @on_fail_action=2,   
    @subsystem=N'TSQL',   
    @command= N'INSERT INTO DeadlockEvents  
                (AlertTime, DeadlockGraph)  
                VALUES (getdate(), N''$(ESCAPE_SQUOTE(WMI(TextData)))'')',  
    @database_name=N'AdventureWorks' ;  
GO  
  
-- Set the job server for the job to the current instance of SQL Server.  
  
EXEC msdb.dbo.sp_add_jobserver @job_name = N'Capture Deadlock Graph' ;  
GO  
  
-- Add an alert that responds to all DEADLOCK_GRAPH events for  
-- the default instance. To monitor deadlocks for a different instance,  
-- change MSSQLSERVER to the name of the instance.  
  
EXEC msdb.dbo.sp_add_alert @name=N'Respond to DEADLOCK_GRAPH',   
@wmi_namespace=N'\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER',   
    @wmi_query=N'SELECT * FROM DEADLOCK_GRAPH',   
    @job_name='Capture Deadlock Graph' ;  
GO  
```  
  
## <a name="testing-the-sample"></a>Тестирование образца  
 Чтобы увидеть выполнение задания, следует искусственно вызвать взаимоблокировку. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] среде Откройте две вкладки **SQL запроса** и подключите оба запроса к одному и тому же экземпляру. Запустите следующий скрипт в одной из вкладок запроса. Этот скрипт выдает один результирующий набор и завершает работу.  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 Выполните следующий скрипт на вкладке второго запроса. Этот скрипт создает один результирующий набор, а затем блокирует, ожидая получения блокировки `Production.Product` .  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 Выполните следующий скрипт на вкладке первого запроса. Этот скрипт блокирует, ожидая получения блокировки `Production.Location` . После короткого времени ожидания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберет этот скрипт или скрипт в образце в качестве жертвы взаимоблокировки и завершит транзакцию.  
  
```  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
```  
  
 После того как будет искусственно вызвана взаимоблокировка, подождите некоторое время, пока агент SQL Server активирует предупреждение и запустит задание. Проанализируйте содержимое таблицы `DeadlockEvents`, запустив следующий скрипт:  
  
```  
SELECT * FROM DeadlockEvents ;  
GO  
```  
  
 Столбец `DeadlockGraph` должен содержать XML-документ, который показывает все свойства события графа взаимоблокировок.  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о поставщике WMI для событий сервера](wmi-provider-for-server-events-concepts.md)  
  
  
