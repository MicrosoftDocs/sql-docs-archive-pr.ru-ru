---
title: Коллекции (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce49c57aad5da52dabba32a0f3fb9b6f4f45b209
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731873"
---
# <a name="collections-master-data-services"></a>Коллекции (службы основных данных)
  Коллекция — это группа конечных или консолидированных элементов из одной сущности. Коллекции используются, когда нет необходимости в полной иерархии и нужно просмотреть разные группы элементов для отчетов или анализа или когда необходимо создать классификацию.  
  
## <a name="what-collections-contain"></a>Содержимое коллекций  
 Коллекции не накладывают ограничений на число или тип включаемых элементов, пока эти элементы находятся в одной сущности. Коллекция может содержать конечные и консолидированные элементы из нескольких обязательных и необязательных явных иерархий.  
  
 При создании коллекции создается не иерархическая структура, а плоский список элементов. При выборе узла из иерархии и добавлении его в коллекцию выделенный объединенный элемент является единственным элементом, который добавляется в коллекцию.  
  
 Коллекция также может содержать другие коллекции. Можно использовать коллекции коллекций для создания классификаций.  
  
 Пользователь, создающий коллекцию, автоматически вносится в список ее владельцев. Если вы являетесь администратором, то при необходимости можете создавать другие атрибуты коллекции.  
  
> [!NOTE]  
>  Перед созданием коллекции для сущности необходимо разрешить использование явных иерархий. Дополнительные сведения см. в разделе [Включение сущности для явных иерархий и коллекций &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
## <a name="subscription-views-for-collections"></a>Представления подписки для коллекций  
 Есть два типа представлений подписки, которые отображают коллекции. Формат **Атрибуты коллекций** отображает список коллекций и другие атрибуты, связанные с коллекциями, например описание или владельца. Формат **Коллекции** отображает все элементы во всех коллекциях, а также вес и порядок сортировки каждого элемента. Дополнительные сведения см. в разделе [Экспорт данных &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md).  
  
 Если для определенных элементов в коллекции установлены взвешенные значения, такие значения доступны в связанных представлениях подписки.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Включение сущности для явных иерархий и коллекций.|[Включение сущности для явных иерархий и коллекций &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|Создание новой коллекции.|[Создание коллекции (службы Master Data Services)](../../2014/master-data-services/create-a-collection-master-data-services.md)|  
|Добавление элементов в существующую коллекцию.|[Добавление элементов в коллекцию (службы Master Data Services)](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Явные иерархии (службы Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Экспорт Master Data Services &#40;данных&#41;](overview-exporting-data-master-data-services.md)  
  
  
