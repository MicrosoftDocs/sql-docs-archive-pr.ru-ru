---
title: Диагностическое соединение для администраторов баз данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], connections
- administrator connections [SQL Server]
- ports [SQL Server], DAC
- DAC
- network connections [SQL Server], dedicated administrator
- diagnostic connections [SQL Server]
- connections [SQL Server], dedicated administrator
- ports [SQL Server]
- dedicated administrator connections [SQL Server]
ms.assetid: 993e0820-17f2-4c43-880c-d38290bf7abc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0d452ca155a5187136c910e81e8bd073e34cad56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665120"
---
# <a name="diagnostic-connection-for-database-administrators"></a>Диагностическое соединение для администраторов баз данных
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет специальное диагностическое соединение для администраторов, когда стандартное соединение с сервером невозможно. Это диагностическое соединение позволяет администратору получить доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения диагностических запросов и устранения проблем, даже когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отвечает на стандартные запросы на соединение.  
  
 Такое выделенное административное соединение (DAC) поддерживает шифрование и другие средства безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Выделенное административное соединение позволяет только изменять контекст пользователя на другого пользователя с правами администратора.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] делает все возможное для успешного установления выделенного административного соединения, но в чрезвычайных ситуациях это может не дать результата.  
  
||  
|-|  
|**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] .|  
  
## <a name="connecting-with-dac"></a>Соединение с помощью выделенного административного соединения  
 По умолчанию, соединение разрешено только из клиента, запущенного на сервере. Сетевые подключения не разрешаются, пока они не настроены с помощью хранимой процедуры sp_configure с параметром [remote admin connections](remote-admin-connections-server-configuration-option.md).  
  
 Только члены роли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin могут подключаться с использованием выделенного административного соединения.  
  
 Выделенное административное соединение доступно и поддерживается через программу командной строки **sqlcmd** со специальным административным параметром (**-A**). Дополнительные сведения об использовании **sqlcmd** см. в разделе [Использование программы sqlcmd с переменными скрипта](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md). Можно также подсоединить префикс `admin:` к имени экземпляра в формате **sqlcmd-садмин:** _<instance_name>._ Кроме того, приложение уровня данных можно запустить из [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] редактора запросов, подключившись к `admin:` \<*instance_name*> .  
  
## <a name="restrictions"></a>Ограничения  
 Так как выделенное административное соединение существует только для диагностики проблем на сервере в редких обстоятельствах, у подключения есть некоторые ограничения.  
  
-   Чтобы гарантировать, что для подключения есть доступные ресурсы, на один экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]разрешено только одно выделенное административное соединение. Если выделенное административное соединение уже активно, любой новый запрос на соединение через DAC отклоняется с ошибкой 17810.  
  
-   Для экономии ресурсов [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] прослушивает порт выделенного административного соединения только при запуске с флагом трассировки 7806.  
  
-   Сначала выделенное административное соединение подключается к базе данных по умолчанию, связанной с именем входа. После успешного соединения можно подключиться к базе данных master. Если база данных по умолчанию находится в режиме вне сети или недоступна по другой причине, соединение вернет ошибку 4060. При этом соединение будет успешным, если вместо базы данных по умолчанию подключиться к базе данных master с помощью следующей команды:  
  
     **Мастер SQLCMD-A-d**  
  
     Рекомендуется подключаться через выделенное административное соединение к базе данных master, так как база данных master будет в любом случае доступна, если запущен экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запрещает выполнение параллельных запросов или команд через выделенное административное соединение. Например, ошибка 3637 возникает при выполнении через выделенное административное соединение любой из следующих инструкций:  
  
    -   RESTORE  
  
    -   BACKUP  
  
-   Через выделенное административное соединение гарантированно доступны только ограниченные ресурсы. Не используйте выделенное административное соединение для запуска ресурсоемких запросов (например, сложного соединения для большой таблицы) или запросов, которые могут блокироваться. Это позволяет обезопасить выделенное административное соединение от осложнения любыми существующими проблемами на сервере. Чтобы избежать сценариев, которые могут приводить к блокировке, следует при возможности запускать запросы, которые могут вызвать блокировку, на уровне изоляции моментального снимка. В противном случае следует установить уровень изоляции транзакций READ UNCOMMITTED и малое значение LOCK_TIMEOUT, например 2000 миллисекунд. Можно также использовать оба способа одновременно. Это позволит предотвратить блокировку сеанса выделенного административного соединения. Но в зависимости от состояния [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанс выделенного административного соединения может быть заблокирован с помощью кратковременной блокировки. Возможно, удастся прекратить сеанс выделенного административного соединения с помощью комбинации клавиш CTRL-C, но это не гарантируется. В таком случае единственным вариантом остается перезапуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Чтобы гарантировать соединение и устранение неполадок через выделенное административное соединение, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] резервирует ограниченные ресурсы для обработки команд, запущенных через него. Этих ресурсов обычно хватает только для простых диагностических функций и устранения неполадок, которые приведены ниже.  
  
 Теоретически можно запустить любую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] , которая не должна исполняться параллельно через выделенное административное соединение, но корпорация Майкрософт настоятельно рекомендует ограничиться применением следующих команд диагностики и устранения неполадок.  
  
-   Запрос таких динамических административных представлений (DMV) для базовой диагностики, как sys.dm_tran_locks для состояния блокировки, sys.dm_os_memory_cache_counters для проверки исправности кэша, а sys.dm_exec_requests и sys.dm_exec_sessions для активных сеансов и запросов. Старайтесь не использовать динамические административные представления DMV, потребляющие много ресурсов (например, представление sys.dm_tran_version_store полностью просматривает хранилище версий, что может привести к резкому увеличению объема ввода-вывода) или использующие сложные соединения. Сведения о влиянии на производительность см. в документации к конкретному [динамическому административному представлению](../../relational-databases/views/views.md).  
  
