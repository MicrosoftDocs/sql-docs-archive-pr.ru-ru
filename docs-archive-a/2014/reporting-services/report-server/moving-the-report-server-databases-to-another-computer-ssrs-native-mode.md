---
title: Перемещение баз данных сервера отчетов на другой компьютер (службы SSRS в собственном режиме) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 44a9854d-e333-44f6-bdc7-8837b9f34416
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49fd35f57cf783b262b3c690e3047e5f479ab193
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727914"
---
# <a name="moving-the-report-server-databases-to-another-computer-ssrs-native-mode"></a>Перемещение баз данных сервера отчетов на другой компьютер (собственный режим служб SSRS)
  Можно переместить базы данных сервера отчетов, используемые при установке, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] в экземпляр служб, расположенный на другом компьютере. Базы данных reportserver и reportservertempdb должны перемещаться или копироваться вместе. Установка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требует наличия обеих баз данных. База данных reportservertempdb должна быть связана по имени с перемещаемой базой данных reportserver.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим.  
  
 Перемещение базы данных не влияет на запланированные операции, определенные в данный момент для элементов сервера отчетов.  
  
-   Расписания будут созданы повторно при первом перезапуске службы сервера отчетов.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующиеся для запуска расписания, будут созданы повторно в новом экземпляре базы данных. Необязательно перемещать эти задания на новый компьютер, однако следует удалить задания на компьютере, на котором они больше не будут использоваться.  
  
-   Подписки, кэшированные отчеты и моментальные снимки сохраняются в перемещенной базе данных. Если моментальный снимок не получает обновленные данные после перемещения базы данных, отмените параметры моментального снимка в диспетчере отчетов, нажмите кнопку **Применить** , чтобы сохранить изменения, повторно создайте расписание и еще раз нажмите кнопку **Применить** , сохранив изменения.  
  
-   Временные данные отчета и пользовательского сеанса, хранящиеся в базе данных reportservertempdb, при перемещении этой базы данных сохраняются.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусматривает несколько подходов к перемещению баз данных, включая резервное копирование и восстановление, присоединение и отсоединение, а также копирование. Не все из них пригодны для переноса существующей базы данных на новый экземпляр сервера. Подход, который следует использовать для перемещения базы данных сервера отчетов, зависит от требований к доступности системы. Наиболее простой способ перемещения баз данных сервера отчетов состоит в их отсоединении и присоединении. Однако такой подход требует, чтобы сервер отчетов во время отсоединения базы данных был переведен в режим «вне сети». Если нужно свести к минимуму перерывы в обслуживании, лучшим выбором будет резервное копирование и восстановление, хотя для выполнения этих операций потребуется запуск команд [!INCLUDE[tsql](../../includes/tsql-md.md)] . Не рекомендуется выполнять копирование базы данных (особенно с помощью мастера копирования базы данных), так как при этом в базе данных не сохраняются настройки разрешений.  
  
> [!IMPORTANT]  
>  Шаги, описанные в этом подразделе, следует выполнять только в том случае, если перемещение базы данных сервера отчетов является единственным изменением, которое вносится в текущую установку. При миграции всей установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (то есть для перемещения базы данных и изменения удостоверения службы Windows сервера отчетов, которая использует эту базу данных) необходима повторная настройка соединения и сброс ключа шифрования.  
  
## <a name="detaching-and-attaching-the-report-server-databases"></a>Отсоединение и присоединение баз данных сервера отчетов  
 Если сервер отчетов может быть переведен в режим «вне сети», можно отсоединить базы данных, чтобы переместить их на тот экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который требуется использовать. При таком подходе разрешения в базах данных сохраняются. Если используется база данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , необходимо переместить ее на другой экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . После перемещения баз данных следует заново настроить соединение сервера отчетов с базой данных сервера отчетов. Если при масштабном развертывании запущено несколько серверов отчетов, необходимо заново настроить подключение к базе данных сервера отчетов для каждого сервера отчетов, входящего в конфигурацию.  
  
 Для перемещения баз данных выполните следующие шаги:  
  
