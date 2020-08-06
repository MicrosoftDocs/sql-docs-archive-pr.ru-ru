---
title: Привязке базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f222b1d5-d2fa-4269-8294-4575a0e78636
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cd163c5d3bc7a2cd9051b8d37b8127a1cc88c30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669406"
---
# <a name="bind-a-database-with-memory-optimized-tables-to-a-resource-pool"></a><span data-ttu-id="b621e-102">Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов</span><span class="sxs-lookup"><span data-stu-id="b621e-102">Bind a Database with Memory-Optimized Tables to a Resource Pool</span></span>
  <span data-ttu-id="b621e-103">Пул ресурсов представляет подмножество физических ресурсов, доступных для управления.</span><span class="sxs-lookup"><span data-stu-id="b621e-103">A resource pool represents a subset of physical resources that can be governed.</span></span> <span data-ttu-id="b621e-104">По умолчанию базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] привязываются к пулу и потребляют ресурсы пула по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b621e-104">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases are bound to and consume the resources of the default resource pool.</span></span> <span data-ttu-id="b621e-105">Чтобы защитить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от использования его ресурсов одной или несколькими оптимизированными для памяти таблицами, а также чтобы другие потребители не занимали память, необходимую таким таблицам, рекомендуется создать отдельный пул ресурсов для управления использованием памяти для базы данных с оптимизированными для памяти таблицами.</span><span class="sxs-lookup"><span data-stu-id="b621e-105">To protect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from having its resources consumed by one or more memory-optimized tables, and to prevent other memory users from consuming memory needed by memory-optimized tables, you should create a separate resource pool to manage memory consumption for the database with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="b621e-106">Базу данных можно привязать только к одному пулу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b621e-106">A database can be bound on only one resource pool.</span></span> <span data-ttu-id="b621e-107">Однако можно привязать несколько баз данных к одному и тому же пулу.</span><span class="sxs-lookup"><span data-stu-id="b621e-107">However, you can bind multiple databases to the same pool.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b621e-108">позволяет привязать базу данных без таблиц, оптимизированных для памяти, к пулу ресурсов, однако это не даст результата.</span><span class="sxs-lookup"><span data-stu-id="b621e-108">allows binding a database without memory-optimized tables to a resource pool but it has no effect.</span></span> <span data-ttu-id="b621e-109">Может потребоваться привязка базы данных к указанному пулу ресурсов, если в будущем потребуется создание в базе данных оптимизированных для памяти таблиц.</span><span class="sxs-lookup"><span data-stu-id="b621e-109">You may want to bind a database to a named resource pool if, in future, you may want to create memory-optimized tables in the database.</span></span>  
  
 <span data-ttu-id="b621e-110">Прежде чем создавать привязку базы данных к пулу ресурсов, как база данных, так и пул ресурсов должны существовать.</span><span class="sxs-lookup"><span data-stu-id="b621e-110">Before you can bind a database to a resource pool both the database and the resource pool must exist.</span></span> <span data-ttu-id="b621e-111">Привязка вступит в силу при следующем переводе базы данных в режим «в сети».</span><span class="sxs-lookup"><span data-stu-id="b621e-111">The binding takes effect the next time the database is brought online.</span></span> <span data-ttu-id="b621e-112">Дополнительные сведения см. в разделе [Состояния базы данных](../databases/database-states.md) .</span><span class="sxs-lookup"><span data-stu-id="b621e-112">See [Database States](../databases/database-states.md) for more information.</span></span>  
  
 <span data-ttu-id="b621e-113">Сведения о пулах ресурсов см. в разделе [Пул ресурсов регулятора ресурсов](../resource-governor/resource-governor-resource-pool.md).</span><span class="sxs-lookup"><span data-stu-id="b621e-113">For information about resource pools, see [Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md).</span></span>  
  
  
## <a name="create-the-database-and-resource-pool"></a><span data-ttu-id="b621e-114">Создайте базу данных и пул ресурсов</span><span class="sxs-lookup"><span data-stu-id="b621e-114">Create the database and resource pool</span></span>  
 <span data-ttu-id="b621e-115">Можно создать базу данных и пул ресурсов в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="b621e-115">You can create the database and resource pool in any order.</span></span> <span data-ttu-id="b621e-116">Важно, чтобы база данных и пул ресурсов существовали еще до привязки.</span><span class="sxs-lookup"><span data-stu-id="b621e-116">What matters is that they both exist prior to binding the database to the resource pool.</span></span>  
  
