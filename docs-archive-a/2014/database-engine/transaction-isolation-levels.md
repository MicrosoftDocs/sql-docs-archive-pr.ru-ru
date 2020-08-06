---
title: Уровни изоляции транзакций оптимизированные для памяти таблицы | Документация Майкрософт
ms.custom: seo-dt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 8a6a82bf-273c-40ab-a101-46bd3615db8a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ee0ba17dc999c9076ca4622d47db28b8200b851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730857"
---
# <a name="transaction-isolation-levels-in-memory-optimized-tables"></a><span data-ttu-id="0ba32-102">Уровни изоляции транзакций в таблицах, оптимизированных для памяти</span><span class="sxs-lookup"><span data-stu-id="0ba32-102">Transaction Isolation Levels in memory-optimized tables</span></span>

  <span data-ttu-id="0ba32-103">Поддерживаются следующие уровни изоляции для транзакций, обращающихся к оптимизированным для памяти таблицам.</span><span class="sxs-lookup"><span data-stu-id="0ba32-103">The following isolation levels are supported for transactions that access memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="0ba32-104">SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="0ba32-104">SNAPSHOT</span></span>  
  
-   <span data-ttu-id="0ba32-105">REPEATABLE READ</span><span class="sxs-lookup"><span data-stu-id="0ba32-105">REPEATABLE READ</span></span>  
  
-   <span data-ttu-id="0ba32-106">SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="0ba32-106">SERIALIZABLE</span></span>  
  
