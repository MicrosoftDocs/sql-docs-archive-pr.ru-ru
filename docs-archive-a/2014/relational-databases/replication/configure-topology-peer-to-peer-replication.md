---
title: Настройка топологии (одноранговая репликация) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.peers.f1
ms.assetid: 5377c59f-2e25-4852-a306-c87ae3dca9fd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2dfc09f5ae7f488afd46f29c301d11b7687e0a4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655093"
---
# <a name="configure-topology-peer-to-peer-replication"></a><span data-ttu-id="6fbbb-102">Настройка топологии (одноранговая репликация)</span><span class="sxs-lookup"><span data-stu-id="6fbbb-102">Configure Topology (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="6fbbb-103">Для выполнения таких наиболее типичных задач конфигурации, как добавление и удаление узлов, а также добавления новых соединений между существующими узлами, служит страница **Настройка топологии** .</span><span class="sxs-lookup"><span data-stu-id="6fbbb-103">Use the **Configure topology** page to perform common configuration tasks, such as adding new nodes, deleting nodes, and adding new connections between existing nodes.</span></span> <span data-ttu-id="6fbbb-104">Узел, выбранный на странице **Публикация** этого мастера, отображается в области конструктора.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-104">The node you selected on the **Publication** page of this wizard is displayed on the design surface.</span></span> <span data-ttu-id="6fbbb-105">Чтобы задать параметры конфигурации, щелкните правой кнопкой мыши узел, соединение или область конструктора.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-105">To specify configuration options, right-click a node, a connection, or the design surface.</span></span>

> [!NOTE]
>  <span data-ttu-id="6fbbb-106">Мастер настройки одноранговой топологии запрашивает сведения о топологии при закрытии этого мастера.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-106">The Configure Peer to Peer Topology Wizard requests topology information when the wizard is closed.</span></span> <span data-ttu-id="6fbbb-107">Если этот мастер был закрыт и вновь открыт до того, как все узлы ответили на запрос на информацию, мастер, возможно, отобразит лишь часть сети.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-107">If the wizard is closed and reopened before all nodes respond to the request for information, the wizard might show a partial network.</span></span>

## <a name="options"></a><span data-ttu-id="6fbbb-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="6fbbb-108">Options</span></span>
 <span data-ttu-id="6fbbb-109">Страница **Настройка топологии** содержит элементы интерфейса и параметры, доступные при щелчке правой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-109">The **Configure topology** page contains interface elements and options that are available when you right-click an element.</span></span> <span data-ttu-id="6fbbb-110">В следующей таблице содержатся описания всех элементов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-110">The following table describes each interface element.</span></span>

