---
title: Средства расширенных событий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], using
- extended events [SQL Server], options for using
ms.assetid: d312a9ff-50ba-4721-baef-50bfd3169d38
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a74080352beeda4f92ad6afa7b8266a8ebee5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668859"
---
# <a name="extended-events-tools"></a>Средства расширенных событий
  Для создания сеансов расширенных событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и управления ими можно использовать следующие средства:  
  
-   Инструкции языка описания данных DDL. Позволяют создавать и изменять сеанс расширенных событий.  
  
-   Динамическое административное представление, представления каталогов и системные таблицы. Позволяют получать данные и метаданные сеансов с помощью инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] . Системные таблицы помогают определить существующие эквиваленты расширенных событий для классов и столбцов событий трассировки SQL.  
  
-   Узел **Расширенные события** в обозревателе объектов. Позволяет запускать, останавливать и удалять сеансы, а также импортировать и экспортировать шаблоны сеансов.  
  
-   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Предоставляет широкий набор функций для создания, изменения сеансов расширенных событий и управления ими. Дополнительные сведения см. в статье [Использование поставщика PowerShell для расширенных событий](use-the-powershell-provider-for-extended-events.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Позволяет создавать и выполнять образцы кода, приведенные в разделах справочника по расширенным событиям. Дополнительные сведения см. в статье [Семантический поиск](../../ssms/object/object-explorer.md).  
  
 Помимо сеансов, которые создает пользователь, на сервере существует системный сеанс по умолчанию для сбора данных о работоспособности системы. В этом сеансе собираются системные данные, которые можно использовать для решения проблем производительности. Дополнительные сведения см. в статье [Использование сеанса system_health](use-the-ssms-xe-profiler.md).  
  
## <a name="ddl-statements"></a>Инструкции DDL  
 Следующие инструкции DDL можно использовать для создания, изменения и удаления сеансов расширенных событий.  
  
|Имя|Описание|  
|----------|-----------------|  
|[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)|Создает объект сеанса расширенных событий, определяющий источник событий, цели и параметры сеанса событий.|  
|[ALTER EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/alter-event-session-transact-sql)|Запускает или останавливает сеанс событий или изменяет конфигурацию сеанса.|  
|[DROP EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/drop-event-session-transact-sql)|Удаляет сеанс событий.|  
  
## <a name="catalog-views"></a>Представления каталога  
 Следующие представления каталога используются для получения метаданных, сформированных при создании сеанса событий.  
  
|Имя|Описание|  
|----------|-----------------|  
|[sys.server_event_sessions (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql)|Содержит список определений всех сеансов событий.|  
|[sys.server_event_session_actions (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-event-session-actions-transact-sql)|Возвращает строку для каждого действия над каждым событием из сеанса событий.|  
|[sys.server_event_session_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-event-session-events-transact-sql)|Возвращает строку для каждого события в сеансе событий.|  
|[sys.server_event_session_fields (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-event-session-fields-transact-sql)|Возвращает строку для каждого настраиваемого столбца, явно установленного на события и цели.|  
|[sys.server_event_session_targets (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-event-session-targets-transact-sql)|Возвращает строку для каждой цели события для сеанса событий.|  
  
## <a name="dynamic-management-views"></a>Динамические административные представления  
 Следующие динамические административные представления используются для получения метаданных и данных сеанса. Метаданные получают из представлений каталога, а данные сеанса создаются при запуске и работе сеанса событий.  
  
> [!NOTE]  
>  Эти представления не содержат данных сеанса до запуска сеанса.  
  
|Имя|Описание|  
|----------|-----------------|  
|[sys.dm_os_dispatcher_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-dispatcher-pools-transact-sql)|Возвращает сведения о пулах диспетчера сеансов.|  
|[sys.dm_xe_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)|Возвращает строку для каждого объекта, представленного пакетом событий.|  
|[sys.dm_xe_object_columns (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql)|Возвращает сведения о схеме для всех объектов.|  
|[sys.dm_xe_packages (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)|Содержит список всех пакетов, зарегистрированных подсистемой расширенных событий.|  
|[sys.dm_xe_sessions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql)|Возвращает сведения об активном сеансе расширенных событий.|  
|[sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)|Возвращает сведения о целевых объектах сеанса.|  
|[sys.dm_xe_session_events (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-events-transact-sql)|Возвращает сведения о событиях сеанса.|  
|[sys.dm_xe_session_event_actions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-event-actions-transact-sql)|Возвращает сведения о действиях сеанса событий.|  
|[sys.dm_xe_map_values (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-map-values-transact-sql)|Содержит сопоставления внутренних цифровых ключей с понятным текстом.|  
|[sys.dm_xe_session_object_columns (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-object-columns-transact-sql)|Отображает значения конфигурации объектов, привязанных к сеансу.|  
  
## <a name="system-tables"></a>Системные таблицы  
 Следующие системные таблицы используются для получения сведений об эквивалентах расширенных событий для классов и столбцов событий трассировки SQL.  
  
|Имя|Описание|  
|----------|-----------------|  
|[trace_xe_event_map (Transact-SQL)](/sql/relational-databases/system-tables/extended-events-tables-trace-xe-event-map)|Содержит одну строку для каждого события из числа расширенных событий, сопоставленного с классом событий трассировки SQL.|  
|[trace_xe_action_map (Transact-SQL)](/sql/relational-databases/system-tables/extended-events-tables-trace-xe-action-map)|Содержит одну строку для каждого действия из числа расширенных событий, сопоставленного с идентификатором столбца трассировки SQL.|  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](../views/views.md)   
 [Представления каталога (Transact-SQL)](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)   
 [SQL Server таблиц расширенных событий &#40;&#41;Transact-SQL](/sql/relational-databases/system-tables/system-tables-transact-sql)   
 [Использование сеанса system_health](use-the-ssms-xe-profiler.md)   
 [Использование поставщика PowerShell для расширенных событий](use-the-powershell-provider-for-extended-events.md)  
  
  
