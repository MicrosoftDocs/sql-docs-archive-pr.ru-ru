---
title: Методы отрисовки и выполнения | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0bc793e9a18e993989563fd3526ff12272f775c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736026"
---
# <a name="rendering-and-execution-methods"></a>Методы подготовки к просмотру и выполнения
  Эти методы можно использовать для управления выполнением и кэшированием элементов и подготовкой отчетов к просмотру.  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|Делает недействительным кэш для элемента.|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|Возвращает конфигурацию кэширования для элемента и параметры, которые описывают, когда истекает срок действия кэшированной копии элемента.|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|Возвращает параметр выполнения и соответствующие настройки для отдельного элемента.|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|Возвращает список поддерживаемых настроек выполнения.|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|Обрабатывает указанный отчет и готовит его к просмотру в заданном формате.|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|Настраивает элемент для кэширования и предоставляет настройки, указывающие, когда истекает срок действия кэшированной копии элемента.|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|Устанавливает параметры выполнения и соответствующие свойства выполнения для указанного элемента.|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|Создает моментальный снимок состояния выполнения элемента для указанного элемента.|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../report-server-web-service.md)   
 [Методы веб-службы сервера отчетов](report-server-web-service-methods.md)   
 [Технический справочник (службы SSRS)](../../technical-reference-ssrs.md)  
  
  
