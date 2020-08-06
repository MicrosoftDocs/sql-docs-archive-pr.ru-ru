---
title: Analysis Services PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56af6f26c29e5c1ddb278b620b6f525c70bd1203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656909"
---
# <a name="analysis-services-powershell"></a>Analysis Services PowerShell
  В службах [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] имеется поставщик Analysis Services PowerShell (SQLAS) и командлеты, позволяющие использовать Windows PowerShell для навигации, администрирования и выполнения запросов к объектам служб Analysis Services.  
  
 В состав Analysis Services PowerShell входит следующее.  
  
-   Поставщик `SQLAS`, используемый для навигации по иерархии объектов AMO.  
  
-   Командлет `Invoke-ASCmd`, используемый для выполнения скриптов многомерного анализа данных (MDX), расширений интеллектуального анализа данных (DMX) или XML для аналитики.  
  
-   Командлеты для отдельных задач, выполняющие типовые операции, в частности, обработку, управление ролями, управление секциями, резервное копирование и восстановление.  
  
## <a name="in-this-article"></a>В этой статье  
 [Предварительные требования](#bkmk_prereq)  
  
 [Поддерживаемые версии и режимы служб Analysis Services](#bkmk_vers)  
  
 [Требования проверки подлинности и соображения безопасности](#bkmk_auth)  
  
 [Задачи Analysis Services PowerShell](#bkmk_tasks)  

Дополнительные сведения о синтаксисе и примерах см. в [справочнике по Analysis Services PowerShell](/sql/analysis-services/powershell/analysis-services-powershell-reference).

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Предварительные требования  
 Должна быть установлена оболочка Windows PowerShell 2.0. В последних версиях операционных систем Windows она устанавливается по умолчанию. Дополнительные сведения см. в [статье Install Windows PowerShell 2,0](https://msdn.microsoft.com/library/ff637750.aspx)

<!-- ff637750.aspx above is linked to by:  (https://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 Необходимо установить компонент SQL Server, включающий модуль SQL Server PowerShell (SQLPS) и клиентские библиотеки. Проще всего это сделать, установив среду SQL Server Management Studio, которая уже включает компонент PowerShell и клиентские библиотеки. Модуль SQL Server PowerShell (SQLPS) содержит поставщики PowerShell и командлеты для всех компонентов SQL Server, включая модуль SQLASCmdlets и поставщик SQLAS, используемый для навигации по иерархии объектов служб Analysis Services.  
  
 Для использования **SQLPS** `SQLAS` поставщика и командлетов необходимо импортировать модуль sqlps. Поставщик SQLAS является расширением `SQLServer` поставщика. Имеется несколько способов импорта модуля SQLPS. Дополнительные сведения см. в разделе [Импорт модуля SQLPS](../../2014/database-engine/import-the-sqlps-module.md).  
  
 Для удаленного доступа к экземпляру служб Analysis Services требуется включить удаленное администрирование и общий доступ к файлам. Дополнительные сведения см. в разделе [Включение удаленного администрирования](#bkmk_remote) этого раздела.  
  
##  <a name="supported-versions-and-modes-of-analysis-services"></a><a name="bkmk_vers"></a>Поддерживаемые версии и режимы Analysis Services  
 В настоящее время Analysis Services PowerShell поддерживается всеми выпусками служб [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services, работающими под управлением Windows Server 2008 R2, Windows Server 2008 SP1 или Windows 7.  
  
 В следующей таблице приведены данные по доступности Analysis Services PowerShell в различных контекстах.  
  
|Контекст|Доступность функций PowerShell|  
|-------------|-------------------------------------|  
|Многомерные экземпляры и базы данных|Поддерживается локальное и удаленное администрирование.<br /><br /> Для слияния секций необходимо локальное соединение.|  
|Табличные экземпляры и базы данных|Поддерживается локальное и удаленное администрирование.<br /><br /> Дополнительные сведения см. в блоге 2011 августа об [управлении табличными моделями с помощью PowerShell](https://go.microsoft.com/fwlink/?linkID=227685).|  
|Экземпляры и базы данных PowerPivot для SharePoint|Ограниченная поддержка. Для просмотра сведений об экземпляре и базе данных можно использовать соединения HTTP и поставщик SQLAS.<br /><br /> Однако использование командлетов не поддерживается. Надстройку PowerShell для служб Analysis Services не следует использовать для резервного копирования и восстановления хранящихся в памяти баз данных PowerPivot, а также для добавления и удаления ролей, обработки данных или запуска произвольных скриптов XMLA.<br /><br /> В целях настройки в PowerPivot для SharePoint имеется встроенная поддержка PowerShell, реализуемая отдельно. Дополнительные сведения см. в [справочнике по PowerShell для PowerPivot для SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).|  
|Собственные соединения с локальными кубами<br /><br /> "Data Source = к:\баккуп\тест.куб"|Не поддерживается.|  
|Соединения HTTP с файлами соединений семантических моделей бизнес-аналитики (BISM-файлами) в SharePoint<br /><br /> "Data Source = http://server/shared_docs/name.bism "|Не поддерживается.|  
|Встроенные соединения с базами данных PowerPivot<br /><br /> "Data Source = $Embedded $"|Не поддерживается.|  
|Контекст локального сервера в хранимых процедурах служб Analysis Services<br /><br /> "Data Source = *"|Не поддерживается.|  
  
##  <a name="authentication-requirements-and-security-considerations"></a><a name="bkmk_auth"></a>Требования к проверке подлинности и вопросы безопасности  
 При соединении со службами Analysis Services необходимо использовать идентификатор пользователя Windows. В большинстве случаев соединение осуществляется с использованием встроенной проверки подлинности Windows, при этом идентификатор текущего пользователя задает контекст, в котором выполняются серверные операции. Однако после настройки доступа к службам Analysis Services по HTTP становятся доступными дополнительные методы проверки подлинности. В этом разделе описывается, как тип соединения влияет на возможные параметры проверки подлинности.  
  
 Соединение к службам Analysis Services может быть собственным либо соединением по HTTP. Собственное соединение — это прямое соединение клиентского приложения к серверу. В сеансе PowerShell клиент PowerShell использует поставщик OLE DB для служб Analysis Services для прямого подключения к экземпляру служб Analysis Services. Собственные соединения всегда осуществляются с использованием встроенной безопасности Windows, при этом PowerShell выполняется от имени текущего пользователя. Службы Analysis Services не поддерживают олицетворение. Если необходимо выполнить операцию от имени определенного пользователя, запустите сеанс PowerShell от имени этого пользователя.  
  
 HTTP-соединения производятся непрямым образом через IIS, что обеспечивает дополнительные возможности проверки подлинности, например использование обычной проверки подлинности при подключении к экземпляру служб Analysis Services. Поскольку службы IIS поддерживают олицетворение, в строке подключения можно указать учетные данные, которые будут использоваться IIS для олицетворения при соединении. Чтобы указать учетные данные, можно использовать параметр-Credential.  
  
 **Использование параметра-Credential в PowerShell**  
  
 Параметр-Credential принимает объект PSCredential, указывающий имя пользователя и пароль. В Analysis Services PowerShell параметр-Credential доступен для командлетов, которые делают запрос на соединение Analysis Services, в отличие от командлетов, которые выполняются в контексте существующего соединения. К командлетам, осуществляющим запрос на соединение, относятся Invoke-ASCmd, Backup-ASDatabase и Restore-ASDatabase. Для этих командлетов можно использовать параметр-Credential, если выполняются следующие условия.  
  
1.  Сервер настроен на доступ по HTTP, то есть соединение обрабатывается сервером IIS, который считывает имя пользователя и пароль и олицетворяет соответствующий идентификатор пользователя при соединении со службами Analysis Services. Дополнительные сведения см. в разделе [Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
2.  Виртуальный каталог IIS, созданный для доступа к службам Analysis Services по HTTP, настроен на обычную проверку подлинности.  
  
3.  Имя пользователя и пароль, предоставляемые объектом учетных данных, разрешаются в идентификатор пользователя Windows. Службы Analysis Services используют этот идентификатор в качестве текущего пользователя. Если пользователь не является пользователем Windows или у него недостаточно прав для выполнения запрошенной операции, запрос завершается с ошибкой.  
  
 Чтобы создать объект учетных данных, можно воспользоваться командлетом Get-Credential для получения учетных данных от оператора. Затем этот объект учетных данных можно использовать в команде подключения к службам Analysis Services. В следующем примере показан один из подходов. В этом примере соединение выполняется с локальным экземпляром ( `SQLSERVER:\SQLAS\HTTP_DS` ), настроенным для доступа по протоколу HTTP.  
  
```powershell
$cred = Get-Credential adventureworks\dbadmin  
Invoke-ASCmd -Inputfile:"c:\discoverconnections.xmla" -Credential:$cred  
```  
  
 При использовании обычной проверки подлинности следует всегда использовать протокол HTTPS с включенным SSL, чтобы имя пользователя и пароль передавались по зашифрованному соединению. Дополнительные сведения см. в статьях [настройка SSL в iis 7,0](https://go.microsoft.com/fwlink/?linkID=184299) и [Настройка обычной проверки подлинности (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=230776).  
  
 Не забывайте, что учетные данные, запросы и команды, вводимые в PowerShell, передаются на транспортный уровень без изменений. Включение конфиденциальных данных в скрипты повышает вероятность вредоносной атаки типа «инъекция».  
  
 **Указание пароля в объекте Microsoft.Secure.String**  
  
 Некоторые операции, например резервное копирование и восстановление, поддерживают параметры шифрования, которые включаются при указании в команде пароля. Указание пароля дает службам Analysis Services команду на шифрование или расшифровку файла резервной копии. В службах Analysis Services экземпляр этого пароля создается в виде объекта защищенной строки. В следующем примере показано, как получить пароль от оператора во время выполнения.  
  
```powershell
$pwd = read-host -AsSecureString -Prompt "Password"  
$pwd -is [System.IDisposable]  
```  
  
 Теперь можно создавать резервную копию зашифрованного файла базы данных и восстанавливать ее, передавая переменную $pwd в параметр пароля. Полный пример, объединяющий эту иллюстрацию с другими командлетами, см. в разделе [командлет Backup-ASDatabase](/powershell/module/sqlserver/backup-asdatabase) и [командлет Restore-ASDatabase](/powershell/module/sqlserver/restore-asdatabase).
  
 В качестве следующего шага удалите пароль и переменную из сеанса.  
  
```powershell
$pwd.Dispose()  
Remove-Variable -Name pwd  
```  
  
##  <a name="analysis-services-powershell-tasks"></a><a name="bkmk_tasks"></a>Analysis Services задач PowerShell  
 Службы Analysis Services PowerShell можно запустить из консоли управления Windows PowerShell или командной строки Windows. Запуск служб Analysis Services PowerShell из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] не поддерживается.  
  
 В этом разделе описываются типичные задачи, для выполнения которых используется Analysis Services PowerShell.  
  
-   [Загрузка поставщика служб Analysis Services и командлетов](#bkmk_load)  
  
-   [Включение удаленного администрирования](#bkmk_remote)  
  
-   [Подключение к объекту служб Analysis Services](#bkmk_connect)  
  
-   [Администрирование службы](#bkmk_admin)  
  
-   [Получение справки по Analysis Services PowerShell](#bkmk_help)  
  
###  <a name="load-the-analysis-services-provider-and-cmdlets"></a><a name="bkmk_load"></a>Загрузка поставщика Analysis Services и командлетов  
 Поставщик Analysis Services — это расширение корневого поставщика SQL Server, которое становится доступным при импорте модуля SQLPS. Командлеты служб Analysis Services загружаются одновременно; их также можно загружать по отдельности, если вы хотите использовать их без поставщика.  
  
-   Запустите командлет Import-module, чтобы загрузить SQLPS, включающий всю функциональность Analysis Services PowerShell. Если импортировать модуль невозможно, можно временно сменить политику выполнения на неограниченную, чтобы загрузить этот модуль. Дополнительные сведения см. в разделе [Импорт модуля SQLPS](../../2014/database-engine/import-the-sqlps-module.md).  
  
    ```powershell
    Import-Module "sqlps"  
    ```  
  
     Вместо этого можно использовать команду `import-module "sqlps" -disablenamechecking` для подавления предупреждений о несоответствии имен команд утвержденным.  
  
-   Чтобы загрузить лишь командлеты служб Analysis Services для определенной задачи, без поставщика служб Analysis Services или командлета Invoke-ASCmd, можно загрузить модуль SQLASCmdlets в рамках независимой операции.  
  
    ```powershell
    Import-Module "sqlascmdlets"  
    ```  
  
###  <a name="enable-remote-administration"></a><a name="bkmk_remote"></a>Включить удаленное администрирование  
 Чтобы можно было использовать службы Analysis Services PowerShell с удаленным экземпляром служб Analysis Services, сначала необходимо включить удаленное администрирование и общий доступ к файлам. Следующая ошибка указывает на ошибку конфигурации брандмауэра: "сервер RPC недоступен. (Исключение HRESULT: 0x800706BA.)".  
  
1.  Убедитесь, что и на локальном, и на удаленном компьютерах установлена версия [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] клиентских и серверных средств.  
  
2.  На удаленном сервере, на котором размещен экземпляр служб Analysis Services, откройте в брандмауэре Windows порт TCP 2383. Если службы Analysis Services установлены как именованный экземпляр или используют заданный пользователем порт, номер порта будет другим. Дополнительные сведения см. в статье [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
3.  Убедитесь, что на удаленном сервере запущены следующие службы: служба удаленного вызова процедур (RPC), служба модуля поддержки NetBIOS TCP/IP, служба инструментарий управления Windows (WMI) (WMI), служба служба удаленного управления Windows (WS-Management).  
  
4.  На удаленном сервере запустите оснастку редактора объектов групповой политики (gpedit.msc).  
  
5.  Откройте последовательно следующие элементы: «Настройка компьютера»,«Административные шаблоны», «Сеть», «Сетевые подключения», «Брандмауэр Windows» и «Профиль домена».  
  
6.  Дважды щелкните **Брандмауэр Windows: разрешить исключение для входящего удаленного администрирования**, выберите **включено**и нажмите кнопку **ОК**.  
  
7.  Дважды щелкните **Брандмауэр Windows: разрешить исключение для входящего общего доступа к файлам и принтерам**, выберите **включено**и нажмите кнопку **ОК**.  
  
8.  На локальном компьютере с клиентскими средствами используйте следующие командлеты для проверки удаленного администрирования, подставив фактическое имя сервера для заполнителя *Remote-Server-Name* . Пропустите имя экземпляра, если службы Analysis Services установлены как экземпляр по умолчанию. Чтобы эта команда работала, необходимо предварительно импортировать модуль SQLPS.  
  
    ```
    PS SQLSERVER:\> cd sqlas
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 В некоторых случаях может понадобиться дополнительная настройка. Возможно, потребуется ввести на удаленном сервере следующую команду, прежде чем на нем можно будет выполнять команды с другого компьютера:  
  
```powershell
Enable-PSRemoting  
```  
  
  
###  <a name="connect-to-an-analysis-services-object"></a><a name="bkmk_connect"></a>Подключение к объекту Analysis Services  
 Поставщик Analysis Services PowerShell поддерживает навигацию по иерархии объектов служб Analysis Services и задает контекст для выполнения команд. Поставщик является расширением корневого поставщика SQLSERVER, доступного в модуле SQLPS. После загрузки модуля SQLPS становится доступной навигация по пути.  
  
 Возможно подключение как к локальному, так и к удаленному экземпляру, но некоторые командлеты работают только на локальном экземпляре (например, merge-partition). Можно использовать собственное соединение или HTTP-соединение с серверами служб Analysis Services, настроенными на доступ по протоколу HTTP. На следующих рисунках показан путь навигации для собственных соединений и для соединений по протоколу HTTP. На следующих рисунках показан путь навигации для собственных соединений и для соединений по протоколу HTTP.  
  
 **Собственные соединения со службами Analysis Services**  
  
 ![Собственное соединение со службами Analysis Services](media/ssas-powershell-nativeconnection.gif "Собственное соединение со службами Analysis Services")  
  
 Следующий пример показывает использование собственного соединения для навигации по иерархии объектов. На поставщике можно воспользоваться командой `dir` для просмотра сведений об экземпляре. Команда `cd` позволяет просмотреть объекты на этом экземпляре.  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 Должны отобразиться следующие коллекции: сборки, базы данных, роли и трассировки. Продолжая использовать `cd` и `dir`, можно просмотреть содержимое всех коллекций.  
  
 **Соединения по протоколу HTTP со службами Analysis Services**  
  
 ![HTTP-соединение со службами Analysis Services](media/ssas-powershell-httpconnection.gif "HTTP-соединение со службами Analysis Services")  
  
 HTTP-подключения полезны, если вы настроили сервер для доступа по протоколу HTTP, выполнив инструкции в этом разделе: [Настройка доступа по протоколу HTTP к Analysis Services на службы IIS &#40;IIS&#41; 8,0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
 Если предположить, что URL-адрес сервера для http://localhost/olap/msmdpump.dll , соединение может выглядеть следующим образом:  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName "http://localhost/olap/msmdpump.dll"  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 Должны отобразиться следующие коллекции: сборки, базы данных, роли и трассировки. Если просмотреть содержимое этих коллекций не удается, проверьте параметры проверки подлинности в виртуальном каталоге OLAP. Убедитесь, что анонимный доступ отключен. Если используется проверка подлинности Windows, убедитесь, что у учетной записи пользователя Windows имеются административные разрешения для экземпляра служб Analysis Services.  
  
###  <a name="administer-the-service"></a><a name="bkmk_admin"></a>Администрирование службы  
 Убедитесь в том, что служба запущена. Возвращает состояние, имя и отображаемое имя служб SQL Server, включая службы Analysis Services (MSSQLServerOLAPService) и компонент Database Engine.  
  
```powershell
Get-Service mssql*  
```  
  
 Возвращает свойства процесса, включая идентификатор процесса, количество дескрипторов и объем используемой памяти:  
  
```powershell
Get-Process msmdsrv  
```  
  
 Перезапускает службу, когда пользователь выполняет следующий командлет из оболочки администратора:  
  
```powershell
Restart-Service mssqlserverolapservice  
```  
  
###  <a name="get-help-for-analysis-services-powershell"></a><a name="bkmk_help"></a>Получение справки по Analysis Services PowerShell  
 Используйте любой из следующих командлетов, чтобы проверить доступность командлетов и получить дополнительные сведения о службах, процессах и объектах.  
  
1.  `Get-Help` возвращает встроенную справку для командлета служб Analysis Services, включая примеры:  
  
    ```powershell
    Get-Help invoke-ascmd -Examples  
    ```  
  
2.  `Get-Command` возвращает список из одиннадцати командлетов Analysis Services PowerShell:  
  
    ```powershell
    Get-Command -module SQLASCmdlets  
    ```  
  
3.  `Get-Member` возвращает свойства или методы службы или процесса.  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Property  
    ```  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Method  
    ```  
  
    ```powershell
    Get-Process msmdsrv | Get-Member -Type Property  
    ```  
  
4.  `Get-Member` также может использоваться для возвращения свойств или методов объекта (например, методов AMO у серверного объекта) с применением поставщика SQLAS, задающего экземпляр сервера.  
  
    ```
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | Get-Member -Type Method  
    ```  
  
5.  `Get-PSdrive` возвращает список поставщиков, установленных в настоящий момент. Если модуль SQLPS импортирован, в списке отобразится поставщик `SQLServer` (SQLAS входит в состав поставщика SQLServer и никогда не появляется в списке отдельно от него):  
  
    ```powershell
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Установка SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md)   
 [Управление табличными моделями с помощью PowerShell (блог)](https://go.microsoft.com/fwlink/?linkID=227685)   
 [Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
