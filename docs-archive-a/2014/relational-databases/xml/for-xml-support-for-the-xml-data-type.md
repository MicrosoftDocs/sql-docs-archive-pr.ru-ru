---
title: Поддержка FOR XML для типа данных XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], XML
- xml data type [SQL Server], FOR XML clause
ms.assetid: 365de07d-694c-4c8b-b671-8825be27f87c
author: rothja
ms.author: jroth
ms.openlocfilehash: 16b03d5f10ded40bb284c409f772ee8986060515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751983"
---
# <a name="for-xml-support-for-the-xml-data-type"></a>Поддержка FOR XML для XML-данных
  Если в предложении SELECT запроса FOR XML указан `xml`-столбец, значения столбца сопоставляются как элементы в возвращенном коде XML, независимо от того, указана ли директива ELEMENTS. XML-декларации в `xml`-столбце не сериализуются.  
  
 Например, следующий запрос получает контактные данные клиента, такие как `BusinessEntityID` `FirstName` столбцы, и `LastName` , а также телефонные номера из `AdditionalContactInfo` столбца `xml` типа.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 Поскольку запрос не содержит директивы ELEMENTS, значения столбцов возвращаются в виде атрибутов. Исключения составляют значения дополнительных сведений о контактах, полученные из `xml`-столбца. Эти значения возвращаются в виде элементов.  
  
 Частичный результат:  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</PhoneNumber>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</PhoneNumber>`  
  
```  
</Person.Person>  
...  
```  
  
 Если для XML-столбца, сформированного средствами языка XQuery, указывается псевдоним, этот псевдоним используется для добавления элемента оболочки вокруг кода XML, сформированного с помощью XQuery. Так, в следующем запросе в качестве псевдонима столбца указывается `MorePhoneNumbers` :  
  
```  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 Код XML, возвращаемый средствами XQuery, упаковывается в элемент <`MorePhoneNumbers`>, как показано в следующем частичном результирующем наборе:  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</MorePhoneNumbers>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</MorePhoneNumbers>`  
  
```  
</Person.Person>  
...  
```  
  
 При указании в запросе директивы ELEMENTS в полученном после его выполнения коде XML значения BusinessEntityID, LastName и FirstName будут возвращены в виде элементов.  
  
 Как видно из следующего примера, процедура обработки FOR XML не сериализует XML-декларации в XML-данных из столбца типа `xml`:  
  
```  
create table t(i int, x xml)  
go  
insert into t values(1, '<?xml version="1.0" encoding="UTF-8" ?>  
                             <Root SomeID="10" />')  
select i, x  
from   t  
for xml auto;  
```  
  
 Результат. В результате XML-декларация <`?xml version="1.0" encoding="UTF-8" ?`> является несериализованной.  
  
```  
<root>  
  <t i="1">  
    <x>  
      <Root SomeID="10" />  
    </x>  
  </t>  
</root>  
```  
  
## <a name="returning-xml-from-a-user-defined-function"></a>Возвращение XML-данных из пользовательской функции  
 Запросы FOR XML можно использовать для возвращения XML-данных из определяемой пользователем функции, которая возвращает один из следующих объектов:  
  
-   таблицу с одним `xml`-столбцом;  
  
-   экземпляр `xml`-типа.  
  
 Так, следующая определяемая пользователем функция возвращает таблицу с одним `xm`-столбцом:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE FUNCTION dbo.MyUDF (@ProudctModelID int)  
RETURNS @T TABLE  
  (  
     ProductDescription xml  
  )  
AS  
BEGIN  
  INSERT @T  
     SELECT CatalogDescription.query('  
declare namespace PD="http://www.adventure-works.com/schemas/products/description";  
                    //PD:ProductDescription  ')  
     FROM Production.ProductModel  
     WHERE ProductModelID = @ProudctModelID  
  RETURN  
END;  
```  
  
 Можно выполнять определяемую пользователем функцию и отправляет запросы к возвращаемой ею таблице. В следующем примере XML-значение, возвращенное в результате запроса к таблице, присваивается `xml`-переменной.  
  
```  
declare @x xml;  
set @x = (SELECT * FROM MyUDF(19));  
select @x;  
```  
  
 Вот еще один пример определяемой пользователем функции. Данная определяемая пользователем функция возвращает экземпляр типа `xml`. В следующем примере определяемая пользователем функция возвращает типизированный экземпляр XML, поскольку здесь указано пространство имен схемы.  
  
```  
DROP FUNCTION dbo.MyUDF;  
GO  
CREATE FUNCTION MyUDF (@ProductModelID int)   
RETURNS xml ([Production].[ProductDescriptionSchemaCollection])  
AS  
BEGIN  
  declare @x xml  
  set @x =   ( SELECT CatalogDescription  
          FROM Production.ProductModel  
          WHERE ProductModelID = @ProductModelID )  
  return @x  
END;  
```  
  
 Возвращенный определяемой пользователем функцией код XML может быть присвоен `xml`-переменной следующим образом:  
  
```  
declare @x xml;  
SELECT @x= dbo.MyUDF4 (19) ;  
select @x;  
```  
  
## <a name="see-also"></a>См. также:  
 [Поддержка FOR XML для различных типов данных SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
