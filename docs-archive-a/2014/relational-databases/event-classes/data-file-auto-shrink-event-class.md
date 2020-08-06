---
title: Класс событий Data File Auto Shrink | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Data File Auto Shrink event class
ms.assetid: ea02b01e-9f87-47ca-9117-afadc382fb45
author: stevestein
ms.author: sstein
ms.openlocfilehash: eed8a4c35aba41af5b5fbc446e8275d14c8a9ca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655763"
---
# <a name="data-file-auto-shrink-event-class"></a><span data-ttu-id="064ef-102">Data File Auto Shrink, класс событий</span><span class="sxs-lookup"><span data-stu-id="064ef-102">Data File Auto Shrink Event Class</span></span>
  <span data-ttu-id="064ef-103">Класс событий **Data File Auto Shrink** сообщает, что файл данных был сжат.</span><span class="sxs-lookup"><span data-stu-id="064ef-103">The **Data File Auto Shrink** event class indicates that the data file has been shrunk.</span></span> <span data-ttu-id="064ef-104">Это событие не происходит при сжатии файла данных, вызванном выполнением инструкции ALTER DATABASE.</span><span class="sxs-lookup"><span data-stu-id="064ef-104">This event is not triggered if the data file shrinks because of an explicit ALTER DATABASE statement.</span></span> <span data-ttu-id="064ef-105">Включайте класс событий **Data File Auto Shrink** в трассировки, отслеживающие изменение размера файла данных.</span><span class="sxs-lookup"><span data-stu-id="064ef-105">Include the **Data File Auto Shrink** event class in traces that monitor the data file size changes.</span></span>  
  
 <span data-ttu-id="064ef-106">Вызываемая включением класса событий **Data File Auto Shrink** в трассировку дополнительная нагрузка незначительна, если сжатие файла данных не происходит часто.</span><span class="sxs-lookup"><span data-stu-id="064ef-106">When the **Data File Auto Shrink** event class is included in a trace, the amount of overhead incurred is low unless the data file frequently shrinks.</span></span>  
  
## <a name="data-file-auto-shrink-event-class-data-columns"></a><span data-ttu-id="064ef-107">Столбцы данных класса событий Data File Auto Shrink</span><span class="sxs-lookup"><span data-stu-id="064ef-107">Data File Auto Shrink Event Class Data Columns</span></span>  
  
