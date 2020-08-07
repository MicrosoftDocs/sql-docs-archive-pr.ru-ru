---
title: Мониторинг и устранение неполадок управляемых объектов базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], performance
- monitoring [CLR integration]
- performance [CLR integration]
ms.assetid: a7b589ac-104d-4b68-b4aa-9f5fc192b13d
author: rothja
ms.author: jroth
ms.openlocfilehash: a7efbc045fc5f152f98ba7dbf2dfc686ff5e86a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734153"
---
# <a name="monitoring-and-troubleshooting-managed-database-objects"></a>Наблюдение и устранение неполадок в управляемых объектах базы данных
  Данный раздел содержит информацию о средствах, которые можно использовать для наблюдения и диагностики управляемых объектов базы данных и сборок, работающих в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="profiler-trace-events"></a>События трассировки профайлера  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет приложение трассировки SQL и уведомления о событиях для мониторинга событий компонента Database Engine. Записывая указанные события, приложение трассировки SQL помогает диагностировать проблемы производительности, проводить аудит активности базы данных, собирать образцы данных для тестовой среды, отлаживать инструкции и хранимые процедуры [!INCLUDE[tsql](../../../includes/tsql-md.md)] и собирать данные для инструментов анализа производительности. Дополнительные сведения см. в разделе [SQL Trace](../sql-trace/sql-trace.md) и [Расширенные события](../extended-events/extended-events.md).  
  
|Событие|Описание|  
|-----------|-----------------|  
|[Класс событий Assembly Load](../../database-engine/assembly-load-event-class.md)|Используется для наблюдения за запросами на загрузку сборок (успех или неудача).|  
|[SQL: BatchStarting](../event-classes/sql-batchstarting-event-class.md), класс событий [SQL: BatchCompleted](../event-classes/sql-batchcompleted-event-class.md)|Предоставляет сведения о пакетах [!INCLUDE[tsql](../../../includes/tsql-md.md)], которые начали или завершили работу.|  
|Класс событий [SP: Starting](../event-classes/sp-starting-event-class.md), [SP: Completed](../event-classes/sp-completed-event-class.md)|Используется для наблюдения за выполнением хранимых процедур [!INCLUDE[tsql](../../../includes/tsql-md.md)].|  
|[SQL: StmtStarting](../event-classes/sql-stmtstarting-event-class.md), класс событий [SQL: StmtCompleted](../event-classes/sql-stmtcompleted-event-class.md)|Используется для наблюдения за выполнением процедур [!INCLUDE[tsql](../../../includes/tsql-md.md)] и среды CLR.|  
  
## <a name="performance-counters"></a>Счетчики производительности  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет объекты и счетчики, которые могут применяться системным монитором для отслеживания активности на компьютере, где запущен экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Объект представляет собой любой ресурс [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], например блокировку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или процесс Windows. В каждом объекте содержатся один или более счетчиков, определяющих различные аспекты объектов для мониторинга. Дополнительные сведения см. в разделе [Использование объектов SQL Server](../performance-monitor/use-sql-server-objects.md).  
  
|Объект|Описание|  
|------------|-----------------|  
|[SQL Server, объект «Среда CLR»](../performance-monitor/sql-server-clr-object.md)|Общее время выполнения в среде CLR.|  
  
## <a name="windows-system-monitor-perfmonexe-counters"></a>Счетчики системного монитора Windows (PERFMON.EXE)  
 Системный монитор Windows (PERFMON.EXE) имеет несколько счетчиков производительности, которые можно использовать для наблюдения за приложениями интеграции со средой CLR. Счетчики производительности .NET CLR можно отфильтровать по имени процесса «sqlservr» для слежения за приложениями интеграции со средой CLR, выполняющимися в данный момент.  
  
