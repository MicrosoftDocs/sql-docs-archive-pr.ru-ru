---
title: Определение запросов, удерживающих блокировки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], extended events
- queries [SQL Server], holding locks
- xe
- extended events [SQL Server], locks
- extended events [SQL Server], holding locks
ms.assetid: bdfce092-3cf1-4b5e-99d5-fd8c6f9ad560
author: rothja
ms.author: jroth
ms.openlocfilehash: 1ecbee10f53ca2a45513bc3386940d96b7e82dce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666617"
---
# <a name="determine-which-queries-are-holding-locks"></a><span data-ttu-id="58db9-102">определить запросы, удерживающие блокировки</span><span class="sxs-lookup"><span data-stu-id="58db9-102">Determine Which Queries Are Holding Locks</span></span>
  <span data-ttu-id="58db9-103">Администраторам баз данных часто нужно определить источник блокировок, приводящих к ухудшению производительности базы данных.</span><span class="sxs-lookup"><span data-stu-id="58db9-103">Database administrators often need to identify the source of locks that are hindering database performance.</span></span>  
  
 <span data-ttu-id="58db9-104">Например, может возникнуть подозрение о том, что проблемы с производительностью сервера вызваны блокировками.</span><span class="sxs-lookup"><span data-stu-id="58db9-104">For example, you suspect that a performance issue on your server could be caused by blocking.</span></span> <span data-ttu-id="58db9-105">При выполнении запроса к sys.dm_exec_requests обнаруживается несколько приостановленных сеансов с типом ожидания, указывающим, что ожидаемым ресурсом является блокировка.</span><span class="sxs-lookup"><span data-stu-id="58db9-105">When you query the sys.dm_exec_requests, you find several sessions in a suspended mode with a wait type indicating that a lock is the resource being waited on.</span></span>  
  
 <span data-ttu-id="58db9-106">Результаты выполнения запроса к представлению sys.dm_tran_locks показывают наличие многих необработанных блокировок, но в представлении sys.dm_exec_requests у сеансов, которым были предоставлены блокировки, никаких активных запросов нет.</span><span class="sxs-lookup"><span data-stu-id="58db9-106">You query sys.dm_tran_locks and the results show that there are many locks outstanding, but the sessions that were granted the locks do not have any active requests showing in sys.dm_exec_requests.</span></span>  
  
 <span data-ttu-id="58db9-107">На этом примере продемонстрирован метод определения запроса, принявшего блокировку, плана запроса и стека [!INCLUDE[tsql](../../includes/tsql-md.md)] в момент принятия блокировки.</span><span class="sxs-lookup"><span data-stu-id="58db9-107">This example demonstrates a method of determining what query took the lock, the plan of the query, and the [!INCLUDE[tsql](../../includes/tsql-md.md)] stack at the time the lock was taken.</span></span> <span data-ttu-id="58db9-108">Этот пример также демонстрирует использование цели «Попарное разбиение событий» в сеансе расширенных событий.</span><span class="sxs-lookup"><span data-stu-id="58db9-108">This example also illustrates how the pairing target is used in an Extended Events session.</span></span>  
  
 <span data-ttu-id="58db9-109">Эта задача решается с помощью редактора запросов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для выполнения следующей процедуры.</span><span class="sxs-lookup"><span data-stu-id="58db9-109">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58db9-110">В примере используется база данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="58db9-110">This example uses the AdventureWorks database.</span></span>  
  
### <a name="to-determine-which-queries-are-holding-locks"></a><span data-ttu-id="58db9-111">Определение запросов, удерживающих блокировки</span><span class="sxs-lookup"><span data-stu-id="58db9-111">To determine which queries are holding locks</span></span>  
  
