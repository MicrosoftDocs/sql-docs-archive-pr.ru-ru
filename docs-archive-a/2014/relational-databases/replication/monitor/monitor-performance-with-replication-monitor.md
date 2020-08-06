---
title: Наблюдение за производительностью с помощью монитора репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Log Reader Agent, monitoring
- Replication Monitor, performance
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication]
ms.assetid: f212397d-1bfd-496b-a246-668952891d09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d02cb17aae5dfe72a9660de62e516e61313ef03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657650"
---
# <a name="monitor-performance-with-replication-monitor"></a><span data-ttu-id="e51d4-102">Наблюдение за производительностью с помощью монитора репликации</span><span class="sxs-lookup"><span data-stu-id="e51d4-102">Monitor Performance with Replication Monitor</span></span>
  <span data-ttu-id="e51d4-103">Монитор репликации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяет осуществлять наблюдение за производительностью репликации транзакций и репликации слиянием следующими способами.</span><span class="sxs-lookup"><span data-stu-id="e51d4-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor allows you to monitor the performance of transactional replication and merge replication in the following ways:</span></span>  
  
-   <span data-ttu-id="e51d4-104">Установка предупреждений и порогов.</span><span class="sxs-lookup"><span data-stu-id="e51d4-104">Setting warnings and thresholds</span></span>  
  
-   <span data-ttu-id="e51d4-105">Просмотр показателей производительности.</span><span class="sxs-lookup"><span data-stu-id="e51d4-105">Viewing performance measurements</span></span>  
  
-   <span data-ttu-id="e51d4-106">Определение задержки с помощью трассировочных токенов (репликация транзакций).</span><span class="sxs-lookup"><span data-stu-id="e51d4-106">Determining latency with tracer tokens (transactional replication)</span></span>  
  
-   <span data-ttu-id="e51d4-107">Просмотр подробной статистики синхронизации (репликация слиянием).</span><span class="sxs-lookup"><span data-stu-id="e51d4-107">Viewing detailed synchronization statistics (merge replication)</span></span>  
  
-   <span data-ttu-id="e51d4-108">Просмотр времени выполнения и доставки транзакций (репликация транзакций).</span><span class="sxs-lookup"><span data-stu-id="e51d4-108">Viewing transactions and delivery time (transactional replication)</span></span>  
  
