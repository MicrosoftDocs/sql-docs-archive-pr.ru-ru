---
title: Интеграция служб Reporting Services с использованием протокола SOAP | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b6fffd65b22900d7c505c4b50ec290b95fe9ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654923"
---
# <a name="integrating-reporting-services-using-soap"></a>Интеграция служб Reporting Services по протоколу SOAP
  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API SOAP предоставляет несколько конечных точек веб-службы для разработки пользовательских решений для создания отчетов. Конечные точки в данный момент делятся на две категории: управления и выполнения. Функции управления реализованы с помощью конечных точек <xref:ReportService2005>, <xref:ReportService2006> и <xref:ReportService2010>. Конечная точка <xref:ReportService2005> используется для управления сервером отчетов, настроенным для работы в собственном режиме; конечная точка <xref:ReportService2006> используется для управления сервером отчетов, настроенным для работы в режиме интеграции с SharePoint. Конечная точка <xref:ReportService2010> объединяет функциональные возможности конечных точек <xref:ReportService2005> и <xref:ReportService2006> и может управлять сервером отчетов, настроенном для работы в собственном режиме или режиме интеграции с SharePoint.  
  
> [!NOTE]  
>  Конечные точки <xref:ReportService2005> и <xref:ReportService2006> являются устаревшими в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Конечная точка <xref:ReportService2010> содержит функциональные возможности обеих конечных точек, а также содержит дополнительные функции управления.  
  
 Функциональные возможности выполнения реализуются посредством конечной точки <xref:ReportExecution2005>, которая используется, если сервер отчетов настроен как на работу в собственном режиме, так и на работу в режиме интеграции с SharePoint. В следующих разделах показывается, как данные конечные точки могут быть использованы для разработки решений по созданию отчетов в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, SharePoint и веб-приложениях.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Использование API SOAP в приложении Windows](integrating-reporting-services-using-soap-windows-application.md)  
 Описывает, как можно использовать API-интерфейс SOAP для интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в среду Windows.  
  
 [Использование API SOAP в веб-приложении](integrating-reporting-services-using-soap-web-application.md)  
 Описывает, как можно использовать API-интерфейс SOAP для интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в веб-среду.  
  
## <a name="see-also"></a>См. также:  
 [Интеграция Reporting Services в приложения](../application-integration/integrating-reporting-services-into-applications.md)   
 [Веб-служба сервера отчетов](../report-server-web-service/report-server-web-service.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