|<span data-ttu-id="6fbbb-111">Элемент интерфейса</span><span class="sxs-lookup"><span data-stu-id="6fbbb-111">Interface Element</span></span>|<span data-ttu-id="6fbbb-112">Description</span><span class="sxs-lookup"><span data-stu-id="6fbbb-112">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="6fbbb-113">Область конструктора</span><span class="sxs-lookup"><span data-stu-id="6fbbb-113">Design surface</span></span>|<span data-ttu-id="6fbbb-114">Отображает другие элементы интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-114">Displays other interface elements.</span></span> <span data-ttu-id="6fbbb-115">Для добавления элементов щелкните правой кнопкой область конструктора.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-115">To add elements, right-click the design surface.</span></span>|
|<span data-ttu-id="6fbbb-116">![Первый узел в топологии](media/p2pwizard-firstnode.gif "Первый узел в топологии")</span><span class="sxs-lookup"><span data-stu-id="6fbbb-116">![The first node in a topology](media/p2pwizard-firstnode.gif "The first node in a topology")</span></span>|<span data-ttu-id="6fbbb-117">Исходный узел в топологии.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-117">The original node in the topology.</span></span> <span data-ttu-id="6fbbb-118">Новые узлы инициализируются с помощью копии базы данных публикации исходного узла.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-118">New nodes are initialized by using a copy of the publication database from the original node.</span></span>|
|<span data-ttu-id="6fbbb-119">![Узел, для которого у нас есть полная информация](media/p2pwizard-complete.gif "Узел, для которого доступны полные сведения") или более поздняя версия, для которой репликация содержит полные сведения.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-119">![A node for which we have complete information](media/p2pwizard-complete.gif "A node for which we have complete information") or a later version, for which replication has complete information.</span></span> <span data-ttu-id="6fbbb-120">Чтобы указать параметры конфигурации, щелкните узел правой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-120">To specify configuration options, right-click the node.</span></span>|
|<span data-ttu-id="6fbbb-121">![Узел, для которого доступны неполные сведения](media/p2pwizard-incomplete.gif "Узел, для которого доступны неполные сведения")</span><span class="sxs-lookup"><span data-stu-id="6fbbb-121">![A node for which we have incomplete information](media/p2pwizard-incomplete.gif "A node for which we have incomplete information")</span></span>|<span data-ttu-id="6fbbb-122">Узел, для которого в репликации имеются неполные сведения.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-122">A node for which replication has incomplete information.</span></span> <span data-ttu-id="6fbbb-123">Чтобы указать параметры конфигурации, щелкните узел правой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-123">To specify configuration options, right-click the node.</span></span> <span data-ttu-id="6fbbb-124">В репликации содержатся неполные сведения по одной из следующих причин.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-124">Replication has incomplete information because of one of the following reasons:</span></span><br /><br /> <span data-ttu-id="6fbbb-125">На узле выполняется экземпляр [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], не хранящий все метаданные, которые требуются мастеру.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-125">The node is running an instance of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], which does not store all the metadata required by the wizard.</span></span><br /><br /> <span data-ttu-id="6fbbb-126">На узле выполняется экземпляр более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но репликации не удается получить с узла сведения о подписке.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-126">The node is running a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but replication cannot retrieve subscription information from the node.</span></span> <span data-ttu-id="6fbbb-127">Чтобы устранить эту неполадку, выполните следующее.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-127">To troubleshoot this situation:</span></span><br /><span data-ttu-id="6fbbb-128">— Убедитесь, что база данных на узле находится в оперативном режиме и к ней можно подключиться, используя те же учетные данные, что и агенты распространителя, подключающиеся к узлу.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-128">-Make sure that the database at the node is online and that you can connect to it by using the same credentials as the Distribution Agents that connect to the node.</span></span><br /><span data-ttu-id="6fbbb-129">Убедитесь, что агент чтения журнала и все агенты распространителя, подключающиеся к узлу, работают.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-129">-Make sure that the Log Reader Agent and all Distribution Agents that connect to the node are running.</span></span><br /><span data-ttu-id="6fbbb-130">— Убедитесь, что время ожидания обновления достаточно велико для сбора всех сведений о топологии.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-130">-Make sure that the refresh timeout is set high enough to gather all topology information.</span></span> <span data-ttu-id="6fbbb-131">Чтобы задать время ожидания обновления, щелкните правой кнопкой мыши область конструктора и выберите **Задать время ожидания обновления**.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-131">To set the time-out, right-click the design surface, and click **Set Refresh Timeout**.</span></span>|
|<span data-ttu-id="6fbbb-132">Серая линия со стрелками</span><span class="sxs-lookup"><span data-stu-id="6fbbb-132">Gray line with arrows</span></span>|<span data-ttu-id="6fbbb-133">Соединение между двумя узлами.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-133">The connection between two nodes.</span></span> <span data-ttu-id="6fbbb-134">Чтобы добавить соединение, щелкните правой кнопкой мыши нужный узел.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-134">To add a connection, right-click one of the nodes that you want to connect.</span></span> <span data-ttu-id="6fbbb-135">Чтобы удалить соединение, щелкните его правой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-135">To remove a connection, right-click the connection.</span></span><br /><br /> <span data-ttu-id="6fbbb-136">Если у линии одна стрелка, в репликации имеются неполные сведения об одном из узлов.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-136">If the line has a single arrow, replication has incomplete information for one of the nodes.</span></span>|

