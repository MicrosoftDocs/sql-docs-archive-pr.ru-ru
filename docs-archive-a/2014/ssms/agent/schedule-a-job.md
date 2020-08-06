---
title: Планирование задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1077766d6853ed7c029b8eefa76515c89ad861fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731325"
---
# <a name="schedule-a-job"></a>Schedule a Job
  В этом разделе описан процесс составления расписания задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для планирования задания используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a>Создание и присоединение расписания к заданию  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , а затем разверните этот экземпляр.  
  
2.  Разверните узел **Агент SQL Server**, **Задания**, правой кнопкой мыши щелкните задание, для которого составляется расписание, и выберите **Свойства**.  
  
3.  Выберите страницу **Расписания** , затем нажмите **Создать**.  
  
4.  В поле **Имя** введите имя нового расписания.  
  
5.  Если расписание не должно вступать в силу немедленно после его создания, сбросьте флажок **Включено** .  
  
6.  Выберите одно из следующих значений для параметра **Тип расписания**:  
  
    -   Для запуска задания во время запуска службы агента **выберите элемент** Запускать автоматически при запуске агента SQL Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Для запуска задания, когда процессоры переходят в бездействующее состояние, щелкните **Запускать при бездействии процессоров** .  
  
    -   Если необходимо составить расписание для периодического выполнения, выберите **Повторяющееся задание** . Затем в диалоговом окне заполните группы **Частота**, **Сколько раз в день**и **Продолжительность** .  
  
    -   Если планируется однократное выполнение, выберите **Один раз** . Для установки расписания **Один раз** заполните в диалоговом окне группу **Однократное выполнение** .  
  
#### <a name="to-attach-a-schedule-to-a-job"></a>Присоединение расписания к заданию  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , а затем разверните этот экземпляр.  
  
2.  Разверните узел **Агент SQL Server**, **Задания**, правой кнопкой мыши щелкните задание, для которого составляется расписание, и выберите **Свойства**.  
  
3.  Выберите страницу **Расписания** и нажмите кнопку **Выбрать**.  
  
4.  Выберите расписание, которое нужно присоединить, и нажмите кнопку **ОК**.  
  
5.  В диалоговом окне **Свойства задания** дважды щелкните присоединенное расписание.  
  
6.  Убедитесь, что значение **Дата начала** настроено правильно. В противном случае установите дату начала расписания и нажмите кнопку **ОК**.  
  
7.  В диалоговом окне **Свойства задания** нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-schedule-a-job"></a>Планирование задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в статьях [sp_add_schedule &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) и [sp_attach_schedule &#40;transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql).  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  
 Воспользуйтесь классом `JobSchedule` в любом языке программирования (Visual Basic, Visual C# или PowerShell). Дополнительные сведения см. в разделе[Управляющие объекты SQL Server](https://msdn.microsoft.com/library/ms162169.aspx).  