-   <span data-ttu-id="0ba32-107">READ COMMITTED</span><span class="sxs-lookup"><span data-stu-id="0ba32-107">READ COMMITTED</span></span>  
  
 <span data-ttu-id="0ba32-108">Уровень изоляции транзакции может быть указан как часть блока ATOMIC хранимой процедуры, скомпилированной в собственном коде.</span><span class="sxs-lookup"><span data-stu-id="0ba32-108">The transaction isolation level can be specified as part of the atomic block of a natively compiled stored procedure.</span></span> <span data-ttu-id="0ba32-109">Дополнительные сведения см. в статье [CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="0ba32-109">For more information, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span> <span data-ttu-id="0ba32-110">При доступе к оптимизированным для памяти таблицам из интерпретируемого [!INCLUDE[tsql](../includes/tsql-md.md)] уровень изоляции можно указать с помощью указаний уровня таблицы.</span><span class="sxs-lookup"><span data-stu-id="0ba32-110">When accessing memory-optimized tables from interpreted [!INCLUDE[tsql](../includes/tsql-md.md)], the isolation level can be specified using table-level hints.</span></span>  
  
 <span data-ttu-id="0ba32-111">При определении скомпилированной в собственном коде хранимой процедуры необходимо указать уровень изоляции транзакции.</span><span class="sxs-lookup"><span data-stu-id="0ba32-111">You must specify the transaction isolation level when you define a natively compiled stored procedure.</span></span> <span data-ttu-id="0ba32-112">Задание уровня изоляции в табличных указаниях требуется при доступе к оптимизированным для памяти таблицам из пользовательских транзакций в интерпретируемом [!INCLUDE[tsql](../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ba32-112">You must specify the isolation level in table hints when accessing memory-optimized tables from user transactions in interpreted [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span> <span data-ttu-id="0ba32-113">Дополнительные сведения см. в разделе [рекомендации по уровню изоляции транзакций с таблицами, оптимизированными для памяти](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span><span class="sxs-lookup"><span data-stu-id="0ba32-113">For more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="0ba32-114">Уровень изоляции READ COMMITTED поддерживается для оптимизированных для памяти таблиц с транзакциями с автоматической фиксацией.</span><span class="sxs-lookup"><span data-stu-id="0ba32-114">The isolation level READ COMMITTED is supported for memory-optimized tables with autocommit transactions.</span></span> <span data-ttu-id="0ba32-115">Использование уровня изоляции READ COMMITTED недопустимо в пользовательских транзакциях или в атомарном блоке.</span><span class="sxs-lookup"><span data-stu-id="0ba32-115">READ COMMITTED is not valid in user transactions or in an atomic block.</span></span> <span data-ttu-id="0ba32-116">Для явных и неявных пользовательских транзакций не поддерживается READ COMMITTED.</span><span class="sxs-lookup"><span data-stu-id="0ba32-116">READ COMMITTED is not supported with explicit or implicit user transactions.</span></span> <span data-ttu-id="0ba32-117">Уровень изоляции READ_COMMITTED_SNAPSHOT поддерживается для таблиц, оптимизированных для памяти, с транзакциями в режиме автофиксации и только в том случае, если запрос не обращается к таблицам на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="0ba32-117">Isolation level READ_COMMITTED_SNAPSHOT is supported for memory-optimized tables with autocommit transactions and only if the query does not access any disk-based tables.</span></span> <span data-ttu-id="0ba32-118">Кроме того, транзакции, которые запущены с использованием интерпретируемого [!INCLUDE[tsql](../includes/tsql-md.md)] с режимом изоляции SNAPSHOT, не могут получить доступ к оптимизированным для памяти таблицам.</span><span class="sxs-lookup"><span data-stu-id="0ba32-118">In addition, transactions that are started using interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] with SNAPSHOT isolation cannot access memory-optimized tables.</span></span> <span data-ttu-id="0ba32-119">Транзакции, использующие интерпретируемый [!INCLUDE[tsql](../includes/tsql-md.md)] с уровнем изоляции REPEATABLE READ или SERIALIZABLE, должны обращаться к оптимизированным для памяти таблицам с использованием режима изоляции SNAPSHOT.</span><span class="sxs-lookup"><span data-stu-id="0ba32-119">Transactions that are use interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] with either REPEATABLE READ or SERIALIZABLE isolation must access memory-optimized tables using SNAPSHOT isolation.</span></span> <span data-ttu-id="0ba32-120">Дополнительные сведения об этом сценарии см. в разделе [транзакции между контейнерами](cross-container-transactions.md).</span><span class="sxs-lookup"><span data-stu-id="0ba32-120">For more information about this scenario, see [Cross-Container Transactions](cross-container-transactions.md).</span></span>  
  
 <span data-ttu-id="0ba32-121">READ COMMITTED — это уровень изоляции по умолчанию в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ba32-121">READ COMMITTED is the default isolation level in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ba32-122">Если уровень изоляции сессии задан как READ COMMITED (или ниже), то можно выполнить одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="0ba32-122">When the isolation level of the session is READ COMMITED (or lower), you can do one of the following:</span></span>  
  
-   <span data-ttu-id="0ba32-123">Явно используйте более высокий уровень изоляции для доступа к оптимизированной для памяти таблицы (например, WITH (SNAPSHOT)).</span><span class="sxs-lookup"><span data-stu-id="0ba32-123">Explicitly use a higher isolation level hint for accessing the memory-optimized table (for example, WITH (SNAPSHOT)).</span></span>  
  
-   <span data-ttu-id="0ba32-124">Укажите параметр `MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT`, который установит уровень изоляции SNAPSHOT для оптимизированных для памяти таблиц (если бы вы добавили указание WITH (SNAPSHOT) в каждую оптимизированную для памяти таблицу).</span><span class="sxs-lookup"><span data-stu-id="0ba32-124">Specify the `MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT` set option, which will set the isolation level for memory-optimized tables to SNAPSHOT (as if you included WITH(SNAPSHOT) hints to every memory-optimized table).</span></span> <span data-ttu-id="0ba32-125">Дополнительные сведения о `MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT` см. в разделе [Параметры ALTER DATABASE SET &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span><span class="sxs-lookup"><span data-stu-id="0ba32-125">For more information about `MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT`, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="0ba32-126">Кроме того, если уровень изоляции сессии задан как уровень изоляции READ COMMITTED, можно использовать режим автоматической фиксации транзакций.</span><span class="sxs-lookup"><span data-stu-id="0ba32-126">Alternatively, if the isolation level of the session is READ COMMITTED, you can use autocommit transactions.</span></span>  
  
 <span data-ttu-id="0ba32-127">Транзакции SNAPSHOT, запущенные в интерпретированном [!INCLUDE[tsql](../includes/tsql-md.md)], не смогут получать доступ к таблицам, оптимизированным для памяти.</span><span class="sxs-lookup"><span data-stu-id="0ba32-127">SNAPSHOT transactions started in interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] cannot access memory-optimized tables.</span></span>  
  
 <span data-ttu-id="0ba32-128">Поддерживаемые для оптимизированных для памяти таблиц уровни изоляции транзакций предоставляют те же логические гарантии, что и дисковые таблицы.</span><span class="sxs-lookup"><span data-stu-id="0ba32-128">The transaction isolation levels supported for memory-optimized tables provide the same logical guarantees as disk-based tables.</span></span> <span data-ttu-id="0ba32-129">Механизм, используемый для предоставления гарантий уровня изоляции, — иной.</span><span class="sxs-lookup"><span data-stu-id="0ba32-129">The mechanism used for providing isolation level guarantees is different.</span></span>  
  
 <span data-ttu-id="0ba32-130">Для дисковых таблиц большинство гарантий уровня изоляции реализуются с использованием блокировки, что предотвращает конфликты через блокировку.</span><span class="sxs-lookup"><span data-stu-id="0ba32-130">For disk-based tables, most isolation level guarantees are implemented using locking, which prevent conflicts through blocking.</span></span> <span data-ttu-id="0ba32-131">Гарантии для оптимизированных для памяти таблиц задаются с помощью механизма обнаружения конфликтов, который исключает необходимость принимать блокировки.</span><span class="sxs-lookup"><span data-stu-id="0ba32-131">For memory-optimized tables, the guarantees are enforced using a conflict detection mechanism, which avoids the need to take locks.</span></span> <span data-ttu-id="0ba32-132">Исключение — режим изоляции SNAPSHOT в дисковых таблицах.</span><span class="sxs-lookup"><span data-stu-id="0ba32-132">The exception is SNAPSHOT isolation on disk-based tables.</span></span> <span data-ttu-id="0ba32-133">Способ реализации такой же, как в режиме изоляции SNAPSHOT для оптимизированных для памяти таблиц с помощью механизма обнаружения конфликтов.</span><span class="sxs-lookup"><span data-stu-id="0ba32-133">This is implemented similarly to SNAPSHOT isolation on memory-optimized tables using a conflict detection mechanism.</span></span>  
  
 <span data-ttu-id="0ba32-134">SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="0ba32-134">SNAPSHOT</span></span>  
 <span data-ttu-id="0ba32-135">Этот уровень изоляции указывает на то, что данные, считанные любой инструкцией транзакции, будут согласованы на уровне транзакции с версией данных, существовавших в ее начале.</span><span class="sxs-lookup"><span data-stu-id="0ba32-135">This isolation level specifies that data read by any statement in a transaction will be the transactionally consistent version of the data that existed at the start of the transaction.</span></span> <span data-ttu-id="0ba32-136">Транзакция распознает только те изменения, которые были зафиксированы до ее начала.</span><span class="sxs-lookup"><span data-stu-id="0ba32-136">The transaction can only recognize data modifications that were committed before the start of the transaction.</span></span> <span data-ttu-id="0ba32-137">Инструкции, выполняемые текущей транзакцией, не видят изменений данных, произведенных другими транзакциями после запуска текущей транзакции.</span><span class="sxs-lookup"><span data-stu-id="0ba32-137">Data modifications made by other transactions after the start of the current transaction are not visible to statements executing in the current transaction.</span></span> <span data-ttu-id="0ba32-138">Инструкции в транзакции получают моментальный снимок зафиксированных данных на момент запуска транзакции.</span><span class="sxs-lookup"><span data-stu-id="0ba32-138">The statements in a transaction get a snapshot of the committed data as it existed at the start of the transaction.</span></span>  
  
 <span data-ttu-id="0ba32-139">Операции записи (обновления, вставки и удаления) всегда полностью изолированы от других транзакций.</span><span class="sxs-lookup"><span data-stu-id="0ba32-139">Write operations (updates, inserts and deletes) are always fully isolated from other transactions.</span></span> <span data-ttu-id="0ba32-140">Таким образом, операции записи в транзакции SNAPSHOT могут конфликтовать с операциями записи других транзакций.</span><span class="sxs-lookup"><span data-stu-id="0ba32-140">Therefore, the write operations in a SNAPSHOT transaction can conflict with write operations by other transactions.</span></span> <span data-ttu-id="0ba32-141">Если текущая транзакция пытается обновить или удалить строку, которая была обновлена или удалена другой транзакцией, зафиксированной после начала текущей транзакции, она прерывается со следующим сообщением об ошибке.</span><span class="sxs-lookup"><span data-stu-id="0ba32-141">When the current transaction attempts to update or delete a row that has been updated or deleted by another transaction that committed after the current transaction started, the transaction terminates with the following error message.</span></span>  
  
 <span data-ttu-id="0ba32-142">Ошибка 41302.</span><span class="sxs-lookup"><span data-stu-id="0ba32-142">Error 41302.</span></span> <span data-ttu-id="0ba32-143">Текущая транзакция попыталась обновить запись в таблице X, которая была изменена после начала этой транзакции.</span><span class="sxs-lookup"><span data-stu-id="0ba32-143">The current transaction attempted to update a record in table X that has been updated since this transaction started.</span></span> <span data-ttu-id="0ba32-144">Транзакция была прервана.</span><span class="sxs-lookup"><span data-stu-id="0ba32-144">The transaction was aborted.</span></span>  
  
 <span data-ttu-id="0ba32-145">Если текущая транзакция попытается вставить строку с тем же значением первичного ключа, как у строки, вставленной другой транзакцией, зафиксированной до текущей транзакции, то произойдет сбой фиксации со следующим сообщением об ошибке.</span><span class="sxs-lookup"><span data-stu-id="0ba32-145">When the current transaction attempts to insert a row with the same primary key value as a row that was inserted by another transaction that committed before the current transaction, there will be a failure to commit with the following error message.</span></span>  
  
 <span data-ttu-id="0ba32-146">Ошибка 41325.</span><span class="sxs-lookup"><span data-stu-id="0ba32-146">Error 41325.</span></span> <span data-ttu-id="0ba32-147">Текущей транзакции не удалось выполнить фиксацию из-за ошибки сериализуемой проверки.</span><span class="sxs-lookup"><span data-stu-id="0ba32-147">The current transaction failed to commit due to a serializable validation failure.</span></span>  
  
 <span data-ttu-id="0ba32-148">Если транзакция выполняет запись в таблицу, которая удалена до того, как транзакция зафиксирована, она прекращается со следующим сообщением об ошибке.</span><span class="sxs-lookup"><span data-stu-id="0ba32-148">If a transaction writes to a table that is dropped before the transaction commits, the transaction terminates with the following error message:</span></span>  
  
 <span data-ttu-id="0ba32-149">Ошибка 41305.</span><span class="sxs-lookup"><span data-stu-id="0ba32-149">Error 41305.</span></span> <span data-ttu-id="0ba32-150">Текущей транзакции не удалось выполнить фиксацию из-за ошибки проверки уровня изоляции REPEATABLE READ.</span><span class="sxs-lookup"><span data-stu-id="0ba32-150">The current transaction failed to commit due to a repeatable read validation failure.</span></span>  
  
 <span data-ttu-id="0ba32-151">REPEATABLE READ</span><span class="sxs-lookup"><span data-stu-id="0ba32-151">REPEATABLE READ</span></span>  
 <span data-ttu-id="0ba32-152">Этот уровень изоляции включает гарантии, заданные уровнем изоляции SNAPSHOT.</span><span class="sxs-lookup"><span data-stu-id="0ba32-152">This isolation level includes the guarantees given by SNAPSHOT isolation level.</span></span> <span data-ttu-id="0ba32-153">Кроме того, REPEATABLE READ гарантирует, что для любой строки, считанной транзакцией, в момент фиксации строка не была изменена никакой другой транзакцией.</span><span class="sxs-lookup"><span data-stu-id="0ba32-153">In addition, REPEATABLE READ guarantees that for any row that is read by the transaction, at the time the transaction commits the row has not been changed by any other transaction.</span></span> <span data-ttu-id="0ba32-154">Каждая операция чтения в транзакции повторяема до конца транзакции.</span><span class="sxs-lookup"><span data-stu-id="0ba32-154">Every read operation in the transaction is repeatable up to the end of the transaction.</span></span>  
  
 <span data-ttu-id="0ba32-155">Если текущая транзакция прочитала любую строку, которая затем обновлена другой транзакцией, которая выполнила фиксацию до текущей транзакции, то фиксация завершается сбоем и возвращает сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="0ba32-155">If the current transaction has read any row that has then been updated by another transaction that has committed before the current transaction, the commit fails with the following error message.</span></span>  
  
 <span data-ttu-id="0ba32-156">Ошибка 41305.</span><span class="sxs-lookup"><span data-stu-id="0ba32-156">Error 41305.</span></span> <span data-ttu-id="0ba32-157">Текущей транзакции не удалось выполнить фиксацию из-за ошибки проверки уровня изоляции REPEATABLE READ.</span><span class="sxs-lookup"><span data-stu-id="0ba32-157">The current transaction failed to commit due to a repeatable read validation failure.</span></span>  
  
 <span data-ttu-id="0ba32-158">SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="0ba32-158">SERIALIZABLE</span></span>  
 <span data-ttu-id="0ba32-159">Этот уровень изоляции включает гарантии, предоставляемые уровнем изоляции REPEATABLE READ.</span><span class="sxs-lookup"><span data-stu-id="0ba32-159">This isolation level includes the guarantees given by REPEATABLE READ.</span></span> <span data-ttu-id="0ba32-160">Фантомные строки не появлялись между созданием моментального снимка и окончанием транзакции.</span><span class="sxs-lookup"><span data-stu-id="0ba32-160">No phantom rows have appeared between the snapshot and the end of the transaction.</span></span> <span data-ttu-id="0ba32-161">Фантомные строки удовлетворяют условию фильтра выбора, обновления или удаления.</span><span class="sxs-lookup"><span data-stu-id="0ba32-161">Phantom rows match the filter condition of a select, update, or delete.</span></span>  
  
 <span data-ttu-id="0ba32-162">Транзакция выполняется, как будто параллельных транзакций нет.</span><span class="sxs-lookup"><span data-stu-id="0ba32-162">The transaction is executed as if there are no concurrent transactions.</span></span> <span data-ttu-id="0ba32-163">Фактически все действия выполняются в одной точке сериализации (время фиксации).</span><span class="sxs-lookup"><span data-stu-id="0ba32-163">All actions virtually occur at a single serialization point (commit time).</span></span>  
  
 <span data-ttu-id="0ba32-164">Если любая из этих гарантий нарушена, транзакции не удастся выполнить фиксацию со следующим сообщением об ошибке.</span><span class="sxs-lookup"><span data-stu-id="0ba32-164">If any of these guarantees is violated, the transaction fails to commit with the following error message:</span></span>  
  
 <span data-ttu-id="0ba32-165">Ошибка 41325.</span><span class="sxs-lookup"><span data-stu-id="0ba32-165">Error 41325.</span></span> <span data-ttu-id="0ba32-166">Текущей транзакции не удалось выполнить фиксацию из-за ошибки сериализуемой проверки.</span><span class="sxs-lookup"><span data-stu-id="0ba32-166">The current transaction failed to commit due to a serializable validation failure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba32-167">См. также:</span><span class="sxs-lookup"><span data-stu-id="0ba32-167">See Also</span></span>  
 <span data-ttu-id="0ba32-168">[Основные сведения о транзакциях в таблицах, оптимизированных для памяти](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="0ba32-168">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="0ba32-169">[Рекомендации по уровню изоляции транзакций с таблицами, оптимизированными для памяти](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="0ba32-169">[Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="0ba32-170">Рекомендации для логики повторного выполнения транзакций для таблиц, оптимизированных для памяти</span><span class="sxs-lookup"><span data-stu-id="0ba32-170">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  