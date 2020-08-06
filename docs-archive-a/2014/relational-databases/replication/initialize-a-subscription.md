---
title: Инициализация подписки | Документация Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f024d360fdeab477ace09970b4f140a97696c2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655594"
---
# <a name="initialize-a-subscription"></a><span data-ttu-id="f1a3a-102">Инициализация подписки</span><span class="sxs-lookup"><span data-stu-id="f1a3a-102">Initialize a Subscription</span></span>
  <span data-ttu-id="f1a3a-103">Подписчики в топологии репликации должны инициализироваться, чтобы иметь по копии схемы каждой статьи в публикации, на которую они подписались, и все необходимые объекты репликации, например хранимые процедуры, триггеры и таблицы метаданных.</span><span class="sxs-lookup"><span data-stu-id="f1a3a-103">Subscribers in a replication topology must be initialized, so that they have a copy of the schema from each article in the publication they have subscribed to and any replication objects that are required, such as stored procedures, triggers, and metadata tables.</span></span> <span data-ttu-id="f1a3a-104">Кроме того, подписчик, как правило, получает первоначальный набор данных.</span><span class="sxs-lookup"><span data-stu-id="f1a3a-104">In addition, the Subscriber typically receives an initial dataset.</span></span> <span data-ttu-id="f1a3a-105">Метод инициализации, который используется по умолчанию, применяет полный моментальный снимок, включающий схему, объекты репликации и данные, но публикации могут также инициализироваться без полного моментального снимка.</span><span class="sxs-lookup"><span data-stu-id="f1a3a-105">The default initialization method uses a full snapshot that includes schema, replication objects, and data, but publications can also be initialized without a full snapshot.</span></span>  
  
 <span data-ttu-id="f1a3a-106">Дополнительные сведения см. в разделах [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) и [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span><span class="sxs-lookup"><span data-stu-id="f1a3a-106">For more information, see [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) and [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
  
