---
title: Запуск, остановка, приостановка, возобновление и перезапуск ядро СУБД, агент SQL Server или службы обозреватель SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4b102c8fd81923d7386c8e556896e715311a07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738696"
---
# <a name="start-stop-pause-resume-restart-the-database-engine-sql-server-agent-or-sql-server-browser-service"></a>Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server
  В этом разделе описано, как запускать, останавливать, приостанавливать, возобновлять или перезапускать [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службу браузера с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , команды **net** из командной строки, [!INCLUDE[tsql](../../includes/tsql-md.md)] или PowerShell.  
  
-   **Перед началом работы**  
  
    -   [Что это за службы?](#Services)  
  
    -   [Дополнительная информация](#MoreInformation)  
  
    -   [Безопасность](#Security)  
  
-   **Инструкции по использованию:**  
  
    -   [Диспетчер конфигурации SQL Server](#SSCMProcedure)  
  
    -   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    -   [Команды NET из окна командной строки](#CommandPrompt)  
  
    -   [Transact-SQL](#TsqlProcedure)  
  
    -   [PowerShell](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="what-is-the-ssdenoversion-service-the-ssnoversion-agent-service-and-the-ssnoversion-browser-service"></a><a name="Services"></a> Что такое служба [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ?  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] являются исполняемыми программами, работающими в качестве служб Windows. Программы, запущенные в качестве служб Windows, работают, не проявляя никакой активности на экране компьютера.  
  
 **[!INCLUDE[ssDE](../../includes/ssde-md.md)]служеб**  
 Исполняемый процесс, который представляет собой компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. [!INCLUDE[ssDE](../../includes/ssde-md.md)] может быть экземпляром по умолчанию (может быть только один на одном компьютере) либо может быть одним из нескольких именованных экземпляров [!INCLUDE[ssDE](../../includes/ssde-md.md)]. С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определите, какие экземпляры [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлены на компьютере. Экземпляр по умолчанию (если он установлен) указан как ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)**. Именованные экземпляры (если они установлены) перечислены как ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)**. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express устанавливается как ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)**.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Служба агента**  
 Служба Microsoft Windows, выполняющая запланированные административные задачи, которые называются заданиями и предупреждениями. Дополнительные сведения см. в статье [SQL Server Agent](../../ssms/agent/sql-server-agent.md). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступен не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Служба браузера**  
 Служба Windows, прослушивающая входящие запросы на ресурсы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и предоставляющая клиентам сведения об экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленных на компьютере. Один экземпляр службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется для всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленных на этом компьютере.  
  
###  <a name="additional-information"></a><a name="MoreInformation"></a>Дополнительные сведения  
  
-   Приостановка службы [!INCLUDE[ssDE](../../includes/ssde-md.md)] делает невозможным подключение новых пользователей к [!INCLUDE[ssDE](../../includes/ssde-md.md)], однако уже подключенные пользователи могут работать до тех пор, пока их соединения не будут разорваны. Приостановите работу службы, если нужно дождаться окончания работы пользователей, прежде чем совсем остановить службу. Это позволяет им завершить транзакции, которые в данный момент выполняются. Возобновление позволяет [!INCLUDE[ssDE](../../includes/ssde-md.md)] снова принимать входящие подключения. Службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нельзя приостановить или возобновить.  
  
-   Диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] отображают текущее состояние служб с помощью следующих значков.  
  
     **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager**  
  
    -   Зеленая стрелка на значке рядом с именем службы указывает на то, что служба запущена.  
  
    -   Красный квадрат на значке рядом с именем службы означает, что служба остановлена.  
  
    -   Пара вертикальных синих полосок на значке рядом с именем службы указывает на то, что служба приостановлена.  
  
    -   При перезапуске [!INCLUDE[ssDE](../../includes/ssde-md.md)]красный квадрат обозначает, что служба остановлена, затем зеленая стрелка покажет, что служба успешно запущена.  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   Белая стрелка на значке с зеленым кругом рядом с именем службы указывает на то, что служба запущена.  
  
    -   Белый квадрат на значке с красным кругом рядом с именем службы означает, что служба остановлена.  
  
    -   Пара вертикальных белых полосок на значке с синим кругом рядом с именем службы указывает, что служба приостановлена.  
  
-   При использовании диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]доступны только применимые параметры. Например, если служба уже запущена, **Пуск** будет недоступен.  
  
-   При эксплуатации на кластере службой [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] лучше всего управлять с помощью администратора кластера.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 По умолчанию только участники локальной группы «Администраторы» могут запускать, останавливать, приостанавливать, возобновлять или перезапускать службу. При необходимости предоставить возможность управления службой для пользователей, не обладающих правами администратора, см. раздел [Как предоставить пользователям права для управления службами в Windows Server 2003](https://support.microsoft.com/kb/325349). (Процесс такой же, как и в других версиях Windows.)  
  
 Для остановки с [!INCLUDE[ssDE](../../includes/ssde-md.md)] помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] `SHUTDOWN` команды требуется членство в предопределенных ролях сервера **sysadmin** или **serveradmin** , и он не может быть передан.  
  
##  <a name="using-ssnoversion-configuration-manager"></a><a name="SSCMProcedure"></a> С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a>Запуск, остановка, приостановка, возобновление или перезапуск экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
2.  В диалоговом окне **Контроль учетных записей** нажмите кнопку **Да**.  
  
3.  На левой панели диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] щелкните **Службы SQL Server**.  
  
4.  На панели результатов щелкните правой кнопкой мыши **SQL Server (MSSQLServer)** или именованный экземпляр, затем выберите **Пуск**, **Остановка**, **Пауза**, **Продолжить**или **Перезапуск**.  
  
5.  Нажмите кнопку **ОК** для выхода из диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Инструкции по запуску экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] с параметрами запуска см. в статье [Настройка параметров запуска сервера (диспетчер конфигурации SQL Server)](scm-services-configure-server-startup-options.md).  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-ssnoversion-browser-or-an-instance-of-the-ssnoversion-agent"></a>Запуск, остановка, приостановка, возобновление или перезапуск браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или экземпляра агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
2.  В диалоговом окне **Контроль учетных записей** нажмите кнопку **Да**.  
  
3.  На левой панели диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] щелкните **Службы SQL Server**.  
  
4.  В области результатов щелкните правой кнопкой мыши ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузер**или ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент (MSSQLServer)** или ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент (<instance_name>)** для именованного экземпляра, а затем выберите пункты **Пуск**, **остановить**, **приостановить**, **продолжить**или **перезапустить**.  
  
5.  Нажмите кнопку **ОК** для выхода из диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент приостановить нельзя.  
  
##  <a name="using-ssnoversion-management-studio"></a><a name="SSMSProcedure"></a> С помощью служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a>Запуск, остановка, приостановка, возобновление или перезапуск экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)], щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssDE](../../includes/ssde-md.md)] , который нужно запустить, и выберите **Пуск**, **Остановка**, **Пауза**, **Продолжить**или **Перезапустить**.  
  
     Либо в разделе "Зарегистрированные серверы" щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssDE](../../includes/ssde-md.md)] , который нужно запустить, наведите указатель на **Управление службами**и выберите **Пуск**, **Остановка**, **Пауза**, **Продолжить**или **Перезапустить**.  
  
