---
title: Определение хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc1f028f822d2289ee79702feb2494487040977c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732158"
---
# <a name="defining-stored-procedures"></a>Определение хранимых процедур
  Хранимые процедуры можно использовать для вызова внешних подпрограмм из [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Для написания внешней подпрограммы, вызываемой хранимой процедурой, можно использовать любой язык среды CLR, например C, C++, C#, Visual Basic или Visual Basic .NET. Хранимую процедуру можно создать один раз и затем вызывать из множества контекстов, например из других хранимых процедур, вычисляемых мер или клиентских приложений. Хранимые процедуры упрощают разработку и реализацию базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] благодаря тому, что общий код создается один раз и сохраняется в одном месте. Хранимые процедуры можно использовать для расширения функциональности приложений за счет добавления дополнительных функций к собственной функциональности многомерных выражений.  
  
 В данном разделе приводятся сведения, необходимые для понимания, проектирования и реализации хранимых процедур.  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Конструирование хранимых процедур](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Содержит описание проектирования сборок для использования со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Создание хранимых процедур](creating-stored-procedures.md)|Содержит описание создания сборок для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Вызов хранимых процедур](calling-stored-procedures.md)|Предоставляет сведения об использовании сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Доступ к контексту запросов в хранимых процедурах](accessing-query-context-in-stored-procedures.md)|Содержит описание получения доступа к данным области и контекстным данным при помощи сборок.|  
|[Настройка безопасности хранимых процедур](setting-security-for-stored-procedures.md)|Содержит описание настройки безопасности для сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Отладка хранимых процедур](debugging-stored-procedures.md)|Содержит описание отладки сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками многомерной модели](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
