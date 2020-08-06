---
title: Экспорт отчета с применением доступа по URL-адресу | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69f340855e37ffde49aec0af096c094a142659d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728074"
---
# <a name="export-a-report-using-url-access"></a>Экспорт отчета с применением доступа по URL-адресу
  При необходимости можно указать формат отображения отчета с помощью параметра *RS: Format* . Например, чтобы получить копию отчета в формате PDF прямо с сервера отчетов, работающего в собственном режиме:  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 И с сервера отчетов, работающего в режиме интеграции с SharePoint:  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 Допустимые значения для этого параметра основаны на модулях подготовки отчетов, установленных на сервер отчетов, к которому осуществляется доступ. Поддерживаемые модули: HTML4.0, WORD, MHTML, IMAGE, EXCEL, WORD, CSV, CSV, PDF, XML и NULL. Если указанный модуль подготовки отчетов не установлен на сервере отчетов, то отчет не будет подготовлен, а браузере выдаст ошибку.  
  
 Если в URL-адрес не включен параметр *Format* , то сервер отчетов определяет браузер и подготавливает для него отчет в соответствующем HTML-формате.  
  
## <a name="see-also"></a>См. также:  
 [Доступ по URL-адресу &#40;службы SSRS&#41;](url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](url-access-parameter-reference.md)  
  
  