1.  Создайте резервную копию ключей шифрования для перемещаемой базы данных. Для этого можно использовать программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Остановите службу сервера отчетов. Для этого можно использовать программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
3.  Запустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и откройте соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляром, на котором размещены базы данных сервера отчетов.  
  
4.  Щелкните правой кнопкой мыши базу данных сервера отчетов, укажите пункт "Задачи" и выберите команду **Отсоединить**. Повторите этот шаг для временной базы данных сервера отчетов.  
  
5.  Скопируйте или переместите MDF- и LDF-файлы в папку данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который необходимо использовать. Поскольку осуществляется перемещение двух баз данных, удостоверьтесь, что скопированы или перемещены все четыре файла.  
  
6.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]установите соединение с новым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором будут размещены базы данных сервера отчетов.  
  
7.  Щелкните правой кнопкой мыши узел "Базы данных" и выберите пункт **Присоединить**.  
  
8.  Нажмите кнопку **Добавить** , чтобы выбрать MDF- и LDF-файлы базы данных сервера отчетов, которые следует присоединить. Повторите этот шаг для временной базы данных сервера отчетов.  
  
9. После присоединения баз данных убедитесь, что `RSExecRole` является ролью базы данных в базе данных сервера отчетов и временной базой данных. `RSExecRole`в таблицах базы данных сервера отчетов должны быть установлены разрешения SELECT, INSERT, Update, DELETE и Reference, а также разрешения на выполнение хранимых процедур. Дополнительные сведения см. в разделе [Создание RSExecRole](../security/create-the-rsexecrole.md).  
  
10. Запустите программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и соединитесь с сервером отчетов.  
  
11. На странице «База данных» выберите новый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и нажмите кнопку **Соединить**.  
  
12. Выберите вновь перемещенную базу данных сервера отчетов и нажмите кнопку **Применить**.  
  
13. На странице «Ключи шифрования» нажмите кнопку «Восстановить». Укажите файл, содержащий резервную копию ключей и пароль для разблокирования этого файла.  
  
14. Перезапустите службу сервера отчетов.  
  
## <a name="backing-up-and-restoring-the-report-server-databases"></a>Резервное копирование и восстановление из копии баз данных сервера отчетов  
 Если сервер отчетов нельзя перевести в режим «вне сети», для перемещения его баз данных можно использовать резервное копирование и восстановление. Чтобы выполнить резервное копирование и восстановление, необходимо использовать инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] . После восстановления баз данных следует настроить сервер отчетов, чтобы он использовал базу данных на новом экземпляре сервера. Дополнительные сведения см. в инструкциях, приведенных в конце этого подраздела.  
  
### <a name="using-backup-and-copy_only-to-backup-the-report-server-databases"></a>Использование для резервного копирования баз данных сервера отчетов инструкций BACKUP и COPY_ONLY  
 При резервном копировании баз данных установите аргумент COPY_ONLY. Убедитесь, что создаются резервные копии как баз данных, так и файлов журналов.  
  
```  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServer  
   SET RECOVERY FULL  
  
-- If the ReportServerData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerData',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerData.bak'  
  
-- Create a logical backup device, ReportServerLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerLog.bak'  
  
-- Back up the full ReportServer database.  
BACKUP DATABASE ReportServer  
   TO ReportServerData  
   WITH COPY_ONLY  
  
-- Back up the ReportServer log.  
BACKUP LOG ReportServer  
   TO ReportServerLog  
   WITH COPY_ONLY  
  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServerTempdb  
   SET RECOVERY FULL  
  
-- If the ReportServerTempDBData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBData',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBData.bak'  
  
-- Create a logical backup device, ReportServerTempDBLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBLog.bak'  
  
-- Back up the full ReportServerTempDB database.  
BACKUP DATABASE ReportServerTempDB  
   TO ReportServerTempDBData  
   WITH COPY_ONLY  
  
-- Back up the ReportServerTempDB log.  
BACKUP LOG ReportServerTempDB  
   TO ReportServerTempDBLog  
   WITH COPY_ONLY  
```  
  