|Объект производительности|Описание|  
|------------------------|-----------------|  
|SqlServer:CLR|Предоставляет статистику по ЦП сервера.|  
|Исключения .NET CLR|Следит за числом исключений в секунду.|  
|Загрузка .NET CLR|Предоставляет данные о доменах приложений и сборках, загруженных на сервере.|  
|Память .NET CLR|Предоставляет сведения об использовании памяти в среде CLR. Этот объект можно использовать для создания предупреждений, если объем используемой памяти слишком сильно вырос.|  
|Поставщик данных .NET для SQL Server|Следит за числом создаваемых и разрываемых соединений в секунду. Этот объект можно использовать для наблюдения за уровнем активности базы данных.|  
  
## <a name="catalog-views"></a>Представления каталога  
 Представления каталога возвращают данные, используемые компонентом Database Engine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Рекомендуется, чтобы использовались представления каталога, потому что они имеют наиболее универсальный интерфейс к метаданным каталога и предоставляют наиболее эффективный способ для получения, преобразования и представления настроенных форм этих данных. Все доступные для пользователя метаданные каталога предоставляются через представления каталога. Дополнительные сведения см. в разделе [Представления каталога (Transact-SQL)](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql).  
  
|Представление каталога|Описание|  
|------------------|-----------------|  
|[sys. assemblies &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-assemblies-transact-sql)|Возвращает сведения о сборках, зарегистрированных в базе данных.|  
|[sys. assembly_references &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-references-transact-sql)|Указывает сборки, которые содержат ссылки на другие сборки.|  
|[sys.assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)|Возвращает информацию обо всех функциях, хранимых процедурах и триггерах, определенных в сборке.|  
|[sys. assembly_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-files-transact-sql)|Возвращает сведения о файлах сборок, зарегистрированных в базе данных.|  
|[sys. assembly_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-types-transact-sql)|Указывает определяемые пользователем типы (UDT), определенные в сборке.|  
|[sys. module_assembly_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-module-assembly-usages-transact-sql)|Указывает сборки, в которых определены модули CLR.|  
|[sys.parameter_type_usages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql)|Возвращает информацию о параметрах, которые представляют собой определяемые пользователем типы.|  
|[sys.server_assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)|Указывает сборки, в которых определен триггер CLR.|  
|[sys.server_triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)|Указывает триггеры DDL уровня сервера на сервере, в том числе триггеры CLR.|  
|[sys. type_assembly_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-type-assembly-usages-transact-sql)|Указывает сборки, в которых определены определяемые пользователем типы.|  
|[sys.types (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-types-transact-sql)|Возвращает системные типы и определяемые пользователем типы, зарегистрированные в базе данных.|  
  
## <a name="dynamic-management-views"></a>Динамические административные представления  
 Динамические административные представления и функции возвращают данные о состоянии сервера, которые могут использоваться для контроля исправности экземпляра сервера, диагностики проблем и настройки производительности. Дополнительные сведения см. в разделе [динамические административные представления и функции &#40;&#41;Transact-SQL ](../views/views.md).  
  
|DMV|Описание|  
|---------|-----------------|  
|[sys. dm_clr_appdomains &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql)|Возвращает сведения о каждом домене приложения на сервере.|  
|[sys. dm_clr_loaded_assemblies &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql)|Указывает все управляемые сборки, зарегистрированные на сервере.|  
|[sys. dm_clr_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-properties-transact-sql)|Возвращает сведения о внутрипроцессной среде CLR.|  
|[sys. dm_clr_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-tasks-transact-sql)|Указывает общее число задач CLR, выполняющихся в настоящий момент.|  
|[sys.dm_exec_cached_plans (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql)|Возвращает сведения о планах выполнения запросов, кэшируемых [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для более быстрого выполнения запросов.|  
|[sys.dm_exec_query_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)|Возвращает суммарную статистику производительности для кэшированных планов запросов.|  
|[sys.dm_exec_requests (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql)|Возвращает сведения о каждом из запросов, выполняющихся в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[sys. dm_os_memory_clerks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql)|Возвращает все клерки памяти, активные в настоящее время в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в том числе клерки памяти CLR.|  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
