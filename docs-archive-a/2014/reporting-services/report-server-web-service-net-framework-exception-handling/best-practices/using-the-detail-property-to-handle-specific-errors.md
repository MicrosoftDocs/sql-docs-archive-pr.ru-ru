---
title: Использование свойства Detail для обработки определенных ошибок | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f8ac62dc381d8f665a44fc0897ba1f4215aa8e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735001"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Использование свойства Detail для обработки определенных ошибок
  В ходе дальнейшей классификации исключений службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] возвращают дополнительные сведения об ошибках в свойстве **InnerText** дочерних элементов свойства **Detail** исключения SOAP. Так как свойство **Detail** является объектом **XmlNode**, с помощью приведенного ниже кода можно обращаться к внутреннему тексту дочернего элемента **Message**.  
  
 Список всех доступных дочерних элементов в свойстве **Detail** см. в разделе [Свойство Detail](../soapexception-class/detail-property.md). Дополнительные сведения см. в разделе "свойство Detail" в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] документации по пакету SDK.  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 Приведенная ниже строка кода выводит на консоль конкретный код ошибки, возвращенный в исключении SOAP. Можно также вычислить код ошибки и выполнить соответствующие действия.  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>См. также:  
 [Введение в обработку исключений в Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services класс SoapException](../soapexception-class/reporting-services-soapexception-class.md)   
 [Таблица ошибок SoapException](../soapexception-class/soapexception-errors-table.md)  
  
  