### <a name="create-the-database"></a><span data-ttu-id="b621e-117">Создание базы данных</span><span class="sxs-lookup"><span data-stu-id="b621e-117">Create the database</span></span>  
 <span data-ttu-id="b621e-118">Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] создает базу данных с именем IMOLTP_DB, которая будет содержать одну или несколько таблиц, оптимизированных для памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-118">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] creates a database named IMOLTP_DB which will contain one or more memory-optimized tables.</span></span> <span data-ttu-id="b621e-119">Путь \<driveAndPath> должен существовать до выполнения этой команды.</span><span class="sxs-lookup"><span data-stu-id="b621e-119">The path \<driveAndPath> must exist prior to running this command.</span></span>  
  
```sql  
CREATE DATABASE IMOLTP_DB  
GO  
ALTER DATABASE IMOLTP_DB ADD FILEGROUP IMOLTP_DB_fg CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP_DB ADD FILE( NAME = 'IMOLTP_DB_fg' , FILENAME = 'c:\data\IMOLTP_DB_fg') TO FILEGROUP IMOLTP_DB_fg;  
GO  
```  
  
### <a name="determine-the-minimum-value-for-min_memory_percent-and-max_memory_percent"></a><span data-ttu-id="b621e-120">Определение минимального значения для MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT</span><span class="sxs-lookup"><span data-stu-id="b621e-120">Determine the minimum value for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT</span></span>  
 <span data-ttu-id="b621e-121">После определения потребностей в памяти для оптимизированных для памяти таблиц нужно определить, какой процент доступной памяти требуется, и задать в процентах это значение или выше.</span><span class="sxs-lookup"><span data-stu-id="b621e-121">Once you determine the memory needs for your memory-optimized tables, you need to determine what percentage of available memory you need, and set the memory percentages to that value or higher.</span></span>  
  
 <span data-ttu-id="b621e-122">**Пример** </span><span class="sxs-lookup"><span data-stu-id="b621e-122">**Example:** </span></span>  
<span data-ttu-id="b621e-123">В этом примере предполагается, что согласно вычислениям для оптимизированных для памяти таблиц и индексов требуется 16 ГБ памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-123">For this example we will assume that from your calculations you determined that your memory-optimized tables and indexes need 16 GB of memory.</span></span> <span data-ttu-id="b621e-124">Предположим, доступно 32 ГБ памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-124">Assume that you have 32 GB of memory committed for your use.</span></span>  
  
 <span data-ttu-id="b621e-125">На первый взгляд может показаться, что для MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT нужно задать значение 50 (16 — это 50 % от 32).</span><span class="sxs-lookup"><span data-stu-id="b621e-125">At first glance it could seem that you need to set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to 50 (16 is 50% of 32).</span></span>  <span data-ttu-id="b621e-126">Но в этом случае оптимизированные для памяти таблицы не получат достаточного объема памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-126">However, that would not give your memory-optimized tables sufficient memory.</span></span> <span data-ttu-id="b621e-127">В приведенной ниже таблице ([Процент доступной памяти для оптимизированных для памяти таблиц и индексов](#percent-of-memory-available-for-memory-optimized-tables-and-indexes)) видно, что при наличии 32 ГБ выделенной памяти только 80 % доступно для оптимизированных для памяти таблиц и индексов.</span><span class="sxs-lookup"><span data-stu-id="b621e-127">Looking at the table below ([Percent of memory available for memory-optimized tables and indexes](#percent-of-memory-available-for-memory-optimized-tables-and-indexes)) we see that if there is 32 GB of committed memory, only 80% of that is available for memory-optimized tables and indexes.</span></span>  <span data-ttu-id="b621e-128">Поэтому следует вычислять минимальный и максимальный процент исходя из доступной памяти, а не общей.</span><span class="sxs-lookup"><span data-stu-id="b621e-128">Therefore, we calculate the min and max percentages based upon the available memory, not the committed memory.</span></span>  
  
 `memoryNeedeed = 16`   
 `memoryCommitted = 32`   
 `availablePercent = 0.8`   
 `memoryAvailable = memoryCommitted * availablePercent`   
 `percentNeeded = memoryNeeded / memoryAvailable`  
  
 <span data-ttu-id="b621e-129">Использование реальных чисел.</span><span class="sxs-lookup"><span data-stu-id="b621e-129">Plugging in real numbes:</span></span>   
