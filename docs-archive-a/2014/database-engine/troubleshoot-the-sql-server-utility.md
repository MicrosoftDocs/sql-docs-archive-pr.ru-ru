---
title: Устранение неполадок служебная программа SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3c139f9f084374aeb711e905ac0c315acc25c6ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735534"
---
# <a name="troubleshoot-the-sql-server-utility"></a>Устранение неполадок служебной программы SQL Server
  При устранении неполадок служебной программы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может понадобиться устранить причину ошибок при регистрации экземпляра SQL Server в пункте управления программой, устранить неполадки, связанные с ошибками при сборе данных и вызывающие отображение серых значков в представлении списка управляемых экземпляров в пункте управления программой, устранить «узкие места» производительности или разрешить проблемы, связанные с исправностью ресурсов. Дополнительные сведения об устранении проблем с работоспособностью ресурсов, обнаруженных в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] точке управления служебной программой, см. в разделе [Устранение неполадок SQL Server Работоспособность ресурсов &#40;служебная программа SQL Server&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a>Неудачная операция регистрации экземпляра SQL Server в служебной программе SQL Server  
 Если при подключении к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для регистрации используется проверка подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , а указанная при этом учетная запись-посредник принадлежит домену Active Directory, отличному от домена, в котором находится пункт управления программой, то проверка экземпляра завершится успешно, но во время операции регистрации произойдет ошибка и отобразится следующее сообщение об ошибке:  
  
 Возникло исключение при выполнении пакета или инструкции Transact-SQL. (Microsoft.SqlServer.ConnectionInfo)  
  
 Дополнительные сведения:  Не удалось получить сведения о пользователе/группе Windows NT «\<DomainName\AccountName>», код ошибки 0x5. (Microsoft SQL Server, ошибка: 15404)  
  
 Например, эта проблема может возникнуть в следующих сценариях.  
  
1.  Пункт управления программой входит в «Домен_1».  
  
2.  Между доменами существует одностороннее отношение доверия, то есть «Домен_1» не является доверенным для «Домен_2», но «Домен_2» является доверенным для «Домен_1».  
  
3.  Экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , который следует зарегистрировать в служебной программе [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , также входит в «Домен_1».  
  
4.  Во время операции регистрации подключитесь к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для регистрации с помощью "SA". Укажите учетную запись-посредник из домена «Домен_2».  
  
5.  Проверка пройдет успешно, но при регистрации возникнет ошибка.  
  
 Чтобы решить эту проблему, используйте приведенный выше пример, чтобы подключиться к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для регистрации в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] программе с помощью "SA" и предоставить учетную запись-посредник из "Domain_1".  
  
## <a name="failed-wmi-validation"></a>Сбой проверки WMI  
 Если в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]WMI настроена неправильно, то при операциях создания пункта управления программой и регистрации управляемого экземпляра будет отображаться предупреждение, но операция не будет прервана. Кроме того, при изменении настройки учетной записи агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] таким образом, что у агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] будут отсутствовать разрешения на доступ к требуемым классам WMI, передача собираемых данных из затронутого изменением управляемого экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в пункте управления программой прекратится. В результате в пункте управления программой будет отображаться серый значок.  
  
 Сбой при сборе данных вызывает отображение серых значков состояния в списке пункта управления программой для затронутых управляемых экземпляров [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Из журнала выполняемых заданий на управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] будет видно, что в sysutility_mi_collect_and_upload происходит сбой на шаге 2 (сбор данных из скрипта PowerShell).  
  
 Возможны следующие сокращенные сообщения об ошибках.  
  
 Выполнение команды прервано, так как для переменной среды "ErrorActionPreference" установлено значение Stop: Access denied.  
  
 Ошибка: \<Date-time (MM/DD/YYYY HH:MM:SS)> : перехвачено исключение при сборе свойств ЦП.  Возможно, произошла ошибка запроса WMI.  ВНИМАНИЕ.  
  
 Чтобы устранить эту проблему, проверьте следующие параметры конфигурации.  
  
-   В Windows Server 2003 служебная учетная запись службы агента SQL Server должна быть членом группы наблюдения за производительностью Windows в управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Служба WMI в управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]должна быть включена и настроена.  
  
-   Возможно, репозиторий WMI на управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]поврежден.  
  
-   Возможно, библиотека производительности на управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]повреждена или отсутствует.  
  
 Чтобы проверить правильность настройки указанного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для передачи данных в пункт управления программой, убедитесь, что указанные ниже классы присутствуют на указанном экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]и доступны для учетной записи службы агента SQL Server.  
  
-   Win32_MountPoint  
  
-   Win32_PerfRawData_PerfProc_Process  
  
-   Win32_PerfRawData_PerfOS_Processor  
  
-   Win32_Processor  
  
-   Win32_Volume  
  
-   Win32_LogicalDisk  
  
 Проверить доступность каждого из классов можно, применив командлет PowerShell Get-WmiObject к этому классу. Выполните следующие командлеты в управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 Дополнительные сведения об устранении неполадок WMI см. на странице [Устранение неполадок WMI](https://go.microsoft.com/fwlink/?LinkId=178250). Обратите внимание, что запросы при этих операциях служебной программы SQL Server выполняются локально, поэтому сведения по удаленному устранению неполадок и устранению неполадок DCOM в таких случаях неприменимы.  
  
## <a name="failed-data-collection"></a>Сбой сбора данных  
 В случае неуспешного завершения событий сбора данных в служебной программе [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] возможны следующие решения:  
  
-   Не меняйте свойства набора элементов сбора "Сведения о программе" на управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], не включайте и не выключайте сбор данных вручную, так как сбор данных происходит под управлением задания агента программы.  
  
