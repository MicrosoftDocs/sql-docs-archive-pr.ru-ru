---
title: 'Контрольный список: использование PowerShell для проверки PowerPivot для SharePoint | Документация Майкрософт'
ms.custom: ''
ms.date: 07/20/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 73a13f05-3450-411f-95f9-4b6167cc7607
author: minewiskan
ms.author: owend
ms.openlocfilehash: 001b3fae82851b9ec08b0383bb3db9e6d011ae32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729958"
---
# <a name="checklist-use-powershell-to-verify-powerpivot-for-sharepoint"></a>Контрольный список: использование PowerShell для проверки PowerPivot для SharePoint
  Ни одна из операций установки или восстановления [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] не завершена без прохождения проверочного теста, который подтверждает работоспособность служб и данных. В этой статье рассказывается о том, как выполнить эти шаги с помощью Windows PowerShell. Каждому шагу посвящен отдельный подраздел с тем, чтобы можно было перейти непосредственно к конкретным задачам. Например, выполните скрипт, приведенный в подразделе [Базы данных](#bkmk_databases) этого раздела для проверки имени приложения службы и баз данных содержимого, если необходимо запланировать их для обслуживания или резервного копирования.

|||
|-|-|
|![Содержимое, связанное с PowerShell](../../../reporting-services/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")|Полный скрипт PowerShell приведен в конце раздела. Используйте полный скрипт в качестве отправной точки создания пользовательского скрипта для аудита полного развертывания [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] .|

||
|-|
|**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|

 **В этой статье**. Обозначенные буквами элементы в содержании соответствуют областям на схеме. На диаграмме показано:

|||
|-|-|
|[Подготовка среды PowerShell](#bkmk_prerequisites)<br /><br /> [Симптомы и рекомендуемые действия](#bkmk_symptoms)<br /><br /> **(A)** [Службы Analysis Services для Windows](#bkmk_windows_service)<br /><br /> **(Б)** [PowerPivotSystemService и PowerPivotEngineService](#bkmk_engine_and_system_service)<br /><br /> **(В)** [Приложения службы PowerPivot и прокси-серверы](#bkmk_powerpivot_service_application)<br /><br /> **(D)** [Базы данных](#bkmk_databases)<br /><br /> [Компоненты SharePoint](#bkmk_features)<br /><br /> [Задания таймера](#bkmk_timer_jobs)<br /><br /> [Правила определения исправности](#bkmk_health_rules)<br /><br /> **(E)** [Журналы Windows и ULS](#bkmk_logs)<br /><br /> [Поставщик MSOLAP](#bkmk_msolap)<br /><br /> [Клиентская библиотека ADOMD.Net](#bkmk_adomd)<br /><br /> [Правила сбора данных об исправности](#bkmk_health_collection)<br /><br /> [Решения](#bkmk_solutions)<br /><br /> [Действия по проверке вручную](#bkmk_manual)<br /><br /> [Дополнительные ресурсы](#bkmk_more_resources)<br /><br /> [Полный скрипт PowerShell](#bkmk_full_script)|![проверка powerpivot с помощью powershell](../../../sql-server/install/media/ssas-powershell-component-verification.png "проверка powerpivot с помощью powershell")|

##  <a name="prepare-your-powershell-environment"></a><a name="bkmk_prerequisites"></a> Подготовка среды PowerShell
 В этом разделе описаны действия по подготовке среды PowerShell. В зависимости от текущей конфигурации среды создания скриптов некоторые действия могут не потребоваться.

 **Разрешения PowerShell**

 Откройте окно Powershell или PowerShell ISE (интегрированная среда скриптов) с **правами администратора**. Если во время выполнения команд у вас не будет прав администратора, то появится сообщение об ошибке следующего вида:

 Get-SPLogEvent: для выполнения этого командлета необходимо иметь **права администратора** на компьютере.

 **SharePoint и модуль [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]**

 Если при запуске связанных с SharePoint командлетов отображается сообщение об ошибке, похожее на следующее, выполните команду Add-PSSnapin:

 Термин "Get-PowerPivotSystemService" **не распознан как имя командлета**, функции, файла скрипта или действующей программы. Проверьте правильность написания имени, а если включен путь, то проверьте правильность пути и повторите попытку.

```
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0
```

 **Windows PowerShell**

 Дополнительные сведения о PowerShell ISE см. в разделе [Общие сведения о Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx) и [Использование Windows PowerShell для администрирования SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx).

|||
|-|-|
|![набор приложений общего характера powerpivot в sharepoint](../../../sql-server/install/media/ssas-powerpivot-logo.png "набор приложений общего характера powerpivot в sharepoint")|При желании можно проверить большинство компонентов в центре администрирования с помощью панели управления [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Чтобы открыть панель мониторинга в центре администрирования, выберите **Общие параметры приложения**, а затем щелкните **Панель мониторинга управления** в **PowerPivot**. Дополнительные сведения о панели мониторинга см. в разделе [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).|

##  <a name="symptoms-and-recommended-actions"></a><a name="bkmk_symptoms"></a>Симптомы и рекомендуемые действия
 В следующей таблице приведен список симптомов или проблем и предложенный подраздел, в котором приведены сведения о том, как устранить данную проблему.

|Симптом|См. в разделе|
|-------------|-----------------|
|Обновление данных не выполняется|См. раздел [Timer Jobs](#bkmk_timer_jobs) и проверьте, что **Оперативное задание таймера обновления данных PowerPivot** находится в сети.|
|На панели мониторинга управления отображаются старые данные|См. раздел [Задания таймера](#bkmk_timer_jobs) и проверьте, что **панель управления заданием таймера обработки** включена.|
|Некоторые части панели мониторинга управления|При установке PowerPivot для SharePoint в ферму с такой топологией (центр администрирования без службы Excel Services или PowerPivot для SharePoint) необходимо загрузить и установить клиентскую библиотеку Microsoft ADOMD.NET, если требуется иметь полный доступ к встроенным на панели управления PowerPivot отчетам. Некоторые отчеты с панели мониторинга используют ADOMD.NET для доступа к внутренним данным, предоставляющим сведения об обработке запросов PowerPivot и исправности сервера в ферме. Дополнительные сведения см. в разделе [ADOMD.Net client Library](#bkmk_adomd) и в статье [Установка ADOMD.NET на веб-серверах, обслуживающих клиентские запросы, под управлением центра администрирования](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).|
|\<future content>||

##  <a name="analysis-services-windows-service"></a><a name="bkmk_windows_service"></a> Службы Analysis Services для Windows
 Приведенный в этом разделе скрипт проверяет экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Убедитесь, что служба **запущена**.

```powershell
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name              DisplayName                                Status
----              -----------                                ------
MSOLAP$POWERPIVOT SQL Server Analysis Services (POWERPIVOT) Running
```

##  <a name="powerpivotsystemservice-and-powerpivotengineservice"></a><a name="bkmk_engine_and_system_service"></a>PowerPivotSystemService и PowerPivotEngineService
 Приведенные в этом разделе скрипты проверяют системные службы [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] . Имеется одна системная служба для развертывания SharePoint 2013 и две для развертывания SharePoint 2010.

 **PowerPivotSystemService**

 Проверьте состояние "в **сети**".

```powershell
Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                  Status Applications                             Farm
--------                                  ------ ------------                             ----
SQL Server PowerPivot Service Application Online {Default PowerPivot Service Application} SPFarm Name=SharePoint_Config_77d8ab0744a34e8aa27c806a2b8c760c
```

 **PowerPivotEngineService**

> [!NOTE]
>  **Пропустите этот скрипт, если** используется SharePoint 2013. PowerPivotEngineService не входит в развертывание SharePoint 2013. При выполнении командлета Get-PowerPivot службы**Engine**Service в SharePoint 2013 откроется сообщение об ошибке примерно следующего содержания. Это сообщение об ошибке возвращается, даже если запущена команда PSSnapin, описанная в разделе предварительных требований этого раздела.
> 
>  Термин «Get-PowerPivotEngineService» не распознан в качестве имени командлета

 В развертывании SharePoint 2010 состояние должно быть **В сети**.

```powershell
Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName  : SQL Server Analysis Services
Status    : Online
Name      : MSOLAP$POWERPIVOT
Instances : {POWERPIVOT}
Farm      : SPFarm Name=SharePoint_Config
```

##  <a name="powerpivot-service-applications-and-proxies"></a><a name="bkmk_powerpivot_service_application"></a>Приложения службы PowerPivot и прокси-серверы
 Состояние должно быть **В сети**. Приложение служб Excel не использует базы данных приложения службы, поэтому командлет не возвращает имя базы данных. Запишите базу данных, которая используется приложением службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , чтобы можно было удостовериться в том, что она находится в сети в подразделе базы данных далее в этом разделе.

 **Приложение службы PowerPivot и Excel**

 В развертывании SharePoint 2010 состояние должно быть **В сети**.

```powershell
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename, DisplayName, status
```

```Output
TypeName          : PowerPivot Service Application
Name              : PowerPivotServiceApplication1
Status            : Online
UnattendedAccount : PowerPivotUnattendedAccount
ApplicationPool   : SPIisWebServiceApplicationPool Name=sqlbi_serviceapp
Farm              : SPFarm Name=SharePoint_Config
Database          : GeminiServiceDatabase Name=PowerPivotServiceApplication1_19648f3f2c944e27acdc6c20aab8487a

TypeName    : Excel Services Application Web Service Application
DisplayName : Excel Services Application
Status      : Online
```

 **Пул приложений службы**

> [!NOTE]
>  Следующий образец кода сначала возвращает свойство applicationpool приложения службы [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] по умолчанию. Имя анализируется из строки и используется для получения сведений о состоянии объекта пула приложений.
> 
>  Проверьте состояние "в **сети**". Если состояние находится не в сети или отображается сообщение "ошибка HTTP" при просмотре [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] сайта, убедитесь, что учетные данные удостоверения в пулах приложений IIS все еще верны. Имя пула приложений IIS — это значение свойства идентификатора, возвращаемого командой Get-SPServiceApplicationPool.

```powershell
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)

Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                           Status ProcessAccountName Id
----                           ------ ------------------ ------- 
SharePoint Web Services System Online DOMAIN\account     89b50ec3-49e3-4de7-881a-2cec4b8b73ea
```

 ![Примечание](../../../reporting-services/media/rs-fyinote.png "Примечание.") . Пул приложений также можно проверить на странице центра администрирования **Управление приложениями служб**. Щелкните имя приложения службы, затем нажмите кнопку **Свойства** на ленте.

 **Прокси-серверы приложения службы PowerPivot и Excel**

 Проверьте состояние "в **сети**".

```powershell
Get-SPServiceApplicationProxy | Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -Like "*powerpivot*" -Or $_.TypeName -Like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                                 Status UnattendedAccount           DisplayName
--------                                                 ------ -----------------           -----------
PowerPivot Service Application Proxy                     Online PowerPivotUnattendedAccount PowerPivotServiceApplication1
Excel Services Application Web Service Application Proxy Online                             Excel Services Application
```

##  <a name="databases"></a><a name="bkmk_databases"></a> Базы данных
 Следующий скрипт возвращает состояние баз данных приложений служб и все базы данных содержимого. Состояние должно быть **В сети**.

```powershell
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -Or $_.TypeName -Like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                                                                       Status Server                  TypeName 
----                                                                       ------ ------                  -------- 
DefaultPowerPivotServiceApplicationDB-38422181-2b68-4ab2-b2bb-9c00c39e5a5e Online SPServer Name=TESTSERVER Microsoft.AnalysisServices.SPAddin.GeminiServiceDatabase
DefaultWebApplicationDB-f0db1a8e-4c22-408c-b9b9-153bd74b0312               Online TESTSERVER\POWERPIVOT    Content Database 
SharePoint_Admin_3cadf0b098bf49e0bb15abd487f5c684                          Online TESTSERVER\POWERPIVOT    Content Database
```

##  <a name="sharepoint-features"></a><a name="bkmk_features"></a>Функции SharePoint
 Убедитесь в том, что компоненты сайта, сети и фермы находятся в сети.

```powershell
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
DisplayName     Status Scope Farm                         
-----------     ------ ----- ----                         
PowerPivotSite  Online  Site SPFarm Name=SharePoint_Config
PowerPivotAdmin Online   Web SPFarm Name=SharePoint_Config
PowerPivot      Online  Farm SPFarm Name=SharePoint_Config
```

##  <a name="timer-jobs"></a><a name="bkmk_timer_jobs"></a>Задания таймера
 Убедитесь в том, что задания таймера находятся **В сети**. Служба [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService не установлена на сервере SharePoint 2013, поэтому скрипт не сформирует список заданий таймера EngineService в развертывании SharePoint 2013.

```powershell
Get-SPTimerJob | Where {$_.service -Like "*power*" -Or $_.service -Like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default
```

```Output
      Status DisplayName                                                                          LastRunTime          Service                             
------ -----------                                                                          -----------          -------                             
Online Health Analysis Job (Daily, SQL Server Analysis Services, All Servers)               4/9/2014 12:00:01 AM EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Hourly, SQL Server Analysis Services, All Servers)              4/9/2014 1:00:01 PM  EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Weekly, SQL Server Analysis Services, All Servers)              4/6/2014 12:00:10 AM EngineService Name=MSOLAP$POWERPIVOT
Online PowerPivot Management Dashboard Processing Timer Job                                 4/8/2014 3:45:38 AM  MidTierService
Online PowerPivot Health Statistics Collector Timer Job                                     4/9/2014 1:00:12 PM  MidTierService
Online PowerPivot Data Refresh Timer Job                                                    4/9/2014 1:09:36 PM  MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, All Servers)  4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, Any Server)   4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, All Servers) 4/6/2014 12:00:03 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, Any Server)  4/6/2014 12:00:03 AM MidTierService
Online PowerPivot Setup Extension Timer Job                                                 4/1/2014 1:40:31 AM  MidTierService
```

##  <a name="health-rules"></a><a name="bkmk_health_rules"></a>Правила определения исправности
 В развертывании SharePoint 2013 меньше правил. Полный список правил для каждой среды SharePoint и объяснение использования правил см. в разделе [PowerPivot Health Rules-configure](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md).

```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                          Enabled Summary
----                          ------- -------         
SecondaryLogonHealthRule         True PowerPivot:  Secondary Logon service (seclogon) is disabled
DataRefreshTimerJobHealthRule    True PowerPivot: The PowerPivot Data Refresh timer job is disabled.
ASUsageLoadHealthRule            True PowerPivot: The ratio of load events to connections is too high.
ASMiniDumpHealthRule             True PowerPivot: One or more minidump files were found in the Logs directory, indicating a program crash
ASUsageCubeRule                  True PowerPivot: Usage data is not getting updated at the expected frequency.
ASADOMDNETHealthRule             True PowerPivot: ADOMD.NET is not installed on a standalone WFE that is configured for central admin
MidTierAcctReadPermissionRule    True PowerPivot: MidTier process account should have 'Full Read' permission on all associated SPWebApplications.
```

##  <a name="windows-and-uls-logs"></a><a name="bkmk_logs"></a>Журналы Windows и ULS
 **Журнал событий Windows**

 Следующая команда выполняет поиск в журнале событий Windows событий, связанных с экземпляром [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме SharePoint. Сведения об отключении событий или изменении уровня событий см. в разделе [Настройка и просмотр файлов журнала SharePoint и журнала диагностики &#40;PowerPivot для SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md).

 **Имя службы:** MSOLAP$POWERPIVOT.

 **Отображаемое имя в службах Windows:** SQL Server Analysis Services (POWERPIVOT).

```powershell
Get-EventLog "application" | Where-Object {$_.source -Like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -property * -AutoSize | Out-Default
```

```Output
TimeGenerated           EntryType Source            Message
-------------           --------- ------            -------
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Service started. Microsoft SQL Server Analysis Services 64 Bit Evaluation (x64) RTM 12.0.1997.5.
4/16/2014 1:45:18 PM  Information MSOLAP$POWERPIVOT The flight recorder was started.
4/14/2014 6:45:37 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
```

 **Журнал ULS SharePoint, последние 48 часов**

 Следующая команда возвращает сообщения [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] из журнала ULS, созданные за последние 48 часов. Настройте параметр addhours в соответствии со своими требованиями.

```powershell
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid,level, message | Format-Table -Property * -AutoSize | Out-Default
```

 Следующий вариант команды возвращает из журнала только события категории **обновление данных** .

```powershell
Get-SPLogEvent -starttime(Get-Date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message
```

```Output
Timestamp   : 4/14/2014 7:15:01 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 43
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : The following error occurred when working with the service application, Default PowerPivot Service Application. Skipping the service application..

Timestamp   : 4/14/2014 7:15:02 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 99
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : EXCEPTION: System.TimeoutException: The request channel timed out while waiting for a reply after 00:00:47.0625313. Increase the timeout value passed to 
              the call to Request or increase the SendTimeout value on the Binding. The time allotted to this operation may have been a portion of a longer timeout. 
              ---> System.TimeoutException: The HTTP request to 'http://localhost:32843/SecurityTokenServiceApplication/securitytoken.svc/actas' has exceeded the 
              allotted timeout of 00:00:54.5930000. The time allotted to this operation may have been a portion of a longer timeout. ---> System.Net.WebException: The 
              operation has timed out     at System.Net.HttpWebRequest.GetResponse()     at 
              System.ServiceModel.Channels.HttpChannelFactory`1.HttpRequestChannel.HttpChannelRequest.WaitForReply(TimeSpan timeout...
```

##  <a name="msolap-provider"></a><a name="bkmk_msolap"></a>Поставщик MSOLAP
 Проверьте поставщик MSOLAP. [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]и [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] требует MSOLAP. 5.

```powershell
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default
```

```Output
ProviderId ProviderType Description
---------- ------------ -----------
MSOLAP     Oledb        Microsoft OLE DB Provider for OLAP Services     
MSOLAP.3   Oledb        Microsoft OLE DB Provider for OLAP Services 9.0 
MSOLAP.4   Oledb        Microsoft OLE DB Provider for OLAP Services 10.0
MSOLAP.5   Oledb        Microsoft OLE DB Provider for OLAP Services 11.0
```

 Дополнительные сведения см. в статьях [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) и [Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services](https://technet.microsoft.com/library/hh758436.aspx).

##  <a name="adomdnet-client-library"></a><a name="bkmk_adomd"></a>Клиентская библиотека ADOMD.Net

```powershell
Get-WMIObject -Class win32_product | Where-Object {$_.name -Like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | out-default
```

```Output
name                                                  version      vendor
----                                                  -------      ------
Microsoft SQL Server 2008 Analysis Services ADOMD.NET 10.1.2531.0  Microsoft Corporation
Microsoft SQL Server 2005 Analysis Services ADOMD.NET 9.00.1399.06 Microsoft Corporation
```

 Дополнительные сведения можно найти в статье [Установка ADOMD.NET на веб-серверах, обслуживающих клиентские запросы, под управлением центра администрирования](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).

##  <a name="health-data-collection-rules"></a><a name="bkmk_health_collection"></a>Правила сбора данных о работоспособности
 Убедитесь в том, что в поле **Состояние** указано значение «В сети», а в поле **Включен** — значение True.

```powershell
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -Like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                         Status Enabled TableName                   DaysToKeepDetailedData
----                         ------ ------- ---------                   ----------------------
PowerPivot Connections       OnlineTrue AnalysisServicesConnections  14
PowerPivot Load Data Usage   Online    True AnalysisServicesLoads                           14
PowerPivot Query Usage       Online    True AnalysisServicesRequests                        14
PowerPivot Unload Data Usage Online    True AnalysisServicesUnloads                         14
```

 Дополнительные сведения см. в статье [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md).

##  <a name="solutions"></a><a name="bkmk_solutions"></a>Решения
 Если другие компоненты находятся в сети, то проверку решений можно пропустить. Однако, если правила определения исправности отсутствуют, убедитесь в том, что существует два решения PowerPivot и при этом они имеют состояние **В сети** и **Развернуто**.

```powershell
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

SharePoint 2013.

```Output
Name                                 Status Deployed        DeploymentState DeployedServers
----                                 ------ --------        --------------- ---------------
powerpivotfarm14solution.wsp         Online     True         GlobalDeployed {UETESTA00}
powerpivotfarmsolution.wsp           Online     True         GlobalDeployed {UETESTA00}
powerpivotwebapplicationsolution.wsp Online     True WebApplicationDeployed {UETESTA00}
```

SharePoint 2010.

```Output
Name                 Status Deployed        DeploymentState DeployedServers 
----                 ------ --------        --------------- --------------- 
powerpivotfarm.wsp   Online     True         GlobalDeployed {uesql11spoint2}
powerpivotwebapp.wsp Online     True WebApplicationDeployed {uesql11spoint2}
```

 Дополнительные сведения о развертывании решений SharePoint см. в разделе [Развертывание пакетов решений (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx).

##  <a name="manual-verification-steps"></a><a name="bkmk_manual"></a> Действия по выполнению проверки вручную
 В этом разделе описаны шаги по проверке, которые нельзя выполнить с помощью командлетов PowerShell.

 **Плановое обновление данных.** Для расписания обновления книги задайте **Кроме того, как можно скорее обновите данные**.  Дополнительные сведения см. в разделе "Проверка обновления данных" раздела [Обновление данных и источники данных, не поддерживающие проверку подлинности Windows &#40;PowerPivot для SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md).

##  <a name="more-resources"></a><a name="bkmk_more_resources"></a>Дополнительные ресурсы
 [Командлеты для администрирования веб-сервера (IIS) в Windows PowerShell](https://technet.microsoft.com/library/ee790599.aspx).

 [PowerShell для проверки служб, состояние веб-сайтов IIS и пула приложений в SharePoint](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0).

 [Ссылка на Windows PowerShell для SharePoint 2013](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)

 [Ссылка на Windows PowerShell для SharePoint Foundation 2010](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)

 [Управление службами Excel с помощью Windows PowerShell (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)

 [Просмотр и чтение файлов журналов программы установки SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)

 [Использование командлета Get-EvenLog](https://technet.microsoft.com/library/ee176846.aspx)

##  <a name="full-powershell-script"></a><a name="bkmk_full_script"></a>Полный сценарий PowerShell
 Следующий скрипт содержит все команды, приведенные в предыдущих разделах. Скрипт выполняет команды в том же порядке, в котором они перечислены в этом разделе. Скрипт содержит некоторые дополнительные изменения команд, приведенных в этом разделе, на тот случай, если необходима дополнительная фильтрация. Изменения отключаются с помощью символа комментария (#). Скрипт также содержит некоторые инструкции для проверки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Инструкции [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] отключаются с помощью символа комментария (#).

```powershell
# This script audits services related to PowerPivot for SharePoint
$starttime = Get-Date
write-host -foregroundcolor DarkGray StartTime $starttime

Write-Host  "Import the SharePoint PowerShell snappin"
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0

Write-Host -ForegroundColor Green "Analysis Services Windows Service"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "PowerPivotEngineService and PowerPivotSystemService"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"

Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotSystemService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotEngineService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

#Write-Host -ForegroundColor Green "Service Instances - optional if you want to associate services with the server"
#Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
#Get-SPServiceInstance | select typename, status, server, service, instance | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel*" -or $_.TypeName -like "*Analysis Services*"} | format-table -property * -autosize | out-default
#Get-PowerPivotEngineServiceInstance  | select typename, ASServername, status, server, service, instance
#Get-PowerPivotSystemServiceInstance  | select typename, ASSServerName, status, server, service, instance

Write-Host -ForegroundColor Green "PowerPivot And Excel Service Applications"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename,  DisplayName, status

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot Service Application pool"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
# the following assumes there is only 1 PowerPivot Service Application, and returns that application's pool name.  if you have more than one, use the 2nd version
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)
Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot and Excel Service Application Proxy"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPServiceApplicationProxy |  Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPServiceApplicationProxy |  select typename, status, unattendedaccount, displayname | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*Reporting Services*" -or $_.TypeName -like "*excel services*"} | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "DATABASES"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPDatabase | select name, status, server, typename | where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*" -or $_.TypeName -like "*ReportingServices*"}

Write-Host -ForegroundColor Green "features"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPFeature | select displayname, status, scope, farm | where {$_.displayName -like "*powerpivot*" -or $_.displayName -like "*ReportServer*"}  | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "Timer Jobs (Job Definitions) -- list is the same as seen in the 'Review timer job definitions' section of the management dashboard"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPTimerJob | Where {$_.service -like "*power*" -or $_.service -like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "health rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "Windows Event Log data MSSQL$POWERPIVOT and "
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -Property * -autosize | Out-Default
#The following is the same command but with the Inforamtion events filtered out.
#Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*" -and ($_.entrytype -match "error" -or $_.entrytype -match "critical" -or $_.entrytype -match "warning")}  |select timegenerated, entrytype , source, message | format-table -property * -autosize | out-default

#Write-Host ""
Write-Host -ForegroundColor Green "ULS Log data"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message | Format-Table -Property * -AutoSize | Out-Default
#the following example filters for the category 'data refresh'
#Get-SPLogEvent -starttime(get-date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | select timestamp, area, category, eventid, level, correlation, message

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "MSOLAP data provider for Excel Servivces, service application"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "ADOMD.net client library"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-WMIObject -Class win32_product | Where-Object {$_.name -like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Usage Data Rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Solutions"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time
```
