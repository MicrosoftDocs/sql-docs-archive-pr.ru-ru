---
title: Добавление бизнес-логики для данных XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 5bf8e9edc36e9c420faa92f2db1a92c311194e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657589"
---
# <a name="add-business-logic-to-xml-data"></a>Добавление бизнес-логики для XML-данных
  Бизнес-логику можно добавить в XML-данные несколькими способами.  
  
-   Можно создать ограничения строк или столбцов, чтобы наложить ограничения, специфические для домена, во время вставки и модификации XML-данных.  
  
-   Можно написать для XML-столбца триггер, срабатывающий при вставке значений в столбец или при их обновлении. Этот триггер может определять специфические для домена правила проверки или заполнять таблицы свойств.  
  
-   Компонент Database Engine может выполнять управляемый код. Эту интеграцию со средой CLR можно использовать для написания в управляемом коде функций, принимающих XML-значения, и использовать средства обработки XML-данных, предоставляемые пространством имен System.Xml. Примером может служить применение преобразования XSL к XML-данным. Также можно десериализовать XML-данные в один или несколько управляемых классов и обработать их в управляемом коде.  
  
-   Можно создать хранимые процедуры и функции Transact-SQL, инициирующие обработку XML-столбца в соответствии с бизнес-потребностями.  
  
## <a name="example-applying-xsl-transformation"></a>Пример Применение преобразования XSL  
 Рассмотрим функцию CLR **TransformXml ()** , которая принимает `xml` экземпляр типа данных и преобразование XSL, хранящиеся в файле, применяет преобразование к XML-данным, а затем ВОЗВРАЩАЕТ преобразованный XML в результат. Вот ее основа, написанная на C#:  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 После регистрации сборки и создания пользовательской функции [!INCLUDE[tsql](../../includes/tsql-md.md)]**SqlXslTransform()** , соответствующей **TransformXml()** , эту функцию можно вызывать из кода Transact-SQL, как показано в следующем запросе:  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 Результат выполнения этого запроса содержит набор строк преобразованных XML-данных.  
  
 Интеграция со средой CLR в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширяет возможности продвижения свойств и декомпозиции XML-данных в таблицы, а также средства запроса XML-данных с использованием управляемых классов из пространства имен System.Xml. Дополнительные сведения см в разделе [Данные XML (SQL Server)](xml-data-sql-server.md).  
  
  
