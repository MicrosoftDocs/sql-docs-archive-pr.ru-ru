---
title: Цель файла событий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- event file target
- file target [SQL Server extended events]
- targets [SQL Server extended events], file target
ms.assetid: 4f0ee6ec-a0a8-4c38-aa61-8293ab6ac7fd
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1a64236b3874543982be5abbd8e60d8169082a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732945"
---
# <a name="event-file-target"></a><span data-ttu-id="d2788-102">Event File Target</span><span class="sxs-lookup"><span data-stu-id="d2788-102">Event File Target</span></span>
  <span data-ttu-id="d2788-103">Цель «Файл событий» — это цель, осуществляющая запись всех буферов на диск.</span><span class="sxs-lookup"><span data-stu-id="d2788-103">The event file target is a target that writes complete buffers to disk.</span></span>  
  
 <span data-ttu-id="d2788-104">В следующей таблице описаны доступные параметры для настройки цели «Файл событий».</span><span class="sxs-lookup"><span data-stu-id="d2788-104">The following table describes the available options for configuring the event file target.</span></span>  
  
|<span data-ttu-id="d2788-105">Параметр</span><span class="sxs-lookup"><span data-stu-id="d2788-105">Option</span></span>|<span data-ttu-id="d2788-106">Допустимые значения</span><span class="sxs-lookup"><span data-stu-id="d2788-106">Allowed values</span></span>|<span data-ttu-id="d2788-107">Описание</span><span class="sxs-lookup"><span data-stu-id="d2788-107">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="d2788-108">filename</span><span class="sxs-lookup"><span data-stu-id="d2788-108">filename</span></span>|<span data-ttu-id="d2788-109">Любая строка длиной до 260 символов.</span><span class="sxs-lookup"><span data-stu-id="d2788-109">Any string up to 260 characters.</span></span> <span data-ttu-id="d2788-110">Это значение обязательно.</span><span class="sxs-lookup"><span data-stu-id="d2788-110">This value is required.</span></span>|<span data-ttu-id="d2788-111">Расположение и имя файла.</span><span class="sxs-lookup"><span data-stu-id="d2788-111">The file location and filename.</span></span><br /><br /> <span data-ttu-id="d2788-112">Можно использовать любое расширение имени файла.</span><span class="sxs-lookup"><span data-stu-id="d2788-112">You can use any filename extension.</span></span>|  
|<span data-ttu-id="d2788-113">max_file_size</span><span class="sxs-lookup"><span data-stu-id="d2788-113">max_file_size</span></span>|<span data-ttu-id="d2788-114">Любое 64-разрядное целое число.</span><span class="sxs-lookup"><span data-stu-id="d2788-114">Any 64 bit integer.</span></span> <span data-ttu-id="d2788-115">Это значение является необязательным.</span><span class="sxs-lookup"><span data-stu-id="d2788-115">This value is optional.</span></span>|<span data-ttu-id="d2788-116">Верхний предел размера файла в мегабайтах (МБ).</span><span class="sxs-lookup"><span data-stu-id="d2788-116">The maximum file size in megabytes (MB).</span></span> <span data-ttu-id="d2788-117">Если аргумент max_file_size не указан, файл будет увеличиваться до исчерпания пространства на диске.</span><span class="sxs-lookup"><span data-stu-id="d2788-117">If max_file_size is not specified, the file will grow until the disk is full.</span></span> <span data-ttu-id="d2788-118">Размер файла по умолчанию составляет 1 ГБ.</span><span class="sxs-lookup"><span data-stu-id="d2788-118">The default file size is 1GB.</span></span><br /><br /> <span data-ttu-id="d2788-119">Аргумент max_file_size должен быть больше по сравнению с текущим размером буфера сеанса.</span><span class="sxs-lookup"><span data-stu-id="d2788-119">max_file_size must be larger than the current size of the session buffers.</span></span> <span data-ttu-id="d2788-120">Иначе целевой файл нельзя будет инициализировать и появится сообщение о недопустимости значения параметра max_file_size.</span><span class="sxs-lookup"><span data-stu-id="d2788-120">If it is not, the file target will fail to initialize, reporting that the max_file_size is invalid.</span></span> <span data-ttu-id="d2788-121">Текущий размер буферов можно получить запросом к столбцу buffer_size в динамическом административном представлении [sys.dm_xe_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) .</span><span class="sxs-lookup"><span data-stu-id="d2788-121">To view the current size of the buffers, query the buffer_size column in the [sys.dm_xe_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) dynamic management view.</span></span><br /><br /> <span data-ttu-id="d2788-122">Если размер файла по умолчанию меньше размера буфера сеанса, рекомендуется задать для max_file_size значение, указанное в столбце max_memory представления каталога [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) .</span><span class="sxs-lookup"><span data-stu-id="d2788-122">If the default file size is smaller than the session buffer size, we recommend setting max_file_size to the value specified in the max_memory column in the [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) catalog view.</span></span><br /><br /> <span data-ttu-id="d2788-123">Если значение параметра max_file_size больше размера буферов сеанса, его можно округлить до ближайшей меньшей величины, кратной размеру буфера сеанса.</span><span class="sxs-lookup"><span data-stu-id="d2788-123">When max_file_size is set to a size larger than the size of the session buffers, it may be rounded down to the nearest multiple of the session buffer size.</span></span> <span data-ttu-id="d2788-124">Созданный в результате целевой файл по размеру может быть меньше заданной величины max_file_size.</span><span class="sxs-lookup"><span data-stu-id="d2788-124">This may create a target file that is smaller than the specified value of max_file_size.</span></span> <span data-ttu-id="d2788-125">Например, если размер буфера составляет 100 МБ, а max_file_size равен 150 МБ, размер результирующего файла округляется до меньшего значения 100 МБ, поскольку второй буфер не уместится в оставшихся 50 МБ.</span><span class="sxs-lookup"><span data-stu-id="d2788-125">For example, if the buffer size is 100MB and max_file_size is set to 150MB, the resultant file size is rounded down to 100MB because a second buffer would not fit in the remaining 50MB of space.</span></span><br /><br /> <span data-ttu-id="d2788-126">Если размер файла по умолчанию меньше размера буфера сеанса, рекомендуется задать для max_file_size значение, указанное в столбце max_memory представления каталога [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) .</span><span class="sxs-lookup"><span data-stu-id="d2788-126">If the default file size is smaller than the session buffer size, we recommend setting max_file_size to the value in the max_memory column in the [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) catalog view.</span></span>|  
|<span data-ttu-id="d2788-127">max_rollover_files</span><span class="sxs-lookup"><span data-stu-id="d2788-127">max_rollover_files</span></span>|<span data-ttu-id="d2788-128">Любое 32-разрядное целое число.</span><span class="sxs-lookup"><span data-stu-id="d2788-128">Any 32 bit integer.</span></span> <span data-ttu-id="d2788-129">Это значение является необязательным.</span><span class="sxs-lookup"><span data-stu-id="d2788-129">This value is optional.</span></span>|<span data-ttu-id="d2788-130">Максимальное число файлов, хранимых в файловой системе.</span><span class="sxs-lookup"><span data-stu-id="d2788-130">The maximum number of files to retain in the file system.</span></span> <span data-ttu-id="d2788-131">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="d2788-131">The default value is 5.</span></span>|  
|<span data-ttu-id="d2788-132">increment</span><span class="sxs-lookup"><span data-stu-id="d2788-132">increment</span></span>|<span data-ttu-id="d2788-133">Любое 32-разрядное целое число.</span><span class="sxs-lookup"><span data-stu-id="d2788-133">Any 32 bit integer.</span></span> <span data-ttu-id="d2788-134">Это значение является необязательным.</span><span class="sxs-lookup"><span data-stu-id="d2788-134">This value is optional.</span></span>|<span data-ttu-id="d2788-135">Шаг увеличения размера файла в мегабайтах (МБ).</span><span class="sxs-lookup"><span data-stu-id="d2788-135">The incremental growth, in megabytes (MB), for the file.</span></span> <span data-ttu-id="d2788-136">Если не указан, то значением по умолчанию будет двойной размер буфера сеанса.</span><span class="sxs-lookup"><span data-stu-id="d2788-136">If unspecified, the default value for increment is twice the session buffer size.</span></span>|  
  
 <span data-ttu-id="d2788-137">При первом создании цели "Файл событий" к заданному имени файла присоединяется _0\_ и длинное целое число.</span><span class="sxs-lookup"><span data-stu-id="d2788-137">The first time that an event file target is created, the filename you specify is appended with _0\_ and a long integer value.</span></span> <span data-ttu-id="d2788-138">Целочисленное значение вычисляется как число миллисекунд между 1 января 1601 и датой и временем создания файла.</span><span class="sxs-lookup"><span data-stu-id="d2788-138">The integer value is calculated as the number of milliseconds between January 1, 1601 and the date and time the file is created.</span></span> <span data-ttu-id="d2788-139">Последующие файлы продолжения используют тот же формат.</span><span class="sxs-lookup"><span data-stu-id="d2788-139">Subsequent rollover files also use this format.</span></span> <span data-ttu-id="d2788-140">Сравнив значения длинных целых, можно определить самый последний файл.</span><span class="sxs-lookup"><span data-stu-id="d2788-140">From examining the value of the long integer, you can determine the most current file.</span></span> <span data-ttu-id="d2788-141">В следующем примере показано, как происходит именование файлов в случае, если в качестве имени файла указано «C:\OutputFiles\MyOutput.xel»:</span><span class="sxs-lookup"><span data-stu-id="d2788-141">The following example illustrates how files are named in a scenario where you specify the filename option as C:\OutputFiles\MyOutput.xel:</span></span>  
  
