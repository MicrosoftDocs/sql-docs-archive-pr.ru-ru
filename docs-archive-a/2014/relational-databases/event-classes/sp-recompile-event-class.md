---
title: Класс событий SP:Recompile | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SP:Recompile event class
ms.assetid: 526c8eae-a07b-4d0e-b91e-8e537835d77d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 12a8be61673183adf6556bd093ffe92d3d65e699
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728293"
---
# <a name="sprecompile-event-class"></a><span data-ttu-id="5feda-102">SP:Recompile, класс событий</span><span class="sxs-lookup"><span data-stu-id="5feda-102">SP:Recompile Event Class</span></span>
  <span data-ttu-id="5feda-103">События класса SP:Recompile указывают на то, что хранимая процедура, триггер или пользовательская функция были перекомпилированы.</span><span class="sxs-lookup"><span data-stu-id="5feda-103">The SP:Recompile event class indicates that a stored procedure, trigger, or user-defined function has been recompiled.</span></span> <span data-ttu-id="5feda-104">Перекомпиляции, о которых сообщают события этого класса, производятся на уровне инструкций.</span><span class="sxs-lookup"><span data-stu-id="5feda-104">Recompilations reported by this event class occur at the statement level.</span></span>  
  
 <span data-ttu-id="5feda-105">Трассировать повторные компиляции на уровне инструкций предпочтительнее с помощью класса событий SQL:StmtRecompile.</span><span class="sxs-lookup"><span data-stu-id="5feda-105">The preferred way to trace statement-level recompilations is to use the SQL:StmtRecompile event class.</span></span> <span data-ttu-id="5feda-106">Класс событий SP:Recompile использовать не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="5feda-106">The SP:Recompile event class is deprecated.</span></span> <span data-ttu-id="5feda-107">Дополнительные сведения см. в статье [SQL:StmtRecompile Event Class](sql-stmtrecompile-event-class.md).</span><span class="sxs-lookup"><span data-stu-id="5feda-107">For more information, see [SQL:StmtRecompile Event Class](sql-stmtrecompile-event-class.md).</span></span>  
  
## <a name="sprecompile-event-class-data-columns"></a><span data-ttu-id="5feda-108">Столбцы данных класса событий SP:Recompile</span><span class="sxs-lookup"><span data-stu-id="5feda-108">SP:Recompile Event Class Data Columns</span></span>  
  
