---
title: Объекты базы данных (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d61e3213356146e1cf9e452e0b62e02c96bd4902
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752464"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a>Объекты баз данных (службы Analysis Services — многомерные данные)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Экземпляр содержит объекты и сборки базы данных для использования с оперативной аналитической обработкой (OLAP) и интеллектуальным анализом данных.  
  
-   В базах данных содержатся объекты OLAP и интеллектуального анализа данных, такие как источники данных, представления источников данных, кубы, меры, группы мер, атрибуты, иерархии, структуры и модели интеллектуального анализа данных, а также роли.  
  
-   В сборках содержатся пользовательские функции, расширяющие функциональность внутренних функций, обеспечиваемых языками многомерных выражений и расширениями интеллектуального анализа данных.  
  
 Объект <xref:Microsoft.AnalysisServices.Database> представляет собой контейнер для всех объектов данных, которые требуются для проектов бизнес-аналитики (таких как кубы OLAP, измерения и структуры интеллектуального анализа данных), а также для поддерживающих их объектов (таких как <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account> и <xref:Microsoft.AnalysisServices.Role>).  
  
 Объект <xref:Microsoft.AnalysisServices.Database> предоставляет доступ ко всем объектам и атрибутам, которые включают следующее.  
  
-   Все кубы, к которым может быть получен доступ, в виде коллекции.  
  
-   Все измерения, к которым может быть получен доступ, в виде коллекции.  
  
-   Все структуры интеллектуального анализа данных, к которым может быть получен доступ, в виде коллекции.  
  
-   Все источники данных и представления источников данных, в виде двух коллекций.  
  
-   Все роли и разрешения базы данных, в виде двух коллекций.  
  
-   Значение параметра сортировки для базы данных.  
  
-   Предполагаемый размер базы данных.  
  
-   Значение языка базы данных.  
  
-   Параметр, определяющий, является ли база данных видимой.  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих подразделах описываются объекты, совместно используемые как OLAP, так и функциями интеллектуального анализа данных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Источники данных в многомерных моделях](../data-sources-in-multidimensional-models.md)|Содержит описание источника данных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Представления источников данных в многомерных моделях](../data-source-views-in-multidimensional-models.md)|Содержит описание моделей логических данных, основанных на одном или более источниках данных в службе[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Кубы в многомерных моделях](../cubes-in-multidimensional-models.md)|Содержит описание кубов и объектов кубов, включая меры, группы мер, связи использования измерений, вычисления, ключевые показатели эффективности, действия, переводы, секции и перспективы.|  
|[Измерения (службы Analysis Services — многомерные данные)](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|Содержит описание измерений и объектов измерений, включая атрибуты, связи атрибутов, иерархии, уровни и элементы.|  
|[Структуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../data-mining/mining-structures-analysis-services-data-mining.md)|Содержит описание структур и объектов интеллектуального анализа данных, включая модели интеллектуального анализа данных.|  
|[Роли безопасности (службы Analysis Services — многомерные данные)](security-roles-analysis-services-multidimensional-data.md)|Содержит описание роли, механизма безопасности, используемого для управления доступом к объектам в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Управление сборками многомерной модели](../multidimensional-model-assemblies-management.md)|Содержит описание сборки, коллекции пользовательских функций, используемой для расширения языков многомерных выражений и для расширений интеллектуального анализа данных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Поддерживаемые источники данных &#40;многомерные&#41;SSAS](../supported-data-sources-ssas-multidimensional.md)   
 [Решения многомерной модели &#40;SSAS&#41;](../multidimensional-model-solutions-ssas.md)   
 [Решения интеллектуального анализа данных](../../data-mining/data-mining-solutions.md)  
  
  
