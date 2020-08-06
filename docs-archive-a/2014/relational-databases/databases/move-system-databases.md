---
title: Перемещение системных баз данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- moving system databases
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- tempdb database [SQL Server], moving
- system databases [SQL Server], moving
- scheduled disk maintenace [SQL Server]
- moving databases
- msdb database [SQL Server], moving
- moving database files
- relocating database files
- planned database relocations [SQL Server]
- master database [SQL Server], moving
- model database [SQL Server], moving
- Resource database [SQL Server]
- databases [SQL Server], moving
ms.assetid: 72bb62ee-9602-4f71-be51-c466c1670878
author: stevestein
ms.author: sstein
ms.openlocfilehash: 748d781d6bbefb0dc710427a34ebd71ec7037fdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752227"
---
# <a name="move-system-databases"></a>Перемещение системных баз данных
  В этом разделе описано, как в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]перемещают системные базы данных. Эта операция может пригодиться в следующих ситуациях:  
  
-   Восстановление после сбоя. Например, база данных находится в подозрительном режиме, или ее работа была прекращена из-за сбоя оборудования;  
  
-   Плановое перемещение.  
  
-   Перемещение для запланированного обслуживания дисков.  
  
 Следующие процедуры применяются для перемещения файлов баз данных в пределах одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перемещение базы данных на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или на другой сервер возможно через операции [резервного копирования и восстановления](../backup-restore/back-up-and-restore-of-sql-server-databases.md) или [отсоединения и присоединения](move-a-database-using-detach-and-attach-transact-sql.md) .  
  
 Для выполнения процедур, описанных в данном разделе, необходимо логическое имя файлов базы данных. Это имя можно получить из столбца name представления каталога [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) .  
  
> [!IMPORTANT]  
>  При перемещении системной базы данных с последующим перестроением базы данных master необходимо заново переместить системную базу данных, поскольку операция перестроения устанавливает все системные базы данных в расположение по умолчанию.  
  
##  <a name="in-this-topic"></a><a name="Intro"></a>**В этом разделе**  
  