### <a name="options-for-the-design-surface"></a><span data-ttu-id="6fbbb-137">Параметры для области конструктора</span><span class="sxs-lookup"><span data-stu-id="6fbbb-137">Options for the Design Surface</span></span>
 <span data-ttu-id="6fbbb-138">**Отрисовать граф заново** Отрисовывает объекты в области конструктора, не обновляя топологию.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-138">**Redraw Graph** Redraw the objects on the design surface without refreshing the topology.</span></span> <span data-ttu-id="6fbbb-139">Отрисовка может помочь лучше представить топологию.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-139">Redrawing might provide a better view of the topology.</span></span>

 <span data-ttu-id="6fbbb-140">**Обновить топологию** Опрашивает каждый узел в топологии и отображает его обновленные сведения.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-140">**Refresh Topology** Query each node in the topology, and display updated information about each node.</span></span> <span data-ttu-id="6fbbb-141">Если в топологии много узлов, этот процесс может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-141">With many nodes, this process can take several minutes.</span></span>

 <span data-ttu-id="6fbbb-142">Если закрыть и вновь открыть мастер в то время, как он запрашивает сведения о топологии, причем не все узлы ответили на запрос, эта страница может отобразить не все узлы в топологии.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-142">If the wizard requests topology information, and then you close and reopen the wizard before all nodes respond to the request, this page might not display all nodes in the topology.</span></span>

 <span data-ttu-id="6fbbb-143">**Добавление нового однорангового узла** Добавьте экземпляр в одноранговую [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] топологию.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-143">**Add a New Peer Node** Add an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the peer-to-peer topology.</span></span> <span data-ttu-id="6fbbb-144">При добавлении экземпляра к узлу на этом экземпляре после завершения мастера создается публикация.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-144">Adding an instance as a node creates a publication at that instance after the wizard completes.</span></span> <span data-ttu-id="6fbbb-145">После добавления узла щелкните его правой кнопкой мыши, чтобы добавить соединение между новым и существующим узлом.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-145">After you add the node, right-click it to add a connection between the new node and an existing node.</span></span>

 <span data-ttu-id="6fbbb-146">Для участия в одноранговой топологии экземпляр должен удовлетворять следующим требованиям.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-146">To participate in a peer-to-peer topology, the instance must meet the following requirements:</span></span>

-   <span data-ttu-id="6fbbb-147">Должен быть сконфигурирован как распространитель или быть связан с удаленным распространителем.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-147">It must already be configured as a Distributor or be associated with a remote Distributor.</span></span>

-   <span data-ttu-id="6fbbb-148">Должен содержать копию базы данных, участвующей в репликации.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-148">It must contain a copy of the database involved in replication.</span></span> <span data-ttu-id="6fbbb-149">Она обычно является восстановленной резервной копией исходной базы данных публикации.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-149">This copy is typically a restored backup of the original publication database.</span></span>

 <span data-ttu-id="6fbbb-150">**Выберите узлы для просмотра** Выберите узлы для просмотра в области конструктора.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-150">**Select Node(s) to View** Select which nodes to view on the design surface.</span></span> <span data-ttu-id="6fbbb-151">Этот параметр полезен, если в топологии большое количество узлов.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-151">This option is useful if the topology has a large number of nodes.</span></span> <span data-ttu-id="6fbbb-152">Необходимо помнить, что соединения можно добавить только между узлами, видимыми в области конструктора.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-152">Be aware that you can add connections only between nodes that are visible on the design surface.</span></span>

 <span data-ttu-id="6fbbb-153">**Задать время ожидания обновления** Укажите, как долго может продолжаться процесс обновления, прежде чем истечет время ожидания.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-153">**Set Refresh Timeout** Specify how long the refresh process can run before the operation times out.</span></span>

### <a name="options-for-each-node"></a><span data-ttu-id="6fbbb-154">Параметры для каждого узла</span><span class="sxs-lookup"><span data-stu-id="6fbbb-154">Options for Each Node</span></span>
 <span data-ttu-id="6fbbb-155">**Добавить новое одноранговое соединение** Добавляет соединение между двумя узлами.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-155">**Add a New Peer Connection** Add a connection between two nodes.</span></span> <span data-ttu-id="6fbbb-156">Например, при добавлении соединения между узлом A и узлом B репликация добавляет две подписки: одна использует узел A для получения изменений от публикации на узле B, вторая позволяет узлу B получать изменения от публикации на узле A.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-156">For example, if you add a connection between Node A and Node B, replication adds two subscriptions: The first enables Node A to receive changes from the publication at Node B, and the second enables Node B to receive changes from the publication at Node A.</span></span>

 <span data-ttu-id="6fbbb-157">**Удалить одноранговый узел** Удаляет узел из топологии.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-157">**Delete Peer Node** Removes a node from the topology.</span></span> <span data-ttu-id="6fbbb-158">Например, при удалении узла C удаляется и публикация на этом узле.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-158">For example, if you remove Node C, the publication at that node is removed.</span></span> <span data-ttu-id="6fbbb-159">Также удаляются подписки между узлом A и узлом C, а также между узлом B и узлом C.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-159">Subscriptions between Node A and Node C, and Node B and Node C are also removed.</span></span> <span data-ttu-id="6fbbb-160">База данных на узле C не удаляется, а публикация и распространение не отключаются.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-160">The database at Node C is not deleted, and publishing and distribution are not disabled.</span></span>

