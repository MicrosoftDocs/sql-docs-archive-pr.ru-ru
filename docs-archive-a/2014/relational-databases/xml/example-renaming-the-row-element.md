---
title: Пример Переименование элемента &lt;row&gt; | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: rothja
ms.author: jroth
ms.openlocfilehash: 39375fa125f451f21d936b3a6897b93928fa2f02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654941"
---
# <a name="example-renaming-the-ltrowgt-element"></a>Пример Переименование элемента &lt;row&gt;
  Для каждой строки результирующего набора режим RAW создает элемент `<row>`. При необходимости можно задать другое имя для этого элемента путем определения дополнительного аргумента в режиме RAW, как показано в данном запросе. Запрос возвращает элемент <`ProductModel`> для каждой строки из набора строк.  
  
## <a name="example"></a>Пример  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 Результат. Из-за того, что в запрос добавлена директива `ELEMENTS` , результат состоит из элементов.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>См. также:  
 [Использование RAW Mode с FOR XML](use-raw-mode-with-for-xml.md)  
  
  