|<span data-ttu-id="5feda-109">Имя столбца данных</span><span class="sxs-lookup"><span data-stu-id="5feda-109">Data column name</span></span>|`Data type`|<span data-ttu-id="5feda-110">Описание</span><span class="sxs-lookup"><span data-stu-id="5feda-110">Description</span></span>|<span data-ttu-id="5feda-111">Идентификатор столбца</span><span class="sxs-lookup"><span data-stu-id="5feda-111">Column ID</span></span>|<span data-ttu-id="5feda-112">Фильтруемый</span><span class="sxs-lookup"><span data-stu-id="5feda-112">Filterable</span></span>|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|<span data-ttu-id="5feda-113">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="5feda-113">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="5feda-114">Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5feda-114">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5feda-115">Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.</span><span class="sxs-lookup"><span data-stu-id="5feda-115">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="5feda-116">10</span><span class="sxs-lookup"><span data-stu-id="5feda-116">10</span></span>|<span data-ttu-id="5feda-117">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-117">Yes</span></span>|  
|<span data-ttu-id="5feda-118">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="5feda-118">ClientProcessID</span></span>|`int`|<span data-ttu-id="5feda-119">Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="5feda-119">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="5feda-120">Заполнение этого столбца данных производится в том случае, если клиент предоставляет идентификатор процесса.</span><span class="sxs-lookup"><span data-stu-id="5feda-120">This data column is populated if the client provides the process ID.</span></span>|<span data-ttu-id="5feda-121">9</span><span class="sxs-lookup"><span data-stu-id="5feda-121">9</span></span>|<span data-ttu-id="5feda-122">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-122">Yes</span></span>|  
|<span data-ttu-id="5feda-123">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="5feda-123">DatabaseID</span></span>|`int`|<span data-ttu-id="5feda-124">Идентификатор базы данных, в которой выполняется хранимая процедура.</span><span class="sxs-lookup"><span data-stu-id="5feda-124">ID of the database in which the stored procedure is running.</span></span> <span data-ttu-id="5feda-125">Определите значение для базы данных, используя функцию DB_ID.</span><span class="sxs-lookup"><span data-stu-id="5feda-125">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="5feda-126">3</span><span class="sxs-lookup"><span data-stu-id="5feda-126">3</span></span>|<span data-ttu-id="5feda-127">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-127">Yes</span></span>|  
|<span data-ttu-id="5feda-128">имя_базы_данных</span><span class="sxs-lookup"><span data-stu-id="5feda-128">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="5feda-129">Имя базы данных, в которой выполняется хранимая процедура.</span><span class="sxs-lookup"><span data-stu-id="5feda-129">Name of the database in which the stored procedure is running.</span></span>|<span data-ttu-id="5feda-130">35</span><span class="sxs-lookup"><span data-stu-id="5feda-130">35</span></span>|<span data-ttu-id="5feda-131">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-131">Yes</span></span>|  
|<span data-ttu-id="5feda-132">EventClass</span><span class="sxs-lookup"><span data-stu-id="5feda-132">EventClass</span></span>|`int`|<span data-ttu-id="5feda-133">Тип события = 37.</span><span class="sxs-lookup"><span data-stu-id="5feda-133">Type of event = 37.</span></span>|<span data-ttu-id="5feda-134">27</span><span class="sxs-lookup"><span data-stu-id="5feda-134">27</span></span>|<span data-ttu-id="5feda-135">Нет</span><span class="sxs-lookup"><span data-stu-id="5feda-135">No</span></span>|  
|<span data-ttu-id="5feda-136">EventSequence</span><span class="sxs-lookup"><span data-stu-id="5feda-136">EventSequence</span></span>|`int`|<span data-ttu-id="5feda-137">Порядковый номер данного события в запросе.</span><span class="sxs-lookup"><span data-stu-id="5feda-137">The sequence of a given event within the request.</span></span>|<span data-ttu-id="5feda-138">51</span><span class="sxs-lookup"><span data-stu-id="5feda-138">51</span></span>|<span data-ttu-id="5feda-139">Нет</span><span class="sxs-lookup"><span data-stu-id="5feda-139">No</span></span>|  
|<span data-ttu-id="5feda-140">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="5feda-140">EventSubClass</span></span>|`int`|<span data-ttu-id="5feda-141">Тип подкласса события.</span><span class="sxs-lookup"><span data-stu-id="5feda-141">Type of event subclass.</span></span> <span data-ttu-id="5feda-142">Указывает причину перекомпиляции.</span><span class="sxs-lookup"><span data-stu-id="5feda-142">Indicates the reason for recompilation.</span></span><br /><br /> <span data-ttu-id="5feda-143">1 = изменение схемы</span><span class="sxs-lookup"><span data-stu-id="5feda-143">1 = Schema Changed</span></span><br /><br /> <span data-ttu-id="5feda-144">2 = изменение статистики</span><span class="sxs-lookup"><span data-stu-id="5feda-144">2 = Statistics Changed</span></span><br /><br /> <span data-ttu-id="5feda-145">3 = перекомпиляция с разрешением имен</span><span class="sxs-lookup"><span data-stu-id="5feda-145">3 = Recompile DNR</span></span><br /><br /> <span data-ttu-id="5feda-146">4 = изменение установленного параметра</span><span class="sxs-lookup"><span data-stu-id="5feda-146">4 = Set Option Changed</span></span><br /><br /> <span data-ttu-id="5feda-147">5 = изменение временной таблицы</span><span class="sxs-lookup"><span data-stu-id="5feda-147">5 = Temp Table Changed</span></span><br /><br /> <span data-ttu-id="5feda-148">6 = изменение удаленного набора строк</span><span class="sxs-lookup"><span data-stu-id="5feda-148">6 = Remote Rowset Changed</span></span><br /><br /> <span data-ttu-id="5feda-149">7 = изменение разрешений на обзор</span><span class="sxs-lookup"><span data-stu-id="5feda-149">7 = For Browse Perms Changed</span></span><br /><br /> <span data-ttu-id="5feda-150">8 = изменение среды уведомлений о запросах</span><span class="sxs-lookup"><span data-stu-id="5feda-150">8 = Query Notification Environment Changed</span></span><br /><br /> <span data-ttu-id="5feda-151">9 = изменение представления MPI</span><span class="sxs-lookup"><span data-stu-id="5feda-151">9 = MPI View Changed</span></span><br /><br /> <span data-ttu-id="5feda-152">10 = изменение параметров курсора</span><span class="sxs-lookup"><span data-stu-id="5feda-152">10 = Cursor Options Changed</span></span><br /><br /> <span data-ttu-id="5feda-153">11 = по значению параметра перекомпиляции</span><span class="sxs-lookup"><span data-stu-id="5feda-153">11 = With Recompile Option</span></span>|<span data-ttu-id="5feda-154">21</span><span class="sxs-lookup"><span data-stu-id="5feda-154">21</span></span>|<span data-ttu-id="5feda-155">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-155">Yes</span></span>|  
|<span data-ttu-id="5feda-156">GroupID</span><span class="sxs-lookup"><span data-stu-id="5feda-156">GroupID</span></span>|`int`|<span data-ttu-id="5feda-157">Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.</span><span class="sxs-lookup"><span data-stu-id="5feda-157">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="5feda-158">66</span><span class="sxs-lookup"><span data-stu-id="5feda-158">66</span></span>|<span data-ttu-id="5feda-159">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-159">Yes</span></span>|  
|<span data-ttu-id="5feda-160">HostName</span><span class="sxs-lookup"><span data-stu-id="5feda-160">HostName</span></span>|`nvarchar`|<span data-ttu-id="5feda-161">Имя компьютера, на котором выполняется клиентская программа.</span><span class="sxs-lookup"><span data-stu-id="5feda-161">Name of the computer on which the client is running.</span></span> <span data-ttu-id="5feda-162">Этот столбец данных заполняется, если клиент предоставляет имя узла.</span><span class="sxs-lookup"><span data-stu-id="5feda-162">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="5feda-163">Чтобы определить имя узла, используйте функцию HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="5feda-163">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="5feda-164">8</span><span class="sxs-lookup"><span data-stu-id="5feda-164">8</span></span>|<span data-ttu-id="5feda-165">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-165">Yes</span></span>|  
|<span data-ttu-id="5feda-166">IntegerData2</span><span class="sxs-lookup"><span data-stu-id="5feda-166">IntegerData2</span></span>|`int`|<span data-ttu-id="5feda-167">Конечное смещение инструкции внутри хранимой процедуры или пакета, вызвавшего повторную компиляцию.</span><span class="sxs-lookup"><span data-stu-id="5feda-167">Ending offset of the statement within the stored procedure or batch that caused recompilation.</span></span> <span data-ttu-id="5feda-168">Конечное смещение равно -1 в том случае, если инструкция является последней инструкцией в пакете.</span><span class="sxs-lookup"><span data-stu-id="5feda-168">Ending offset is -1 if the statement is the last statement in its batch.</span></span>|<span data-ttu-id="5feda-169">55</span><span class="sxs-lookup"><span data-stu-id="5feda-169">55</span></span>|<span data-ttu-id="5feda-170">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-170">Yes</span></span>|  
|<span data-ttu-id="5feda-171">IsSystem</span><span class="sxs-lookup"><span data-stu-id="5feda-171">IsSystem</span></span>|`int`|<span data-ttu-id="5feda-172">Указывает, произошло событие в системном или в пользовательском процессе.</span><span class="sxs-lookup"><span data-stu-id="5feda-172">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="5feda-173">1 = системный, 0 = пользовательский.</span><span class="sxs-lookup"><span data-stu-id="5feda-173">1 = system, 0 = user.</span></span>|<span data-ttu-id="5feda-174">60</span><span class="sxs-lookup"><span data-stu-id="5feda-174">60</span></span>|<span data-ttu-id="5feda-175">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-175">Yes</span></span>|  
|<span data-ttu-id="5feda-176">LoginName</span><span class="sxs-lookup"><span data-stu-id="5feda-176">LoginName</span></span>|`nvarchar`|<span data-ttu-id="5feda-177">Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).</span><span class="sxs-lookup"><span data-stu-id="5feda-177">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="5feda-178">11</span><span class="sxs-lookup"><span data-stu-id="5feda-178">11</span></span>|<span data-ttu-id="5feda-179">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-179">Yes</span></span>|  
|<span data-ttu-id="5feda-180">LoginSid</span><span class="sxs-lookup"><span data-stu-id="5feda-180">LoginSid</span></span>|`image`|<span data-ttu-id="5feda-181">Идентификатор безопасности вошедшего в систему пользователя.</span><span class="sxs-lookup"><span data-stu-id="5feda-181">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="5feda-182">Эти сведения можно найти в представлении каталога sys.server_principals.</span><span class="sxs-lookup"><span data-stu-id="5feda-182">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="5feda-183">Значение идентификатора безопасности уникально для каждого имени входа на сервере.</span><span class="sxs-lookup"><span data-stu-id="5feda-183">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="5feda-184">41</span><span class="sxs-lookup"><span data-stu-id="5feda-184">41</span></span>|<span data-ttu-id="5feda-185">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-185">Yes</span></span>|  
|<span data-ttu-id="5feda-186">NestLevel</span><span class="sxs-lookup"><span data-stu-id="5feda-186">NestLevel</span></span>|`int`|<span data-ttu-id="5feda-187">Уровень вложенности хранимой процедуры.</span><span class="sxs-lookup"><span data-stu-id="5feda-187">The nesting level of the stored procedure.</span></span>|<span data-ttu-id="5feda-188">29</span><span class="sxs-lookup"><span data-stu-id="5feda-188">29</span></span>|<span data-ttu-id="5feda-189">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-189">Yes</span></span>|  
|<span data-ttu-id="5feda-190">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="5feda-190">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="5feda-191">Домен Windows, к которому принадлежит пользователь.</span><span class="sxs-lookup"><span data-stu-id="5feda-191">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="5feda-192">7</span><span class="sxs-lookup"><span data-stu-id="5feda-192">7</span></span>|<span data-ttu-id="5feda-193">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-193">Yes</span></span>|  
|<span data-ttu-id="5feda-194">NTUserName</span><span class="sxs-lookup"><span data-stu-id="5feda-194">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="5feda-195">Имя пользователя Windows.</span><span class="sxs-lookup"><span data-stu-id="5feda-195">Windows user name.</span></span>|<span data-ttu-id="5feda-196">6</span><span class="sxs-lookup"><span data-stu-id="5feda-196">6</span></span>|<span data-ttu-id="5feda-197">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-197">Yes</span></span>|  
|<span data-ttu-id="5feda-198">ObjectID</span><span class="sxs-lookup"><span data-stu-id="5feda-198">ObjectID</span></span>|`int`|<span data-ttu-id="5feda-199">Назначенный системой идентификатор хранимой процедуры.</span><span class="sxs-lookup"><span data-stu-id="5feda-199">System-assigned ID of the stored procedure.</span></span>|<span data-ttu-id="5feda-200">22</span><span class="sxs-lookup"><span data-stu-id="5feda-200">22</span></span>|<span data-ttu-id="5feda-201">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-201">Yes</span></span>|  
|<span data-ttu-id="5feda-202">ObjectName</span><span class="sxs-lookup"><span data-stu-id="5feda-202">ObjectName</span></span>|`nvarchar`|<span data-ttu-id="5feda-203">Имя объекта, запустившего повторную компиляцию.</span><span class="sxs-lookup"><span data-stu-id="5feda-203">Name of the object that triggered the recompile.</span></span>|<span data-ttu-id="5feda-204">34</span><span class="sxs-lookup"><span data-stu-id="5feda-204">34</span></span>|<span data-ttu-id="5feda-205">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-205">Yes</span></span>|  
|<span data-ttu-id="5feda-206">ObjectType</span><span class="sxs-lookup"><span data-stu-id="5feda-206">ObjectType</span></span>|`int`|<span data-ttu-id="5feda-207">Значение, представляющее тип объекта, связанного с событием.</span><span class="sxs-lookup"><span data-stu-id="5feda-207">Value that represents the type of object involved in the event.</span></span> <span data-ttu-id="5feda-208">Дополнительные сведения см. в статье [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span><span class="sxs-lookup"><span data-stu-id="5feda-208">For more information, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="5feda-209">28</span><span class="sxs-lookup"><span data-stu-id="5feda-209">28</span></span>|<span data-ttu-id="5feda-210">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-210">Yes</span></span>|  
|<span data-ttu-id="5feda-211">Offset</span><span class="sxs-lookup"><span data-stu-id="5feda-211">Offset</span></span>|`int`|<span data-ttu-id="5feda-212">Начальное смещение инструкции внутри хранимой процедуры или пакета, вызвавшего повторную компиляцию.</span><span class="sxs-lookup"><span data-stu-id="5feda-212">Starting offset of the statement within the stored procedure or batch that caused recompilation.</span></span>|<span data-ttu-id="5feda-213">61</span><span class="sxs-lookup"><span data-stu-id="5feda-213">61</span></span>|<span data-ttu-id="5feda-214">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-214">Yes</span></span>|  
|<span data-ttu-id="5feda-215">RequestID</span><span class="sxs-lookup"><span data-stu-id="5feda-215">RequestID</span></span>|`int`|<span data-ttu-id="5feda-216">Идентификатор запроса, содержащего инструкцию.</span><span class="sxs-lookup"><span data-stu-id="5feda-216">ID of the request containing the statement.</span></span>|<span data-ttu-id="5feda-217">49</span><span class="sxs-lookup"><span data-stu-id="5feda-217">49</span></span>|<span data-ttu-id="5feda-218">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-218">Yes</span></span>|  
|<span data-ttu-id="5feda-219">ServerName</span><span class="sxs-lookup"><span data-stu-id="5feda-219">ServerName</span></span>|`nvarchar`|<span data-ttu-id="5feda-220">Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.</span><span class="sxs-lookup"><span data-stu-id="5feda-220">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="5feda-221">26</span><span class="sxs-lookup"><span data-stu-id="5feda-221">26</span></span>|<span data-ttu-id="5feda-222">Нет</span><span class="sxs-lookup"><span data-stu-id="5feda-222">No</span></span>|  
|<span data-ttu-id="5feda-223">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="5feda-223">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="5feda-224">Имя входа пользователя, создавшего этот сеанс.</span><span class="sxs-lookup"><span data-stu-id="5feda-224">Login name of the user who originated the session.</span></span> <span data-ttu-id="5feda-225">Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2.</span><span class="sxs-lookup"><span data-stu-id="5feda-225">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="5feda-226">В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.</span><span class="sxs-lookup"><span data-stu-id="5feda-226">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="5feda-227">64</span><span class="sxs-lookup"><span data-stu-id="5feda-227">64</span></span>|<span data-ttu-id="5feda-228">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-228">Yes</span></span>|  
|<span data-ttu-id="5feda-229">SPID</span><span class="sxs-lookup"><span data-stu-id="5feda-229">SPID</span></span>|`int`|<span data-ttu-id="5feda-230">Идентификатор сеанса, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="5feda-230">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="5feda-231">12</span><span class="sxs-lookup"><span data-stu-id="5feda-231">12</span></span>|<span data-ttu-id="5feda-232">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-232">Yes</span></span>|  
|<span data-ttu-id="5feda-233">SqlHandle</span><span class="sxs-lookup"><span data-stu-id="5feda-233">SqlHandle</span></span>|`varbinary`|<span data-ttu-id="5feda-234">64-разрядная версия хэша, основанная на тексте нерегламентированного запроса или базы данных и на идентификаторе объекта SQL.</span><span class="sxs-lookup"><span data-stu-id="5feda-234">64-bit hash based on the text of an ad hoc query or the database and object ID of an SQL object.</span></span> <span data-ttu-id="5feda-235">Это значение может быть передано в функцию sys.dm_exec_sql_text, чтобы получить связанный SQL-текст.</span><span class="sxs-lookup"><span data-stu-id="5feda-235">This value can be passed to sys.dm_exec_sql_text to retrieve the associated SQL text.</span></span>|<span data-ttu-id="5feda-236">63</span><span class="sxs-lookup"><span data-stu-id="5feda-236">63</span></span>|<span data-ttu-id="5feda-237">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-237">Yes</span></span>|  
|<span data-ttu-id="5feda-238">StartTime</span><span class="sxs-lookup"><span data-stu-id="5feda-238">StartTime</span></span>|`datetime`|<span data-ttu-id="5feda-239">Время начала события, если оно известно.</span><span class="sxs-lookup"><span data-stu-id="5feda-239">Time at which the event started, if available.</span></span>|<span data-ttu-id="5feda-240">14</span><span class="sxs-lookup"><span data-stu-id="5feda-240">14</span></span>|<span data-ttu-id="5feda-241">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-241">Yes</span></span>|  
|<span data-ttu-id="5feda-242">TextData</span><span class="sxs-lookup"><span data-stu-id="5feda-242">TextData</span></span>|`ntext`|<span data-ttu-id="5feda-243">Текст инструкции Transact-SQL, вызвавший перекомпиляцию на уровне инструкции.</span><span class="sxs-lookup"><span data-stu-id="5feda-243">Text of the Transact-SQL statement that caused a statement-level recompilation.</span></span>|<span data-ttu-id="5feda-244">1</span><span class="sxs-lookup"><span data-stu-id="5feda-244">1</span></span>|<span data-ttu-id="5feda-245">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-245">Yes</span></span>|  
|<span data-ttu-id="5feda-246">TransactionID</span><span class="sxs-lookup"><span data-stu-id="5feda-246">TransactionID</span></span>|`bigint`|<span data-ttu-id="5feda-247">Назначенный системой идентификатор транзакции.</span><span class="sxs-lookup"><span data-stu-id="5feda-247">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="5feda-248">4</span><span class="sxs-lookup"><span data-stu-id="5feda-248">4</span></span>|<span data-ttu-id="5feda-249">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-249">Yes</span></span>|  
|<span data-ttu-id="5feda-250">XactSequence</span><span class="sxs-lookup"><span data-stu-id="5feda-250">XactSequence</span></span>|`bigint`|<span data-ttu-id="5feda-251">Токен, используемый для описания текущей транзакции.</span><span class="sxs-lookup"><span data-stu-id="5feda-251">Token used to describe the current transaction.</span></span>|<span data-ttu-id="5feda-252">50</span><span class="sxs-lookup"><span data-stu-id="5feda-252">50</span></span>|<span data-ttu-id="5feda-253">Да</span><span class="sxs-lookup"><span data-stu-id="5feda-253">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5feda-254">См. также:</span><span class="sxs-lookup"><span data-stu-id="5feda-254">See Also</span></span>  
 <span data-ttu-id="5feda-255">[Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5feda-255">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="5feda-256">Класс событий SQL:StmtRecompile</span><span class="sxs-lookup"><span data-stu-id="5feda-256">SQL:StmtRecompile Event Class</span></span>](sql-stmtrecompile-event-class.md)  
  
  