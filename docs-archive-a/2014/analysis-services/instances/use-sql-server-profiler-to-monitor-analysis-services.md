---
title: Использование SQL Server Profiler для отслеживания Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e144c1d858670f8a46b164ffc9885e6e082c4b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656675"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>Use SQL Server Profiler to Monitor Analysis Services
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отслеживает события обработки ядра, например начало пакета или транзакции, и фиксирует данные об этих событиях, тем самым давая возможность осуществлять мониторинг операций серверов и баз данных (например, пользовательские операции запросов и входа в систему). Можно фиксировать данные приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или файл для дальнейшего анализа, а также можно воспроизводить зафиксированные события в том же или в другом экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , чтобы точно определить, что произошло. Можно воспроизводить события в режиме реального времени или в пошаговом режиме. Также очень полезно запускать события трассировки вместе со счетчиками приложения «Производительность» на одном и том же компьютере. Приложение SQL Profiler может определять корреляцию между ними на основе времени и отображать их совместно на одной временной шкале. События трассировки предоставят подробные сведения, в то время как счетчики приложения «Производительность» дадут общее представление. Дополнительные сведения о создании и запуске трассировок см. в разделе [Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)](create-profiler-traces-for-replay-analysis-services.md).  
  
 В следующей таблице описаны подразделы, содержащиеся в этом разделе.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Введение в мониторинг служб Analysis Services при помощи приложения SQL Server Profiler](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|Содержит описание использования приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для мониторинга экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Создание трассировки приложения Profiler для воспроизведения (службы Analysis Services)](create-profiler-traces-for-replay-analysis-services.md)|Содержит требования к созданию трассировки для воспроизведения с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[События трассировки служб Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|Содержит описание классов событий служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Эти классы событий соответствуют действиям, формируемым службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , и используются для воспроизведения трассировок.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за экземпляром служб Analysis Services](monitor-an-analysis-services-instance.md)  
  
  