-   [Запланированное перемещение и запланированная процедура обслуживания диска](#Planned)  
  
-   [Процедура восстановления после сбоя](#Failure)  
  
-   [Перемещение базы данных master](#master)  
  
-   [Перемещение базы данных Resource](#Resource)  
  
-   [Дальнейшие действия. После перемещения всех системных баз данных](#Follow)  
  
-   [Примеры](#Examples)  
  
##  <a name="planned-relocation-and-scheduled-disk-maintenance-procedure"></a><a name="Planned"></a> Запланированное перемещение и процедура запланированного обслуживания диска  
 Чтобы переместить данные системной базы данных или файл журнала в рамках запланированного перемещения (операции запланированного обслуживания), следуйте следующим указаниям: Данная процедура применима ко всем системным базам данных, кроме master и Resource.  
  
1.  Для каждого перемещаемого файла выполните следующую инструкцию.  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
2.  Остановите работу экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или выключите систему для проведения работ по обслуживанию дисков. Дополнительные сведения см. в статье [Iniciar, parar, pausar, retomar e reiniciar os serviços SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
3.  Переместите файл или файлы в новое расположение.  
  
4.  Перезапустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или сервер. Дополнительные сведения см. в статье [Iniciar, parar, pausar, retomar e reiniciar os serviços SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
5.  Проверьте изменения в файле с помощью следующего запроса.  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
 Если база данных msdb перемещена, а экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для компонента [Database Mail](../database-mail/database-mail.md), выполните следующие дополнительные шаги.  
  
1.  С помощью следующего запроса убедитесь, что в базе данных msdb включен компонент [!INCLUDE[ssSB](../../../includes/sssb-md.md)] .  
  
    ```  
    SELECT is_broker_enabled   
    FROM sys.databases  
    WHERE name = N'msdb';  
    ```  
  
     Дополнительные сведения о включении [!INCLUDE[ssSB](../../../includes/sssb-md.md)]см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)перемещают системные базы данных.  
  
2.  Отправкой тестового сообщения проверьте работоспособность компонента Database Mail.  
  
##  <a name="failure-recovery-procedure"></a><a name="Failure"></a> Процедура восстановления после сбоя  
 Если нужно перенести файл из-за сбоя оборудования, необходимо выполнить приведенные ниже действия для его перемещения на новое место. Данная процедура применима ко всем системным базам данных, кроме master и Resource.  
  
> [!IMPORTANT]  
>  Если базу данных запустить нельзя, она находится в подозрительном режиме или в невосстановленном состоянии, то файл может быть перемещен только членом предопределенной роли sysadmin.  
  
1.  Остановите работу экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если он запущен.  
  
2.  Запустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме восстановления «только master», запустив из командной строки одну из следующих команд. В задаваемых для них параметрах учитывается регистр символов. Команды завершаются ошибкой, если параметры заданы не так, как показано.  
  
    -   В случае с экземпляром по умолчанию (MSSQLSERVER) запустите следующую команду:  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   В случае с именованным экземпляром запустите следующую команду:  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     Дополнительные сведения см. в статье [Iniciar, parar, pausar, retomar e reiniciar os serviços SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
3.  Для каждого перемещаемого файла используйте команды **sqlcmd** или [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] для выполнения следующей инструкции.  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
     Дополнительные сведения об использовании программы **sqlcmd** см. в статье [Использование программы sqlcmd](../scripting/sqlcmd-use-the-utility.md).  
  
4.  Завершите работу программы **sqlcmd** или [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
5.  Остановите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например, выполните команду `NET STOP MSSQLSERVER`.  
  
6.  Переместите файл или файлы в новое расположение.  
  
7.  Повторно запустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например, выполните команду `NET START MSSQLSERVER`.  
  
8.  Проверьте изменения в файле с помощью следующего запроса.  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
##  <a name="moving-the-master-database"></a><a name="master"></a> Перемещение базы данных master  
 Чтобы переместить базу данных master, выполните следующие действия.  
  
1.  В меню **Пуск** выберите **Все программы**, укажите **Microsoft SQL Server**, затем **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
2.  Находясь в узле **Службы SQL Server** , щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например **SQL Server (MSSQLSERVER)** , и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства SQL Server ( ***имя_экземпляра ***)** перейдите на вкладку **Параметры запуска** .  
  
4.  В поле **Существующие параметры** выберите параметр -d, чтобы переместить файл данных master. Нажмите **Обновить** для сохранения изменений.  
  
     В поле **Укажите параметр запуска** задайте новый путь к базе данных master.  
  
5.  В поле **Существующие параметры** выберите параметр -l, чтобы переместить файл журнала master. Нажмите **Обновить** для сохранения изменений.  
  
     В поле **Укажите параметр запуска** задайте новый путь к базе данных master.  
  
     Значение параметра для файла данных должно соответствовать параметру `-d` , а значение для файла журнала — параметру `-l` . В следующем примере показаны значения параметров для указания местоположения файла базы данных master по умолчанию.  
  
     `-dC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\master.mdf`  
  
     `-lC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\mastlog.ldf`  
  
     Если планируется переместить файл данных базы данных master в расположение `E:\SQLData`, значения параметра будут изменены следующим образом.  
  
     `-dE:\SQLData\master.mdf`  
  
     `-lE:\SQLData\mastlog.ldf`  
  
6.  Остановите работу экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , щелкнув правой кнопкой мыши имя экземпляра и выбрав команду **Остановить**.  
  
7.  Переместите файлы master.mdf и mastlog.ldf на новое место.  
  
8.  Повторно запустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
9. Проверьте правильность изменений для базы данных master, выполнив следующий запрос.  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID('master');  
    GO  
    ```  
  
##  <a name="moving-the-resource-database"></a><a name="Resource"></a> Перемещение базы данных Resource  
 База данных находится в каталоге \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\. Эту базу данных нельзя переместить.  
  
##  <a name="follow-up-after-moving-all-system-databases"></a><a name="Follow"></a> Дальнейшие действия. После перемещения всех системных баз данных  
 Если все системные базы данных перемещаются на новый диск или том либо на другой сервер с другой буквой диска, выполните следующие обновления.  
  
-   Измените путь к журналу агента SQL Server. Если этого не сделать, то агент SQL Server не сможет запуститься.  
  
-   Измените расположение по умолчанию для базы данных. Создание новой базы данных может завершиться ошибкой, если буква диска и путь, указанные в качестве места расположения по умолчанию, не существуют.  
  
#### <a name="change-the-sql-server-agent-log-path"></a>Измените путь к журналу агента SQL Server.  
  
1.  В среде SQL Server Management Studio в обозревателе объектов разверните узел **Агент SQL Server**.  
  
2.  Щелкните правой кнопкой мыши **Журналы ошибок** и выберите пункт **Настроить**.  
  
3.  В диалоговом окне **Настройка журналов ошибок агента SQL Server** задайте новое расположение для файла SQLAGENT.OUT. Расположение по умолчанию — C:\Program Files\Microsoft SQL Server\MSSQL12. <instance_name> \MSSQL\Log \\ .  
  
#### <a name="change-the-database-default-location"></a>Измените расположение по умолчанию для базы данных  
  
1.  В среде SQL Server Management Studio в обозревателе объектов щелкните правой кнопкой мыши сервер SQL Server и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Свойства сервера** выберите пункт **Настройки базы данных**.  
  
3.  На панели **Места хранения, используемые базой данных по умолчанию**можно просмотреть текущие места хранения, используемые по умолчанию для новых файлов данных и файлов журнала.  
  
4.  Остановите и запустите службу SQL Server, чтобы завершить изменение.  
  
##  <a name="examples"></a><a name="Examples"></a> Примеры  
  
### <a name="a-moving-the-tempdb-database"></a>A. Перемещение базы данных tempdb  
 В следующем примере показано перемещение файлов базы данных `tempdb` и журнала на новое место в рамках запланированного перемещения.  
  
> [!NOTE]  
>  Поскольку база данных tempdb создается повторно при каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то нет необходимости физически переносить файлы данных и журнала. Файлы создаются в новом месте во время перезагрузки службы на шаге 3. До перезагрузки службы база данных tempdb продолжает использовать файлы данных и файл журнала, расположенные в существующем месте.  
  
1.  Определение логических имен файлов базы данных `tempdb` и их текущего местоположения на диске.  
  
    ```  
    SELECT name, physical_name AS CurrentLocation  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    GO  
    ```  
  
2.  Измените местоположение каждого файла с помощью `ALTER DATABASE`.  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'F:\SQLLog\templog.ldf');  
    GO  
    ```  
  
3.  Остановите и перезапустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Проверьте изменение файла.  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    ```  
  
5.  Удалите файлы `tempdb.mdf` и `templog.ldf` из исходного местоположения.  
  
## <a name="see-also"></a>См. также:  
 [База данных Resource](resource-database.md)   
 [База данных tempdb](tempdb-database.md)   
 [База данных master](master-database.md)   
 [База данных msdb](msdb-database.md)   
 [База данных model](model-database.md)   
 [Перемещение пользовательских баз данных](move-user-databases.md)   
 [Перемещение файлов базы данных](move-database-files.md)   
 [Запуск, остановка, приостановка, возобновление и перезапуск ядра СУБД, агента SQL Server и обозревателя SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)   
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [Перестроение системных баз данных](system-databases.md)  
  
  
