---
title: Разрешения модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2846918b515bba16d12d48cd7058cf25863bf569
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664297"
---
# <a name="model-permissions-master-data-services"></a>Разрешения модели (службы Master Data Services)
  Разрешения модели применяются ко всем сущностям, явным и производным иерархиям и коллекциям, существующим в модели. Разрешения, назначенные для модели, можно переопределить для любого отдельного объекта.  
  
> [!NOTE]  
>  Если пользователь является администратором модели, то модель отображается во всех функциональных областях пользовательского интерфейса. В противном случае модель отображается только в функциональной области **Обозреватель** . Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Только для чтения**|В **обозревателе**эта модель отображается, но пользователь не может добавлять или удалять элементы, а также не может обновлять значения атрибутов, членства в иерархиях и членства в коллекциях.|  
|**Обновление**|В **обозревателе**отображается модель, и пользователь может добавлять и удалять элементы, обновлять значения атрибутов, членства в иерархии и членства в коллекциях.|  
|**Запретить**|Модель не отображается.|  
  
 При назначении разрешения модели пользователь получает доступ ко всем версиям модели. Нельзя назначить разрешение для отдельной версии.  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения сущности &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [Разрешения коллекции (службы Master Data Services)](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
