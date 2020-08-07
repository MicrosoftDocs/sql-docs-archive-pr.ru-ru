---
title: Использование ключевых слов строки подключения с SQL Server Native Client | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b8d1de2ad5e95ea83d323c6e5e772f31f59c549
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730625"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Использование ключевых слов строки подключения с собственным клиентом SQL Server
  Некоторые API собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используют строки подключения, чтобы указать свойства соединения. Строки подключения являются списками ключевых слов и связанных значений, причем каждое ключевое слово определяет определенный атрибут соединения.  
  
 **Обратите внимание!** Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает неоднозначность строк соединения для обеспечения обратной совместимости (например, некоторые ключевые слова могут быть указаны несколько раз, и конфликты ключевых слов могут разрешаться на основании их положения или приоритета). В следующих версиях собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] неоднозначность в строках соединения может стать недопустимой. При изменении приложения для работы с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо предусмотреть устранение любых зависимостей от неоднозначности строки соединения.  
  
 В следующих разделах описываются ключевые слова, которые могут использоваться с поставщиком OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и объектами данных ActiveX (ADO) при использовании собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве поставщика данных.  
  
## <a name="odbc-driver-connection-string-keywords"></a>Ключевые слова в строке подключения драйвера ODBC  
 Приложения ODBC используют строки подключения в качестве параметров для функций [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) и [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md) .  
  
 Строки подключения, используемые ODBC, имеют следующий синтаксис:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Значения атрибутов можно (и рекомендуется) дополнительно заключить в фигурные скобки. Это позволяет избежать проблем, если значения атрибутов содержат символы, отличные от буквенно-цифровых. Предполагается, что первая закрывающая фигурная скобка в значении служит признаком конца значения, поэтому само значение не может содержать символы закрывающей фигурной скобки.  
  
 В следующей таблице описываются ключевые слова, которые можно использовать со строкой соединения ODBC.  
  
