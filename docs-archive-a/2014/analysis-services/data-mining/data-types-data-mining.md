---
title: Типы данных (интеллектуальный анализ данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9027ff3928f40d43f16bb31b52e0c1d52e072847
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669177"
---
# <a name="data-types-data-mining"></a>Типы данных (интеллектуальный анализ данных)
  При создании модели или структуры интеллектуального анализа данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо определить типы данных для каждого столбца в структуре интеллектуального анализа данных. Тип данных сообщает модулю интеллектуального анализа, является ли источник данных числовым или текстовым и каким образом следует обрабатывать данные. Например, если исходные данные числовые, можно указать, должны числа обрабатываться как целые или содержать десятичные разряды.  
  
 Каждый тип данных поддерживает один или несколько типов содержимого. Указывая типы содержимого, можно настроить способ обработки данных в столбце или вычисления в модели интеллектуального анализа данных.  
  
 Например, если столбец содержит числовые данные, можно выбрать, как их обрабатывать: как числовые или как текстовые данные. Если выбран числовой тип данных, можно задать несколько разных типов содержимого: можно дискретизировать числа или обрабатывать их как непрерывные значения. Список всех типов содержимого см. в разделе [Типы содержимого (интеллектуальный анализ данных)](content-types-data-mining.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают следующие типы данных для столбцов структуры интеллектуального анализа данных.  
  
|Тип данных|Поддерживаемые типы содержимого|  
|---------------|-----------------------------|  
|`Text`|Cyclical, Discrete, Discretized, Key Sequence, Ordered, Sequence|  
|`Long`|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time<br /><br /> Classified|  
|`Boolean`|Cyclical, Discrete, Ordered|  
|`Double`|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time<br /><br /> Classified|  
|`Date`|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered|  
  
> [!NOTE]  
>  Типы содержимого Time и Sequence поддерживаются только алгоритмами сторонних производителей. Типы содержимого Cyclical и Ordered поддерживаются, однако большинство алгоритмов обрабатывает их как дискретные величины и не производит их особой обработки.  
  
## <a name="specifying-a-data-type"></a>Указание типа данных  
 При создании модели интеллектуального анализа непосредственно с помощью расширений интеллектуального анализа данных можно определить тип данных для каждого столбца при определении модели, а службы Analysis Services в то же время создадут соответствующую структуру интеллектуального анализа с указанными типами данных. Если модель или структура интеллектуального анализа данных создается с помощью мастера, то службы Analysis Services предложат тип данных или же можно будет выбрать тип данных из списка.  
  
## <a name="changing-a-data-type"></a>Изменение типа данных  
 При изменении типа данных в столбце необходимо всегда снова обрабатывать структуру и модели интеллектуального анализа данных, основанные на этой структуре. Иногда при изменении типа данных столбец более не может использоваться в определенной модели. В этом случае службы Analysis Services либо вернут ошибку при повторной обработке модели, либо обработают модель, но пропустят определенный столбец.  
  
## <a name="see-also"></a>См. также:  
 [Типы содержимого &#40;&#41;интеллектуального анализа данных](content-types-data-mining.md)   
 [Типы содержимого &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/content-types-dmx)   
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Структуры интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ&#41;](mining-structures-analysis-services-data-mining.md)   
 [Типы данных &#40;DMX&#41;](/sql/dmx/data-types-dmx)   
 [Столбцы модели интеллектуального анализа данных](mining-model-columns.md)   
 [Столбцы структуры интеллектуального анализа данных](mining-structure-columns.md)  
  
  
