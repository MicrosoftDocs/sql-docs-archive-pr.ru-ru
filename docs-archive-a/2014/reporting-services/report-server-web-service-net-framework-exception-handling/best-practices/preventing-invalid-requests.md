---
title: Предотвращение использования недопустимых запросов | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 12343955c46fb98fea75048a38749b1db993fa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667561"
---
# <a name="preventing-invalid-requests"></a>Предотвращение недопустимых запросов
  Возникновение некоторых типов исключений можно предотвратить, проведя анализ потока работы приложения и убедившись в том, что все запросы, направляемые на сервер отчетов, являются допустимыми. Например, в приложениях, предоставляющих пользователям возможность добавить или обновить имя отчета, источник данных или другие параметры сервера отчетов, необходимо проверять текст, вводимый пользователем. Перед отправкой запроса на сервер отчетов следует всегда проверять, нет ли в нем зарезервированных символов. Чтобы предупредить пользователя о том, что он не выполнил необходимых условий для отправки запросов на сервер отчетов, используйте в коде условные операторы **if** или другие логические конструкции.  
  
 В следующем упрощенном примере на языке C# при попытке создать отчет с именем, содержащим символ косой черты (/), пользователи получают понятное сообщение об ошибке.  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 Дополнительные сведения о типах ошибок, которые могут быть устранены до отправки запросов на сервер отчетов, см. в разделе [Таблица ошибок SoapException](../soapexception-class/soapexception-errors-table.md). Дополнительные сведения об усовершенствовании предыдущего примера с помощью блоков try и catch см. в разделе [Использование блоков Try-Catch](using-try-and-catch-blocks.md).  
  
## <a name="see-also"></a>См. также:  
 [Введение в обработку исключений в Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
