---
title: Новые&#39;построитель отчетов для SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ce72af225130bc3f081a53008a303c5213db636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665227"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a>Новые&#39;в построитель отчетов для SQL Server 2014
  В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] появилось несколько функций служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
 Сведения о функциях этого выпуска для других [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] продуктов и технологий см. [в статье новые возможности SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
> [!TIP]  
>  Последние сведения и ресурсы, относящиеся к новым функциям этого выпуска, см. в разделе Дополнительные сведения о новых возможностях [SQL Server Reporting Services (службы SSRS)](https://go.microsoft.com/fwlink/?LinkId=207147).  
  
##  <a name="excel-renderer-for-microsoft-excel-2007-2010-and-microsoft-excel-2003"></a><a name="ExcelRenderer"></a>Модуль подготовки отчетов Excel для Microsoft Excel 2007-2010 и Microsoft Excel 2003  
 Модуль подготовки отчетов Excel для служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], который впервые появился в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], подготавливает к просмотру отчет как документ Excel, совместимый с [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007–2010, а также [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 с установленным пакетом совместимости Microsoft Office для Word, Excel и PowerPoint. Это формат Office Open XML, а соответствующие файлы имеют расширение XLSX.  
  
 Модуль подготовки отчетов в формате Excel устраняет ограничения прежней версии, совместимой с Excel 2003. В следующих списках перечислены новые возможности модуля подготовки отчетов.  
  
-   Максимальное число строк на листе равно 1 048 576.  
  
-   Максимальное число столбцов на листе равно 16 384.  
  
-   Число цветов, которые можно использовать на листе, приблизительно равно 16 млн (24-разрядный цвет).  
  
-   Сжатие данных в формате ZIP обеспечивает меньший размер файлов.  
  
 Дополнительные сведения см. в разделе [Экспорт в Microsoft Excel (построитель отчетов и службы SSRS)](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
##  <a name="word-renderer-for-microsoft-word-2007-2010-and-microsoft-word-2003"></a><a name="WordRenderer"></a>Модуль подготовки отчетов Word для Microsoft Word 2007-2010 и Microsoft Word 2003  
 Модуль подготовки отчетов Word для служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], который впервые появился в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], подготавливает к просмотру отчет как документ Word, совместимый с [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007–2010, а также [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003 с установленным пакетом совместимости [!INCLUDE[msCoName](../includes/msconame-md.md)] Office для Word, Excel и PowerPoint. Это формат Office Open XML, а также соответствующие файлы имеют расширение DOCX.  
  
 В дополнение к тому, что для экспортированных отчетов стали доступными новые средства Word 2007–2010, файлы экспортированных отчетов с расширением DOCX, как правило, имеют меньший размер. Отчеты, экспортированные с использованием модуля подготовки отчетов Word, обычно намного меньше, чем такие же отчеты, экспортированные с использованием модуля подготовки отчетов Word 2003.  
  
 Дополнительные сведения см. в разделе [Экспорт в Microsoft Word (построитель отчетов и службы SSRS)](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Построитель отчетов в SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
