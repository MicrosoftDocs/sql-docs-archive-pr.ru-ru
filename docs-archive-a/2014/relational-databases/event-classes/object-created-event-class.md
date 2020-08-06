---
title: Класс событий Object:Created | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Object:Created event class
ms.assetid: 57536924-5e66-4b09-a76d-8fcea2131771
author: stevestein
ms.author: sstein
ms.openlocfilehash: e82f9d68a5b796c6152531437265a665a9b85a68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657126"
---
# <a name="objectcreated-event-class"></a><span data-ttu-id="e13e0-102">Object:Created, класс событий</span><span class="sxs-lookup"><span data-stu-id="e13e0-102">Object:Created Event Class</span></span>
  <span data-ttu-id="e13e0-103">События класса Object:Created указывают на то, что объект был создан, например с помощью инструкций CREATE INDEX, CREATE TABLE или CREATE DATABASE.</span><span class="sxs-lookup"><span data-stu-id="e13e0-103">The Object:Created event class indicates that an object has been created, for example, by the CREATE INDEX, CREATE TABLE, or CREATE DATABASE statements.</span></span>  
  
 <span data-ttu-id="e13e0-104">Этот класс событий используется для определения того, создаются ли объекты, например приложениями ODBC, которые часто создают временные хранимые процедуры.</span><span class="sxs-lookup"><span data-stu-id="e13e0-104">This event class can be used to determine if objects are being created, for example, by ODBC applications that often create temporary stored procedures.</span></span> <span data-ttu-id="e13e0-105">По содержимому столбцов LoginName и NTUserName можно определить имя пользователя, создающего, удаляющего объекты или осуществляющего доступ к ним.</span><span class="sxs-lookup"><span data-stu-id="e13e0-105">By monitoring the LoginName and NTUserName data columns, you can determine the name of the user who is creating, deleting, or accessing objects.</span></span>  
  
## <a name="objectcreated-event-class-data-columns"></a><span data-ttu-id="e13e0-106">Столбцы данных класса событий Object:Created</span><span class="sxs-lookup"><span data-stu-id="e13e0-106">Object:Created Event Class Data Columns</span></span>  
  