|<span data-ttu-id="064ef-108">Имя столбца данных</span><span class="sxs-lookup"><span data-stu-id="064ef-108">Data Column Name</span></span>|<span data-ttu-id="064ef-109">Тип данных</span><span class="sxs-lookup"><span data-stu-id="064ef-109">Data Type</span></span>|<span data-ttu-id="064ef-110">Description</span><span class="sxs-lookup"><span data-stu-id="064ef-110">Description</span></span>|<span data-ttu-id="064ef-111">Идентификатор столбца</span><span class="sxs-lookup"><span data-stu-id="064ef-111">Column ID</span></span>|<span data-ttu-id="064ef-112">Фильтруемый</span><span class="sxs-lookup"><span data-stu-id="064ef-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="064ef-113">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="064ef-113">**ApplicationName**</span></span>|<span data-ttu-id="064ef-114">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="064ef-114">**nvarchar**</span></span>|<span data-ttu-id="064ef-115">Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="064ef-115">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="064ef-116">Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.</span><span class="sxs-lookup"><span data-stu-id="064ef-116">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="064ef-117">10</span><span class="sxs-lookup"><span data-stu-id="064ef-117">10</span></span>|<span data-ttu-id="064ef-118">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-118">Yes</span></span>|  
|<span data-ttu-id="064ef-119">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="064ef-119">**ClientProcessID**</span></span>|<span data-ttu-id="064ef-120">**Int**</span><span class="sxs-lookup"><span data-stu-id="064ef-120">**Int**</span></span>|<span data-ttu-id="064ef-121">Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="064ef-121">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="064ef-122">Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.</span><span class="sxs-lookup"><span data-stu-id="064ef-122">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="064ef-123">9</span><span class="sxs-lookup"><span data-stu-id="064ef-123">9</span></span>|<span data-ttu-id="064ef-124">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-124">Yes</span></span>|  
|<span data-ttu-id="064ef-125">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="064ef-125">**DatabaseID**</span></span>|<span data-ttu-id="064ef-126">**int**</span><span class="sxs-lookup"><span data-stu-id="064ef-126">**int**</span></span>|<span data-ttu-id="064ef-127">Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась.</span><span class="sxs-lookup"><span data-stu-id="064ef-127">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="064ef-128">отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен.</span><span class="sxs-lookup"><span data-stu-id="064ef-128">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="064ef-129">Определите значение для базы данных, используя функцию DB_ID.</span><span class="sxs-lookup"><span data-stu-id="064ef-129">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="064ef-130">3</span><span class="sxs-lookup"><span data-stu-id="064ef-130">3</span></span>|<span data-ttu-id="064ef-131">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-131">Yes</span></span>|  
|<span data-ttu-id="064ef-132">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="064ef-132">**DatabaseName**</span></span>|<span data-ttu-id="064ef-133">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="064ef-133">**nvarchar**</span></span>|<span data-ttu-id="064ef-134">Имя базы данных, в которой выполняется пользовательская инструкция.</span><span class="sxs-lookup"><span data-stu-id="064ef-134">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="064ef-135">35</span><span class="sxs-lookup"><span data-stu-id="064ef-135">35</span></span>|<span data-ttu-id="064ef-136">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-136">Yes</span></span>|  
|<span data-ttu-id="064ef-137">**Длительность**</span><span class="sxs-lookup"><span data-stu-id="064ef-137">**Duration**</span></span>|<span data-ttu-id="064ef-138">**bigint**</span><span class="sxs-lookup"><span data-stu-id="064ef-138">**bigint**</span></span>|<span data-ttu-id="064ef-139">Время (в миллисекундах), потребовавшееся для сжатия файла.</span><span class="sxs-lookup"><span data-stu-id="064ef-139">Time (in milliseconds) to shrink the file.</span></span>|<span data-ttu-id="064ef-140">13</span><span class="sxs-lookup"><span data-stu-id="064ef-140">13</span></span>|<span data-ttu-id="064ef-141">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-141">Yes</span></span>|  
|<span data-ttu-id="064ef-142">**EndTime**</span><span class="sxs-lookup"><span data-stu-id="064ef-142">**EndTime**</span></span>|<span data-ttu-id="064ef-143">**datetime**</span><span class="sxs-lookup"><span data-stu-id="064ef-143">**datetime**</span></span>|<span data-ttu-id="064ef-144">Время завершения автоматического сжатия.</span><span class="sxs-lookup"><span data-stu-id="064ef-144">Time that the auto shrink ended.</span></span>|<span data-ttu-id="064ef-145">18</span><span class="sxs-lookup"><span data-stu-id="064ef-145">18</span></span>|<span data-ttu-id="064ef-146">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-146">Yes</span></span>|  
|<span data-ttu-id="064ef-147">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="064ef-147">**EventClass**</span></span>|<span data-ttu-id="064ef-148">**int**</span><span class="sxs-lookup"><span data-stu-id="064ef-148">**int**</span></span>|<span data-ttu-id="064ef-149">Тип записанного события = 94.</span><span class="sxs-lookup"><span data-stu-id="064ef-149">Type of event recorded = 94.</span></span>|<span data-ttu-id="064ef-150">27</span><span class="sxs-lookup"><span data-stu-id="064ef-150">27</span></span>|<span data-ttu-id="064ef-151">нет</span><span class="sxs-lookup"><span data-stu-id="064ef-151">No</span></span>|  
|<span data-ttu-id="064ef-152">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="064ef-152">**EventSequence**</span></span>|<span data-ttu-id="064ef-153">**int**</span><span class="sxs-lookup"><span data-stu-id="064ef-153">**int**</span></span>|<span data-ttu-id="064ef-154">Порядковый номер класса событий в пакете.</span><span class="sxs-lookup"><span data-stu-id="064ef-154">Sequence of event class in batch.</span></span>|<span data-ttu-id="064ef-155">51</span><span class="sxs-lookup"><span data-stu-id="064ef-155">51</span></span>|<span data-ttu-id="064ef-156">нет</span><span class="sxs-lookup"><span data-stu-id="064ef-156">No</span></span>|  
|<span data-ttu-id="064ef-157">**Имя файла**</span><span class="sxs-lookup"><span data-stu-id="064ef-157">**Filename**</span></span>|<span data-ttu-id="064ef-158">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="064ef-158">**nvarchar**</span></span>|<span data-ttu-id="064ef-159">Логическое имя сжимаемого файла.</span><span class="sxs-lookup"><span data-stu-id="064ef-159">Logical name of the file being shrunk.</span></span>|<span data-ttu-id="064ef-160">36</span><span class="sxs-lookup"><span data-stu-id="064ef-160">36</span></span>|<span data-ttu-id="064ef-161">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-161">Yes</span></span>|  
|<span data-ttu-id="064ef-162">**HostName**</span><span class="sxs-lookup"><span data-stu-id="064ef-162">**HostName**</span></span>|<span data-ttu-id="064ef-163">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="064ef-163">**nvarchar**</span></span>|<span data-ttu-id="064ef-164">Имя компьютера, на котором выполняется клиентская программа.</span><span class="sxs-lookup"><span data-stu-id="064ef-164">Name of the computer on which the client is running.</span></span> <span data-ttu-id="064ef-165">Этот столбец данных заполняется, если клиент предоставляет имя узла.</span><span class="sxs-lookup"><span data-stu-id="064ef-165">This data column is populated if client provides the host name.</span></span> <span data-ttu-id="064ef-166">Чтобы определить имя узла, используйте функцию HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="064ef-166">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="064ef-167">8</span><span class="sxs-lookup"><span data-stu-id="064ef-167">8</span></span>|<span data-ttu-id="064ef-168">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-168">Yes</span></span>|  
|<span data-ttu-id="064ef-169">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="064ef-169">**IntegerData**</span></span>|<span data-ttu-id="064ef-170">**int**</span><span class="sxs-lookup"><span data-stu-id="064ef-170">**int**</span></span>|<span data-ttu-id="064ef-171">Количество 8-килобайтных страниц, на которое уменьшился размер файла.</span><span class="sxs-lookup"><span data-stu-id="064ef-171">Number of 8-KB pages by which the file was reduced.</span></span>|<span data-ttu-id="064ef-172">25</span><span class="sxs-lookup"><span data-stu-id="064ef-172">25</span></span>|<span data-ttu-id="064ef-173">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-173">Yes</span></span>|  
|<span data-ttu-id="064ef-174">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="064ef-174">**IsSystem**</span></span>|<span data-ttu-id="064ef-175">**int**</span><span class="sxs-lookup"><span data-stu-id="064ef-175">**int**</span></span>|<span data-ttu-id="064ef-176">Указывает, произошло событие в системном или в пользовательском процессе.</span><span class="sxs-lookup"><span data-stu-id="064ef-176">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="064ef-177">1 = системный, 0 = пользовательский.</span><span class="sxs-lookup"><span data-stu-id="064ef-177">1 = system, 0 = user.</span></span>|<span data-ttu-id="064ef-178">60</span><span class="sxs-lookup"><span data-stu-id="064ef-178">60</span></span>|<span data-ttu-id="064ef-179">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-179">Yes</span></span>|  
|<span data-ttu-id="064ef-180">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="064ef-180">**LoginName**</span></span>|<span data-ttu-id="064ef-181">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="064ef-181">**nvarchar**</span></span>|<span data-ttu-id="064ef-182">Имя входа пользователя (имя входа системы безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате ДОМЕН\имя_пользователя).</span><span class="sxs-lookup"><span data-stu-id="064ef-182">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\Username).</span></span>|<span data-ttu-id="064ef-183">11</span><span class="sxs-lookup"><span data-stu-id="064ef-183">11</span></span>|<span data-ttu-id="064ef-184">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-184">Yes</span></span>|  
|<span data-ttu-id="064ef-185">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="064ef-185">**LoginSid**</span></span>|<span data-ttu-id="064ef-186">**image**</span><span class="sxs-lookup"><span data-stu-id="064ef-186">**image**</span></span>|<span data-ttu-id="064ef-187">Идентификатор безопасности вошедшего в систему пользователя.</span><span class="sxs-lookup"><span data-stu-id="064ef-187">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="064ef-188">Эти сведения можно найти в представлении каталога **sys.server_principals** .</span><span class="sxs-lookup"><span data-stu-id="064ef-188">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="064ef-189">Значение идентификатора безопасности уникально для каждого имени входа на сервере.</span><span class="sxs-lookup"><span data-stu-id="064ef-189">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="064ef-190">41</span><span class="sxs-lookup"><span data-stu-id="064ef-190">41</span></span>|<span data-ttu-id="064ef-191">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-191">Yes</span></span>|  
|<span data-ttu-id="064ef-192">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="064ef-192">**NTDomainName**</span></span>|<span data-ttu-id="064ef-193">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="064ef-193">**nvarchar**</span></span>|<span data-ttu-id="064ef-194">Домен Windows, к которому принадлежит пользователь.</span><span class="sxs-lookup"><span data-stu-id="064ef-194">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="064ef-195">7</span><span class="sxs-lookup"><span data-stu-id="064ef-195">7</span></span>|<span data-ttu-id="064ef-196">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-196">Yes</span></span>|  
|<span data-ttu-id="064ef-197">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="064ef-197">**ServerName**</span></span>|<span data-ttu-id="064ef-198">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="064ef-198">**nvarchar**</span></span>|<span data-ttu-id="064ef-199">Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.</span><span class="sxs-lookup"><span data-stu-id="064ef-199">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="064ef-200">26</span><span class="sxs-lookup"><span data-stu-id="064ef-200">26</span></span>|<span data-ttu-id="064ef-201">нет</span><span class="sxs-lookup"><span data-stu-id="064ef-201">No</span></span>|  
|<span data-ttu-id="064ef-202">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="064ef-202">**SessionLoginName**</span></span>|<span data-ttu-id="064ef-203">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="064ef-203">**nvarchar**</span></span>|<span data-ttu-id="064ef-204">Имя входа пользователя, создавшего этот сеанс.</span><span class="sxs-lookup"><span data-stu-id="064ef-204">Login name of the user who originated the session.</span></span> <span data-ttu-id="064ef-205">Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2".</span><span class="sxs-lookup"><span data-stu-id="064ef-205">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="064ef-206">В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.</span><span class="sxs-lookup"><span data-stu-id="064ef-206">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="064ef-207">64</span><span class="sxs-lookup"><span data-stu-id="064ef-207">64</span></span>|<span data-ttu-id="064ef-208">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-208">Yes</span></span>|  
|<span data-ttu-id="064ef-209">**SPID**</span><span class="sxs-lookup"><span data-stu-id="064ef-209">**SPID**</span></span>|<span data-ttu-id="064ef-210">**int**</span><span class="sxs-lookup"><span data-stu-id="064ef-210">**int**</span></span>|<span data-ttu-id="064ef-211">Идентификатор сеанса, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="064ef-211">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="064ef-212">12</span><span class="sxs-lookup"><span data-stu-id="064ef-212">12</span></span>|<span data-ttu-id="064ef-213">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-213">Yes</span></span>|  
|<span data-ttu-id="064ef-214">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="064ef-214">**StartTime**</span></span>|<span data-ttu-id="064ef-215">**datetime**</span><span class="sxs-lookup"><span data-stu-id="064ef-215">**datetime**</span></span>|<span data-ttu-id="064ef-216">Время начала события, если оно известно.</span><span class="sxs-lookup"><span data-stu-id="064ef-216">Time at which the event started, if available.</span></span>|<span data-ttu-id="064ef-217">14</span><span class="sxs-lookup"><span data-stu-id="064ef-217">14</span></span>|<span data-ttu-id="064ef-218">Да</span><span class="sxs-lookup"><span data-stu-id="064ef-218">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="064ef-219">См. также:</span><span class="sxs-lookup"><span data-stu-id="064ef-219">See Also</span></span>  
 <span data-ttu-id="064ef-220">[Расширенные события](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="064ef-220">[Extended Events](../extended-events/extended-events.md) </span></span>  
 [<span data-ttu-id="064ef-221">Хранимая процедура sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="064ef-221">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  