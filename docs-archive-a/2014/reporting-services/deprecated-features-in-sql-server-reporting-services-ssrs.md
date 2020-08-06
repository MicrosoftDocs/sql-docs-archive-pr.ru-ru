---
title: Устаревшие функции в SQL Server Reporting Services в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af858ae94bf5ea3d9f0cfe0b99759442dabd6629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664757"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a>Устаревшие функции служб SQL Server Reporting Services в SQL Server 2014
  В этом разделе описываются устаревшие функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Эти функции по-прежнему доступны в выпуске, где они признаны устаревшими, однако запланировано их удаление в следующем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
 В этом разделе:  
  
-   [Устаревшие функции служб SQL Server 2014 Reporting Services](#bkmk_2014)  
  
-   [Устаревшие функции служб SQL Server 2012 SP1 Reporting Services](#bkmk_2012sp1)  
  
-   [Устаревшие функции служб SQL Server 2012 Reporting Services](#bkmk_2012)  
  
-   [Устаревшие функции служб SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a>SQL Server 2014 Reporting Services устаревшие функции  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Функции, не поддерживаемые в следующей версии SQL Server  
 Следующие [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] возможности не будут поддерживаться в **следующей** версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Не используйте их при работе над новыми приложениями и как можно скорее измените приложения, в которых они в настоящее время используются.  
  
#### <a name="html-rendering-extension-device-information-settings"></a>Параметры сведений об устройстве для модуля подготовки отчетов в формате HTML  
 Следующие параметры сведений об устройстве для модуля подготовки отчетов в формате HTML являются устаревшими.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 Дополнительные сведения о модуле подготовки отчетов в формате HTML см. в разделе [HTML Device Information Settings](html-device-information-settings.md)  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Подготовка отчетов в формате Microsoft Word и Microsoft Excel 1997-2003  
 Модули подготовки отчетов BIFF8 передается [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] Формат двоичного файла обмена Word и Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]включает расширения, которые отображаются в [!INCLUDE[msCoName](../includes/msconame-md.md)] формате Open XML для Office 2007-2010.  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a>Язык определения отчетов 2005 и более ранних версий  
 Язык определения отчетов 2005 и более ранних версий считается устаревшим. Дополнительные сведения об RDL см. в разделе [язык определения отчетов &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Дополнительные сведения об обновлении отчетов см. в разделе [Upgrade Reports](install-windows/upgrade-reports.md).  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a>Пользовательские элементы отчета SQL Server 2005 и более ранних версий  
 Пользовательские элементы отчета (CRI), скомпилированные для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 и более ранних версий, являются устаревшими.  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a>Моментальные снимки служб Reporting Services 2005 и более ранних версий  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]моментальные снимки, отображаемые с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 и более ранних версий, являются устаревшими.  
  
#### <a name="report-models"></a>Модели отчетов  
 Модели отчетов на языке семантического моделирования (SMDL) больше не поддерживаются. Несмотря на то, что можно продолжать использовать существующие модели отчетов в качестве источников данных в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчетах, рекомендуется обновить отчеты, чтобы удалить зависимость от моделей отчетов.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]не [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] включает средства для создания или обновления моделей отчетов. Дополнительные сведения см. в разделе [критические изменения в SQL Server Reporting Services в SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Устаревшие методы в конечной точке веб-службы  
 В конечной точке веб-службы <xref:ReportService2010.ReportingService2010> устарели следующие операции:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a>Веб-части SharePoint  
 Установочный CAB-файл **RSWebParts.cab** и веб-части SharePoint, которые можно извлечь из него, являются устаревшими. Нерекомендуемые веб-части — это Обозреватель отчетов (проверяющий **. dwp**) и средство просмотра отчетов (**рецензент. dwp**).  
  
 Дополнительные сведения об устаревших веб-частях см. в статье [Просмотр и изучение отчетов в собственном режиме с помощью SharePoint веб-части (службы SSRS)](https://msdn.microsoft.com/library/ms159772.aspx) .  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Функции, не поддерживаемые в будущей версии SQL Server  
 Поддержка приведенных ниже функций компонента [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]будет сохранена, однако будет удалена в более поздней версии. (с какой именно версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , пока не определено).  
  
 В [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отсутствуют устаревшие функции служб [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a>SQL Server 2012 с пакетом обновления 1 (SP1) Reporting Services устаревшие функции  
 В этом разделе описываются функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , признанные устаревшими в [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]. Поддержка приведенных ниже функций компонента [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в следующей версии [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]будет сохранена, однако будет удалена в более поздней версии. (с какой именно версии [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , пока не определено).  
  
### <a name="sharepoint-web-parts"></a>Веб-части SharePoint  
 Установочный CAB-файл **RSWebParts.cab** и веб-части SharePoint, которые можно извлечь из него, являются устаревшими. Нерекомендуемые веб-части — это Обозреватель отчетов (проверяющий **. dwp**) и средство просмотра отчетов (**рецензент. dwp**).  
  
 Дополнительные сведения об устаревших веб-частях см. в статье [Просмотр и изучение отчетов в собственном режиме с помощью SharePoint веб-части (службы SSRS)](https://msdn.microsoft.com/library/ms159772.aspx) .  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a>SQL Server 2012 Reporting Services устаревшие функции  
 В этом разделе описываются функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , признанные устаревшими в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
### <a name="html-rendering-extension-device-information-settings"></a>Параметры сведений об устройстве для модуля подготовки отчетов в формате HTML  
 Следующие параметры сведений об устройстве для модуля подготовки отчетов в формате HTML являются устаревшими.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 Дополнительные сведения о модуле подготовки отчетов в формате HTML см. в разделе [HTML Device Information Settings](html-device-information-settings.md)  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Подготовка отчетов в формате Microsoft Word и Microsoft Excel 1997-2003  
 Модули подготовки отчетов BIFF8 передается [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] Формат двоичного файла обмена Word и Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]включает расширения, которые отображаются в [!INCLUDE[msCoName](../includes/msconame-md.md)] формате Open XML для Office 2007-2010.  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a>Язык определения отчетов 2005 и более ранних версий  
 Язык определения отчетов 2005 и более ранних версий считается устаревшим. Дополнительные сведения об RDL см. в разделе [язык определения отчетов &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Дополнительные сведения об обновлении отчетов см. в разделе [Upgrade Reports](install-windows/upgrade-reports.md).  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a>Пользовательские элементы отчета SQL Server 2005 и более ранних версий  
 Пользовательские элементы отчета (CRI), скомпилированные для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 и более ранних версий, являются устаревшими.  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a>Моментальные снимки служб Reporting Services 2005 и более ранних версий  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]моментальные снимки, отображаемые с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 и более ранних версий, являются устаревшими.  
  
### <a name="report-models"></a>Модели отчетов  
 Модели отчетов на языке семантического моделирования (SMDL) больше не поддерживаются. Несмотря на то, что можно продолжать использовать существующие модели отчетов в качестве источников данных в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчетах, рекомендуется обновить отчеты, чтобы удалить зависимость от моделей отчетов.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]не [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] включает средства для создания или обновления моделей отчетов. Дополнительные сведения см. в разделе [критические изменения в SQL Server Reporting Services в SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Устаревшие методы в конечной точке веб-службы  
 В конечной точке веб-службы <xref:ReportService2010.ReportingService2010> устарели следующие операции:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services устаревшие функции  
  
> [!NOTE]  
>  Поскольку SQL Server 2008 R2 содержит изменения дополнительного номера версии по сравнению с SQL Server 2008, рекомендуется также просмотреть содержимое раздела по SQL Server 2008.  
  
### <a name="report-server-web-service-endpoints"></a>Конечные точки веб-службы сервера отчетов  
 В этом выпуске считаются устаревшими веб-службы <xref:ReportService2005.ReportingService2005> и <xref:ReportService2006.ReportingService2006>. Эти конечные точки были заменены новой конечной точкой: <xref:ReportService2010.ReportingService2010>.  
  
 Новая конечная точка включает все функциональные возможности, доступные в устаревшей конечной точке, и новые средства, введенные в SQL Server 2008 R2.  
  
## <a name="see-also"></a>См. также:  
 [Новые возможности &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Обратная совместимость](../getting-started/backward-compatibility.md)   
 [Изменения в работе SQL Server Reporting Services в SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Неподдерживаемые возможности в службах SQL Server Reporting Services в версии SQL Server "2014"](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
