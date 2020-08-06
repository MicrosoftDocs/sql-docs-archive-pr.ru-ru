---
title: Слияние секций (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 65840066d3e95571db511a2015a1bee64aa8d922
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658476"
---
# <a name="merging-partitions-xmla"></a>Слияние секций (XMLA)
  Если секции имеют одинаковую статистическую схему и структуру, можно выполнить слияние секции с помощью команды [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) в XML для АНАЛИТИКИ (XMLA). При управлении секциями их слияние является важным действием, особенно для тех секций, в которых содержатся исторические данные, секционированные по дате.  
  
 Например, в финансовом кубе может быть две секции.  
  
-   Одна секция представляет финансовые данные по текущему году, используя для обеспечения высокой производительности параметры хранения реляционной OLAP (ROLAP) в реальном времени.  
  
-   Другая секция содержит финансовые данные по предыдущим годам, используя параметры хранения многомерной OLAP (MOLAP) для обеспечения хранения.  
  
 В двух секциях установлены разные параметры хранения, но одинаковые статистические схемы. Вместо того чтобы в конце года обрабатывать куб по годам исторических данных, можно воспользоваться командой `MergePartitions`, чтобы выполнить слияние секции для текущего года с секцией для предыдущих лет. В этом случае будут сохранены данные статистических вычислений; при этом не требуется полной обработки куба, на что может уйти много времени.  
  
## <a name="specifying-partitions-to-merge"></a>Указание секций для слияния  
 При `MergePartitions` выполнении команды данные агрегирования, хранящиеся в исходных секциях, указанных в свойстве [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) , добавляются в целевую секцию, указанную в свойстве [Target](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) .  
  
> [!NOTE]  
>  Свойство `Source` может содержать несколько ссылок объектов на секции. Но свойство `Target` не предоставляет такой возможности.  
  
 Чтобы слияние секций, указанных в свойствах `Source` и `Target`, было выполнено успешно, они должны содержаться в одной группе мер и иметь одинаковые статистические схемы. В противном случае возникает ошибка.  
  
 Секции, указанные в свойстве `Source`, после успешного выполнения команды `MergePartitions` удаляются.  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 В следующем примере выполняется слияние всех секций в группе мер " **Подсчет клиентов** " Куба **Adventure** Works в образце базы данных **Adventure Works DW** в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] раздел **Customers_2004** .  
  
### <a name="code"></a>Код  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>См. также:  
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
