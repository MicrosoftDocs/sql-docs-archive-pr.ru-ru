---
title: Настройка свойств меры | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- additivity [Analysis Services]
- ID property
- ErrorConfiguration property
- AggregateFunction property
- DisplayFolder property
- IgnoreUnrelatedDimensions property
- FormatString property
- Description property
- semiadditive
- properties [Analysis Services], measure groups
- aggregate functions [Analysis Services]
- DataType property
- ProcessingMode property
- MeasureExpression property
- AggregationPrefix property
- Visible property
- properties [Analysis Services], measures
- StorageLocation property
- StorageMode property
- formats [Analysis Services], measures
- Source property
- aggregations [Analysis Services], measures
- measures [Analysis Services], properties
- nonadditive [Analysis Services]
- Name property
- measures [Analysis Services], display formats
- ProcessingPriority property
- measure groups [Analysis Services], properties
- Type property
- ProactiveCaching property
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ca291a5181fdb3f7a88845431d61ffd7a1034eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737109"
---
# <a name="configure-measure-properties"></a>Настройка свойств мер
  Меры имеют свойства, позволяющие определять и управлять их работой и отображением для пользователей.  
  
 Свойства в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] можно задать при создании или изменении куба или меры. Можно также задать их программным способом с помощью многомерных выражений или объектов AMO. Дополнительные сведения см. в разделах [Создание мер и групп мер в многомерных моделях](create-measures-and-measure-groups-in-multidimensional-models.md), [Инструкция CREATE MEMBER (многомерные выражения)](/sql/mdx/mdx-data-definition-create-member) и [Программирование основных объектов AMO OLAP](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects).  
  
## <a name="measure-properties"></a>Свойства мер  
 Меры наследуют определенные свойства у группы мер, элементами которых они являются, если только эти свойства не переопределены на уровне мер. Свойства мер определяют статистическое вычисление, тип данных, отображаемые для пользователей имена, папку отображения, строку форматирования, выражения меры, базовые исходные столбцы и видимость для пользователей.  
  
|Свойство|Определение|  
|--------------|----------------|  
|`AggregateFunction`|Обязательный. Определяет, как выполняется статистическое вычисление мер. `Sum` — это агрегирование по умолчанию. Описание каждой функции см. в разделе [Use Aggregate Functions](use-aggregate-functions.md) .|  
|`DataType`|Обязательный элемент. Указывает тип данных столбца базовой таблицы фактов, к которым привязана мера. Это значение наследуется из исходного столбца по умолчанию.|  
|`Description`|Содержит описание меры, которое может быть видно в клиентских приложениях.|  
|`DisplayFolder`|Указывает папку отображения, в которой будет представлена мера при подключении пользователя к кубу. Если куб содержит множество мер, папки отображения позволяют разбить их по категориям мер, упростив доступ к ним.|  
|`FormatString`|Можно выбрать формат, используемый для отображения значений меры пользователям, используя свойство `FormatString` меры.<br /><br /> Список форматов отображения представлен в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], но можно указать множество дополнительных форматов, не содержащихся в этом списке. Можно указать любой именованный или определенный пользователем формат, допустимый в языке Microsoft Visual Basic.|  
|`ID`|Обязательный элемент. Отображает уникальный идентификатор (ID) меры. Это свойство доступно только для чтения.|  
|`MeasureExpression`|Указывает ограниченное многомерное выражение, определяющее значение меры. Выражение вычисляется на конечном уровне до агрегирования и позволяет получить взвешенное значение. Например, конвертация валют, где объем продаж взвешен с учетом обменного курса.|  
|`Name`|Обязательный элемент. Имя меры.|  
|`Source`|Обязательный элемент. Столбец в представлении источника данных, к которому привязана мера. См. раздел [Источники данных и привязки (многомерные службы SSAS)](data-sources-and-bindings-ssas-multidimensional.md).|  
|`Visible`|Определяет видимость меры в клиентских приложениях.|  
  
## <a name="see-also"></a>См. также:  
 [Настройка свойств группы мер](configure-measure-group-properties.md)   
 [Изменение мер](../lesson-3-1-modifying-measures.md)  
  
  
