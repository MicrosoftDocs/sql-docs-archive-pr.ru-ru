---
title: Класс событий Broker:Activation | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
author: stevestein
ms.author: sstein
ms.openlocfilehash: 653085cd6e88fe5b18653a0a8ed82491f5b4333e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666637"
---
# <a name="brokeractivation-event-class"></a><span data-ttu-id="d974c-102">Broker:Activation, класс событий</span><span class="sxs-lookup"><span data-stu-id="d974c-102">Broker:Activation Event Class</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d974c-103">формирует событие **Broker:Activation** , если монитор очереди запускает хранимую процедуру активации, отправляет уведомление QUEUE_ACTIVATION или если существует хранимая процедура активации, запущенная монитором очереди.</span><span class="sxs-lookup"><span data-stu-id="d974c-103">generates a **Broker:Activation** event when a queue monitor starts an activation stored procedure, sends a QUEUE_ACTIVATION notification, or when an activation stored procedure started by a queue monitor exits.</span></span>  
  
## <a name="brokeractivation-event-class-data-columns"></a><span data-ttu-id="d974c-104">Столбцы данных класса событий Broker:Activation</span><span class="sxs-lookup"><span data-stu-id="d974c-104">Broker:Activation Event Class Data Columns</span></span>  
  
|<span data-ttu-id="d974c-105">Столбец данных</span><span class="sxs-lookup"><span data-stu-id="d974c-105">Data column</span></span>|<span data-ttu-id="d974c-106">Тип</span><span class="sxs-lookup"><span data-stu-id="d974c-106">Type</span></span>|<span data-ttu-id="d974c-107">Description</span><span class="sxs-lookup"><span data-stu-id="d974c-107">Description</span></span>|<span data-ttu-id="d974c-108">Номер столбца</span><span class="sxs-lookup"><span data-stu-id="d974c-108">Column number</span></span>|<span data-ttu-id="d974c-109">Фильтруемый</span><span class="sxs-lookup"><span data-stu-id="d974c-109">Filterable</span></span>|  
|-----------------|----------|-----------------|-------------------|----------------|  
|<span data-ttu-id="d974c-110">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="d974c-110">**ClientProcessID**</span></span>|`int`|<span data-ttu-id="d974c-111">Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="d974c-111">The ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="d974c-112">Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.</span><span class="sxs-lookup"><span data-stu-id="d974c-112">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="d974c-113">9</span><span class="sxs-lookup"><span data-stu-id="d974c-113">9</span></span>|<span data-ttu-id="d974c-114">Да</span><span class="sxs-lookup"><span data-stu-id="d974c-114">Yes</span></span>|  
|<span data-ttu-id="d974c-115">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="d974c-115">**DatabaseID**</span></span>|`int`|<span data-ttu-id="d974c-116">Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database*не выполнялась.</span><span class="sxs-lookup"><span data-stu-id="d974c-116">The ID of the database specified by the USE *database* statement, or the ID of the default database if no USE *database*statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="d974c-117">отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен.</span><span class="sxs-lookup"><span data-stu-id="d974c-117">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="d974c-118">Определите значение для базы данных, используя функцию DB_ID.</span><span class="sxs-lookup"><span data-stu-id="d974c-118">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="d974c-119">3</span><span class="sxs-lookup"><span data-stu-id="d974c-119">3</span></span>|<span data-ttu-id="d974c-120">Да</span><span class="sxs-lookup"><span data-stu-id="d974c-120">Yes</span></span>|  
|<span data-ttu-id="d974c-121">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="d974c-121">**EventClass**</span></span>|`int`|<span data-ttu-id="d974c-122">Тип захваченного класса событий.</span><span class="sxs-lookup"><span data-stu-id="d974c-122">The type of event class captured.</span></span> <span data-ttu-id="d974c-123">Всегда **163** для **Broker:Activation**.</span><span class="sxs-lookup"><span data-stu-id="d974c-123">Always **163** for **Broker:Activation**.</span></span>|<span data-ttu-id="d974c-124">27</span><span class="sxs-lookup"><span data-stu-id="d974c-124">27</span></span>|<span data-ttu-id="d974c-125">Нет</span><span class="sxs-lookup"><span data-stu-id="d974c-125">No</span></span>|  
|<span data-ttu-id="d974c-126">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="d974c-126">**EventSequence**</span></span>|`int`|<span data-ttu-id="d974c-127">Порядковый номер этого события.</span><span class="sxs-lookup"><span data-stu-id="d974c-127">Sequence number for this event.</span></span>|<span data-ttu-id="d974c-128">51</span><span class="sxs-lookup"><span data-stu-id="d974c-128">51</span></span>|<span data-ttu-id="d974c-129">Нет</span><span class="sxs-lookup"><span data-stu-id="d974c-129">No</span></span>|  
|<span data-ttu-id="d974c-130">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="d974c-130">**EventSubClass**</span></span>|`nvarchar`|<span data-ttu-id="d974c-131">Конкретное действие, о котором сообщает это событие.</span><span class="sxs-lookup"><span data-stu-id="d974c-131">The specific action that this event reports.</span></span> <span data-ttu-id="d974c-132">Принимает одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="d974c-132">One of the following values:</span></span><br /><br /> <span data-ttu-id="d974c-133">**Начало**работы:</span><span class="sxs-lookup"><span data-stu-id="d974c-133">**start**:</span></span> <br />                [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d974c-134">запустил хранимую процедуру активации.</span><span class="sxs-lookup"><span data-stu-id="d974c-134">started an activation stored procedure.</span></span><br /><br /> <span data-ttu-id="d974c-135">**закончено**: хранимая процедура активации завершила работу нормально.</span><span class="sxs-lookup"><span data-stu-id="d974c-135">**ended**: The activation stored procedure exited normally.</span></span><br /><br /> <span data-ttu-id="d974c-136">**прервано**: хранимая процедура активации завершила работу с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="d974c-136">**aborted**: The activation stored procedure exited with an error.</span></span>|<span data-ttu-id="d974c-137">21</span><span class="sxs-lookup"><span data-stu-id="d974c-137">21</span></span>|<span data-ttu-id="d974c-138">нет</span><span class="sxs-lookup"><span data-stu-id="d974c-138">No</span></span>|  
|<span data-ttu-id="d974c-139">**HostName**</span><span class="sxs-lookup"><span data-stu-id="d974c-139">**HostName**</span></span>|`nvarchar`|<span data-ttu-id="d974c-140">Имя компьютера, на котором выполняется клиентская программа.</span><span class="sxs-lookup"><span data-stu-id="d974c-140">The name of the computer on which the client is running.</span></span> <span data-ttu-id="d974c-141">Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла.</span><span class="sxs-lookup"><span data-stu-id="d974c-141">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="d974c-142">Чтобы определить имя узла, используйте функцию HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="d974c-142">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="d974c-143">8</span><span class="sxs-lookup"><span data-stu-id="d974c-143">8</span></span>|<span data-ttu-id="d974c-144">Да</span><span class="sxs-lookup"><span data-stu-id="d974c-144">Yes</span></span>|  
|<span data-ttu-id="d974c-145">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="d974c-145">**IntegerData**</span></span>|`int`|<span data-ttu-id="d974c-146">Число активных задач в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="d974c-146">The number of tasks active on this queue.</span></span>|<span data-ttu-id="d974c-147">25</span><span class="sxs-lookup"><span data-stu-id="d974c-147">25</span></span>|<span data-ttu-id="d974c-148">Нет</span><span class="sxs-lookup"><span data-stu-id="d974c-148">No</span></span>|  
|<span data-ttu-id="d974c-149">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="d974c-149">**IsSystem**</span></span>|`int`|<span data-ttu-id="d974c-150">Указывает, произошло событие в системном или в пользовательском процессе.</span><span class="sxs-lookup"><span data-stu-id="d974c-150">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="d974c-151">1 = системный, 0 = пользовательский.</span><span class="sxs-lookup"><span data-stu-id="d974c-151">1 = system, 0 = user.</span></span>|<span data-ttu-id="d974c-152">60</span><span class="sxs-lookup"><span data-stu-id="d974c-152">60</span></span>|<span data-ttu-id="d974c-153">нет</span><span class="sxs-lookup"><span data-stu-id="d974c-153">No</span></span>|  
|<span data-ttu-id="d974c-154">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="d974c-154">**LoginSid**</span></span>|`image`|<span data-ttu-id="d974c-155">Идентификатор безопасности вошедшего в систему пользователя.</span><span class="sxs-lookup"><span data-stu-id="d974c-155">The security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="d974c-156">Значение идентификатора безопасности уникально для каждого имени входа на сервере.</span><span class="sxs-lookup"><span data-stu-id="d974c-156">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="d974c-157">41</span><span class="sxs-lookup"><span data-stu-id="d974c-157">41</span></span>|<span data-ttu-id="d974c-158">Да</span><span class="sxs-lookup"><span data-stu-id="d974c-158">Yes</span></span>|  
|<span data-ttu-id="d974c-159">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="d974c-159">**NTDomainName**</span></span>|`nvarchar`|<span data-ttu-id="d974c-160">Домен Windows, к которому принадлежит пользователь.</span><span class="sxs-lookup"><span data-stu-id="d974c-160">The Windows domain to which the user belongs.</span></span>|<span data-ttu-id="d974c-161">7</span><span class="sxs-lookup"><span data-stu-id="d974c-161">7</span></span>|<span data-ttu-id="d974c-162">Да</span><span class="sxs-lookup"><span data-stu-id="d974c-162">Yes</span></span>|  
|<span data-ttu-id="d974c-163">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="d974c-163">**NTUserName**</span></span>|`nvarchar`|<span data-ttu-id="d974c-164">Имя пользователя, которому принадлежит соединение, создавшее это событие.</span><span class="sxs-lookup"><span data-stu-id="d974c-164">The name of the user that owns the connection that generated this event.</span></span>|<span data-ttu-id="d974c-165">6</span><span class="sxs-lookup"><span data-stu-id="d974c-165">6</span></span>|<span data-ttu-id="d974c-166">Да</span><span class="sxs-lookup"><span data-stu-id="d974c-166">Yes</span></span>|  
|<span data-ttu-id="d974c-167">**ObjectID**</span><span class="sxs-lookup"><span data-stu-id="d974c-167">**ObjectID**</span></span>|`int`|<span data-ttu-id="d974c-168">Очередь, связанная с этим событием.</span><span class="sxs-lookup"><span data-stu-id="d974c-168">The queue associated with this event.</span></span>|<span data-ttu-id="d974c-169">22</span><span class="sxs-lookup"><span data-stu-id="d974c-169">22</span></span>|<span data-ttu-id="d974c-170">нет</span><span class="sxs-lookup"><span data-stu-id="d974c-170">No</span></span>|  
|<span data-ttu-id="d974c-171">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="d974c-171">**ServerName**</span></span>|`nvarchar`|<span data-ttu-id="d974c-172">Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемого трассировке.</span><span class="sxs-lookup"><span data-stu-id="d974c-172">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="d974c-173">26</span><span class="sxs-lookup"><span data-stu-id="d974c-173">26</span></span>|<span data-ttu-id="d974c-174">нет</span><span class="sxs-lookup"><span data-stu-id="d974c-174">No</span></span>|  
|<span data-ttu-id="d974c-175">**SPID**</span><span class="sxs-lookup"><span data-stu-id="d974c-175">**SPID**</span></span>|`int`|<span data-ttu-id="d974c-176">Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.</span><span class="sxs-lookup"><span data-stu-id="d974c-176">The server process ID assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the process associated with the client.</span></span>|<span data-ttu-id="d974c-177">12</span><span class="sxs-lookup"><span data-stu-id="d974c-177">12</span></span>|<span data-ttu-id="d974c-178">Да</span><span class="sxs-lookup"><span data-stu-id="d974c-178">Yes</span></span>|  
|<span data-ttu-id="d974c-179">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="d974c-179">**StartTime**</span></span>|`datetime`|<span data-ttu-id="d974c-180">Время начала события, если доступно.</span><span class="sxs-lookup"><span data-stu-id="d974c-180">The time at which the event started, when available.</span></span>|<span data-ttu-id="d974c-181">14</span><span class="sxs-lookup"><span data-stu-id="d974c-181">14</span></span>|<span data-ttu-id="d974c-182">Да</span><span class="sxs-lookup"><span data-stu-id="d974c-182">Yes</span></span>|  
|<span data-ttu-id="d974c-183">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="d974c-183">**TransactionID**</span></span>|`bigint`|<span data-ttu-id="d974c-184">Назначенный системой идентификатор транзакции.</span><span class="sxs-lookup"><span data-stu-id="d974c-184">The system-assigned ID of the transaction.</span></span>|<span data-ttu-id="d974c-185">4</span><span class="sxs-lookup"><span data-stu-id="d974c-185">4</span></span>|<span data-ttu-id="d974c-186">нет</span><span class="sxs-lookup"><span data-stu-id="d974c-186">No</span></span>|  
  
  