---
title: Определение свойств иерархии куба | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8903a49754357aad9cf24ee63fffa45fbf120e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728889"
---
# <a name="define-cube-hierarchy-properties"></a>Определение свойств иерархии куба
  Свойства иерархии куба позволяют указывать уникальные настройки многоуровневых иерархий в измерениях куба на основе одного измерения базы данных. В следующей таблице описаны свойства иерархии куба.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`Enabled`|Указывает, включена ли иерархия для измерения куба.|  
|`HierarchyID`|Содержит уникальный идентификатор (ID) иерархии.|  
|`OptimizedState`|Определяет уровень оптимизации, применяемый к иерархии. Это свойство может иметь следующие значения:<br /><br /> `FullyOptimized`: экземпляр создает индексы иерархии для улучшения производительности запросов. Это значение по умолчанию.<br /><br /> `NotOptimized`: экземпляр не создает дополнительные индексы.|  
|`Visible`|Определяет видимость иерархии кубов. Значение по умолчанию — `True`.|  
  
## <a name="see-also"></a>См. также:  
 [Пользовательские иерархии](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
