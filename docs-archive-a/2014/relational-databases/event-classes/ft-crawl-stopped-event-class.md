---
title: Класс событий FT:Crawl Stopped | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Crawl Stopped event class
ms.assetid: dbc91bf7-687c-4083-9694-02f3e102c175
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4fe72aa8b6c38a25baf537eb01bac7924d43e290
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657128"
---
# <a name="ftcrawl-stopped-event-class"></a><span data-ttu-id="1dea7-102">Класс событий FT:Crawl Stopped</span><span class="sxs-lookup"><span data-stu-id="1dea7-102">FT:Crawl Stopped Event Class</span></span>
  <span data-ttu-id="1dea7-103">Класс событий **:Crawl Stopped** указывает на то, что полнотекстовое сканирование (заполнение) было остановлено.</span><span class="sxs-lookup"><span data-stu-id="1dea7-103">The **:Crawl Stopped** event class indicates that a full-text crawl (population) has stopped.</span></span> <span data-ttu-id="1dea7-104">Остановка может быть результатом успешного завершения сканирования или появления неустранимой ошибки.</span><span class="sxs-lookup"><span data-stu-id="1dea7-104">The stop can be due to a successfully completed crawl or a fatal error.</span></span>  
  
## <a name="ftcrawl-stopped-event-class-data-columns"></a><span data-ttu-id="1dea7-105">Столбцы данных класса событий FT:Crawl Stopped</span><span class="sxs-lookup"><span data-stu-id="1dea7-105">FT:Crawl Stopped Event Class Data Columns</span></span>  
  
