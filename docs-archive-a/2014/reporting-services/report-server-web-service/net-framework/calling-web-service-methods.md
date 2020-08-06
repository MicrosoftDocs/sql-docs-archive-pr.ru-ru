---
title: Вызов методов веб-служб | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 87f1485b4e3c0ed064e42bb3b411fece96eba8d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730142"
---
# <a name="calling-web-service-methods"></a>Вызов методов веб-служб
  При использовании [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] класса прокси для вызова операций веб-службы это выполняется с помощью методов этого класса. Эти методы работают аналогично любому другому методу в классе из библиотеки классов платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Все методы веб-служб доступны для открытого доступа, при котором необходимо указывать соответствующее число аргументов и типы аргументов. После создания экземпляра класса-посредника в проекте можно вызывать методы для выполнения операций с отчетами на сервере отчетов. В следующем коде на языке C# показано использование метода <xref:ReportService2010.ReportingService2010.ListChildren%2A> класса прокси <xref:ReportService2010.ReportingService2010>. Этот код используется для рекурсивного вызова веб-службы, которая возвращает массив объектов <xref:ReportService2010.CatalogItem>, содержащий список всех элементов в базе данных сервера отчетов:  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../report-server-web-service.md)   
 [Технический справочник (службы SSRS)](../../technical-reference-ssrs.md)  
  
  