|<span data-ttu-id="e13e0-107">Имя столбца данных</span><span class="sxs-lookup"><span data-stu-id="e13e0-107">Data column name</span></span>|<span data-ttu-id="e13e0-108">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e13e0-108">Data type</span></span>|<span data-ttu-id="e13e0-109">Description</span><span class="sxs-lookup"><span data-stu-id="e13e0-109">Description</span></span>|<span data-ttu-id="e13e0-110">Идентификатор столбца</span><span class="sxs-lookup"><span data-stu-id="e13e0-110">Column ID</span></span>|<span data-ttu-id="e13e0-111">Фильтруемый</span><span class="sxs-lookup"><span data-stu-id="e13e0-111">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="e13e0-112">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="e13e0-112">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-113">Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e13e0-113">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e13e0-114">Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.</span><span class="sxs-lookup"><span data-stu-id="e13e0-114">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="e13e0-115">10</span><span class="sxs-lookup"><span data-stu-id="e13e0-115">10</span></span>|<span data-ttu-id="e13e0-116">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-116">Yes</span></span>|  
|<span data-ttu-id="e13e0-117">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="e13e0-117">ClientProcessID</span></span>|`int`|<span data-ttu-id="e13e0-118">Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="e13e0-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="e13e0-119">Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.</span><span class="sxs-lookup"><span data-stu-id="e13e0-119">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="e13e0-120">9</span><span class="sxs-lookup"><span data-stu-id="e13e0-120">9</span></span>|<span data-ttu-id="e13e0-121">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-121">Yes</span></span>|  
|<span data-ttu-id="e13e0-122">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="e13e0-122">DatabaseID</span></span>|`int`|<span data-ttu-id="e13e0-123">Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась.</span><span class="sxs-lookup"><span data-stu-id="e13e0-123">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="e13e0-124">отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен.</span><span class="sxs-lookup"><span data-stu-id="e13e0-124">displays the name of the database if the ServerName data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="e13e0-125">Определите значение для базы данных, используя функцию DB_ID.</span><span class="sxs-lookup"><span data-stu-id="e13e0-125">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="e13e0-126">3</span><span class="sxs-lookup"><span data-stu-id="e13e0-126">3</span></span>|<span data-ttu-id="e13e0-127">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-127">Yes</span></span>|  
|<span data-ttu-id="e13e0-128">имя_базы_данных</span><span class="sxs-lookup"><span data-stu-id="e13e0-128">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-129">Имя базы данных, в которой выполняется пользовательская инструкция.</span><span class="sxs-lookup"><span data-stu-id="e13e0-129">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="e13e0-130">35</span><span class="sxs-lookup"><span data-stu-id="e13e0-130">35</span></span>|<span data-ttu-id="e13e0-131">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-131">Yes</span></span>|  
|<span data-ttu-id="e13e0-132">EventClass</span><span class="sxs-lookup"><span data-stu-id="e13e0-132">EventClass</span></span>|`int`|<span data-ttu-id="e13e0-133">Тип события = 46.</span><span class="sxs-lookup"><span data-stu-id="e13e0-133">Type of event = 46.</span></span>|<span data-ttu-id="e13e0-134">27</span><span class="sxs-lookup"><span data-stu-id="e13e0-134">27</span></span>|<span data-ttu-id="e13e0-135">Нет</span><span class="sxs-lookup"><span data-stu-id="e13e0-135">No</span></span>|  
|<span data-ttu-id="e13e0-136">EventSequence</span><span class="sxs-lookup"><span data-stu-id="e13e0-136">EventSequence</span></span>|`int`|<span data-ttu-id="e13e0-137">Порядковый номер данного события в запросе.</span><span class="sxs-lookup"><span data-stu-id="e13e0-137">The sequence of a given event within the request.</span></span>|<span data-ttu-id="e13e0-138">51</span><span class="sxs-lookup"><span data-stu-id="e13e0-138">51</span></span>|<span data-ttu-id="e13e0-139">Нет</span><span class="sxs-lookup"><span data-stu-id="e13e0-139">No</span></span>|  
|<span data-ttu-id="e13e0-140">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="e13e0-140">EventSubClass</span></span>|`int`|<span data-ttu-id="e13e0-141">Тип подкласса события.</span><span class="sxs-lookup"><span data-stu-id="e13e0-141">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="e13e0-142">0 = начало</span><span class="sxs-lookup"><span data-stu-id="e13e0-142">0=Begin</span></span><br /><br /> <span data-ttu-id="e13e0-143">1 = фиксация</span><span class="sxs-lookup"><span data-stu-id="e13e0-143">1=Commit</span></span><br /><br /> <span data-ttu-id="e13e0-144">2 = откат</span><span class="sxs-lookup"><span data-stu-id="e13e0-144">2=Rollback</span></span>|<span data-ttu-id="e13e0-145">21</span><span class="sxs-lookup"><span data-stu-id="e13e0-145">21</span></span>|<span data-ttu-id="e13e0-146">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-146">Yes</span></span>|  
|<span data-ttu-id="e13e0-147">GroupID</span><span class="sxs-lookup"><span data-stu-id="e13e0-147">GroupID</span></span>|`int`|<span data-ttu-id="e13e0-148">Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.</span><span class="sxs-lookup"><span data-stu-id="e13e0-148">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="e13e0-149">66</span><span class="sxs-lookup"><span data-stu-id="e13e0-149">66</span></span>|<span data-ttu-id="e13e0-150">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-150">Yes</span></span>|  
|<span data-ttu-id="e13e0-151">HostName</span><span class="sxs-lookup"><span data-stu-id="e13e0-151">HostName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-152">Имя компьютера, на котором выполняется клиентская программа.</span><span class="sxs-lookup"><span data-stu-id="e13e0-152">Name of the computer on which the client is running.</span></span> <span data-ttu-id="e13e0-153">Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла.</span><span class="sxs-lookup"><span data-stu-id="e13e0-153">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="e13e0-154">Чтобы определить имя узла, используйте функцию HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="e13e0-154">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="e13e0-155">8</span><span class="sxs-lookup"><span data-stu-id="e13e0-155">8</span></span>|<span data-ttu-id="e13e0-156">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-156">Yes</span></span>|  
|<span data-ttu-id="e13e0-157">IndexID</span><span class="sxs-lookup"><span data-stu-id="e13e0-157">IndexID</span></span>|`int`|<span data-ttu-id="e13e0-158">Идентификатор индекса объекта, связанного с событием.</span><span class="sxs-lookup"><span data-stu-id="e13e0-158">ID for the index on the object affected by the event.</span></span> <span data-ttu-id="e13e0-159">Для определения идентификатора индекса для объекта используйте столбец index_id представления каталога sys.indexes.</span><span class="sxs-lookup"><span data-stu-id="e13e0-159">To determine the index ID for an object, use the index_id column of the sys.indexes catalog view.</span></span>|<span data-ttu-id="e13e0-160">24</span><span class="sxs-lookup"><span data-stu-id="e13e0-160">24</span></span>|<span data-ttu-id="e13e0-161">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-161">Yes</span></span>|  
|<span data-ttu-id="e13e0-162">IntegerData</span><span class="sxs-lookup"><span data-stu-id="e13e0-162">IntegerData</span></span>|`int`|<span data-ttu-id="e13e0-163">Целочисленное значение, зависящее от класса событий, перехватываемых при трассировке.</span><span class="sxs-lookup"><span data-stu-id="e13e0-163">Integer value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="e13e0-164">25</span><span class="sxs-lookup"><span data-stu-id="e13e0-164">25</span></span>|<span data-ttu-id="e13e0-165">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-165">Yes</span></span>|  
|<span data-ttu-id="e13e0-166">IsSystem</span><span class="sxs-lookup"><span data-stu-id="e13e0-166">IsSystem</span></span>|`int`|<span data-ttu-id="e13e0-167">Указывает, произошло событие в системном или в пользовательском процессе.</span><span class="sxs-lookup"><span data-stu-id="e13e0-167">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="e13e0-168">1 = системный, 0 = пользовательский.</span><span class="sxs-lookup"><span data-stu-id="e13e0-168">1 = system, 0 = user.</span></span>|<span data-ttu-id="e13e0-169">60</span><span class="sxs-lookup"><span data-stu-id="e13e0-169">60</span></span>|<span data-ttu-id="e13e0-170">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-170">Yes</span></span>|  
|<span data-ttu-id="e13e0-171">LoginName</span><span class="sxs-lookup"><span data-stu-id="e13e0-171">LoginName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-172">Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).</span><span class="sxs-lookup"><span data-stu-id="e13e0-172">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="e13e0-173">11</span><span class="sxs-lookup"><span data-stu-id="e13e0-173">11</span></span>|<span data-ttu-id="e13e0-174">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-174">Yes</span></span>|  
|<span data-ttu-id="e13e0-175">LoginSid</span><span class="sxs-lookup"><span data-stu-id="e13e0-175">LoginSid</span></span>|`image`|<span data-ttu-id="e13e0-176">Идентификатор безопасности вошедшего в систему пользователя.</span><span class="sxs-lookup"><span data-stu-id="e13e0-176">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="e13e0-177">Эти сведения можно найти в представлении каталога sys.server_principals.</span><span class="sxs-lookup"><span data-stu-id="e13e0-177">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="e13e0-178">Значение идентификатора безопасности уникально для каждого имени входа на сервере.</span><span class="sxs-lookup"><span data-stu-id="e13e0-178">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="e13e0-179">41</span><span class="sxs-lookup"><span data-stu-id="e13e0-179">41</span></span>|<span data-ttu-id="e13e0-180">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-180">Yes</span></span>|  
|<span data-ttu-id="e13e0-181">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="e13e0-181">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-182">Домен Windows, к которому принадлежит пользователь.</span><span class="sxs-lookup"><span data-stu-id="e13e0-182">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="e13e0-183">7</span><span class="sxs-lookup"><span data-stu-id="e13e0-183">7</span></span>|<span data-ttu-id="e13e0-184">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-184">Yes</span></span>|  
|<span data-ttu-id="e13e0-185">NTUserName</span><span class="sxs-lookup"><span data-stu-id="e13e0-185">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-186">Имя пользователя Windows.</span><span class="sxs-lookup"><span data-stu-id="e13e0-186">Windows user name.</span></span>|<span data-ttu-id="e13e0-187">6</span><span class="sxs-lookup"><span data-stu-id="e13e0-187">6</span></span>|<span data-ttu-id="e13e0-188">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-188">Yes</span></span>|  
|<span data-ttu-id="e13e0-189">ObjectID</span><span class="sxs-lookup"><span data-stu-id="e13e0-189">ObjectID</span></span>|`int`|<span data-ttu-id="e13e0-190">Идентификатор объекта, назначенный системой.</span><span class="sxs-lookup"><span data-stu-id="e13e0-190">System-assigned ID of the object.</span></span>|<span data-ttu-id="e13e0-191">22</span><span class="sxs-lookup"><span data-stu-id="e13e0-191">22</span></span>|<span data-ttu-id="e13e0-192">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-192">Yes</span></span>|  
|<span data-ttu-id="e13e0-193">ObjectID2</span><span class="sxs-lookup"><span data-stu-id="e13e0-193">ObjectID2</span></span>|`bigint`|<span data-ttu-id="e13e0-194">Идентификатор связанного объекта или сущности.</span><span class="sxs-lookup"><span data-stu-id="e13e0-194">ID of the related object or entity.</span></span>|<span data-ttu-id="e13e0-195">56</span><span class="sxs-lookup"><span data-stu-id="e13e0-195">56</span></span>|<span data-ttu-id="e13e0-196">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-196">Yes</span></span>|  
|<span data-ttu-id="e13e0-197">ObjectName</span><span class="sxs-lookup"><span data-stu-id="e13e0-197">ObjectName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-198">Имя объекта, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="e13e0-198">Name of the object being referenced.</span></span>|<span data-ttu-id="e13e0-199">34</span><span class="sxs-lookup"><span data-stu-id="e13e0-199">34</span></span>|<span data-ttu-id="e13e0-200">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-200">Yes</span></span>|  
|<span data-ttu-id="e13e0-201">ObjectType</span><span class="sxs-lookup"><span data-stu-id="e13e0-201">ObjectType</span></span>|`int`|<span data-ttu-id="e13e0-202">Значение, представляющее тип объекта, связанного с событием.</span><span class="sxs-lookup"><span data-stu-id="e13e0-202">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="e13e0-203">Это значение соответствует столбцу type в таблице sys.objects.</span><span class="sxs-lookup"><span data-stu-id="e13e0-203">This value corresponds to the type column in sys.objects.</span></span> <span data-ttu-id="e13e0-204">Значения см. в разделе [Столбец события ObjectType Trace](objecttype-trace-event-column.md).</span><span class="sxs-lookup"><span data-stu-id="e13e0-204">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="e13e0-205">28</span><span class="sxs-lookup"><span data-stu-id="e13e0-205">28</span></span>|<span data-ttu-id="e13e0-206">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-206">Yes</span></span>|  
|<span data-ttu-id="e13e0-207">RequestID</span><span class="sxs-lookup"><span data-stu-id="e13e0-207">RequestID</span></span>|`int`|<span data-ttu-id="e13e0-208">Идентификатор запроса, содержащего инструкцию.</span><span class="sxs-lookup"><span data-stu-id="e13e0-208">ID of the request containing the statement.</span></span>|<span data-ttu-id="e13e0-209">49</span><span class="sxs-lookup"><span data-stu-id="e13e0-209">49</span></span>|<span data-ttu-id="e13e0-210">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-210">Yes</span></span>|  
|<span data-ttu-id="e13e0-211">ServerName</span><span class="sxs-lookup"><span data-stu-id="e13e0-211">ServerName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-212">Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.</span><span class="sxs-lookup"><span data-stu-id="e13e0-212">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="e13e0-213">26</span><span class="sxs-lookup"><span data-stu-id="e13e0-213">26</span></span>|<span data-ttu-id="e13e0-214">Нет</span><span class="sxs-lookup"><span data-stu-id="e13e0-214">No</span></span>|  
|<span data-ttu-id="e13e0-215">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="e13e0-215">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="e13e0-216">Имя входа пользователя, создавшего этот сеанс.</span><span class="sxs-lookup"><span data-stu-id="e13e0-216">Login name of the user who originated the session.</span></span> <span data-ttu-id="e13e0-217">Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2, SessionLoginName будет содержать значение Login1, а LoginName — значение Login2.</span><span class="sxs-lookup"><span data-stu-id="e13e0-217">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows as Login2.</span></span> <span data-ttu-id="e13e0-218">В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.</span><span class="sxs-lookup"><span data-stu-id="e13e0-218">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="e13e0-219">64</span><span class="sxs-lookup"><span data-stu-id="e13e0-219">64</span></span>|<span data-ttu-id="e13e0-220">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-220">Yes</span></span>|  
|<span data-ttu-id="e13e0-221">SPID</span><span class="sxs-lookup"><span data-stu-id="e13e0-221">SPID</span></span>|`int`|<span data-ttu-id="e13e0-222">Идентификатор сеанса, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="e13e0-222">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="e13e0-223">12</span><span class="sxs-lookup"><span data-stu-id="e13e0-223">12</span></span>|<span data-ttu-id="e13e0-224">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-224">Yes</span></span>|  
|<span data-ttu-id="e13e0-225">StartTime</span><span class="sxs-lookup"><span data-stu-id="e13e0-225">StartTime</span></span>|`datetime`|<span data-ttu-id="e13e0-226">Время начала события, если оно известно.</span><span class="sxs-lookup"><span data-stu-id="e13e0-226">Time at which the event started, if available.</span></span>|<span data-ttu-id="e13e0-227">14</span><span class="sxs-lookup"><span data-stu-id="e13e0-227">14</span></span>|<span data-ttu-id="e13e0-228">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-228">Yes</span></span>|  
|<span data-ttu-id="e13e0-229">TransactionID</span><span class="sxs-lookup"><span data-stu-id="e13e0-229">TransactionID</span></span>|`bigint`|<span data-ttu-id="e13e0-230">Назначенный системой идентификатор транзакции.</span><span class="sxs-lookup"><span data-stu-id="e13e0-230">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="e13e0-231">4</span><span class="sxs-lookup"><span data-stu-id="e13e0-231">4</span></span>|<span data-ttu-id="e13e0-232">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-232">Yes</span></span>|  
|<span data-ttu-id="e13e0-233">XactSequence</span><span class="sxs-lookup"><span data-stu-id="e13e0-233">XactSequence</span></span>|`bigint`|<span data-ttu-id="e13e0-234">Токен, используемый для описания текущей транзакции.</span><span class="sxs-lookup"><span data-stu-id="e13e0-234">Token used to describe the current transaction.</span></span>|<span data-ttu-id="e13e0-235">50</span><span class="sxs-lookup"><span data-stu-id="e13e0-235">50</span></span>|<span data-ttu-id="e13e0-236">Да</span><span class="sxs-lookup"><span data-stu-id="e13e0-236">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e13e0-237">См. также:</span><span class="sxs-lookup"><span data-stu-id="e13e0-237">See Also</span></span>  
 [<span data-ttu-id="e13e0-238">Хранимая процедура sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e13e0-238">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  