|Ключевое слово|Описание|  
|-------------|-----------------|  
|`Addr`|Синоним для «Address».|  
|`Address`|Сетевой адрес сервера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. `Address` обычно является сетевым именем сервера, но может быть и другим именем, например именем канала, IP-адресом или портом TCP/IP с адресом сокета.<br /><br /> Если указывается IP-адрес, убедитесь, что в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включен протокол TCP/IP или протокол именованных каналов.<br /><br /> Значение `Address` имеет приоритет над значением, передаваемым в `Server` в строках соединения ODBC, если используется собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Также следует отметить, что строка `Address=;` соединяется с сервером, указанным в ключевом слове `Server`, а при использовании ключевых слов `Address= ;, Address=.;`, `Address=localhost;` и `Address=(local);` устанавливается соединение с локальным сервером.<br /><br /> Далее представлен полный синтаксис ключевого слова `Address`:<br /><br /> [*protocol* `:` ]*Address*[ `,` *port &#124;\pipe\pipename*]<br /><br /> *протокол* может быть `tcp` (TCP/IP), `lpc` (общая память) или `np` (именованные каналы). Дополнительные сведения см. в статье [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Если не *protocol* указано ни протокол `Network` , ни ключевое слово, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент будет использовать порядок протоколов, указанный в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* — это порт указанного сервера, к которому выполняется подключение. По умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует порт 1433.|  
|`AnsiNPW`|Если задано значение «yes», то в драйвере используются определяемые стандартами ANSI правила обработки сравнений со значением NULL, дополнения символьных данных, формирования предупреждений и выполнения операция объединений со значением NULL. При использовании значения «no» определенные стандартом ANSI действия не используются. Дополнительные сведения о поведении ANSI НПВ см. в разделе [влияние параметров ISO](../../native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|`APP`|Имя приложения, вызывающего [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) (необязательно). Если указано, это значение сохраняется в столбце **master.dbo.sysprocesses** **program_name** и возвращается [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) и функциями [APP_NAME](/sql/t-sql/functions/app-name-transact-sql) .|  
|`ApplicationIntent`|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения: `ReadOnly` и `ReadWrite`. Например: ApplicationIntent = ReadOnly<br /><br /> Значение по умолчанию — `ReadWrite`. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержке собственного клиента для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделе [Поддержка высокого уровня доступности и аварийного восстановления в SQL Server Native Client](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`AttachDBFileName`|Имя первичного файла присоединяемой базы данных. Необходимо указать полный путь и экранировать любые символы \ при использовании символьной строковой переменной C:<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Эта база данных присоединяется и становится для соединения базой данных по умолчанию. Для использования необходимо `AttachDBFileName` также указать имя базы данных либо в параметре базы данных [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) , либо в атрибуте подключения SQL_COPT_CURRENT_CATALOG. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|`AutoTranslate`|Если имеет значение «yes», строки символов ANSI, которыми обмениваются клиент и сервер, переводятся с использованием Юникода, чтобы минимизировать проблемы сопоставления символов национальных алфавитов кодовых страниц клиента и сервера.<br /><br /> Клиентские SQL_C_CHAR данные, отправляемые в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] переменную **типа char**, **varchar**или **Text** , параметр или столбец, преобразуются из символов в Юникод с помощью клиентской кодовой страницы ANSI (ACP), а затем преобразуются из Юникода в символьный с помощью ACP сервера.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]данные **типа char**, **varchar**или **Text** , отправленные в переменную клиента SQL_C_CHAR, преобразуются из символа в Юникод с помощью ACP сервера, а затем преобразуются из Юникода в символьный с помощью клиента ACP.<br /><br /> Эти преобразования выполняются на клиенте драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Для этого необходимо, чтобы на сервере была доступна такая же кодовая страница ANSI, какая используется на клиенте.<br /><br /> Следующие параметры не влияют на преобразования, выполняемые для этих передач.<br /><br /> -Юникод SQL_C_WCHAR клиентские данные, отправляемые на сервер **char**, **varchar**или **Text** .<br />-   данные **типа char**, **varchar**или **Text** Server, отправленные в переменную SQL_C_WCHAR в Юникоде на клиенте.<br />-ANSI SQL_C_CHAR данные клиента, отправляемые в Юникоде **nchar**, **nvarchar**или **ntext** на сервере.<br />— Данные в Юникоде **nchar**, **nvarchar**или **ntext** , отправленные в переменную SQL_C_CHAR ANSI на клиенте.<br /><br /> Если имеет значение «no», перевод символов не выполняется.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Драйвер ODBC для собственного клиента не преобразует клиентский символ ANSI SQL_C_CHAR данные, отправляемые в переменные **char**, **varchar**или **Text** , параметры или столбцы на сервере. Не выполняется перевод данных **типа char**, **varchar**или **Text** , отправляемых с сервера, в SQL_C_CHAR переменные на клиенте.<br /><br /> Если клиент и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используют разные кодовые страницы ANSI, символы национального алфавита могут быть переведены неправильно.|  
|`Database`|Имя базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], используемой для соединения по умолчанию. Если ключевое слово `Database` не указано, используется база данных, определенная по умолчанию для имени входа. База данных по умолчанию из источника данных ODBC переопределяет базу данных по умолчанию, определенную для имени входа. База данных должна существовать, если не указан параметр `AttachDBFileName`. Если также указано ключевое слово `AttachDBFileName`, выполняется присоединение первичного файла, на который оно указывает, после чего присваивается имя базы данных, указанное ключевым словом `Database`.|  
|`Driver`|Имя драйвера, возвращаемое функцией [SQLDrivers](../../native-client-odbc-api/sqldrivers.md). Значение ключевого слова для драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] – «{SQL Server Native Client 11.0}». Ключевое слово `Server` требуется, если указано ключевое слово `Driver`, и ключевое слово `DriverCompletion` имеет значение SQL_DRIVER_NOPROMPT.<br /><br /> Дополнительные сведения об именах драйверов см. [в разделе использование SQL Server Native Client файлов заголовков и библиотек](using-the-sql-server-native-client-header-and-library-files.md).|  
|`DSN`|Имя существующего пользователя ODBC или системного источника данных. Это ключевое слово переопределяет все значения, указанные в ключевых словах `Server`, `Network` и `Address`.|  
|`Encrypt`|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|`Fallback`|Это ключевое слово является устаревшим, и его значение не учитывается драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Failover_Partner`|Имя сервера партнера по обеспечению отработки отказа, которое будет использоваться, если невозможно установить соединение с сервером-источником.|  
|`FailoverPartnerSPN`|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное драйвером.|  
|`FileDSN`|Имя существующего файлового источника данных ODBC.|  
|`Language`|Имя языка [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (необязательно). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]может хранить сообщения для нескольких языков в таблице **sysmessages**. При соединении с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с несколькими языками ключевое слово `Language` указывает, какой набор сообщений будет использован для соединения.|  
|`MARS_Connection`|Включает или отключает режим MARS для соединения. Распознаются значения «yes» и «no». Значение по умолчанию — «no».|  
|`MultiSubnetFailover`|Всегда указывайте параметр `multiSubnetFailover=Yes` при соединении с прослушивателем группы доступности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или экземпляром отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Параметр `multiSubnetFailover=Yes` настраивает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client для ускоренного обнаружения активного (в данный момент) сервера и подключения к нему. Возможные значения: `Yes` и `No`. Пример:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Значение по умолчанию — `No`. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержке собственного клиента для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделе [Поддержка высокого уровня доступности и аварийного восстановления в SQL Server Native Client](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Net`|Синоним для «Network».|  
|`Network`|Допустимые значения: **dbnmpntw** (именованные каналы) и **dbmssocn** (TCP/IP).<br /><br /> Одновременное указание значения для ключевого слова `Network` и префикса протокола в ключевом слове `Server` является ошибкой.|  
|`PWD`|Пароль для учетной записи входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], указанный в параметре UID. Указание `PWD` не требуется в случае, если пароль у имени входа равен NULL, либо при использовании проверки подлинности Windows (`Trusted_Connection = yes`).|  
|`QueryLog_On`|Если имеет значение «yes», для соединения включается регистрация данных длительных запросов. Если имеет значение «no», данные длительных запросов не регистрируются.|  
|`QueryLogFile`|Полный путь и имя файла, используемого для регистрации данных длительных запросов.|  
|`QueryLogTime`|Строка цифровых символов, указывающая порог (в миллисекундах) для регистрации длительных запросов. Любой запрос, ответ на который не поступает за указанное время, записывается в файл регистрации длительных запросов.|  
|`QuotedId`|Если имеет значение «yes», параметр QUOTED_IDENTIFIERS при соединении устанавливается в значение ON. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует правила ISO в отношении использования кавычек в инструкциях SQL. Если параметр равен «no», то параметр QUOTED_IDENTIFIERS для соединения отключается (принимает значение OFF). В этом случае [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] следует правилам устаревших версий [!INCLUDE[tsql](../../../includes/tsql-md.md)] относительно использования кавычек в инструкциях SQL. Дополнительные сведения см. в разделе [влияние параметров ISO](../../native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|`Regional`|Если имеет значение «yes», драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует настройки клиента при преобразовании данных валюты, даты и времени в символьные данные. Преобразование является односторонним, то есть драйвер не распознает строки даты и значения валюты, отличные от стандарта ODBC, например, параметры инструкций INSERT или UPDATE. Если имеет значение «no», драйвер использует стандартные строки ODBC для представления данных валюты, даты и времени, преобразуемых в символьные данные.|  
|`SaveFile`|Имя исходного файла данных ODBC, в который сохраняются атрибуты текущего соединения, если соединение успешно установлено.|  
|`Server`|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Значением должно быть имя сервера в сети, IP-адрес или имя псевдонима диспетчера конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Ключевое слово `Address` переопределяет ключевое слово `Server`.<br /><br /> Чтобы подключиться к экземпляру по умолчанию на локальном сервере, можно указать одно из следующих ключевых слов:<br /><br /> -   `Server=;`<br />-   `Server=.;`<br />-   `Server=(local);`<br />-   `Server=(localhost);`<br />-   **Server = (LocalDB) \\ ** _имя_экземпляра_`;`<br /><br /> Дополнительные сведения о поддержке LocalDB см. в разделе [поддержка SQL Server Native Client для LocalDB](../features/sql-server-native-client-support-for-localdb.md).<br /><br /> Чтобы указать именованный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], добавьте **\\** _InstanceName_.<br /><br /> Если сервер не указан, устанавливается соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Если указывается IP-адрес, убедитесь, что в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включен протокол TCP/IP или протокол именованных каналов.<br /><br /> Далее представлен полный синтаксис ключевого слова `Server`:<br /><br /> `Server=`[*протокол* `:` ] *Сервер*[ `,` *порт*]<br /><br /> *протокол* может быть `tcp` (TCP/IP), `lpc` (общая память) или `np` (именованные каналы).<br /><br /> Ниже приводится пример указания именованного канала:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Эта строка указывает протокол именованных каналов, именованный канал на локальном компьютере (`\\.\pipe`), имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) и имя по умолчанию для именованного канала (`sql/query`).<br /><br /> Если не указано ни *протокол* `Network` , ни ключевое слово, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент будет использовать порядок протоколов, указанный в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* — это порт указанного сервера, к которому выполняется подключение. По умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует порт 1433.<br /><br /> Пробелы в начале значения, передаваемого в аргументе `Server` строки подключения ODBC, не учитываются, когда используется собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`ServerSPN`|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное драйвером.|  
|`StatsLog_On`|Если имеет значение «yes», включается сбор данных производительности драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если имеет значение «no», данные производительности драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для соединения недоступны.|  
|`StatsLogFile`|Полный путь и имя файла для записи статистики производительности драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Trusted_Connection`|Значение «yes» предписывает драйверу ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать режим проверки подлинности Windows для проверки имени входа. В противном случае для проверки имени входа драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должен использовать имя пользователя и пароль [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а также необходимо указать ключевые слова UID и PWD.|  
|`TrustServerCertificate`|Если используется с ключевым словом `Encrypt`, включает шифрование с использованием самозаверяющего сертификата сервера.|  
|`UID`|Допустимая учетная запись входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ключевое слово UID не нужно указывать при использовании проверки подлинности Windows.|  
|`UseProcForPrepare`|Это ключевое слово является устаревшим, и его значение не учитывается драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`WSID`|Идентификатор рабочей станции. Обычно это сетевое имя компьютера, на котором находится приложение (необязательно). Если это значение указано, оно хранится в столбце **master.dbo.sysобрабатывает** **имя узла** и возвращается [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) и функцией [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) .|  
  
 **Региональные параметры преобразования применяются к типам данных валют, числовых типов, дат и времени. Параметр преобразования применяется только к преобразованию вывода и отображается только при преобразовании значений денежных единиц, чисел, дат и времени в символьные строки**.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует настройки локали текущего пользователя, установленные в реестре. Драйвер не учитывает языковой стандарт текущего потока, если приложение устанавливает его после соединения, например, путем вызова **сетсреадлокале**.  
  
 Изменение режима работы источника данных с региональными параметрами может привести к ошибке приложения. Изменение этого значения может отрицательно повлиять на работу приложения, анализирующего строки даты и предполагающего, что строки даты будут выводиться в виде, определенном ODBC.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Ключевые слова строки подключения поставщика OLE DB  
 Приложения OLE DB могут инициализировать объекты источника данных двумя способами:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 В первом случае строка поставщика может использоваться для инициализации свойств соединения посредством установки свойства DBPROP_INIT_PROVIDERSTRING в наборе свойств DBPROPSET_DBINIT. Во втором случае строка инициализации может быть передана методу **IDataInitialize::GetDataSource** для инициализации свойств соединения. При использовании каждого из этих методов инициализируются одни и те же свойства соединения OLE DB, однако, для этого применяются разные наборы ключевых слов. Набор ключевых слов, используемых методом **IDataInitialize::GetDataSource**, представляет собой по меньшей мере описание свойств, входящих в группу свойств инициализации.  
  
 Для любого параметра, указанного в строке поставщика, который имеет соответствующее свойство OLE DB, устанавливаемое в некоторое значение по умолчанию или явным образом установленное в некоторое значение, значение свойства OLE DB переопределяет значение, указанное в строке поставщика.  
  
 Логические свойства, установленные в строках поставщика через значения DBPROP_INIT_PROVIDERSTRING, устанавливаются с помощью значений «yes» и «no». Логические свойства, установленные в строках инициализации с помощью метода **IDataInitialize::GetDataSource**, устанавливаются с использованием значений true и false.  
  
 Приложения, использующие **IDataInitialize::-DataSource** , могут также использовать ключевые слова, используемые **IDBInitialize:: Initialize** , но только для свойств, которые не имеют значения по умолчанию. Если приложение одновременно использует в строке инициализации ключевые слова методов **IDataInitialize::GetDataSource** и **IDBInitialize::Initialize**, используется ключевое слово метода **IDataInitialize::GetDataSource**. Настоятельно рекомендуется не использовать в приложениях ключевые слова **IDBInitialize::Initialize** в строках подключения **IDataInitialize:GetDataSource**, так как это поведение может не поддерживаться в будущих версиях.  
  
 **Примечание.** Строка подключения, передаваемая через **IDataInitialize::-DataSource** , преобразуется в свойства и применяется через **интерфейс IDBProperties:: SetProperties**. Если службы компонентов обнаруживают описание свойства в **IDBProperties::GetPropertyInfo**, это свойство будет применяться в качестве изолированного. В противном случае оно будет применяться через свойство DBPROP_PROVIDERSTRING. Например, если указать строку подключения **Data Source = Server1; Server = Server2** `Data Source` будет задан как свойство, но будет передаваться `Server` в строку поставщика.  
  
 Если указать несколько экземпляров одного свойства поставщика, то будет использоваться первое значение первого свойства.  
  
 Строки подключения, используемые в приложениях OLE DB, в которых используется DBPROP_INIT_PROVIDERSTRING и **IDBInitialize::Initialize**, имеют следующий синтаксис.  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Значения атрибутов можно (и рекомендуется) дополнительно заключить в фигурные скобки. Это позволяет избежать проблем, если значения атрибутов содержат символы, отличные от буквенно-цифровых. Предполагается, что первая закрывающая фигурная скобка в значении служит признаком конца значения, поэтому само значение не может содержать символы закрывающей фигурной скобки.  
  
 Пробельный символ после знака равенства (=) в строке подключения будет считаться литералом, даже если значение заключено в кавычки.  
  
 В следующей таблице рассматриваются ключевые слова, которые можно использовать со свойством DBPROP_INIT_PROVIDERSTRING.  
  
|Ключевое слово|Свойство инициализации|Описание|  
|-------------|-----------------------------|-----------------|  
|`Addr`|SSPROP_INIT_NETWORKADDRESS|Синоним для «Address».|  
|`Address`|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова ODBC `Address` далее в этом разделе.|  
|`APP`|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|`ApplicationIntent`|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения: `ReadOnly` и `ReadWrite`.<br /><br /> Значение по умолчанию — `ReadWrite`. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержке собственного клиента для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделе [Поддержка высокого уровня доступности и аварийного восстановления в SQL Server Native Client](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`AttachDBFileName`|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Чтобы использовать ключевое слово `AttachDBFileName`, необходимо также указать имя базы данных с помощью ключевого слова DATABASE в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «yes» и «no».|  
|`Database`|DBPROP_INIT_CATALOG|Имя базы данных.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Указывает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных SQL Server 2000).|  
|`Encrypt`|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|`FailoverPartner`|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|`FailoverPartnerSPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|`Language`|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`MarsConn`|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения для сервера версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|`Net`|SSPROP_INIT_NETWORKLIBRARY|Синоним для «Network».|  
|`Network`|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Синоним для «Network».|  
|`PacketSize`|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|`PersistSensitive`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «yes» и «no». Если используется значение «no», объекту источника данных запрещено хранить конфиденциальные данные проверки подлинности.|  
|`PWD`|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Server`|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова ODBC `Server` в этом разделе.|  
|`ServerSPN`|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|`Timeout`|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|`Trusted_Connection`|DBPROP_AUTH_INTEGRATED|Значение «yes» предписывает поставщику OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать режим проверки подлинности Windows для проверки имени входа. В противном случае для проверки имени входа поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должен использовать имя пользователя и пароль [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а также необходимо указать ключевые слова UID и PWD.|  
|`TrustServerCertificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «yes» и «no». По умолчанию имеет значение «no», которое указывает, что сертификат сервера будет проверяться.|  
|`UID`|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`UseProcForPrepare`|SSPROP_INIT_USEPROCFORPREP|Это ключевое слово является устаревшим, и его значение не обрабатывается поставщиком OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`WSID`|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
 Строки подключения, используемые приложениями OLE DB, в которых используется **IDataInitialize::GetDataSource**, имеют следующий синтаксис.  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 Использование свойства должно соответствовать синтаксическим правилам, действующим в его области.  Например, в `WSID` заключается в фигурные скобки (`{}`), а `Application Name` — в апострофы (`'`) или двойные кавычки (`"`). Заключать в кавычки можно только строковые свойства. Заключение в кавычки целочисленного или перечисляемого свойства приведет к ошибке «Строка подключения не соответствует спецификации OLE DB».  
  
 Значения атрибутов можно при желании заключать в одинарные или двойные кавычки, а фактически это даже рекомендуется. Это позволяет избежать проблем, если значения содержат символы, отличные от буквенно-цифровых. Используемый символ кавычек может также появиться в значении при условии его удвоения.  
  
 Пробельный символ после знака равенства (=) в строке подключения будет считаться литералом, даже если значение заключено в кавычки.  
  
 Если строка подключения содержит несколько свойств из тех, которые приведены в следующей таблице, то будет использоваться значение последнего свойства.  
  
 В следующей таблице рассматриваются ключевые слова, которые можно использовать с **IDataInitialize::GetDataSource**.  
  