> [!NOTE]
>  <span data-ttu-id="6fbbb-161">Настраивая одноранговую репликацию, укажите идентификатор для каждого узла.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-161">When you configure peer-to-peer replication, you specify an ID for each node.</span></span> <span data-ttu-id="6fbbb-162">Этот идентификатор должен быть уникальным на всех узлах в топологии. Он хранится в столбце originator_id системной таблицы [MSpeer_originatorid_history](/sql/relational-databases/system-tables/mspeer-originatorid-history-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="6fbbb-162">This ID, which must be unique across all nodes in the topology, is stored in the originator_id column in the [MSpeer_originatorid_history](/sql/relational-databases/system-tables/mspeer-originatorid-history-transact-sql) system table.</span></span> <span data-ttu-id="6fbbb-163">Если узел удаляется из топологии, идентификатор сохраняется в таблице журнала.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-163">If a node is removed from the topology, the ID is still retained in the history table.</span></span> <span data-ttu-id="6fbbb-164">Идентификатор сохраняется, чтобы предотвратить ложные конфликты, если в топологии продолжается репликация изменений, сделанных в удаленном узле.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-164">The ID is retained to prevent false conflicts from occurring if there are changes from the removed node that are still being replicated across the topology.</span></span> <span data-ttu-id="6fbbb-165">Если нужно повторно использовать идентификатор для нового узла, сначала необходимо вручную удалить идентификатор из таблицы MSpeer_originatorid_history на всех узлах.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-165">If you want to reuse the ID for a new node, you must first manually delete the ID from the MSpeer_originatorid_history table at all nodes.</span></span> <span data-ttu-id="6fbbb-166">Прежде чем удалить идентификатор для узла, выполните процедуру [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) , чтобы убедиться, что все изменения, исходящие с этого узла, были реплицированы.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-166">Before you delete an ID for a node, execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) to verify that all changes that originated from that node have been replicated.</span></span>

 <span data-ttu-id="6fbbb-167">**Подключиться ко всем отображенным узлам** Добавляет соединение между выбранным узлом и всеми остальными узлами.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-167">**Connect to ALL Displayed Nodes** Adds connections between the selected node and all other nodes.</span></span> <span data-ttu-id="6fbbb-168">Например, если в трехузловой топологии выбрать этот параметр для узла C, репликация добавляет четыре подписки: две используют узел A и узел B для получения изменений от публикации на узле C, а две используют узел C для получения изменений от публикаций на узле A и узле B.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-168">For example, if you selected this option for Node C in a three node topology, replication adds four subscriptions: two that enable Node A and Node B to receive changes from the publication at Node C, and two that enable Node C to receive changes from the publications at Node A and Node B.</span></span>

 <span data-ttu-id="6fbbb-169">**Выберите узлы для просмотра** Выберите узлы для просмотра в области конструктора.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-169">**Select Node(s) to View** Select which nodes to view on the design surface.</span></span> <span data-ttu-id="6fbbb-170">Этот параметр полезен, если в топологии большое количество узлов.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-170">This option is useful if the topology has a large number of nodes.</span></span> <span data-ttu-id="6fbbb-171">Необходимо помнить, что соединения можно добавить только между узлами, видимыми в области конструктора.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-171">Be aware that you can add connections only between nodes that are visible on the design surface.</span></span>

### <a name="options-for-the-connection-arrows"></a><span data-ttu-id="6fbbb-172">Параметры для стрелок соединений</span><span class="sxs-lookup"><span data-stu-id="6fbbb-172">Options for the Connection Arrows</span></span>
 <span data-ttu-id="6fbbb-173">**Удалить одноранговое соединение** Удаляет соединение между двумя узлами.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-173">**Remove Peer Connection** Remove a connection between two nodes.</span></span> <span data-ttu-id="6fbbb-174">Например, при удалении соединения между узлом A и узлом B репликация удаляет две подписки: одна использовала узел A для получения изменений от публикации на узле B, вторая — узел B для получения изменений от публикации на узле A.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-174">For example, if you remove a connection between Node A and Node B, replication drops two subscriptions: the one that enables Node A to receive changes from the publication at Node B, and the one that enables Node B to receive changes from the publication at Node A.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fbbb-175">См. также:</span><span class="sxs-lookup"><span data-stu-id="6fbbb-175">See Also</span></span>
 <span data-ttu-id="6fbbb-176">[Настройка публикации и распространения](configure-publishing-and-distribution.md) администрирование одноранговой [топологии &#40;программирование репликации на языке Transact-SQL&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) [одноранговой репликации транзакций](transactional/peer-to-peer-transactional-replication.md)</span><span class="sxs-lookup"><span data-stu-id="6fbbb-176">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)</span></span>

