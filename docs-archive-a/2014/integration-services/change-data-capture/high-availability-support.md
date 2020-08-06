---
title: Поддержка высокого уровня доступности | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2e0f6d3f-0536-46d9-8630-835e199515bf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3075b300061b3d87b12a7cb3c4363b5e218f34d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728621"
---
# <a name="high-availability-support"></a><span data-ttu-id="91a9f-102">Поддержка высокого уровня доступности</span><span class="sxs-lookup"><span data-stu-id="91a9f-102">High Availability Support</span></span>
  <span data-ttu-id="91a9f-103">Служба CDC для Oracle разработана с учетом требований высокого уровня доступности.</span><span class="sxs-lookup"><span data-stu-id="91a9f-103">The CDC Service for Oracle is designed for high availability.</span></span> <span data-ttu-id="91a9f-104">Следующие функции составляют часть функций поддержки высокого уровня доступности:</span><span class="sxs-lookup"><span data-stu-id="91a9f-104">The following features provide part of the high availability support:</span></span>  
  
-   <span data-ttu-id="91a9f-105">Служба CDC для Oracle не использует никаких файлов ресурсов (локальных или сетевых).</span><span class="sxs-lookup"><span data-stu-id="91a9f-105">The CDC Service for Oracle does not use any file resource (local or otherwise).</span></span> <span data-ttu-id="91a9f-106">Все состояние сохраняется в целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="91a9f-106">Its entire state is stored in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="91a9f-107">Это позволяет без труда запустить службу на другом компьютере, использующем тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если в компьютере, на котором запущена служба, произойдет сбой.</span><span class="sxs-lookup"><span data-stu-id="91a9f-107">This makes it easy to start the service on a different computer that uses the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance if the computer the service runs on fails.</span></span> <span data-ttu-id="91a9f-108">Чтобы сократить время восстановления, длительные транзакции Oracle хранятся в промежуточной таблице целевого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], благодаря чему устраняется необходимость повторного сканирования множества журналов транзакций сразу после сбоя (или перезапуска службы).</span><span class="sxs-lookup"><span data-stu-id="91a9f-108">To reduce recovery time, long or long-running Oracle transactions are kept in a staging table in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], preventing the need to re-scan many Oracle transaction logs following a failure (or service restart).</span></span>  
  
-   <span data-ttu-id="91a9f-109">Служба CDC для Oracle может использовать кластеризованные экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для восстановления после сбоя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и последующей отработки отказа на другом узле кластера.</span><span class="sxs-lookup"><span data-stu-id="91a9f-109">The CDC Service for Oracle can use clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances so it can recover after the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance fails over to another cluster node.</span></span> <span data-ttu-id="91a9f-110">Администратору компьютера, на котором запущена служба Oracle CDC, при создании службы Oracle CDC Service необходимо лишь указать сведения о подключении к кластеризованному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="91a9f-110">The Oracle CDC Service Computer Administrator only needs to specify the connection information to the clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance when creating an Oracle CDC Service.</span></span>  
  
-   <span data-ttu-id="91a9f-111">Служба CDC для Oracle может использовать функцию зеркального отображения базы данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**AlwaysOn** .</span><span class="sxs-lookup"><span data-stu-id="91a9f-111">The CDC Service for Oracle can use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**AlwaysOn** database mirroring feature.</span></span> <span data-ttu-id="91a9f-112">Поддержка этой функции требует, чтобы MSXDBCDC и все остальные базы данных CDC находились в одной группе доступности.</span><span class="sxs-lookup"><span data-stu-id="91a9f-112">This support requires that the MSXDBCDC and all the CDC databases are in the same availability group.</span></span> <span data-ttu-id="91a9f-113">Кроме того, администратор компьютера службы Oracle CDC должен указать соответствующие сведения о подключении **AlwaysOn** для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] группы доступности (например, свойства соединения `Failover_Partner and Network=dbmssocn` ).</span><span class="sxs-lookup"><span data-stu-id="91a9f-113">It also requires the Oracle CDC Service Computer Administrator to specify the appropriate **AlwaysOn** connection information to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] availability group (for example, the connection properties `Failover_Partner and Network=dbmssocn`).</span></span> <span data-ttu-id="91a9f-114">Это позволяет службе CDC автоматически возобновить обработку на вторичной реплике баз данных после отработки отказа.</span><span class="sxs-lookup"><span data-stu-id="91a9f-114">This allows the CDC service to automatically resume processing on a secondary replication of the databases following a failover.</span></span>  
  
-   <span data-ttu-id="91a9f-115">Службу CDC для Oracle можно настроить как ресурс общей службы, расположенный на отказоустойчивом кластере Windows (совместно или отдельно от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), что упрощает отработку отказа, и повторить обработку CDC при помощи ресурсов кластера.</span><span class="sxs-lookup"><span data-stu-id="91a9f-115">The CDC Service for Oracle can be configured as a generic service resource on a Windows failover cluster (along with, or separate from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), making it simple to fail over and fall back CDC processing with the cluster.</span></span> <span data-ttu-id="91a9f-116">Чтобы настроить службу CDC для Oracle в качестве ресурса отказоустойчивого кластера, системному администратору необходимо настроить службу CDC для Oracle в качестве ресурса общей службы — для каждого узла отказоустойчивого кластера.</span><span class="sxs-lookup"><span data-stu-id="91a9f-116">To configure the CDC Service for Oracle as a resource in a failover cluster, the system administrator must set the CDC Service for Oracle as a Generic Service Resource on each node on the failover cluster.</span></span>  
  
-   <span data-ttu-id="91a9f-117">Служба CDC для Oracle поддерживает Oracle RAC, благодаря чему возможен обмен данными между ней и базой данных Oracle, а также обработка журналов вызова, даже если один из узлов Oracle RAC отключен.</span><span class="sxs-lookup"><span data-stu-id="91a9f-117">The CDC Service for Oracle supports Oracle RAC, which allows it to communicate with the Oracle database and process logs even when one of the Oracle RAC nodes is down.</span></span>  
  
  