-   Запрос представлений каталога.  
  
-   Основные команды DBCC, например DBCC FREEPROCCACHE, DBCC FREESYSTEMCACHE, DBCC DROPCLEANBUFFERS`,` а также DBCC SQLPERF. Не запускайте ресурсоемкие команды, такие как **DBCC** CHECKDB, DBCC DBREINDEX или DBCC SHRINKDATABASE.  
  
-   Команда [!INCLUDE[tsql](../../includes/tsql-md.md)]KILL *\<spid>* . В зависимости от состояния [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]команда KILL не всегда выполняется успешно. В этом случае единственным выходом остается перезапуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Рассмотрим несколько общих правил.  
  
    -   С помощью запроса `SELECT * FROM sys.dm_exec_sessions WHERE session_id = <spid>`убедитесь, что SPID был действительно отключен. Если строки не возвращаются, значит, сеанс был остановлен.  
  
    -   Если сеанс продолжается, проверьте с помощью запроса `SELECT * FROM sys.dm_os_tasks WHERE session_id = <spid>`наличие задач, назначенных для этого сеанса. Если задача присутствует, то, скорее всего, сеанс закрывается в настоящий момент. Заметьте, что это может занять немало времени и завершиться неуспешно.  
  
    -   Если в sys.dm_os_tasks нет задач, связанных с данным сеансом, но сеанс остается в sys.dm_exec_sessions после выполнения команды KILL, это означает, что отсутствует доступный рабочий процессор. Чтобы освободить рабочий поток, выберите одну из текущих задач (задача в представлении sys.dm_os_tasks со значением `sessions_id <> NULL`) и остановите связанный с ней сеанс. Заметьте, что остановка одного сеанса может оказаться недостаточной: может потребоваться остановить несколько сеансов.  
  
## <a name="dac-port"></a>Порт выделенного административного соединения  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выделенных административных соединений прослушивает TCP-порт 1434, если он доступен, или TCP-порт, динамически назначаемый при запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Журнал ошибок содержит номер порта, на котором ожидается выделенное административное соединение. По умолчанию, выделенное административное соединение ожидается только на местном порте. Образец кода, активирующего удаленные административные соединения, см. в разделе [Параметр конфигурации сервера "remote admin connections"](remote-admin-connections-server-configuration-option.md).  
  
 После настройки административного соединения средство прослушивания выделенных административных соединений включается без необходимости перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и клиент может удаленно подключиться к DAC. Средству прослушивания соединений DAC можно разрешить прием удаленных соединений, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отвечает. Для этого можно сначала подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] локально посредством выделенного административного соединения, а затем выполнить хранимую процедуру sp_configure для приема удаленных соединений.  
  
 В кластерных конфигурациях выделенное административное соединение по умолчанию выключено. Обеспечить доступ к удаленным соединениям средству прослушивания DAC пользователи могут с помощью хранимой процедуры sp_configure с параметром remote admin connection. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отвечает, а средство прослушивания выделенных административных соединений отключено, то для подключения к DAC, возможно, потребуется перезапустить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поэтому корпорация Майкрософт рекомендует включать вариант конфигурации remote admin connections в кластеризованных системах.  
  
 Порт выделенных административных соединений присваивается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] динамически во время запуска. При соединении с экземпляром по умолчанию DAC стремится не использовать запрос протокола разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSRP) к службе обозревателя SQL Server. Сначала выполняется попытка подключиться через TCP-порт 1434. В случае ошибки следует вызов SSRP на получение порта. Если браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не ожидает запросов SSRP, запрос на подключение возвращает ошибку. Обратитесь к журналу ошибок, чтобы найти номер порта, на котором ожидается выделенное административное соединение. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для приема удаленных административных подключений, выделенное административное соединение должно быть инициировано с явно указанным номером порта:  
  
 **sqlcmd-stcp:** _ \<server> , \<port> _  
  
 Журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приводит номер порта для выделенного административного соединения; по умолчанию он равен 1434. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для приема только локальных выделенных административных соединений, подключайтесь через адаптер замыкания на себя с использованием следующей команды:  
  
 **sqlcmd-s 127.0.0.1**,`1434`  
  
## <a name="example"></a>Пример  
 В этом примере администратор видит, что сервер `URAN123` не отвечает, и пытается определить неполадку. Для этого пользователь активирует программу командной строки `sqlcmd` и подключается к серверу `URAN123` с помощью ключа `-A` , чтобы обозначить выделенное административное соединение.  
  
 `sqlcmd -S URAN123 -U sa -P <xxx> -A`  
  
 Теперь администратор может запускать запросы для определения проблемы и, возможно, прекращения не отвечающих сеансов.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
## <a name="related-content"></a>См. также  
 [Использование программы sqlcmd с переменными скрипта](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)  
  
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)  
  
 [sp_who (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql)  
  
 [sp_lock (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-lock-transact-sql)  
  
 [KILL (Transact-SQL)](/sql/t-sql/language-elements/kill-transact-sql)  
  
 [DBCC CHECKALLOC (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)  
  
 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [DBCC OPENTRAN (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-opentran-transact-sql)  
  
 [DBCC INPUTBUFFER (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-inputbuffer-transact-sql)  
  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)  
  
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql)  
  
 [Флаги трассировки (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
