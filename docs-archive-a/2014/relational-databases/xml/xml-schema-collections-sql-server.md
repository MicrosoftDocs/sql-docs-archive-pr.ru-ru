---
title: Коллекции схем XML (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- xml_schema_namespace function
- XML schema collections [SQL Server], about XML schema collections
- metadata [SQL Server], XML schema collections
- queries [XML in SQL Server], XML schema collections
- schema collections [SQL Server]
- schemas [SQL Server], XML
- XML [SQL Server], schema collections
- XML schema collections [SQL Server]
- schema collections [SQL Server], about XML schema collections
ms.assetid: 659d41aa-ccec-4554-804a-722a96ef25c2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ee4757f1353278447ee55e97c8d4ba23aa2d649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665893"
---
# <a name="xml-schema-collections-sql-server"></a>Коллекции XML-схем (SQL Server)
  Как описано в разделе [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql), SQL Server предоставляет собственное хранилище XML-данных через `xml` тип данных. При необходимости можно связать схемы XSD с переменной или столбцом `xml` типа с помощью коллекции схем XML. Коллекция XML-схем хранит импортированные XML-схемы и используется для решения следующих задач:  
  
-   проверка экземпляров XML;  
  
-   типизация XML-данных, хранимых в базе данных.  
  
 Коллекция XML-схем — это сущность класса метаданных, подобная таблице в базе данных. Можно создавать, изменять и удалять эти схемы. Схемы, указанные в инструкции [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) , автоматически импортируются в создаваемую коллекцию XML-схем. Можно импортировать дополнительные схемы или компоненты схем в существующую в базе данных коллекцию при помощи инструкции [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) .  
  
 Как описано в разделе [Сравнение типизированного и нетипизированного XML](../xml/compare-typed-xml-to-untyped-xml.md), код XML, хранимый в столбце или переменной, с которой связана схема, называется **типизированным**, потому что схема предоставляет необходимую информацию о типах данных экземпляра. В SQL Server эта информация о типах используется для оптимизации хранения данных.  
  
 Механизм обработки запросов применяет схемы для проверки типов, а также оптимизации запросов и изменения данных.  
  
 Кроме того, SQL Server использует связанную коллекцию XML-схем (в случае типизированной) `xml` для проверки экземпляра XML. Если экземпляр XML соответствует схеме, база данных позволяет сохранить его в системе с информацией о его типах. В противном случае она отклоняет экземпляр.  
  
 Встроенная функция XML_SCHEMA_NAMESPACE позволяет получить коллекцию схем, хранимую в базе данных. Дополнительные сведения см. в разделе [Просмотр хранимой коллекции схем XML](../xml/view-a-stored-xml-schema-collection.md).  
  
 Кроме того, можно использовать коллекцию схем XML для типизации переменных, параметров и столбцов типа XML.  
  
##  <a name="ddl-for-managing-schema-collections"></a><a name="ddl"></a> DDL для управления коллекциями схем  
 В базе данных можно создавать коллекции схем XML и связывать их с переменными и столбцами типа `xml`. Для управления коллекциями схем в базе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусмотрены следующие инструкции DDL:  
  
-   [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) импортирует компоненты схемы в базу данных.  
  
-   [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) изменяет компоненты схемы в существующей коллекции схем XML.  
  
-   [DROP XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) полностью удаляет коллекцию схем XML и все ее компоненты.  
  
 Чтобы использовать коллекцию XML-схем и содержащиеся в ней схемы, следует сначала создать коллекцию и схемы с помощью инструкции CREATE XML SCHEMA COLLECTION. После создания коллекции схемы можно создавать переменные и столбцы типа `xml` и связать с ними коллекцию схем. Обратите внимание, что после создания коллекции различные компоненты схем будут храниться в метаданных. Кроме того, добавлять большие компоненты в существующие схемы или новые схемы в существующую коллекцию можно с помощью инструкции ALTER XML SCHEMA COLLECTION.  
  
 Удалить коллекцию схем можно с помощью инструкции DROP XML SCHEMA COLLECTION. При этом удаляются все схемы в коллекции и сам объект коллекции. Обратите внимание, что для удаления коллекции схем должны выполняться условия, описанные в разделе [DROP XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql).  
  
##  <a name="understanding-schema-components"></a><a name="components"></a> Основные сведения о компонентах схемы  
 При использовании инструкции CREATE XML SCHEMA COLLECTION в базу данных импортируются различные компоненты схемы. К компонентам схемы относятся ее элементы, атрибуты и определения типов. При использовании инструкции DROP XML SCHEMA COLLECTION коллекция удаляется целиком.  
  
 Инструкция CREATE XML SCHEMA COLLECTION сохраняет компоненты схемы в различных системных таблицах.  
  
 Например, рассмотрим следующую схему:  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            targetNamespace="uri:Cust_Orders2"  
            xmlns="uri:Cust_Orders2" >  
  <xsd:attribute name="SomeAttribute" type="xsd:int" />  
  <xsd:complexType name="SomeType" />  
  <xsd:complexType name="OrderType" >  
    <xsd:sequence>  
      <xsd:element name="OrderDate" type="xsd:date" />  
      <xsd:element name="RequiredDate" type="xsd:date" />  
      <xsd:element name="ShippedDate" type="xsd:date" />  
    </xsd:sequence>  
    <xsd:attribute name="OrderID" type="xsd:ID" />  
    <xsd:attribute name="CustomerID"  />  
    <xsd:attribute name="EmployeeID"  />  
  </xsd:complexType>  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order" type="OrderType"  
                     maxOccurs="unbounded" />  
       </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
      <xsd:attribute name="OrderIDList" type="xsd:IDREFS" />  
  </xsd:complexType>  
  <xsd:element name="Customer" type="CustomerType" />  
</xsd:schema>  
```  
  
 В приведенной выше схеме показаны различные типы компонентов, которые могут храниться в базе данных. Это компоненты `SomeAttribute`, `SomeType`, `OrderType`, `CustomerType`, `Customer`, `Order`, `CustomerID`, `OrderID`, `OrderDate`, `RequiredDate`и `ShippedDate`.  
  
### <a name="component-categories"></a>Категории компонентов  
 Компоненты схемы, хранящиеся в базе данных, делятся на следующие категории:  
  
-   ELEMENT  
  
-   ATTRIBUTE  
  
-   TYPE (для простых и сложных типов);  
  
-   ATTRIBUTEGROUP;  
  
-   MODELGROUP.  
  
 Пример:  
  
-   **SomeAttribute** является компонентом ATTRIBUTE.  
  
-   **SomeType**, **OrderType**и **CustomerType** — это компоненты TYPE.  
  
-   **Customer** является компонентом ELEMENT.  
  
 При импорте схемы в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сохраняет саму схему. Вместо этого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет различные отдельные компоненты. Таким образом, тег \<Schema> не сохраняется, а сохраняются только компоненты, заданные внутри него. Все элементы схемы не сохраняются. Если тег \<Schema> содержит атрибуты, которые задают поведение по умолчанию для его компонентов, то во время импорта эти атрибуты перемещаются в компоненты схемы внутри нее, как показано в следующей таблице.  
  
|Имя атрибута|Поведение|  
|--------------------|--------------|  
|**attributeFormDefault**|Атрибут **form** применяется ко всем объявлениям атрибутов в схеме, где его еще нет. Ему присваивается значение, равное значению атрибута **attributeFormDefault** .|  
|**elementFormDefault**|Атрибут **form** применяется ко всем объявлениям элементов в схеме, где его еще нет. Ему присваивается значение, равное значению атрибута **elementFormDefault** .|  
|**blockDefault**|Атрибут **block** применяется ко всем объявлениям элементов и определениям типов в схеме, где его еще нет. Ему присваивается значение, равное значению атрибута **blockDefault** .|  
|**finalDefault**|Атрибут **final** применяется ко всем объявлениям элементов и определениям типов в схеме, где его еще нет. Ему присваивается значение, равное значению атрибута **finalDefault** .|  
|**targetNamespace**|Сведения о компонентах, принадлежащих целевому пространству имен, хранятся в метаданных.|  
  
##  <a name="permissions-on-an-xml-schema-collection"></a><a name="perms"></a> Разрешения на коллекцию схем XML  
 При этом требуется иметь соответствующие разрешения на выполнение следующих операций:  
  
-   создание и загрузка коллекции XML-схем;  
  
-   модификация коллекции XML-схем;  
  
-   удаление коллекции XML-схем;  
  
-   Коллекция XML-схем используется для типа `xml` столбцов, переменных и параметров, а также для использования в ограничениях таблиц и столбцов.  
  
 Модель безопасности SQL Server предусматривает разрешение CONTROL для каждого объекта. Обладателю этого разрешения предоставляются все остальные разрешения для данного объекта. Владелец объекта также имеет все разрешения для этого объекта.  
  
 Владелец и обладатель разрешения CONTROL для объекта могут давать любые разрешения на этот объект. Пользователь, не являющийся владельцем и не имеющий разрешения CONTROL, может давать разрешения на объект при использовании параметра WITH GRANT OPTION. Допустим, что пользователь A имеет предоставленное с помощью настройки WITH GRANT OPTION разрешение REFERENCES на коллекцию XML-схем S, но не имеет других разрешений на коллекцию S. В этом случае пользователь A может предоставить пользователю Б разрешение REFERENCES на коллекцию схем S.  
  
 Кроме того, модель безопасности допускает создание и использование разрешениями коллекций XML-схем или передачу данных о принадлежности от одного пользователя другому. Разрешения на коллекции XML-схем описываются в следующих подразделах.  
  
-   [Предоставление разрешений на коллекции схем XML](../xml/grant-permissions-on-an-xml-schema-collection.md)  
  
     В этом подразделе речь идет о том, каким образом предоставляются разрешения на создание коллекции XML-схем и разрешения на объекты коллекции XML-схем.  
  
-   [Отмена разрешений на коллекцию схем XML](../xml/revoke-permissions-on-an-xml-schema-collection.md)  
  
     В этом подразделе речь идет о том, каким образом можно использовать отмену разрешений для предотвращения создания коллекции XML-схем и как отменять разрешения на объекты коллекции XML-схем.  
  
-   [Запрет разрешения на коллекцию схем XML](../xml/deny-permissions-on-an-xml-schema-collection.md)  
  
     В этом подразделе речь идет о том, каким образом запрещаются разрешения на создание коллекции XML-схем и разрешения на объекты коллекции схем XML.  
  
##  <a name="getting-information-about-xml-schemas-and-schema-collections"></a><a name="info"></a> Получение информации о схемах XML и коллекциях схем  
 Коллекции XML-схем перечислены в представлении каталога sys.xml_schema_collections. Коллекция XML-схем «sys» определяется системой. Она содержит предопределенные пространства имен, которые можно использовать во всех пользовательских коллекциях XML-схем, не загружая их явно. Этот список содержит пространства имен xml, xs, xsi, fn и xdt. Двумя другими представлениями каталога являются sys.xml_schema_namespaces, в котором перечислены все пространства имен каждой коллекции XML-схем и sys.xml_components, в котором перечислены все компоненты каждой XML-схемы.  
  
 Встроенная функция **xml_schema_namespace**, *schemaName, XmlSchemacollectionName, Namespace-URI*, возвращает `xml` экземпляр типа данных. Этот экземпляр содержит фрагменты для XML-схем, содержащихся в коллекции XML-схем, за исключением предопределенных XML-схем.  
  
 Перечислить содержимое коллекции XML-схем можно двумя способами:  
  
-   написать запросы Transact-SQL, адресованные соответствующим представлениям каталога, связанным с коллекциями XML-схем;  
  
-   Используйте встроенную функцию **XML_SCHEMA_NAMESPACE()** . К `xml` выходным данным этой функции можно применить методы типа данных. Однако изменять базовые XML-схемы нельзя.  
  
 Все это поясняют следующие примеры.  
  
### <a name="example-enumerate-the-xml-namespaces-in-an-xml-schema-collection"></a>Пример Перечисление пространств имен XML, входящих в коллекцию XML-схем  
 Выполните следующий запрос для коллекции XML-схем «myCollection»:  
  
```  
SELECT XSN.name  
FROM    sys.xml_schema_collections XSC JOIN sys.xml_schema_namespaces XSN  
    ON (XSC.xml_collection_id = XSN.xml_collection_id)  
WHERE    XSC.name = 'myCollection'     
```  
  
### <a name="example-enumerate-the-contents-of-an-xml-schema-collection"></a>Пример Перечисление содержимого коллекции XML-схем  
 Следующая инструкция перебирает содержимое коллекции XML-схем «myCollection» реляционной схемы dbo.  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection')  
```  
  
 Отдельные XML-схемы в коллекции можно получить в виде `xml` экземпляров типа данных, указав целевое пространство имен в качестве третьего аргумента для **xml_schema_namespace ()**. Это показано в следующем примере.  
  
### <a name="example-output-a-specified-schema-from-an-xml-schema-collection"></a>Пример Вывод конкретной схемы из коллекции XML-схем  
 Следующая инструкция выводит XML-схему с целевым пространством имен "<https://www.microsoft.com/books>" из коллекции XML-схем "myCollection" реляционной схемы dbo.  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection',   
N'https://www.microsoft.com/books')  
```  
  
### <a name="querying-xml-schemas"></a>Запросы XML-схем  
 Запрашивать XML-схемы, загруженные в коллекцию XML-схем, можно перечисленными ниже способами.  
  
-   Написать адресованные представлениям каталога запросы Transact-SQL о получении пространств имен XML-схем.  
  
-   Создать таблицу со столбцом данных типа `xml` для хранения XML-схем и их загрузки в систему типов XML. Данные из XML-столбца можно запросить при помощи методов типа данных `xml`. Кроме того, можно создать для этого столбца XML-индекс. Однако при этом подходе в приложении нужно поддерживать согласованность между XML-схемами, хранимыми в XML-столбце, и системой типов XML. Например, при удалении пространства имен XML-схемы из системы типов XML для сохранения согласованности необходимо будет удалить его и из таблицы.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр хранимой коллекции схем XML](../xml/view-a-stored-xml-schema-collection.md)   
 [Предпроцессор схемы для слияния включаемых схем](../xml/preprocess-a-schema-to-merge-included-schemas.md)   
 [Требования и ограничения для коллекций схем XML на сервере](../xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
