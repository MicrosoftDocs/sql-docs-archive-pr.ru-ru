---
title: Синтаксис пути к элементу для XML-данных отчета (SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ElementPath syntax
- XML [Reporting Services], data retrieval
ms.assetid: 07bd7a4e-fd7a-4a72-9344-3258f7c286d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d66b39761dc278abff25a3b22ccd18ca74272b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751779"
---
# <a name="element-path-syntax-for-xml-report-data-ssrs"></a>Синтаксис пути к элементу для XML-данных отчета (SSRS)
  В конструкторе отчетов для определения данных из источника данных XML, которые должны использоваться в отчете, указывается путь к элементу с учетом регистра. Путь к элементу — это путь по иерархическим XML-узлам в источнике XML-данных и атрибуты этих узлов. Чтобы использовать путь к элементу по умолчанию, оставьте пустым запрос набора данных или XML `ElementPath` для XML-`Query`. При получении данных из источника XML-данных узлы элементов, которые имеют текстовые значения и атрибуты узла элемента, преобразуются в столбцы результирующего набора. При выполнении запроса значения этих узлов и атрибуты преобразуются в данные строк. Эти столбцы появляются в качестве коллекции полей набора данных в области данных отчета. В этом разделе содержится информация о синтаксисе пути к элементу.  
  
> [!NOTE]  
>  Синтаксис пути к элементу не зависит от пространства имен. Чтобы использовать пространства имен в пути к элементу, используйте синтаксис XML-запроса, включающий XML- `ElementPath` элемент, описанный в разделе [синтаксис запроса XML для XML-данных отчета &#40;&#41;SSRS ](report-data-ssrs.md).  
  
 В следующей таблице указаны обозначения, используемые для определения пути к элементу.  
  
|Обозначение|Используется для|  
|----------------|--------------|  
|**полужирный**|Текст, который должен вводиться точно так, как показано.|  
|&#124; (вертикальная линия)|Разделяет элементы синтаксиса. Можно выбрать только один из элементов.|  
|`[ ] (brackets)`|Необязательные элементы синтаксиса. Скобки не вводятся.|  
|**{}** (фигурные скобки)|Разделяют параметры элементов синтаксиса.|  
|[ **,** ...*n*]|Указывает на то, что предшествующий элемент можно повторить *n* раз. Отдельные вхождения элемента разделяются запятыми.|  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Element path ::=  
    ElementNode[/Element path]  
ElementNode ::=  
    XMLName[(Encoding)][{[FieldList]}]  
XMLName ::=  
    [NamespacePrefix:]XMLLocalName  
Encoding ::=  
        HTMLEncoded | Base64Encoded  
FieldList ::=  
    Field[,FieldList]  
Field ::=  
    Attribute | Value | Element | ElementNode  
Attribute ::=  
        @XMLName[(Type)]  
Value ::=  
        @[(Type)]  
Element ::=  
    XMLName[(Type)]  
Type ::=  
        String | Integer | Boolean | Float | Decimal | Date | XML   
NamespacePrefix ::=  
    Identifier that specifies the namespace.  
XMLLocalName :: =  
    Identifier in the XML tag.   
```  
  
## <a name="remarks"></a>Remarks  
 В следующей таблице указаны термины пути к элементу. Примеры в этой таблице ссылаются на учебный XML-документ Customers.xml в подразделе «Примеры» этого раздела.  
  
> [!NOTE]  
>  В XML-тегах различается регистр символов. Определение ElementNode в пути к элементу должно точно соответствовать XML-тегам в источнике данных.  
  
|Термин|Определение|  
|----------|----------------|  
|Путь к элементу|Определяет последовательность узлов, которые необходимо пройти в XML-документе, чтобы получить поля данных для набора данных из источника XML-данных.|  
|`ElementNode`|XML-узел в XML-документе. Узлы обозначаются тегами и находятся в иерархической связи с другими узлами. Например, \<Customers> — это корневой узел элемента. \<Customer>является вложенным элементом \<Customers> .|  
|`XMLName`|Имя узла. Например, именем узла Customers является Customers. Чтобы дать каждому узлу уникальное имя, `XMLName` может иметь префикс с идентификатором пространства имен.|  
|`Encoding`|Указывает, что `Value` для этого элемента закодировано на языке XML, требует декодирования и включается как подэлемент этого элемента.|  
|`FieldList`|Определяет набор элементов и атрибутов, используемых для получения данных.<br /><br /> Если не указано иное, все атрибуты и подэлементы используются в качестве полей. Если указан пустой список полей ( **{}** ), поля из этого узла не используются.<br /><br /> `FieldList` не может одновременно содержать `Value` и `Element` или `ElementNode`.|  
|`Field`|Определяет данные, извлекаемые как поле набора данных.|  
|`Attribute`|Пара «имя-значение» в `ElementNode`. Например, в узле element \<Customer ID="1"> `ID` является атрибутом и `@ID(Integer)` возвращает "1" как целочисленный тип в соответствующем поле данных `ID` .|  
|`Value`|Значение элемента. `Value` может использоваться для последнего `ElementNode` в пути к элементу. Например, поскольку \<Return> является конечным узлом, если включить его в конец пути к элементу, значение `Return {@}` равно `Chair` .|  
|`Element`|Значение именованного подэлемента. Например, Customers {}/Customer {}/LastName извлекает значения только для элемента LastName.|  
|`Type`|Необязательный тип данных, который должен использоваться для поля, созданного из этого элемента.|  
|`NamespacePrefix`|`NamespacePrefix` определяется в элементе XML-запроса. Если элемента XML-запроса не существует, пространства имен в XML `ElementPath` не обрабатываются. Если элемент XML-запроса существует, XML `ElementPath` имеет необязательный атрибут `IgnoreNamespaces`. Если IgnoreNamespaces имеет значение `true` , то пространства имен XML `ElementPath` и XML-документа игнорируются. Дополнительные сведения см. в разделе [Синтаксис запроса XML для XML-данных отчета &#40;SSRS&#41;](report-data-ssrs.md).|  
  
## <a name="example---no-namespaces"></a>Пример (без пространств имен)  
 В следующих примерах используется XML-документ Customers.XML. Эта таблица содержит примеры синтаксиса пути к элементу и результаты использования пути в запросе. Источником данных является XML-документ.  
  
 Обратите внимание, что если путь к элементу пуст, запрос использует путь к элементу по умолчанию: первый путь к коллекции конечных узлов. В первом примере пустой путь к элементу эквивалентен указанию пути /Customers/Customer/Orders/Order. Все значения узлов и атрибуты на этом пути возвращаются в результирующем наборе, а имена узлов и имена атрибутов представляются в качестве полей набора данных.  
  
-   *Пусто*  
  
    |Порядок|Количество|ID|FirstName|LastName|Customer.ID|xmlns|  
    |-----------|---------|--------|---------------|--------------|-----------------|-----------|  
    |Chair|6|1|Bobby|Moore|11|http://www.adventure-works.com|  
    |Таблица|1|2|Bobby|Moore|11|http://www.adventure-works.com|  
    |Sofa|2|8|Crystal|Hu|20|http://www.adventure-works.com|  
    |EndTables|2|15|Wyatt|Diaz|33|http://www.adventure-works.com|  
  
-   `Customers {}/Customer`  
  
    |FirstName|LastName|ID|  
    |---------------|--------------|--------|  
    |Bobby|Moore|11|  
    |Crystal|Hu|20|  
    |Wyatt|Diaz|33|  
  
-   `Customers {}/Customer {}/LastName`  
  
    |LastName|  
    |--------------|  
    |Moore|  
    |Hu|  
    |Diaz|  
  
-   `Customers {}/Customer {}/Orders/Order {@,@Qty}`  
  
    |Порядок|Количество|  
    |-----------|---------|  
    |Chair|6|  
    |Таблица|1|  
    |Sofa|2|  
    |EndTables|2|  
  
-   `Customers {}/Customer/Orders/Order{ @ID(Integer)}`  
  
    |Order.ID|FirstName|LastName|ID|  
    |--------------|---------------|--------------|--------|  
    |1|Bobby|Moore|11|  
    |2|Bobby|Moore|11|  
    |8|Crystal|Hu|20|  
    |15|Wyatt|Diaz|33|  
  
#### <a name="xml-document-customersxml"></a>XML-документ: Customers.xml  
 Чтобы проверить примеры пути к элементу из предыдущего раздела, можно скопировать этот XML-документ и сохранить его в URL-адресе, доступном из конструктора отчетов, а затем использовать этот XML-документ в качестве источника XML-данных, например `http://localhost/Customers.xml`.  
  
```  
<?xml version="1.0"?>  
<Customers xmlns="http://www.adventure-works.com">  
   <Customer ID="11">  
      <FirstName>Bobby</FirstName>  
      <LastName>Moore</LastName>  
      <Orders>  
         <Order ID="1" Qty="6">Chair</Order>  
         <Order ID="2" Qty="1">Table</Order>  
      </Orders>  
      <Returns>  
         <Return ID="1" Qty="2">Chair</Return>  
      </Returns>  
   </Customer>  
   <Customer ID="20">  
      <FirstName>Crystal</FirstName>  
      <LastName>Hu</LastName>  
      <Orders>  
         <Order ID="8" Qty="2">Sofa</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
   <Customer ID="33">  
      <FirstName>Wyatt</FirstName>  
      <LastName>Diaz</LastName>  
      <Orders>  
         <Order ID="15" Qty="2">EndTables</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
</Customers>  
```  
  
 В качестве альтернативы можно создать источник XML-данных без строки соединения и внедрить документ Customers.XML в запрос с помощью следующей процедуры:  
  
###### <a name="to-embed-customersxml-in-a-query"></a>Внедрение документа Customers.XML в запрос  
  
1.  Создайте источник XML-данных с пустой строкой соединения.  
  
2.  Создайте новый набор данных для источника XML-данных.  
  
3.  В диалоговом окне **Свойства набора данных** нажмите кнопку **Конструктор запросов**. Откроется текстовое диалоговое окно конструктора запросов.  
  
4.  На панели запросов введите следующие две строки:  
  
     `<Query>`  
  
     `<XmlData>`  
  
5.  Скопируйте содержимое документа Customers.XML и вставьте его на панель запроса после `<XmlData>`.  
  
6.  На панели запроса удалите первую строку, скопированную из документа Customers.XML: `<?xml version="1.0"?>`  
  
7.  В конце запроса добавьте две следующие строки:  
  
     `<XmlData>`  
  
     `<Query>`  
  
8.  Нажмите кнопку **Выполнить запрос** (!).  
  
     Результирующий набор отображает 4 строки данных со следующими столбцами: `xmlns`, `Customer.ID`, `FirstName`, `LastName`, `ID`, `Qty`, `Order`.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Тип подключения XML &#40;SSRS&#41;](xml-connection-type-ssrs.md)   
 [Reporting Services учебники &#40;службы SSRS&#41;](../reporting-services-tutorials-ssrs.md)   
 [Добавление, изменение и обновление полей в области данных отчета (построитель отчетов и службы SSRS)](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)  
  
  