### <a name="using-restore-and-move-to-relocate-the-report-server-databases"></a>Использование для перемещения баз данных сервера отчетов инструкций RESTORE и MOVE  
 При восстановлении баз данных из копии обязательно включите аргумент MOVE, чтобы можно было указать путь. Для первоначального восстановления используйте аргумент NORECOVERY, это позволяет сохранить базу данных в состоянии RESTORING и даст время для просмотра резервных копий журналов, чтобы определить, какой из них следует восстанавливать. В качестве последнего шага следует повторить операцию RESTORE с аргументом RECOVERY.  
  
 В аргументе MOVE используется логическое имя файла данных. Чтобы определить логическое имя, выполните следующую инструкцию: `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`  
  
 Следующие примеры включают аргумент FILE, что позволяет указать позицию файла журнала, который требуется восстановить. Чтобы определить позицию файла, выполните следующую инструкцию: `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`  
  
 При восстановлении из копии файлов базы данных и журнала каждую операцию RESTORE следует выполнять отдельно.  
  
```  
-- Restore the report server database and move to new instance folder   
RESTORE DATABASE ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore the report server log file to new instance folder   
RESTORE LOG ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore and move the report server temporary database  
RESTORE DATABASE ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Restore the temporary database log file to new instance folder   
RESTORE LOG ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServer  
   WITH RECOVERY  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServerTempDB  
   WITH RECOVERY  
GO  
```  
  
### <a name="how-to-configure-the-report-server-database-connection"></a>Настройка подключения к базе данных сервера отчетов  
  
1.  Запустите диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и подключитесь к серверу отчетов.  
  
2.  На странице «База данных» нажмите кнопку **Изменить базу данных**. Щелкните **Далее**.  
  
3.  Щелкните **Выбрать существующую базу данных сервера отчетов**. Щелкните **Далее**.  
  
4.  Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором находится база данных сервера отчетов, и нажмите кнопку **Проверить соединение**. Щелкните **Далее**.  
  
5.  В поле «Имя базы данных» выберите нужную базу данных сервера отчета. Щелкните **Далее**.  
  
6.  В поле «Учетные данные» укажите учетные данные, которые сервер отчетов будет использовать для подключения к базе данных сервера отчетов. Щелкните **Далее**.  
  
7.  Нажмите кнопку **Далее** , затем — кнопку **Готово**.  
  
> [!NOTE]  
>  Установка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требует, чтобы экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] включал роль `RSExecRole`. Создание роли, регистрация имени входа и назначения ролей происходят, когда с помощью программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливается подключение к базе данных сервера отчетов. При иных подходах к настройке соединения (особенно если используется программа командной строки rsconfig.exe) сервер отчетов окажется в неработоспособном состоянии. Чтобы сервер отчетов стал доступным, возможно, придется записать код инструментария WMI. Дополнительные сведения см. в разделе [Доступ к поставщику WMI для служб Reporting Services](../tools/access-the-reporting-services-wmi-provider.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание роли RSExecRole](../security/create-the-rsexecrole.md)   
 [Запуск и остановка службы сервера отчетов](start-and-stop-the-report-server-service.md)   
 [Настройка подключения к базе данных сервера отчетов &#40;службы SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Настройка учетной записи автоматического выполнения &#40;Configuration Manager SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Программа rsconfig &#40;службы SSRS&#41;](../tools/rsconfig-utility-ssrs.md)   
 [Настройка ключей шифрования и управление ими &#40;служб SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)   
 [База данных сервера отчетов (службы Reporting Services в собственном режиме)](report-server-database-ssrs-native-mode.md)  
  
  