2.  В диалоговом окне **Контроль учетных записей** нажмите кнопку **Да**.  
  
3.  При появлении запроса о необходимости выполнения действия нажмите кнопку **Да**.  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-ssnoversion-agent"></a>Запуск, остановка или перезапуск экземпляра агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  В обозревателе объектов подключитесь к экземпляру, щелкните [!INCLUDE[ssDE](../../includes/ssde-md.md)] правой кнопкой мыши ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент**, а затем выберите **запустить**, **Закрыть**или **перезапустить**.  
  
2.  В диалоговом окне **Контроль учетных записей** нажмите кнопку **Да**.  
  
3.  При появлении запроса о необходимости выполнения действия нажмите кнопку **Да**.  
  
##  <a name="from-the-command-prompt-window-using-net-commands"></a><a name="CommandPrompt"></a>Из окна командной строки с помощью команд net  
 Службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно запустить, остановить или приостановить с помощью команд **net**[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
###  <a name="to-start-the-default-instance-of-the-ssde"></a><a name="dbDefault"></a>Запуск экземпляра по умолчанию[!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   В командной строке введите одну из следующих команд:  
  
     **net start "SQL Server (MSSQLSERVER)"**  
  
     -или-  
  
     **net start MSSQLSERVER**  
  
###  <a name="to-start-a-named-instance-of-the-ssde"></a><a name="dbNamed"></a> Запуск именованного экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   В командной строке введите одну из следующих команд: Замените *\<instancename>* именем экземпляра, которым необходимо управлять.  
  
     **net start "SQL Server (** *имя_экземпляра* **)"**  
  
     -или-  
  
     **net start MSSQL$** *имя_экземпляра*  
  
###  <a name="to-start-the-ssde-with-startup-options"></a><a name="dbStartup"></a> Запуск [!INCLUDE[ssDE](../../includes/ssde-md.md)] с параметрами запуска  
  
-   Укажите разделенные пробелами параметры запуска в конце команды **net start "SQL Server (MSSQLSERVER)"** . При запуске с помощью команды **net start**в параметрах запуска используется косая черта (/), а не дефис (-).  
  
     **net start "SQL Server (MSSQLSERVER)" /f /m**  
  
     -или-  
  
     **net start MSSQLSERVER /f /m**  
  
    > [!NOTE]  
    >  Дополнительные сведения о параметрах запуска см. в разделе [Параметры запуска службы Database Engine](database-engine-service-startup-options.md).  
  
###  <a name="to-start-the-ssnoversion-agent-on-the-default-instance-of-ssnoversion"></a><a name="agDefault"></a> Запуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   В командной строке введите одну из следующих команд:  
  
     **net start "SQL Server Agent (MSSQLSERVER)"**  
  
     -или-  
  
     **net start SQLSERVERAGENT**  
  
###  <a name="to-start-the-ssnoversion-agent-on-a-named-instance-of-ssnoversion"></a><a name="agNamed"></a> Перезапуск агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на именованном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   В командной строке введите одну из следующих команд: Замените *имя_экземпляра* именем экземпляра, которым необходимо управлять.  
  
     **net start "SQL Server Agent(** *имя_экземпляра* **)"**  
  
     -или-  
  
     **net start SQLAgent$** *имя_экземпляра*  
  
 Сведения о запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в подробном режиме для устранения неполадок см. в статье [sqlagent90 Application](../../tools/sqlagent90-application.md).  
  
###  <a name="to-start-the-ssnoversion-browser"></a><a name="Browser"></a> Запуск браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   В командной строке введите одну из следующих команд:  
  
     **net start "SQL Server Browser"**  
  
     -или-  
  
     **net start SQLBrowser**  
  
###  <a name="to-pause-or-stop-services-from-the-command-prompt-window"></a><a name="pauseStop"></a> Приостановка или остановка служб из окна командной строки  
  
-   Чтобы приостановить или остановить службы, измените команды следующими способами.  
  
    -   Чтобы приостановить службу, вместо **net start** введите **net pause**.  
  
    -   Чтобы остановить службу, вместо **net start** введите **net stop**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно остановить с помощью инструкции `SHUTDOWN`.  
  
#### <a name="to-stop-the-ssde-using-tsql"></a>Остановка [!INCLUDE[ssDE](../../includes/ssde-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
-   Чтобы дождаться завершения запущенных в настоящий момент инструкций и хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] с последующей остановкой [!INCLUDE[ssDE](../../includes/ssde-md.md)], выполните следующую инструкцию.  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   Чтобы остановить [!INCLUDE[ssDE](../../includes/ssde-md.md)] немедленно, выполните следующую инструкцию.  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 Дополнительные сведения об `SHUTDOWN` инструкции см. в разделе [Shutdown &#40;TRANSACT-SQL&#41;](/sql/t-sql/language-elements/shutdown-transact-sql).  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
  
#### <a name="to-start-and-stop-ssde-services"></a>Запуск и остановка служб [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
1.  В окне командной строки запустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell с помощью следующей команды.  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  В окне командной строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell путем выполнения следующей команды. Замените `computername` именем нужного компьютера.  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (Get-Item .).ManagedComputer
    ```  
  
3.  Определите службу, которую нужно остановить или запустить. Выберите одну из следующих строк. Замените `instancename` именем именованного экземпляра.  
  
    -   Получение ссылки на экземпляр [!INCLUDE[ssDE](../../includes/ssde-md.md)]по умолчанию.  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   Получение ссылки на именованный экземпляр [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   Получение ссылки на службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на экземпляре [!INCLUDE[ssDE](../../includes/ssde-md.md)]по умолчанию.  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   Получение ссылки на службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на именованном экземпляре [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   Получение ссылки на службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  Завершите пример, чтобы запустить и затем остановить выбранную службу.  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Запуск SQL Server с минимальной конфигурацией](start-sql-server-with-minimal-configuration.md)   
 [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