-   <span data-ttu-id="d2788-142">первый созданный файл — C:\OutputFiles\MyOutput_0_128500310259380000.xel</span><span class="sxs-lookup"><span data-stu-id="d2788-142">first file created - C:\OutputFiles\MyOutput_0_128500310259380000.xel</span></span>  
  
-   <span data-ttu-id="d2788-143">первый файл продолжения — C:\OutputFiles\MyOutput_0_128505831770890000.xel</span><span class="sxs-lookup"><span data-stu-id="d2788-143">first rollover file - C:\OutputFiles\MyOutput_0_128505831770890000.xel</span></span>  
  
-   <span data-ttu-id="d2788-144">второй файл продолжения — C:\OutputFiles\MyOutput_0_132410772966237000.xel</span><span class="sxs-lookup"><span data-stu-id="d2788-144">second rollover file - C:\OutputFiles\MyOutput_0_132410772966237000.xel</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="d2788-145">Добавление цели к сеансу</span><span class="sxs-lookup"><span data-stu-id="d2788-145">Adding the Target to a Session</span></span>  
 <span data-ttu-id="d2788-146">Для добавления целевого файла событий в сеанс расширенных событий следует использовать следующую инструкцию при создании или изменении сеанса события, заменив *имя_файла* нужным именем файла и его расположением.</span><span class="sxs-lookup"><span data-stu-id="d2788-146">To add the event file target to an Extended Events session, you would include the following statements when you create or alter an event session, replacing *file_name* with the desired file name and path:</span></span>  
  
