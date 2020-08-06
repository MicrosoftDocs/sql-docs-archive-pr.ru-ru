---
title: Пример схемы XSD с заметками для примеров XPath (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], annotated XSD schemas in queries
- annotated XSD schemas, samples
- annotated XSD schemas, queries
ms.assetid: fefa2cc8-2d3c-4336-aeae-ce063a3a8df2
author: rothja
ms.author: jroth
ms.openlocfilehash: 7c7065bed89d867dda3ecffc7d80f2f729832e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655007"
---
# <a name="sample-annotated-xsd-schema-for-xpath-examples-sqlxml-40"></a>Образец схемы XSD с заметками для примеров XPath (SQLXML 4.0)
  Образцы запросов XPath в этом разделе обращаются к схеме сопоставления. Схема сопоставления — это XSD-файл с заметками схемы XML. Дополнительные сведения о схемах сопоставления см. [в статье Введение в схемы XSD с Заметками &#40;SQLXML 4,0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).  
  
 Для выполнения запросов XPath к схеме XSD с заметками необходимо выполнить следующее.  
  
-   Создайте шаблон с запросом XPath. В шаблоне укажите схему сопоставления, к который следует выполнять запрос XPath. В данном случае схема сопоставления должна храниться в каталоге (или одном из вложенных каталогов — в этом случае относительный путь указывается в виде значения атрибута `mapping-schema` в шаблоне), связанном с файлом шаблона.  
  
-   Создайте тестовое приложение, использующее для выполнения запросов расширения SQLXML для ADO. Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Во всех примерах этого раздела запросы XPath в целях иллюстрации указаны в шаблоне, и шаблон выполняется с помощью ADO. Поэтому необходимо использовать следующий файл схемы сопоставления — SampleSchema1.xml. Сохраните этот файл в каталоге, где хранятся шаблоны.  
  
## <a name="sample-annotated-xsd-schema-sampleschema1xml"></a>Образец схемы XSD с заметками (SampleSchema1.xml)  
  
```  
<?xml version="1.0"?>  
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
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders" />  
     </xsd:sequence>  
     <xsd:attribute name="CustomerID" type="xsd:ID"/>  
     <xsd:attribute name="TerritoryID"/>  
     <xsd:attribute name="AccountNumber"/>  
     <xsd:attribute name="CustomerType"/>  
     <xsd:attribute name="Orders" type="xsd:IDREFS" sql:prefix="Ord-"/>  
  </xsd:complexType>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="OrderType"/>  
  
  <xsd:complexType name="OrderType">  
     <xsd:sequence>  
        <xsd:element name="OrderDetail"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOrderDetail" />  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:ID" sql:prefix="Ord-"/>  
     <xsd:attribute name="SalesPersonID"/>  
     <xsd:attribute name="OrderDate"/>  
     <xsd:attribute name="DueDate"/>  
     <xsd:attribute name="ShipDate"/>  
  </xsd:complexType>  
  
  <xsd:element name="OrderDetail" sql:relation="Sales.SalesOrderDetail" type="OrderDetailType"/>  
  
  <xsd:complexType name="OrderDetailType">  
    <xsd:attribute name="ProductID" type="xsd:IDREF"/>  
    <xsd:attribute name="UnitPrice"/>  
    <xsd:attribute name="OrderQty"/>  
    <xsd:attribute name="UnitPriceDiscount"/>  
  </xsd:complexType>  
  
  <xsd:element name="UnitPriceDiscount" sql:relation="Sales.SalesOrderDetail" type="DiscountType"/>  
  
  <xsd:complexType name="DiscountType">  
    <xsd:simpleContent>  
       <xsd:extension base="xsd:string">  
          <xsd:anyAttribute namespace="##other" processContents="lax"/>  
       </xsd:extension>  
    </xsd:simpleContent>  
  </xsd:complexType>  
  
  <xsd:element name="Contact" sql:relation="Person.Contact" type="ContactType"/>  
  
  <xsd:complexType name="ContactType">  
    <xsd:attribute name="ContactID"/>  
    <xsd:attribute name="LastName"/>  
    <xsd:attribute name="FirstName"/>  
    <xsd:attribute name="Title"/>  
  </xsd:complexType>  
  
</xsd:schema>  
```  
  
  