`percentNeeded = 16 / (32 * 0.8) = 16 / 25.6 = 0.625`  
  
 <span data-ttu-id="b621e-130">Таким образом, необходимо по крайней мере 62,5 % доступной памяти, чтобы уложиться в требование 16 ГБ для оптимизированных для памяти таблиц и индексов.</span><span class="sxs-lookup"><span data-stu-id="b621e-130">Thus you need at least 62.5% of the available memory to meet the 16 GB requirement of your memory-optimized tables and indexes.</span></span>  <span data-ttu-id="b621e-131">Поскольку значения MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT должны быть целыми числами, рекомендуется задать для них значение не менее 63 %.</span><span class="sxs-lookup"><span data-stu-id="b621e-131">Since the values for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT must be integers, we set them to at least 63%.</span></span>  
  
### <a name="create-a-resource-pool-and-configure-memory"></a><span data-ttu-id="b621e-132">Создайте новый пул ресурсов и настройте память.</span><span class="sxs-lookup"><span data-stu-id="b621e-132">Create a resource pool and configure memory</span></span>  
 <span data-ttu-id="b621e-133">При настройке памяти для таблиц, оптимизированных для памяти, планирование загрузки следует выполнять на основе MIN_MEMORY_PERCENT, но не MAX_MEMORY_PERCENT.</span><span class="sxs-lookup"><span data-stu-id="b621e-133">When configuring memory for memory-optimized tables, the capacity planning should be done based on MIN_MEMORY_PERCENT, not on MAX_MEMORY_PERCENT.</span></span>  <span data-ttu-id="b621e-134">Сведения о MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT см. в разделе [ALTER RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/alter-resource-pool-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="b621e-134">See [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) for information on MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span> <span data-ttu-id="b621e-135">Это повышает прогнозируемую доступность памяти для таблиц, оптимизированных для памяти, так как использование MIN_MEMORY_PERCENT повышает нагрузку на другие пулы ресурсов, чтобы добиться выделения памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-135">This provides more predictable memory availability for memory-optimized tables as MIN_MEMORY_PERCENT causes memory pressure to other resource pools to make sure it is honored.</span></span> <span data-ttu-id="b621e-136">Чтобы обеспечить доступность памяти и избежать ее нехватки, значения MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT должны быть одинаковыми.</span><span class="sxs-lookup"><span data-stu-id="b621e-136">To ensure that memory is available and help avoid out-of-memory conditions, the values for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT should be the same.</span></span> <span data-ttu-id="b621e-137">В разделе [Процент доступной памяти для оптимизированных для памяти таблиц и индексов](#percent-of-memory-available-for-memory-optimized-tables-and-indexes) ниже процент доступной памяти для таблиц, оптимизированных для памяти, основан на объеме выделенной памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-137">See [Percent of memory available for memory-optimized tables and indexes](#percent-of-memory-available-for-memory-optimized-tables-and-indexes) below for the percent of memory available for memory-optimized tables based on the amount of committed memory.</span></span>  
  
 <span data-ttu-id="b621e-138">Дополнительные сведения о работе в среде виртуальных машин см. в статье [Рекомендации по использованию выполняющейся в памяти OLTP в среде виртуальных машин](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md).</span><span class="sxs-lookup"><span data-stu-id="b621e-138">See [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information when working in a VM environment.</span></span>  
  
 <span data-ttu-id="b621e-139">Следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] создает пул ресурсов с именем Pool_IMOLTP, в котором для использования будет доступно 50 % памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-139">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a resource pool named Pool_IMOLTP with half of the memory available for its use.</span></span>  <span data-ttu-id="b621e-140">После создания пула регулятор ресурсов настраивается для включения Pool_IMOLTP.</span><span class="sxs-lookup"><span data-stu-id="b621e-140">After the pool is created Resource Governor is reconfigured to include Pool_IMOLTP.</span></span>  
  
```sql  
-- set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value  
CREATE RESOURCE POOL Pool_IMOLTP   
  WITH   
    ( MIN_MEMORY_PERCENT = 63,   
    MAX_MEMORY_PERCENT = 63 );  
GO  
  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="bind-the-database-to-the-pool"></a><span data-ttu-id="b621e-141">Привязка базы данных к пулу</span><span class="sxs-lookup"><span data-stu-id="b621e-141">Bind the database to the pool</span></span>  
 <span data-ttu-id="b621e-142">Используйте системную функцию `sp_xtp_bind_db_resource_pool` , чтобы привязать базу данных к пулу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b621e-142">Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool.</span></span> <span data-ttu-id="b621e-143">Эта функция принимает два параметра: имя базы данных и имя пула ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b621e-143">The function takes two parameters: the database name and the resource pool name.</span></span>  
  
 <span data-ttu-id="b621e-144">Следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] определяет привязку базы данных IMOLTP_DB к пулу ресурсов Pool_IMOLTP.</span><span class="sxs-lookup"><span data-stu-id="b621e-144">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] defines a binding of the database IMOLTP_DB to the resource pool Pool_IMOLTP.</span></span> <span data-ttu-id="b621e-145">Привязка не вступит в силу до тех пор, пока база данных не будет переведена в режим запуска.</span><span class="sxs-lookup"><span data-stu-id="b621e-145">The binding does not become effective until you bring the database online.</span></span>  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
 <span data-ttu-id="b621e-146">Системная функция sp_xtp_bind_db_resourece_pool принимает два строковых параметра: database_name и pool_name.</span><span class="sxs-lookup"><span data-stu-id="b621e-146">The system function sp_xtp_bind_db_resourece_pool takes two string parameters: database_name and pool_name.</span></span>  
  
## <a name="confirm-the-binding"></a><span data-ttu-id="b621e-147">Подтвердите привязку</span><span class="sxs-lookup"><span data-stu-id="b621e-147">Confirm the binding</span></span>  
 <span data-ttu-id="b621e-148">Подтвердите привязку, указав идентификатор пула ресурсов для IMOLTP_DB.</span><span class="sxs-lookup"><span data-stu-id="b621e-148">Confirm the binding, noting the resource pool id for IMOLTP_DB.</span></span> <span data-ttu-id="b621e-149">Он не должен принимать значение NULL.</span><span class="sxs-lookup"><span data-stu-id="b621e-149">It should not be NULL.</span></span>  
  
```sql  
SELECT d.database_id, d.name, d.resource_pool_id  
FROM sys.databases d  
GO  
```  
  
## <a name="make-the-binding-effective"></a><span data-ttu-id="b621e-150">Сделайте привязку эффективной</span><span class="sxs-lookup"><span data-stu-id="b621e-150">Make the binding effective</span></span>  
 <span data-ttu-id="b621e-151">Необходимо вывести базу данных из сети, а затем снова вернуть в сеть после ее привязки к пулу ресурсов, чтобы привязка вступила в силу.</span><span class="sxs-lookup"><span data-stu-id="b621e-151">You must take the database offline and back online after binding it to the resource pool for binding to take effect.</span></span> <span data-ttu-id="b621e-152">Если база данных была ранее привязана к другому пулу, то перезапуск базы данных удаляет выделенную память из предыдущего пула ресурсов, после этого память будет выделяться для оптимизированных для памяти таблиц и индексов пула ресурсов, только что привязанного к базе данных.</span><span class="sxs-lookup"><span data-stu-id="b621e-152">If your database was bound to an a different pool earlier, this removes the allocated memory from the previous resource pool and memory allocations for your memory-optimized table and indexes will now come from the resource pool newly bound with the database.</span></span>  
  
```sql  
USE master  
GO  
  
ALTER DATABASE IMOLTP_DB SET OFFLINE  
GO  
ALTER DATABASE IMOLTP_DB SET ONLINE  
GO  
  
USE IMOLTP_DB  
GO  
```  
  
 <span data-ttu-id="b621e-153">Теперь база данных будет привязана к пулу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b621e-153">And now, the database is bound to the resource pool.</span></span>  
  
## <a name="change-min-memory-percent-and-max-memory-percent-on-an-existing-pool"></a><span data-ttu-id="b621e-154">Изменение МИНИМАЛЬного процента памяти и максимального объема памяти в существующем пуле</span><span class="sxs-lookup"><span data-stu-id="b621e-154">Change MIN MEMORY PERCENT and MAX MEMORY PERCENT on an existing pool</span></span>  
 <span data-ttu-id="b621e-155">Если на сервере увеличилась дополнительная память либо если изменился объем памяти, необходимый оптимизированным для памяти таблицам, может потребоваться изменить значения MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT.</span><span class="sxs-lookup"><span data-stu-id="b621e-155">If you add additional memory to the server or the amount of memory needed for your memory-optimized tables changes, you may need to alter the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span> <span data-ttu-id="b621e-156">Следующие шаги показывают, как изменить значение MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT в пуле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b621e-156">The following steps show you how to alter the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on a resource pool.</span></span> <span data-ttu-id="b621e-157">Инструкции по использованию значений для MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT см. ниже.</span><span class="sxs-lookup"><span data-stu-id="b621e-157">See the section below, for guidance on what values to use for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span>  <span data-ttu-id="b621e-158">Дополнительные сведения см. в разделе [Рекомендации по использованию выполняющейся в памяти OLTP в среде виртуальных машин](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md).</span><span class="sxs-lookup"><span data-stu-id="b621e-158">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
1.  <span data-ttu-id="b621e-159">Используйте `ALTER RESOURCE POOL` , чтобы изменить значение как MIN_MEMORY_PERCENT, так и MAX_MEMORY_PERCENT.</span><span class="sxs-lookup"><span data-stu-id="b621e-159">Use `ALTER RESOURCE POOL` to change the value of both MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span>  
  
2.  <span data-ttu-id="b621e-160">Используйте `ALTER RESURCE GOVERNOR` , чтобы настроить регулятор ресурсов с новыми значениями.</span><span class="sxs-lookup"><span data-stu-id="b621e-160">Use `ALTER RESURCE GOVERNOR` to reconfigure the Resource Governor with the new values.</span></span>  
  
 <span data-ttu-id="b621e-161">**Образец кода**</span><span class="sxs-lookup"><span data-stu-id="b621e-161">**Sample Code**</span></span>  
  
```sql  
ALTER RESOURCE POOL Pool_IMOLTP  
WITH  
     ( MIN_MEMORY_PERCENT = 70,  
       MAX_MEMORY_PERCENT = 70 )   
GO  
  
-- reconfigure the Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
```  
  
## <a name="percent-of-memory-available-for-memory-optimized-tables-and-indexes"></a><span data-ttu-id="b621e-162">Процент доступной памяти для оптимизированных для памяти таблиц и индексов</span><span class="sxs-lookup"><span data-stu-id="b621e-162">Percent of memory available for memory-optimized tables and indexes</span></span>  
 <span data-ttu-id="b621e-163">Если база данных, в которой есть оптимизированные для памяти таблицы, и рабочая нагрузка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставлены с одним и тем же пулом ресурсов, регулятор ресурсов задает внутренний порог для использования служб [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] , чтобы пользователи пула не имели конфликтов при его использовании.</span><span class="sxs-lookup"><span data-stu-id="b621e-163">If you map a database with memory-optimized tables and a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] workload to the same resource pool, the Resource Governor sets an internal threshold for [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] use so that the users of the pool do not have conflicts over pool usage.</span></span> <span data-ttu-id="b621e-164">В целом, порог для использования [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] составляет 80 % из пула.</span><span class="sxs-lookup"><span data-stu-id="b621e-164">Generally speaking, the threshold for [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] use is about 80% of the pool.</span></span> <span data-ttu-id="b621e-165">В следующей таблице показаны фактические пороговые значения для разного размера памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-165">The following table shows actual thresholds for various memory sizes.</span></span>  
  
 <span data-ttu-id="b621e-166">При создании выделенного пула ресурсов для базы данных [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] необходимо оценить объем физической памяти, который потребуется для таблиц в памяти после учета версий строк и роста объема данных.</span><span class="sxs-lookup"><span data-stu-id="b621e-166">When you create a dedicated resource pool for the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] database, you need to estimate how much physical memory you need for the in-memory tables after accounting for row versions and data growth.</span></span> <span data-ttu-id="b621e-167">Когда требуется оценка памяти, необходимо создать пул ресурсов с частью памяти целевого объема для экземпляра SQL, который показан в столбце committed_target_kb в динамическом административном представлении `sys.dm_os_sys_info` (см. [sys.dm_os_sys_info](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql)).</span><span class="sxs-lookup"><span data-stu-id="b621e-167">Once estimate the memory needed, you create a resource pool with a percent of the commit target memory for SQL Instance as reflected by column 'committed_target_kb' in the DMV `sys.dm_os_sys_info` (see [sys.dm_os_sys_info](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql)).</span></span> <span data-ttu-id="b621e-168">Например, можно создать пул ресурсов P1 с 40 % от общего объема памяти, доступного для экземпляра.</span><span class="sxs-lookup"><span data-stu-id="b621e-168">For example, you can create a resource pool P1 with 40% of the total memory available to the instance.</span></span> <span data-ttu-id="b621e-169">Из этих 40 % модуль [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] получает малый процент для хранения данных [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b621e-169">Out of this 40%, the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine gets a smaller percent to store [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] data.</span></span>  <span data-ttu-id="b621e-170">Это необходимо для того, чтобы удостовериться, что [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] не использует всю память из этого пула.</span><span class="sxs-lookup"><span data-stu-id="b621e-170">This is done to make sure [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] does not consume all the memory from this pool.</span></span>  <span data-ttu-id="b621e-171">Это значение меньшего процента зависит от целевого объема зафиксированной памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-171">This value of the smaller percent depends upon the Target committed Memory.</span></span> <span data-ttu-id="b621e-172">В следующей таблице показана память, доступная в пуле ресурсов (именованном или стандартном) для базы данных [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] до появлении ошибки нехватки памяти.</span><span class="sxs-lookup"><span data-stu-id="b621e-172">The following table describes memory available to [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] database in a resource pool (named or default) before an OOM error is raised.</span></span>  
  
|<span data-ttu-id="b621e-173">Память, выделенная в целевом режиме</span><span class="sxs-lookup"><span data-stu-id="b621e-173">Target Committed Memory</span></span>|<span data-ttu-id="b621e-174">Процент доступной памяти для таблиц</span><span class="sxs-lookup"><span data-stu-id="b621e-174">Percent available for in-memory tables</span></span>|  
|-----------------------------|---------------------------------------------|  
|<span data-ttu-id="b621e-175"><= 8 ГБ</span><span class="sxs-lookup"><span data-stu-id="b621e-175"><= 8 GB</span></span>|<span data-ttu-id="b621e-176">70 %</span><span class="sxs-lookup"><span data-stu-id="b621e-176">70%</span></span>|  
|<span data-ttu-id="b621e-177"><= 16 ГБ</span><span class="sxs-lookup"><span data-stu-id="b621e-177"><= 16 GB</span></span>|<span data-ttu-id="b621e-178">75 %</span><span class="sxs-lookup"><span data-stu-id="b621e-178">75%</span></span>|  
|<span data-ttu-id="b621e-179"><= 32 ГБ</span><span class="sxs-lookup"><span data-stu-id="b621e-179"><= 32 GB</span></span>|<span data-ttu-id="b621e-180">80 %</span><span class="sxs-lookup"><span data-stu-id="b621e-180">80%</span></span>|  
|<span data-ttu-id="b621e-181">\<= 96 ГБ</span><span class="sxs-lookup"><span data-stu-id="b621e-181">\<= 96 GB</span></span>|<span data-ttu-id="b621e-182">85 %</span><span class="sxs-lookup"><span data-stu-id="b621e-182">85%</span></span>|  
|<span data-ttu-id="b621e-183">>96 ГБ</span><span class="sxs-lookup"><span data-stu-id="b621e-183">>96 GB</span></span>|<span data-ttu-id="b621e-184">90 %</span><span class="sxs-lookup"><span data-stu-id="b621e-184">90%</span></span>|  
  
 <span data-ttu-id="b621e-185">Например, если "целевая зафиксированная память" равна 100 ГБ, а, по вашей оценке для таблиц и индексов, оптимизированных для памяти, требуется 60 ГБ, можно создать пул ресурсов с параметром MAX_MEMORY_PERCENT = 67 (60 требуемых ГБ / 0,90 = 66,667 ГБ, после округления — 67 ГБ; 67 ГБ/100 установленных ГБ = 67 %), чтобы обеспечить объем памяти, необходимый объектам [!INCLUDE[hek_2](../../../includes/hek-2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b621e-185">For example, if your 'target committed memory' is 100 GB, and you estimate your memory-optimized tables and indexes need 60GBof memory, then you can create a resource pool with MAX_MEMORY_PERCENT = 67 (60GB needed / 0.90 = 66.667GB - round up to 67GB; 67GB / 100GB installed = 67%) to ensure that your [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] objects have the 60GB they need.</span></span>  
  
 <span data-ttu-id="b621e-186">После привязки базы данных к указанному пулу ресурсов выполните следующий запрос, чтобы узнать объем выделенной памяти в разных пулах ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b621e-186">Once a database has been bound to a named resource pool, use the following query to see memory allocations across different resource pools.</span></span>  
  
```sql  
SELECT pool_id  
     , Name  
     , min_memory_percent  
     , max_memory_percent  
     , max_memory_kb/1024 AS max_memory_mb  
     , used_memory_kb/1024 AS used_memory_mb   
     , target_memory_kb/1024 AS target_memory_mb  
   FROM sys.dm_resource_governor_resource_pools  
```  
  
 <span data-ttu-id="b621e-187">Этот пример вывода показывает, что память, занятая оптимизированными для памяти объектами, равна 1356 МБ в пуле ресурсов PoolIMOLTP с верхней границей в 2307 МБ.</span><span class="sxs-lookup"><span data-stu-id="b621e-187">This sample output shows that the memory taken by memory-optimized objects is 1356 MB in resource pool, PoolIMOLTP, with an upper bound of 2307 MB.</span></span> <span data-ttu-id="b621e-188">Эта верхняя граница определяет общий объем памяти, который может быть занят пользовательскими и оптимизированными для памяти объектами, сопоставленными с этим пулом.</span><span class="sxs-lookup"><span data-stu-id="b621e-188">This upper bound controls the total memory that can be taken by user and system memory-optimized objects mapped to this pool.</span></span>  
  
 <span data-ttu-id="b621e-189">**Образец вывода** </span><span class="sxs-lookup"><span data-stu-id="b621e-189">**Sample Output** </span></span>  
<span data-ttu-id="b621e-190">Этот вывод из базы данных и таблиц, созданных ранее.</span><span class="sxs-lookup"><span data-stu-id="b621e-190">This output is from the database and tables we created above.</span></span>  
  
```  
pool_id     Name        min_memory_percent max_memory_percent max_memory_mb used_memory_mb target_memory_mb  
----------- ----------- ------------------ ------------------ ------------- -------------- ----------------   
1           internal    0                  100                3845          125            3845  
2           default     0                  100                3845          32             3845  
259         PoolIMOLTP 0                  100                3845          1356           2307  
```  
  
 <span data-ttu-id="b621e-191">Дополнительные сведения см. в разделе [sys.dm_resource_governor_resource_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="b621e-191">For more information see [sys.dm_resource_governor_resource_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql).</span></span>  
  
 <span data-ttu-id="b621e-192">Если не привязать базу данных к именованному пулу ресурсов, она привязывается к пулу ресурсов default.</span><span class="sxs-lookup"><span data-stu-id="b621e-192">If you do not bind your database to a named resource pool, it is bound to the 'default' pool.</span></span> <span data-ttu-id="b621e-193">Поскольку стандартный пул ресурсов используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и при других операциях выделения памяти, вы не сможете отслеживать память, потребляемую таблицами, оптимизированными для памяти, в нужной базе данных с помощью динамического административного представления sys.dm_resource_governor_resource_pools.</span><span class="sxs-lookup"><span data-stu-id="b621e-193">Since default resource pool is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for most other allocations, you will not be able to monitor memory consumed by memory-optimized tables using the DMV sys.dm_resource_governor_resource_pools accurately for the database of interest.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b621e-194">См. также:</span><span class="sxs-lookup"><span data-stu-id="b621e-194">See Also</span></span>  
 <span data-ttu-id="b621e-195">[sys.sp_xtp_bind_db_resource_pool (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b621e-195">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="b621e-196">[sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b621e-196">[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="b621e-197">[регулятор ресурсов](../resource-governor/resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="b621e-197">[Resource Governor](../resource-governor/resource-governor.md) </span></span>  
 <span data-ttu-id="b621e-198">[Пул ресурсов регулятора ресурсов](../resource-governor/resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="b621e-198">[Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="b621e-199">[Создание пула ресурсов](../resource-governor/create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="b621e-199">[Create a Resource Pool](../resource-governor/create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="b621e-200">[Изменение параметров пула ресурсов](../resource-governor/change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="b621e-200">[Change Resource Pool Settings](../resource-governor/change-resource-pool-settings.md) </span></span>  
 [<span data-ttu-id="b621e-201">Удаление пула ресурсов</span><span class="sxs-lookup"><span data-stu-id="b621e-201">Delete a Resource Pool</span></span>](../resource-governor/delete-a-resource-pool.md)  
  
  