```  
ADD TARGET package0.event_file(  
   SET filename='file_name.xel')  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="d2788-147">Просмотр целевого вывода</span><span class="sxs-lookup"><span data-stu-id="d2788-147">Reviewing the Target Output</span></span>  
 <span data-ttu-id="d2788-148">Для просмотра результата цели "Файл" следует использовать функцию sys.fn_xe_file_target_read_file function.</span><span class="sxs-lookup"><span data-stu-id="d2788-148">To review the output from the file target, you must use the sys.fn_xe_file_target_read_file function.</span></span> <span data-ttu-id="d2788-149">Рекомендуется представлять данные в виде XML.</span><span class="sxs-lookup"><span data-stu-id="d2788-149">We recommend that you cast the data as XML.</span></span> <span data-ttu-id="d2788-150">Можно использовать следующий синтаксис, заменив *имя_файла* именем файла и его расположением, указанными при добавлении цели.</span><span class="sxs-lookup"><span data-stu-id="d2788-150">You can use the following syntax, replacing *file_name* with the file name and path that you specified when you added the target:</span></span>  
  
```  
SELECT *, CAST(event_data AS XML) AS 'event_data_XML'  
FROM sys.fn_xe_file_target_read_file('file_name*.xel', NULL, NULL, NULL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2788-151">См. также:</span><span class="sxs-lookup"><span data-stu-id="d2788-151">See Also</span></span>  
 <span data-ttu-id="d2788-152">[Цели расширенных событий SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="d2788-152">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="d2788-153">[sys. fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d2788-153">[sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql) </span></span>  
 <span data-ttu-id="d2788-154">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d2788-154">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="d2788-155">ALTER EVENT SESSION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d2788-155">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  