---
title: 'Создание допустимых атрибутов типа ID, IDREF и IDREFS с помощью SQL: prefix (SQLXML 4,0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- annotated XSD schemas, ID type attribute
- IDREF type attribute [SQLXML]
- annotated XSD schemas, IDREFS type attribute
- ID type attribute [SQLXML]
- sql:prefix
- prefix annotation
- IDREF relationships [SQLXML]
- IDREFS type attribute [SQLXML]
- annotated XSD schemas, IDREF type attribute
- ID relationships [SQLXML]
ms.assetid: 1c7f77d3-81f3-4820-bb63-c4aaa4ea9aa1
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9e63bebd0cebbfeed75ea5cbe2ea62683234fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664121"
---
# <a name="creating-valid-id-idref-and-idrefs-type-attributes-using-sqlprefix-sqlxml-40"></a>Создание допустимых атрибутов типа ID, IDREF и IDREFS с использованием sql:prefix (SQLXML 4.0)
  Атрибут может быть задан как атрибут типа ID. Атрибуты, заданные как IDREF или IDREFS, могут затем использоваться для ссылки на атрибуты типа ID, создавая ссылки между документами.  
  
 ID, IDREF и IDREFS соответствуют связям PK/FK («первичный ключ-внешний ключ») в базе данных, не считая некоторых отличий. В XML-документе значения атрибутов типа ID должны быть различными. Если атрибуты **CustomerID** и **OrderID** указаны в XML-документе как тип идентификатора, эти значения должны быть разными. Но в базе данных столбцы CustomerID и OrderID могут иметь одинаковые значения. (Например, в базе данных допустимы значения CustomerID = 1 и OrderID = 1.)  
  
 Чтобы атрибуты ID, IDREF и IDREFS были допустимыми, должны выполняться следующие условия.  
  
-   Значение атрибута ID должно быть уникальным в пределах XML-документа.  
  
-   Для каждого атрибута IDREF и IDREFS в XML-документе должны присутствовать значения ID, на которые ссылается этот атрибут.  
  
-   Значение атрибутов ID, IDREF и IDREFS должно быть именованным токеном. (Например, целочисленное значение 101 не может быть значением ID.)  
  
-   Атрибуты типа ID, IDREF и IDREFS не могут быть сопоставлены столбцам типа `text`, `ntext`, `image` или любого другого двоичного типа (например, `timestamp`).  
  
 Если XML-документ содержит несколько значений ID, необходимо использовать заметку `sql:prefix` для обеспечения уникальности значений.  
  
 Обратите внимание, что заметку `sql:prefix` невозможно использовать с атрибутом неизменности XSD.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-id-and-idrefs-types"></a>A. Задание типов ID и IDREFS  
 В следующей схеме **\<Customer>** элемент состоит из **\<Order>** дочернего элемента. **\<Order>** Элемент также имеет дочерний элемент — **\<OrderDetail>** элемент.  
  
 Атрибут **ордеридлист** атрибута **\<Customer>** является атрибутом типа IDREFS, который ссылается на атрибут **OrderID** **\<Order>** элемента.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
                 parent="Sales.Customer"  
                 parent-key="CustomerID"  
                 child="Sales.SalesOrderHeader"  
                 child-key="CustomerID" />  
    <sql:relationship name="OrderOrderDetail"  
                 parent="Sales.SalesOrderHeader"  
                 parent-key="SalesOrderID"  
                 child="Sales.SalesOrderDetail"  
                 child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
               sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                   sql:relationship="OrderOrderDetail"   
                   maxOccurs="unbounded" >  
                  <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="ProductID" type="xsd:string" />  
                   <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
               </xsd:element>  
             </xsd:sequence>  
             <xsd:attribute name="SalesOrderID"   
                            type="xsd:ID" sql:prefix="ord-" />  
             <xsd:attribute name="OrderDate" type="xsd:date" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CustomerID" type="xsd:string" />  
    <xsd:attribute name="OrderIDList" type="xsd:IDREFS"   
                   sql:relation="Sales.SalesOrderHeader" sql:field="SalesOrderID"  
                   sql:relationship="CustOrders" sql:prefix="ord-">  
    </xsd:attribute>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем sqlPrefix.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем sqlPrefixT.xml в том же каталоге, в котором был сохранен файл sqlPrefix.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="sqlPrefix.xml">  
        /Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу для схемы сопоставления (sqlPrefix.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlPrefix.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Частичный результат:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" OrderIDList="ord-43860 ord-44501 ord-45283 ord-46042">  
    <Order SalesOrderID="ord-43860" OrderDate="2001-08-01" CustomerID="1">  
      <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
      ...  
    </Order>  
    ...  
 </Customer>  
</ROOT>  
```  
  
  
