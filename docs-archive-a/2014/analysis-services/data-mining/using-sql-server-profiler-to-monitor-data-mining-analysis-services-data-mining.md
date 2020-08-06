---
title: Использование SQL Server Profiler для мониторинга интеллектуального анализа данных (Analysis Services — интеллектуальный анализ данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 655ac93c-5c5c-4565-914b-915327f7d349
author: minewiskan
ms.author: owend
ms.openlocfilehash: eb59d122e07a51c6546eee8affd31cc9eea1028b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654589"
---
# <a name="using-sql-server-profiler-to-monitor-data-mining-analysis-services---data-mining"></a>Наблюдение за интеллектуальным анализом данных с помощью приложения SQL Server Profiler (службы Analysis Services — интеллектуальный анализ данных)
  При наличии необходимых разрешений приложение SQL Server Profiler можно использовать для наблюдения за интеллектуальным анализом данных, в процессе которого выполняются запросы к экземпляру служб SQL Server Analysis Services. В это понятие включается обработка моделей и структур, запросы прогнозов и содержимого, а также создание новых моделей и структур.  
  
 Приложение SQL Server Profiler использует `trace` для наблюдения за запросами от нескольких клиентов, в том числе среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], среды SQL Server Management Studio, веб-служб и надстройки интеллектуального анализа данных для Excel, поскольку при всех обращениях к службам SQL Server Analysis Services используется один экземпляр. Для каждого отслеживаемого экземпляра служб SQL Server Analysis Services необходима отдельная трассировка. Общие сведения о трассировках и об использовании приложения SQL Server Profiler см. в разделе [Использование приложения SQL Server Profiler для мониторинга служб Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Справочные сведения о типах захватываемых событий см. в разделе [Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)](../instances/create-profiler-traces-for-replay-analysis-services.md).  
  
## <a name="using-traces-to-monitor-data-mining"></a>Наблюдение за интеллектуальным анализом данных с помощью трассировок  
 При захвате данных в трассировке можно указать место их сохранения: в файле или в таблице на экземпляре SQL Server. Независимо от применяемого метода сохранения данных приложение SQL Server Profiler позволяет просматривать трассировку и фильтровать ее по событиям. В следующей таблице приведены некоторые из событий и подклассов в трассировке, создаваемой службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] по умолчанию, которые представляют интерес для интеллектуального анализа данных.  
  
|EventClass|EventSubclass|Описание|  
|----------------|-------------------|-----------------|  
|**Query Begin**<br /><br /> **Query End**|**0 — MDXQuery**|Содержит текст всех вызовов хранимых процедур служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|**Query Begin**<br /><br /> **Query End**|**1 — DMXQuery**|Содержит текст и результаты инструкций расширений интеллектуального анализа данных (DMX).|  
|**Progress Report Begin**<br /><br /> **Progress Report End**|**34 - DataMiningProgress**|Содержит сведения о ходе выполнения алгоритма интеллектуального анализа данных: например, при построении модели кластеризации в сообщении о ходе выполнения указывается кандидат в кластеры, для которого производится построение.|  
|**Query Begin**<br /><br /> **Query End**|EXECUTESQL|Содержит текст выполняемого запроса Transact-SQL.|  
|**Query Begin**<br /><br /> **Query End**|**2 — SQLQuery**|Содержит текст всех запросов к наборам строк схемы в форме системных таблиц.|  
|**Начало обнаружения**<br /><br /> **Конец обнаружения**|Несколько|Содержит текст вызова DMX-функций или инструкций DISCOVER, инкапсулированных в XML для аналитики.|  
|**Ошибка**|(нет)|Содержит текст ошибки, переданной сервером клиенту.<br /><br /> Сообщения об ошибках, предваряемые фразой **Ошибка (интеллектуальный анализ данных):** или **Информация (интеллектуальный анализ данных):** , выдаются именно в ответ на DMX-запросы. Однако просмотра только этих сообщений бывает недостаточно. К интеллектуальному анализу данных могут иметь отношения и другие ошибки, не имеющие такого префикса (например, выданные синтаксическим анализатором).|  
  
 Просмотр инструкций команд в журнале трассировки дает также возможность ознакомиться с синтаксисом сложных инструкций, передаваемых клиентом серверу служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , включая вызовы системных хранимых процедур. Эти сведения могут оказаться полезными при отладке или в качестве источника шаблонов для создания новых прогнозирующих запросов и моделей. С несколькими примерами вызовов хранимых процедур, которые могут быть получены через трассировку, можно ознакомиться в разделе [Примеры запросов к модели кластеризации](clustering-model-query-examples.md).  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг экземпляра Analysis Services](../instances/monitor-an-analysis-services-instance.md)   
 [Используйте SQL Server расширенные события &#40;&#41; XEvents для отслеживания Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
  