|Ключевое слово|Свойство инициализации|Описание|  
|-------------|-----------------------------|-----------------|  
|`Application Name`|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|`Application Intent`|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения: `ReadOnly` и `ReadWrite`.<br /><br /> Значение по умолчанию — `ReadWrite`. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержке собственного клиента для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделе [Поддержка высокого уровня доступности и аварийного восстановления в SQL Server Native Client](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «true» и «false».|  
|`Connect Timeout`|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|`Current Language`|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Data Source`|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова ODBC `Server` далее в этом разделе.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Указывает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]).|  
|`Failover Partner`|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|`Failover Partner SPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|`Initial Catalog`|DBPROP_INIT_CATALOG|Имя базы данных.|  
|`Initial File Name`|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Чтобы использовать ключевое слово `AttachDBFileName`, необходимо также указать имя базы данных с помощью ключевого слова DATABASE в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|`Integrated Security`|DBPROP_AUTH_INTEGRATED|Принимает значение «SSPI» для проверки подлинности Windows.|  
|`MARS Connection`|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения. Распознаются значения «true» и «false». Значение по умолчанию — «false».|  
|`Network Address`|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова ODBC `Address` далее в этом разделе.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|`Packet Size`|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|`Password`|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Persist Security Info`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «true» и «false». Если указано значение «false», объекту источника данных не разрешается сохранять конфиденциальные сведения проверки подлинности.|  
|`Provider`||Для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо указывать значение «SQLNCLI11».|  
|`Server SPN`|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|`Trust Server Certificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «true» и «false». По умолчанию имеет значение «false», которое указывает, что сертификат сервера будет проверяться.|  
|`Use Encryption for Data`|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».|  
|`User ID`|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Workstation ID`|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
 **Примечание**. В строке подключения свойство Old Password устанавливает значение свойства SSPROP_AUTH_OLD_PASSWORD, которое является текущим паролем (возможно, с истекшим сроком действия), недоступным через свойство строки поставщика.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Ключевые слова строки подключения объектов данных ActiveX (ADO)  
 Приложения ADO устанавливают свойство **ConnectionString** объектов **ADODBConnection** или указывают строку подключения как параметр метода **Open** объектов **ADODBConnection**.  
  
 В приложениях ADO также могут применяться ключевые слова, используемые методом OLE DB **IDBInitialize::Initialize**, но только для свойств, у которых отсутствует значение по умолчанию. Если в строке инициализации приложения содержатся ключевые слова ADO и ключевые слова **IDBInitialize::Initialize**, используется параметр ключевого слова ADO. Настоятельно рекомендуется, чтобы приложение использовало для строк соединения только ключевые слова ADO.  
  
 Строки подключения, используемые ADO, имеют следующий синтаксис:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Значения атрибутов можно (и рекомендуется) дополнительно заключить в двойные кавычки. Это позволяет избежать проблем, если значения содержат символы, отличные от буквенно-цифровых. Значения атрибутов не могут содержать двойные кавычки.  
  
 В следующей таблице описываются ключевые слова, которые можно использовать со строками соединения ADO.  
  
|Ключевое слово|Свойство инициализации|Описание|  
|-------------|-----------------------------|-----------------|  
|`Application Intent`|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения: `ReadOnly` и `ReadWrite`.<br /><br /> Значение по умолчанию — `ReadWrite`. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержке собственного клиента для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделе [Поддержка высокого уровня доступности и аварийного восстановления в SQL Server Native Client](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Application Name`|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «true» и «false».|  
|`Connect Timeout`|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|`Current Language`|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Data Source`|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова ODBC `Server` в этом разделе.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Задает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных SQL Server 2000).|  
|`Failover Partner`|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|`Failover Partner SPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|`Initial Catalog`|DBPROP_INIT_CATALOG|Имя базы данных.|  
|`Initial File Name`|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Чтобы использовать ключевое слово `AttachDBFileName`, необходимо также указать имя базы данных с помощью ключевого слова DATABASE в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|`Integrated Security`|DBPROP_AUTH_INTEGRATED|Принимает значение «SSPI» для проверки подлинности Windows.|  
|`MARS Connection`|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения для сервера версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Распознаются значения «true» и «false». По умолчанию используется значение «false».|  
|`Network Address`|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова ODBC `Address` в этом разделе.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|`Packet Size`|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|`Password`|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Persist Security Info`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «true» и «false». Если указано значение «false», объекту источника данных не разрешается сохранять конфиденциальные сведения проверки подлинности.|  
|`Provider`||Для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо указывать значение «SQLNCLI11».|  
|`Server SPN`|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|`Trust Server Certificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «true» и «false». По умолчанию имеет значение «false», которое указывает, что сертификат сервера будет проверяться.|  
|`Use Encryption for Data`|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».|  
|`User ID`|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Workstation ID`|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
 **Примечание**. В строке подключения свойство Old Password устанавливает значение свойства SSPROP_AUTH_OLD_PASSWORD, которое является текущим паролем (возможно, с истекшим сроком действия), недоступным через свойство строки поставщика.  
  
## <a name="see-also"></a>См. также:  
 [Построение приложений с использованием SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