## <a name="set-warnings-and-thresholds"></a><span data-ttu-id="e51d4-109">Настройка предупреждений и пороговых значений</span><span class="sxs-lookup"><span data-stu-id="e51d4-109">Set Warnings and Thresholds</span></span>  
 <span data-ttu-id="e51d4-110">С помощью монитора репликации можно включить предупреждения для ряда условий производительности.</span><span class="sxs-lookup"><span data-stu-id="e51d4-110">Replication Monitor allows you to enable warnings for a number of performance conditions.</span></span> <span data-ttu-id="e51d4-111">При включении предупреждения требуется задать пороговое значение.</span><span class="sxs-lookup"><span data-stu-id="e51d4-111">When you enable a warning, you specify a threshold.</span></span> <span data-ttu-id="e51d4-112">Если при выполнении транзакции было достигнуто или превышено пороговое значение, предупреждение отображается в столбце **Состояние** для подписки и публикации, с которой она синхронизируется (за исключением случаев, когда требуется отобразить сообщение с более высоким приоритетом).</span><span class="sxs-lookup"><span data-stu-id="e51d4-112">When that threshold is met or exceeded, a warning is displayed in the **Status** column for the subscription and the publication with which it synchronizes (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="e51d4-113">Достижение порогового значения помимо отображения предупреждения в мониторе репликации может также вызывать системное предупреждение.</span><span class="sxs-lookup"><span data-stu-id="e51d4-113">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="e51d4-114">Можно включить предупреждения для следующих условий производительности:</span><span class="sxs-lookup"><span data-stu-id="e51d4-114">You can enable warnings for the following performance conditions:</span></span>  
  
-   <span data-ttu-id="e51d4-115">Превышение указанного времени задержки (время между моментом фиксирования транзакции на издателе и моментом фиксирования соответствующей транзакции на подписчике).</span><span class="sxs-lookup"><span data-stu-id="e51d4-115">Exceeding the specified latency (the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber).</span></span>  
  
     <span data-ttu-id="e51d4-116">Это условие применяется к репликации транзакций.</span><span class="sxs-lookup"><span data-stu-id="e51d4-116">This applies to transactional replication.</span></span> <span data-ttu-id="e51d4-117">Когда достигается или превышается указанное значение порога, состояние отображается как **Критическое для производительности**.</span><span class="sxs-lookup"><span data-stu-id="e51d4-117">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span>  
  
-   <span data-ttu-id="e51d4-118">Превышение заданного времени синхронизации.</span><span class="sxs-lookup"><span data-stu-id="e51d4-118">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="e51d4-119">Это условие применяется к репликации слиянием.</span><span class="sxs-lookup"><span data-stu-id="e51d4-119">This applies to merge replication.</span></span> <span data-ttu-id="e51d4-120">Когда достигается или превышается указанное значение порога, состояние отображается как **Продолжительное слияние**.</span><span class="sxs-lookup"><span data-stu-id="e51d4-120">If the specified threshold is met or exceeded, the status is displayed as **Long-running merge**.</span></span> <span data-ttu-id="e51d4-121">Для коммутируемого соединения и соединения по локальной сети можно задать разные пороговые значения.</span><span class="sxs-lookup"><span data-stu-id="e51d4-121">You can specify different thresholds for dial-up and Local Area Network (LAN) connections.</span></span>  
  
-   <span data-ttu-id="e51d4-122">Невозможность обработки заданного числа строк за указанное время.</span><span class="sxs-lookup"><span data-stu-id="e51d4-122">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="e51d4-123">Это условие применяется к репликации слиянием.</span><span class="sxs-lookup"><span data-stu-id="e51d4-123">This applies to merge replication.</span></span> <span data-ttu-id="e51d4-124">Когда достигается или превышается указанное значение порога, состояние отображается как **Критическое для производительности**.</span><span class="sxs-lookup"><span data-stu-id="e51d4-124">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span> <span data-ttu-id="e51d4-125">Для коммутируемого соединения и соединения по локальной сети можно задать разные пороговые значения.</span><span class="sxs-lookup"><span data-stu-id="e51d4-125">You can specify different thresholds for dial-up and LAN connections.</span></span>  
  
 <span data-ttu-id="e51d4-126">Дополнительные сведения см. в статье [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span><span class="sxs-lookup"><span data-stu-id="e51d4-126">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
## <a name="view-performance-measurements"></a><span data-ttu-id="e51d4-127">Просмотр показателей производительности</span><span class="sxs-lookup"><span data-stu-id="e51d4-127">View Performance Measurements</span></span>  
 <span data-ttu-id="e51d4-128">Монитор репликации отображает значения качества производительности для репликации транзакций и репликации слиянием в столбцах **Текущая средняя производительность** и **Худшая производительность в данный момент** для публикации и в столбце **Производительность** для подписок.</span><span class="sxs-lookup"><span data-stu-id="e51d4-128">Replication Monitor displays performance quality values for transactional replication and merge replication in the **Current Average Performance** and **Current Worst Performance** columns for publications and the **Performance** column for subscriptions.</span></span> <span data-ttu-id="e51d4-129">Значения качества производительности:</span><span class="sxs-lookup"><span data-stu-id="e51d4-129">The values are:</span></span>  
  
-   <span data-ttu-id="e51d4-130">Высокая</span><span class="sxs-lookup"><span data-stu-id="e51d4-130">Excellent</span></span>  
  
-   <span data-ttu-id="e51d4-131">Хорошая.</span><span class="sxs-lookup"><span data-stu-id="e51d4-131">Good</span></span>  
  
-   <span data-ttu-id="e51d4-132">удовлетворительная</span><span class="sxs-lookup"><span data-stu-id="e51d4-132">Fair</span></span>  
  
-   <span data-ttu-id="e51d4-133">Низкая</span><span class="sxs-lookup"><span data-stu-id="e51d4-133">Poor</span></span>  
  
-   <span data-ttu-id="e51d4-134">Критическое (только для репликаций транзакций).</span><span class="sxs-lookup"><span data-stu-id="e51d4-134">Critical (transactional replication only)</span></span>  
  
 <span data-ttu-id="e51d4-135">Значения определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e51d4-135">The values are determined in the following ways:</span></span>  
  
-   <span data-ttu-id="e51d4-136">Для репликаций транзакций качество производительности определяется пороговым значением времени задержки.</span><span class="sxs-lookup"><span data-stu-id="e51d4-136">For transactional replication, performance quality is determined by the latency threshold.</span></span> <span data-ttu-id="e51d4-137">Если пороговое значение не задано, значение не отображается.</span><span class="sxs-lookup"><span data-stu-id="e51d4-137">If the threshold is not set, a value is not displayed.</span></span> <span data-ttu-id="e51d4-138">В следующей таблице показана взаимосвязь между пороговым значением и значением качества производительности.</span><span class="sxs-lookup"><span data-stu-id="e51d4-138">The following table shows the correlation between the threshold and the performance quality value.</span></span> <span data-ttu-id="e51d4-139">Например, если для порога задано значение 60 секунд, а текущая задержка — 30 секунд, то задержка составляет 50% заданного порогового значения, что приводит к значению качества производительности «Хорошее».</span><span class="sxs-lookup"><span data-stu-id="e51d4-139">For example, if the threshold is set to 60 seconds and the actual latency is 30 seconds, latency is 50% of the threshold, resulting in a value of Good.</span></span>  
  
    |<span data-ttu-id="e51d4-140">Высокая</span><span class="sxs-lookup"><span data-stu-id="e51d4-140">Excellent</span></span>|<span data-ttu-id="e51d4-141">Хорошая.</span><span class="sxs-lookup"><span data-stu-id="e51d4-141">Good</span></span>|<span data-ttu-id="e51d4-142">удовлетворительная</span><span class="sxs-lookup"><span data-stu-id="e51d4-142">Fair</span></span>|<span data-ttu-id="e51d4-143">Низкая</span><span class="sxs-lookup"><span data-stu-id="e51d4-143">Poor</span></span>|<span data-ttu-id="e51d4-144">Critical</span><span class="sxs-lookup"><span data-stu-id="e51d4-144">Critical</span></span>|  
    |---------------|----------|----------|----------|--------------|  
    |<span data-ttu-id="e51d4-145">0–34 %</span><span class="sxs-lookup"><span data-stu-id="e51d4-145">0 - 34%</span></span>|<span data-ttu-id="e51d4-146">35–59 %</span><span class="sxs-lookup"><span data-stu-id="e51d4-146">35 - 59%</span></span>|<span data-ttu-id="e51d4-147">60–84 %</span><span class="sxs-lookup"><span data-stu-id="e51d4-147">60 - 84%</span></span>|<span data-ttu-id="e51d4-148">85–99 %</span><span class="sxs-lookup"><span data-stu-id="e51d4-148">85 - 99%</span></span>|<span data-ttu-id="e51d4-149">100 % +</span><span class="sxs-lookup"><span data-stu-id="e51d4-149">100% +</span></span>|  
  
-   <span data-ttu-id="e51d4-150">Для репликаций слиянием качество производительности не зависит ни от каких пороговых значений (пороговое значение для обработки строк определяет только появление значения **Критическое для производительности** в столбце **Состояние** ).</span><span class="sxs-lookup"><span data-stu-id="e51d4-150">For merge replication, performance quality is independent of either threshold (the row processing threshold does determine if a value of **Performance critical** is displayed in the **Status** column).</span></span> <span data-ttu-id="e51d4-151">Оценка качества производительности определяется посредством сравнения производительности индивидуальной подписки со средним значением производительности за длительный период для подписок на данную публикацию, имеющих один и тот же тип соединения (коммутируемое или по локальной сети).</span><span class="sxs-lookup"><span data-stu-id="e51d4-151">Performance quality is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="e51d4-152">Монитор репликации отображает значение после пяти синхронизаций, использующих один тип соединения, каждая из которых содержит 50 или более изменений.</span><span class="sxs-lookup"><span data-stu-id="e51d4-152">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="e51d4-153">В случае, если произошло менее 5 синхронизаций с 50 и более изменениями или если в последней выполненной синхронизации менее 50 изменений, монитор репликации не отображает это значение.</span><span class="sxs-lookup"><span data-stu-id="e51d4-153">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, Replication Monitor does not display a value.</span></span>  
  
     <span data-ttu-id="e51d4-154">В следующей таблице показана взаимосвязь между средней производительностью и значением качества производительности.</span><span class="sxs-lookup"><span data-stu-id="e51d4-154">The following table shows the correlation between the average performance and the performance quality value.</span></span> <span data-ttu-id="e51d4-155">Например, если десять подписчиков осуществили синхронизацию, используя соединение по локальной сети со средним показателем 100 строк в секунду, после чего при синхронизации одной из подписок показатель был 125 строк в секунду, производительность синхронизации для этого подписчика будет 125% от среднего значения, что соответствует качеству производительности «Хорошее».</span><span class="sxs-lookup"><span data-stu-id="e51d4-155">For example, if ten Subscribers have synchronized over a LAN connection with an average rate of 100 rows per second, and one of the subscriptions then synchronizes at a rate of 125 rows per second, the performance for that Subscriber's synchronization is 125% of the average, resulting in a value of Good.</span></span>  
  
    |<span data-ttu-id="e51d4-156">Высокая</span><span class="sxs-lookup"><span data-stu-id="e51d4-156">Excellent</span></span>|<span data-ttu-id="e51d4-157">Хорошая.</span><span class="sxs-lookup"><span data-stu-id="e51d4-157">Good</span></span>|<span data-ttu-id="e51d4-158">удовлетворительная</span><span class="sxs-lookup"><span data-stu-id="e51d4-158">Fair</span></span>|<span data-ttu-id="e51d4-159">Низкая</span><span class="sxs-lookup"><span data-stu-id="e51d4-159">Poor</span></span>|  
    |---------------|----------|----------|----------|  
    |<span data-ttu-id="e51d4-160">151+%</span><span class="sxs-lookup"><span data-stu-id="e51d4-160">151+%</span></span>|<span data-ttu-id="e51d4-161">76–150 %</span><span class="sxs-lookup"><span data-stu-id="e51d4-161">76 - 150%</span></span>|<span data-ttu-id="e51d4-162">26–75 %</span><span class="sxs-lookup"><span data-stu-id="e51d4-162">26 - 75%</span></span>|<span data-ttu-id="e51d4-163">0–25 %</span><span class="sxs-lookup"><span data-stu-id="e51d4-163">0 - 25%</span></span>|  
  
 <span data-ttu-id="e51d4-164">Дополнительные сведения о просмотре информации о подписках см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](view-information-and-perform-tasks-replication-monitor.md).</span><span class="sxs-lookup"><span data-stu-id="e51d4-164">For more information about viewing subscription information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="determine-latency-with-tracer-tokens"></a><span data-ttu-id="e51d4-165">Определение времени задержки с помощью трассировочных токенов</span><span class="sxs-lookup"><span data-stu-id="e51d4-165">Determine Latency with Tracer Tokens</span></span>  
 <span data-ttu-id="e51d4-166">Репликация транзакций позволяет измерить период задержки в системе путем вставки токена (некоторого количества данных) в журнал транзакций базы данных публикации и записи периода времени, необходимого токену для прибытия на распространитель и подписчики.</span><span class="sxs-lookup"><span data-stu-id="e51d4-166">Transactional replication allows you to measure the latency in a system by inserting a token (a small amount of data) in the transaction log of the publication database and recording how long it takes to arrive at the Distributor and Subscribers.</span></span> <span data-ttu-id="e51d4-167">Токен позволяет также определить случаи, когда данные не достигают распространителя или подписчика.</span><span class="sxs-lookup"><span data-stu-id="e51d4-167">The token also allows you to identify if data is not reaching the Distributor or Subscriber.</span></span> <span data-ttu-id="e51d4-168">Дополнительные сведения см. в статье [Измерение задержки и проверка правильности соединений для репликации транзакций](measure-latency-and-validate-connections-for-transactional-replication.md).</span><span class="sxs-lookup"><span data-stu-id="e51d4-168">For more information, see [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
## <a name="view-detailed-synchronization-performance-for-merge-replication"></a><span data-ttu-id="e51d4-169">Просмотр подробных сведений о производительности синхронизации для репликации слиянием</span><span class="sxs-lookup"><span data-stu-id="e51d4-169">View Detailed Synchronization Performance for Merge Replication</span></span>  
 <span data-ttu-id="e51d4-170">Для репликаций слиянием монитор репликации отображает подробную статистику для каждой статьи, обработанной в процессе синхронизации, включая время, затраченное на каждую стадию обработки (передача изменений, загрузка изменений и т.д.).</span><span class="sxs-lookup"><span data-stu-id="e51d4-170">For merge replication, Replication Monitor displays detailed statistics for each article processed during synchronization, including the amount of time spent in each processing phase (uploading changes, downloading changes, and so on).</span></span> <span data-ttu-id="e51d4-171">С помощью монитора репликации можно обнаружить особые таблицы, вызывающие замедление, к тому же, в мониторе репликации удобно устранять проблемы, связанные с производительностью подписок на публикацию слиянием.</span><span class="sxs-lookup"><span data-stu-id="e51d4-171">It can help pinpoint specific tables that are causing slow downs and is the best place to troubleshoot performance issues with merge subscriptions.</span></span> <span data-ttu-id="e51d4-172">Дополнительные сведения о просмотре подробной статистики см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](view-information-and-perform-tasks-replication-monitor.md).</span><span class="sxs-lookup"><span data-stu-id="e51d4-172">For more information on viewing detailed statistics, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="view-transactions-and-delivery-time-for-transactional-replication"></a><span data-ttu-id="e51d4-173">Просмотр времени выполнения и доставки транзакций для репликации транзакций</span><span class="sxs-lookup"><span data-stu-id="e51d4-173">View Transactions and Delivery Time for Transactional Replication</span></span>  
 <span data-ttu-id="e51d4-174">Для репликации транзакций монитор репликации отображает информацию о количестве транзакций в базе данных распространителя, которые еще не были переданы на подписчик, и предполагаемое время, затрачиваемое на распространение этих транзакций.</span><span class="sxs-lookup"><span data-stu-id="e51d4-174">For transactional replication, Replication Monitor displays information about the number of transactions in the distribution database that have not yet been distributed to a Subscriber and the estimated time for distributing these transactions.</span></span> <span data-ttu-id="e51d4-175">Дополнительные сведения см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](view-information-and-perform-tasks-replication-monitor.md).</span><span class="sxs-lookup"><span data-stu-id="e51d4-175">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51d4-176">См. также:</span><span class="sxs-lookup"><span data-stu-id="e51d4-176">See Also</span></span>  
 <span data-ttu-id="e51d4-177">[Наблюдение за репликацией](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e51d4-177">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 [<span data-ttu-id="e51d4-178">Set Thresholds and Warnings in Replication Monitor</span><span class="sxs-lookup"><span data-stu-id="e51d4-178">Set Thresholds and Warnings in Replication Monitor</span></span>](set-thresholds-and-warnings-in-replication-monitor.md)  
  
  