1.  <span data-ttu-id="58db9-112">В редакторе запросов выполните следующие инструкции.</span><span class="sxs-lookup"><span data-stu-id="58db9-112">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    -- Perform cleanup.   
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='FindBlockers')  
        DROP EVENT SESSION FindBlockers ON SERVER  
    GO  
    -- Use dynamic SQL to create the event session and allow creating a -- predicate on the AdventureWorks database id.  
    --  
    DECLARE @dbid int  
  
    SELECT @dbid = db_id('AdventureWorks')  
  
    IF @dbid IS NULL  
    BEGIN  
        RAISERROR('AdventureWorks is not installed. Install AdventureWorks before proceeding', 17, 1)  
        RETURN  
    END  
  
    DECLARE @sql nvarchar(1024)  
    SET @sql = '  
    CREATE EVENT SESSION FindBlockers ON SERVER  
    ADD EVENT sqlserver.lock_acquired   
        (action   
            ( sqlserver.sql_text, sqlserver.database_id, sqlserver.tsql_stack,  
             sqlserver.plan_handle, sqlserver.session_id)  
        WHERE ( database_id=' + cast(@dbid as nvarchar) + ' AND resource_0!=0)   
        ),  
    ADD EVENT sqlserver.lock_released   
        (WHERE ( database_id=' + cast(@dbid as nvarchar) + ' AND resource_0!=0 ))  
    ADD TARGET package0.pair_matching   
        ( SET begin_event=''sqlserver.lock_acquired'',   
                begin_matching_columns=''database_id, resource_0, resource_1, resource_2, transaction_id, mode'',   
                end_event=''sqlserver.lock_released'',   
                end_matching_columns=''database_id, resource_0, resource_1, resource_2, transaction_id, mode'',  
        respond_to_memory_pressure=1)  
    WITH (max_dispatch_latency = 1 seconds)'  
  
    EXEC (@sql)  
    --   
    -- Create the metadata for the event session  
    -- Start the event session  
    --  
    ALTER EVENT SESSION FindBlockers ON SERVER  
    STATE = START  
  
    ```  
  
2.  <span data-ttu-id="58db9-113">Чтобы выявить запросы, до сих пор удерживающие блокировки, после выполнения рабочей нагрузки на сервере выполните в редакторе запросов следующие инструкции.</span><span class="sxs-lookup"><span data-stu-id="58db9-113">After execution of a workload on the server, issue the following statements in Query Editor to find queries still holding locks.</span></span>  
  
    ```  
    --  
    -- The pair matching targets report current unpaired events using   
    -- the sys.dm_xe_session_targets dynamic management view (DMV)  
    -- in XML format.  
    -- The following query retrieves the data from the DMV and stores  
    -- key data in a temporary table to speed subsequent access and  
    -- retrieval.  
    --  
    SELECT   
    objlocks.value('(action[@name="session_id"]/value)[1]', 'int')  
            AS session_id,  
        objlocks.value('(data[@name="database_id"]/value)[1]', 'int')   
            AS database_id,  
        objlocks.value('(data[@name="resource_type"]/text)[1]', 'nvarchar(50)' )   
            AS resource_type,  
        objlocks.value('(data[@name="resource_0"]/value)[1]', 'bigint')   
            AS resource_0,  
        objlocks.value('(data[@name="resource_1"]/value)[1]', 'bigint')   
            AS resource_1,  
        objlocks.value('(data[@name="resource_2"]/value)[1]', 'bigint')   
            AS resource_2,  
        objlocks.value('(data[@name="mode"]/text)[1]', 'nvarchar(50)')   
            AS mode,  
        objlocks.value('(action[@name="sql_text"]/value)[1]', 'varchar(MAX)')   
            AS sql_text,  
        CAST(objlocks.value('(action[@name="plan_handle"]/value)[1]', 'varchar(MAX)') AS xml)   
            AS plan_handle,      
        CAST(objlocks.value('(action[@name="tsql_stack"]/value)[1]', 'varchar(MAX)') AS xml)   
            AS tsql_stack  
    INTO #unmatched_locks  
    FROM (  
        SELECT CAST(xest.target_data as xml)   
            lockinfo  
        FROM sys.dm_xe_session_targets xest  
        JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
        WHERE xest.target_name = 'pair_matching' AND xes.name = 'FindBlockers'  
    ) heldlocks  
    CROSS APPLY lockinfo.nodes('//event[@name="lock_acquired"]') AS T(objlocks)  
  
    --  
    -- Join the data acquired from the pairing target with other   
    -- DMVs to return provide additional information about blockers  
    --  
    SELECT ul.*  
        FROM #unmatched_locks ul  
        INNER JOIN sys.dm_tran_locks tl ON ul.database_id = tl.resource_database_id AND ul.resource_type = tl.resource_type  
        WHERE resource_0 IS NOT NULL  
        AND session_id IN   
            (SELECT blocking_session_id FROM sys.dm_exec_requests WHERE blocking_session_id != 0)  
        AND tl.request_status='wait'  
        AND REPLACE(ul.mode, 'LCK_M_', '' ) = tl.request_mode  
  
    ```  
  
3.  <span data-ttu-id="58db9-114">После определения проблем удалите все временные таблицы и сеанс события.</span><span class="sxs-lookup"><span data-stu-id="58db9-114">After identifying the issues, drop any temporary tables and the event session.</span></span>  
  
    ```  
    DROP TABLE #unmatched_locks  
    DROP EVENT SESSION FindBlockers ON SERVER  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="58db9-115">См. также:</span><span class="sxs-lookup"><span data-stu-id="58db9-115">See Also</span></span>  
 <span data-ttu-id="58db9-116">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58db9-116">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="58db9-117">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58db9-117">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 <span data-ttu-id="58db9-118">[DROP EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/drop-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58db9-118">[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql) </span></span>  
 <span data-ttu-id="58db9-119">[sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58db9-119">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 [<span data-ttu-id="58db9-120">sys.dm_xe_sessions (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="58db9-120">sys.dm_xe_sessions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql)  
  
  
