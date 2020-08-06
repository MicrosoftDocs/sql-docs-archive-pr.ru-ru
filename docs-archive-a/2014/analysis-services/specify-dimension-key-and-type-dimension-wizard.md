---
title: Указание ключа и типа измерения (мастер измерений) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc08584ed12de8597b8289fd223cc47945d7d087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666782"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>Указание ключа и типа измерения (мастер измерений)
  На странице **Определение ключа и типа измерения** можно определить ключевой атрибут измерения и указать, является ли измерение медленно меняющимся измерением (SCD).  
  
> [!NOTE]  
>   Эта страница отображается, только если на странице **Выбор метода построения** выбран параметр **Построить измерение без использования источника данных** и если на странице **Выбор типа измерения** выбрано **Стандартное измерение** .  
  
## <a name="options"></a>Варианты  
 **Ключевой атрибут**  
 Выберите атрибут, который будет ключевым атрибутом для измерения.  
  
> [!NOTE]  
>  Если для измерения не определены никакие атрибуты, единственным значением, доступным для этого параметра, является **Создать ключевой атрибут автоматически** . Это значение недоступно, если для измерения определены какие-либо атрибуты.  
  
 **Это изменяющееся измерение**  
 Этот параметр указывает, что измерение является медленно меняющимся измерением. При выборе этого параметра создаются новые столбцы и атрибуты, которые могут использоваться для отслеживания перемещения элементов в иерархиях измерения с течением времени.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 мастера измерений](dimension-wizard-f1-help.md)   
 [Измерения &#40;Analysis Services многомерных данных&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Измерения в многомерных моделях](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