|<span data-ttu-id="1dea7-106">Имя столбца данных</span><span class="sxs-lookup"><span data-stu-id="1dea7-106">Data column name</span></span>|<span data-ttu-id="1dea7-107">Тип данных</span><span class="sxs-lookup"><span data-stu-id="1dea7-107">Data type</span></span>|<span data-ttu-id="1dea7-108">Description</span><span class="sxs-lookup"><span data-stu-id="1dea7-108">Description</span></span>|<span data-ttu-id="1dea7-109">Идентификатор столбца</span><span class="sxs-lookup"><span data-stu-id="1dea7-109">Column ID</span></span>|<span data-ttu-id="1dea7-110">Фильтруемый</span><span class="sxs-lookup"><span data-stu-id="1dea7-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="1dea7-111">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="1dea7-111">**DatabaseID**</span></span>|<span data-ttu-id="1dea7-112">**int**</span><span class="sxs-lookup"><span data-stu-id="1dea7-112">**int**</span></span>|<span data-ttu-id="1dea7-113">Идентификатор базы данных, в которой было остановлено полнотекстовое сканирование.</span><span class="sxs-lookup"><span data-stu-id="1dea7-113">ID of the database in which the full-text crawl has stopped.</span></span> <span data-ttu-id="1dea7-114">Определите значение для базы данных, используя функцию DB_ID.</span><span class="sxs-lookup"><span data-stu-id="1dea7-114">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="1dea7-115">3</span><span class="sxs-lookup"><span data-stu-id="1dea7-115">3</span></span>|<span data-ttu-id="1dea7-116">Да</span><span class="sxs-lookup"><span data-stu-id="1dea7-116">Yes</span></span>|  
|<span data-ttu-id="1dea7-117">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="1dea7-117">**EventClass**</span></span>|<span data-ttu-id="1dea7-118">**int**</span><span class="sxs-lookup"><span data-stu-id="1dea7-118">**int**</span></span>|<span data-ttu-id="1dea7-119">Тип события = 156.</span><span class="sxs-lookup"><span data-stu-id="1dea7-119">Type of event = 156.</span></span>|<span data-ttu-id="1dea7-120">27</span><span class="sxs-lookup"><span data-stu-id="1dea7-120">27</span></span>|<span data-ttu-id="1dea7-121">нет</span><span class="sxs-lookup"><span data-stu-id="1dea7-121">No</span></span>|  
|<span data-ttu-id="1dea7-122">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="1dea7-122">**EventSequence**</span></span>|<span data-ttu-id="1dea7-123">**int**</span><span class="sxs-lookup"><span data-stu-id="1dea7-123">**int**</span></span>|<span data-ttu-id="1dea7-124">Последовательность данного события в запросе.</span><span class="sxs-lookup"><span data-stu-id="1dea7-124">Sequence of a given event within the request.</span></span>|<span data-ttu-id="1dea7-125">51</span><span class="sxs-lookup"><span data-stu-id="1dea7-125">51</span></span>|<span data-ttu-id="1dea7-126">нет</span><span class="sxs-lookup"><span data-stu-id="1dea7-126">No</span></span>|  
|<span data-ttu-id="1dea7-127">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="1dea7-127">**IsSystem**</span></span>|<span data-ttu-id="1dea7-128">**int**</span><span class="sxs-lookup"><span data-stu-id="1dea7-128">**int**</span></span>|<span data-ttu-id="1dea7-129">Указывает, произошло событие в системном или в пользовательском процессе.</span><span class="sxs-lookup"><span data-stu-id="1dea7-129">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="1dea7-130">1 = системный, 0 = пользовательский.</span><span class="sxs-lookup"><span data-stu-id="1dea7-130">1 = system, 0 = user.</span></span>|<span data-ttu-id="1dea7-131">60</span><span class="sxs-lookup"><span data-stu-id="1dea7-131">60</span></span>|<span data-ttu-id="1dea7-132">Да</span><span class="sxs-lookup"><span data-stu-id="1dea7-132">Yes</span></span>|  
|<span data-ttu-id="1dea7-133">**ObjectID**</span><span class="sxs-lookup"><span data-stu-id="1dea7-133">**ObjectID**</span></span>|<span data-ttu-id="1dea7-134">**int**</span><span class="sxs-lookup"><span data-stu-id="1dea7-134">**int**</span></span>|<span data-ttu-id="1dea7-135">Идентификатор объекта, назначенный системой.</span><span class="sxs-lookup"><span data-stu-id="1dea7-135">System-assigned ID of the object.</span></span> <span data-ttu-id="1dea7-136">Полнотекстовое сканирование было остановлено до полнотекстового индекса на данном объекте.</span><span class="sxs-lookup"><span data-stu-id="1dea7-136">The full-text crawl has stopped for the full-text index on this object.</span></span>|<span data-ttu-id="1dea7-137">22</span><span class="sxs-lookup"><span data-stu-id="1dea7-137">22</span></span>|<span data-ttu-id="1dea7-138">Да</span><span class="sxs-lookup"><span data-stu-id="1dea7-138">Yes</span></span>|  
|<span data-ttu-id="1dea7-139">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="1dea7-139">**SessionLoginName**</span></span>|<span data-ttu-id="1dea7-140">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="1dea7-140">**nvarchar**</span></span>|<span data-ttu-id="1dea7-141">Имя входа пользователя, создавшего этот сеанс.</span><span class="sxs-lookup"><span data-stu-id="1dea7-141">Login name of the user who originated the session.</span></span> <span data-ttu-id="1dea7-142">Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2".</span><span class="sxs-lookup"><span data-stu-id="1dea7-142">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="1dea7-143">В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span><span class="sxs-lookup"><span data-stu-id="1dea7-143">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows logins.</span></span>|<span data-ttu-id="1dea7-144">64</span><span class="sxs-lookup"><span data-stu-id="1dea7-144">64</span></span>|<span data-ttu-id="1dea7-145">Да</span><span class="sxs-lookup"><span data-stu-id="1dea7-145">Yes</span></span>|  
|<span data-ttu-id="1dea7-146">**SPID**</span><span class="sxs-lookup"><span data-stu-id="1dea7-146">**SPID**</span></span>|<span data-ttu-id="1dea7-147">**int**</span><span class="sxs-lookup"><span data-stu-id="1dea7-147">**int**</span></span>|<span data-ttu-id="1dea7-148">Идентификатор сеанса, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="1dea7-148">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="1dea7-149">12</span><span class="sxs-lookup"><span data-stu-id="1dea7-149">12</span></span>|<span data-ttu-id="1dea7-150">Да</span><span class="sxs-lookup"><span data-stu-id="1dea7-150">Yes</span></span>|  
|<span data-ttu-id="1dea7-151">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="1dea7-151">**StartTime**</span></span>|<span data-ttu-id="1dea7-152">**datetime**</span><span class="sxs-lookup"><span data-stu-id="1dea7-152">**datetime**</span></span>|<span data-ttu-id="1dea7-153">Время начала события, если оно известно.</span><span class="sxs-lookup"><span data-stu-id="1dea7-153">Time at which the event started, if available.</span></span>|<span data-ttu-id="1dea7-154">14</span><span class="sxs-lookup"><span data-stu-id="1dea7-154">14</span></span>|<span data-ttu-id="1dea7-155">Да</span><span class="sxs-lookup"><span data-stu-id="1dea7-155">Yes</span></span>|  
|<span data-ttu-id="1dea7-156">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="1dea7-156">**TransactionID**</span></span>|<span data-ttu-id="1dea7-157">**bigint**</span><span class="sxs-lookup"><span data-stu-id="1dea7-157">**bigint**</span></span>|<span data-ttu-id="1dea7-158">Назначенный системой идентификатор транзакции.</span><span class="sxs-lookup"><span data-stu-id="1dea7-158">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="1dea7-159">4</span><span class="sxs-lookup"><span data-stu-id="1dea7-159">4</span></span>|<span data-ttu-id="1dea7-160">Да</span><span class="sxs-lookup"><span data-stu-id="1dea7-160">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1dea7-161">См. также:</span><span class="sxs-lookup"><span data-stu-id="1dea7-161">See Also</span></span>  
 [<span data-ttu-id="1dea7-162">Хранимая процедура sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1dea7-162">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  