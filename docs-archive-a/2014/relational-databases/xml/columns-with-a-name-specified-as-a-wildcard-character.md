---
title: Столбцы с именем, заданным в виде подстановочного символа | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b363baf8792628c2e17b1a695c19a6a338f4fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664055"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a>Столбцы с именем, заданным в виде символа-шаблона
  Если указанное имя столбца представляет собой подстановочный знак (\*), содержимое этого столбца вставляется, как будто имя столбца не указано. Если этот столбец имеет тип, отличный от `xml`, содержимое столбца вставляется в качестве текстового узла, как это показано в следующем примере:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 Результат:  
  
 `<row EmpID="1">KenJS??nchez</row>`  
  
 Если столбец имеет тип -`xml`, вставляется соответствующее дерево XML. Например, в следующем запросе столбец, содержащий XML-данные, возвращенные в результате запроса на языке XQuery к столбцу Instructions, имеет имя «*».  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 Результат. Запрос на языке XQuery возвращает XML-данные, которые вставляются без закрытия элемента.  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a>См. также:  
 [Использование режима PATH совместно с FOR XML](use-path-mode-with-for-xml.md)  
  
  