-   Сбой или отсутствие поддержки проверки WMI. Дополнительные сведения см. в подразделе «Сбой проверки WMI» этого раздела.  
  
-   Обновите данные в списке управляемых экземпляров, поскольку данные с точках просмотра служебной программы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не обновляются автоматически. Чтобы обновить данные, щелкните правой кнопкой мыши узел **Управляемые экземпляры** на панели навигации **Обозревателя программ** и выберите команду **Обновить**либо щелкните правой кнопкой мыши имя экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в представлении списка и выберите **Обновить**. Обратите внимание, что после регистрации экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в UCP до появления первых данных на панели мониторинга и точках просмотра панели содержимого обозревателя программ может пройти до 30 минут.  
  
-   С помощью диспетчера конфигурации SQL Server проверьте, что этот экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] работает.  
  
-   Если произошел сбой передачи или сбора данных в связи со временем ожидания, нужно обновить функцию dbo.fn_sysutility_mi_get_collect_script() в базе данных MSDB. В частности, в функцию «Invoke-BulkCopyCommand()» нужно добавить строку:  
  
    ```
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     По умолчанию время ожидания составляет 30 секунд.  
  
-   Если экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не кластеризован, проверьте, что служба агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] работает и настроена на автоматический запуск на UCP и управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Удостоверьтесь, что для выполнения сбора данных на управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]используется допустимая учетная запись. Например, срок действия пароля может истечь. Если срок действия пароля к учетной записи-посреднику истек, обновите пароль учетных данных в среде SSMS следующим образом.  
  
    1.  В **обозревателе объектов**среды SSMS разверните узел **Безопасность** , а затем узел **Учетные данные** .  
  
    2.  Щелкните правой кнопкой мыши **UtilityAgentProxyCredential_ \<GUID> ** и выберите пункт **Свойства**.  
  
    3.  В диалоговом окне Свойства учетных данных обновите учетные данные, необходимые для **UtilityAgentProxyCredential_ \<GUID> ** учетных данных.  
  
    4.  Нажмите кнопку **ОК**, чтобы подтвердить изменение.  
  
-   В пункте управления программой и управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]должен быть включен протокол TCP/IP. Включите протокол TCP/IP с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Служба обозревателя SQL Server должна быть запущена на UCP и настроена для автоматического запуска. Если в организации запрещено использование службы обозревателя SQL Server, то для обеспечения подключения управляемого экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] к UCP выполните следующие действия.  
  
    1.  На панели задач Windows на управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] нажмите кнопку **Пуск**и выберите команду **выполнить...**.  
  
    2.  Введите «cliconfg.exe» в соответствующем поле и нажмите кнопку **ОК**.  
  
    3.  При запросе разрешить запуск «Средства настройки клиента SQL» нажмите кнопку**Продолжить**.  
  
    4.  В диалоговом окне **SQL Server клиентская сетевая программа** » перейдите на вкладку **псевдоним** и нажмите кнопку **Добавить...**.  
  
    5.  В диалоговом окне **Добавление конфигурации сетевой библиотеки** .  
  
    6.  В списке сетевых библиотек укажите TCP/IP.  
  
    7.  В текстовом поле **Псевдоним сервера** укажите «ИмяКомпьютера\ИмяЭкземпляра UCP».  
  
    8.  В текстовом поле **Имя сервера** укажите «ИмяКомпьютера UCP».  
  
    9. Снимите флажок **Определять порт динамически** .  
  
    10. В текстовом поле **Номер порта** укажите номер порта, который прослушивает UCP.  
  
    11. Нажмите кнопку **ОК** , чтобы сохранить внесенные изменения.  
  
    12. Повторите эти действия для каждого управляемого экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , который подключается к UCP при выключенной службе обозревателя SQL Server.  
  
-   Управляемые экземпляры [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] должны быть подключены к сети.  
  
-   При наличии на управляемом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]баз данных с таким же именем, но другими параметрами учета регистра идентификация между базой данных и ее точками просмотра может быть неверной, в результате чего могут возникнуть ошибки при сборе данных. Например, база данных «МОЯБАЗАДАННЫХ» может показывать состояния исправности базы данных «МояБазаДанных». В этом сценарии ошибки не формируются. Ошибки при сборе данных также могут возникнуть при несоответствиях учета регистра и в других отображаемых в пункте управления программой объектах, таких как имена файлов баз данных и групп файлов.  
  
-   Если управляемый экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] расположен на компьютере под управлением Windows Server 2003, то учетная запись службы агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] должна входить в группу безопасности пользователей системного монитора или группу локальных администраторов. В противном случае сбор данных выполнить не удастся из-за отказа в доступе. Чтобы добавить учетную запись службы агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в группу безопасности пользователей системного монитора, выполните следующие действия.  
  
    1.  Откройте оснастку **Управление компьютером**, затем **Локальные пользователи и группы**, выберите **Группы**.  
  
    2.  Щелкните правой кнопкой мыши **Пользователи системного монитора** и выберите **Добавить в группу**.  
  
    3.  Нажмите кнопку **Добавить**.  
  
    4.  Введите учетную запись, под которой работает служба агента SQL Server, и нажмите кнопку **ОК**.  
  
    5.  Если экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] уже был зарегистрирован в UCP до добавления пользователя в эту группу, перезапустите службу агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server)](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)