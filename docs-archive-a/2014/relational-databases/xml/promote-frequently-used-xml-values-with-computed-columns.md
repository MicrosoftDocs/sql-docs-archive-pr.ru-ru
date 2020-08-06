---
title: Продвижение часто используемых значений XML с помощью вычисляемых столбцов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- promoting properties [XML in SQL Server]
- property promotion [XML in SQL Server]
ms.assetid: f5111896-c2fd-4209-b500-f2baa45489ad
author: rothja
ms.author: jroth
ms.openlocfilehash: bfb83b7772ffd92eab7087db11e4c3ffd96afa47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733670"
---
# <a name="promote-frequently-used-xml-values-with-computed-columns"></a>Продвижение часто используемых XML-значений с помощью вычисляемых столбцов
  Если часто запрашивается небольшое количество значений элементов и атрибутов, можно выполнить их продвижение до реляционных столбцов. Это полезно, если запрос выполняется для небольшой части XML-данных, тогда как извлекается весь экземпляр XML. Создавать XML-индекс для XML-столбца не требуется. Вместо этого можно проиндексировать столбец, созданный на основе свойства. В запросах необходимо использовать этот столбец, потому что оптимизатор запросов не перенаправляет запросы XML-столбца столбцу, созданному на основе свойства.  
  
 Столбец, созданный на основе свойства, может быть вычисляемым столбцом в той же таблице или отдельным пользовательским столбцом таблицы. Если для каждого экземпляра XML выполняется продвижение одинарных значений, этого достаточно. Однако в случае многозначных свойств необходимо создать для свойства отдельную таблицу. Это описывается в следующем разделе.  
  
## <a name="computed-column-based-on-the-xml-data-type"></a>Вычисляемый столбец, основанный на типе данных xml  
 Вычисляемый столбец можно создать с помощью определяемой пользователем функции, которая вызывает `xml` методы типа данных. Вычисляемый столбец может иметь любой тип SQL, в том числе XML. Это продемонстрировано в следующем примере.  
  
### <a name="example-computed-column-based-on-the-xml-data-type-method"></a>Пример Вычисляемый столбец, основанный на методе типа данных xml  
 Создание пользовательской функции, возвращающей ISBN-номер книги:  
  
```  
CREATE FUNCTION udf_get_book_ISBN (@xData xml)  
RETURNS varchar(20)  
BEGIN  
   DECLARE @ISBN   varchar(20)  
   SELECT @ISBN = @xData.value('/book[1]/@ISBN', 'varchar(20)')  
   RETURN @ISBN   
END  
```  
  
 Добавление в таблицу вычисляемого столбца для хранения значений ISBN:  
  
```  
ALTER TABLE      T  
ADD   ISBN AS dbo.udf_get_book_ISBN(xCol)  
```  
  
 Теперь вычисляемый столбец можно проиндексировать обычным способом.  
  
### <a name="example-queries-on-a-computed-column-based-on-xml-data-type-methods"></a>Пример Запросы данных из вычисляемого столбца на основе методов типа данных xml  
 Чтобы получить элемент <`book`> с ISBN-номером 0-7356-1588-2, можно выполнить следующее:  
  
```  
SELECT xCol  
FROM   T  
WHERE  xCol.exist('/book/@ISBN[. = "0-7356-1588-2"]') = 1  
```  
  
 Запрос данных из XML-столбца можно переписать так, чтобы в нем использовался вычисляемый столбец:  
  
```  
SELECT xCol  
FROM   T  
WHERE  ISBN = '0-7356-1588-2'  
```  
  
 Можно создать определяемую пользователем функцию для возврата `xml` типа данных и вычисляемого столбца с помощью определяемой пользователем функции. Однако создать XML-индекс для вычисляемого XML-столбца нельзя.  
  
## <a name="creating-property-tables"></a>Создание таблиц свойств  
 Иногда целесообразно выполнить продвижение некоторых многозначных свойств XML-данных до одной или нескольких таблиц, создать индексы для этих таблиц и перенаправить запросы к этим таблицам. Типичная ситуация, когда это полезно, имеет место тогда, когда в большинстве запросов обращение происходит к небольшому числу свойств. Можно сделать следующее.  
  
-   Создать одну или несколько таблиц для хранения многозначных свойств. Иногда удобно хранить одно свойство в каждой таблице и продублировать первичный ключ базовой таблицы в таблицах свойств для их соединения с базовой таблицей.  
  
-   Если требуется сохранить относительный порядок свойств, для этого нужно создать отдельный столбец.  
  
-   Создать триггеры для XML-столбца с целью обслуживания таблиц свойств. В триггерах сделайте что-либо одно из следующего перечисленного ниже.  
  
    -   `xml`Для вставки и удаления строк таблиц свойств используются методы типа данных, такие как **nodes ()** и **value ()**.  
  
    -   Создайте в среде CLR потоковые возвращающие табличное значение функции для вставки строк в таблицы свойств и их удаления.  
  
    -   Напишите запросы, осуществляющие основанный на SQL доступ к таблицам свойств и основанный на XML доступ к XML-столбцу базовой таблицы, соединяя таблицы с использованием их первичного ключа.  
  
### <a name="example-create-a-property-table"></a>Пример Создание таблицы свойств  
 Предположим, что требуется выполнить продвижение свойства, представляющего имена авторов. У книги может быть несколько авторов, поэтому данное свойство является многозначным. Каждое имя хранится в отдельной строке таблицы свойств. Первичный ключ базовой таблицы дублируется в таблице свойств ради обратного соединения таблиц.  
  
```  
create table tblPropAuthor (propPK int, propAuthor varchar(max))  
```  
  
### <a name="example-create-a-user-defined-function-to-generate-a-rowset-from-an-xml-instance"></a>Пример Создание пользовательской функции для создания набора строк на основе экземпляра XML  
 Следующая возвращающая табличное значение функция, udf_XML2Table, принимает значение первичного ключа и экземпляр XML. Она извлекает имена всех авторов из элемента <`book`> и возвращает набор строк, состоящий из пар (первичный ключ / имя).  
  
```  
create function udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (propPK int, propAuthor varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
      select @pk, nref.value('.', 'varchar(max)')  
      from   @xCol.nodes('/book/author/first-name') R(nref)  
      return  
end  
```  
  
### <a name="example-create-triggers-to-populate-a-property-table"></a>Пример Создание триггеров для заполнения таблицы свойств  
 Триггер вставки вставляет строки в таблицу свойств:  
  
```  
create trigger trg_docs_INS on T for insert  
as  
      declare @wantedXML xml  
      declare @FK int  
      select @wantedXML = xCol from inserted  
      select @FK = PK from inserted  
  
   insert into tblPropAuthor  
   select * from dbo.udf_XML2Table(@FK, @wantedXML)  
```  
  
 Триггер удаления удаляет строки из таблицы свойств на основе значения первичного ключа:  
  
```  
create trigger trg_docs_DEL on T for delete  
as  
   declare @FK int  
   select @FK = PK from deleted  
   delete tblPropAuthor where propPK = @FK  
```  
  
 Триггер обновления удаляет строки из таблицы свойств в соответствии с обновленным экземпляром XML и вставляет в таблицу свойств новые строки:  
  
```  
create trigger trg_docs_UPD  
on T  
for update  
as  
if update(xCol) or update(pk)  
begin  
      declare @FK int  
      declare @wantedXML xml  
      select @FK = PK from deleted  
      delete tblPropAuthor where propPK = @FK  
  
   select @wantedXML = xCol from inserted  
   select @FK = pk from inserted  
  
   insert into tblPropAuthor   
      select * from dbo.udf_XML2Table(@FK, @wantedXML)  
end  
```  
  
### <a name="example-find-xml-instances-whose-authors-have-the-same-first-name"></a>Пример Поиск экземпляров XML, включающих авторов с именем "David"  
 Можно составить такой запрос для XML-столбца или найти в таблице свойств записи с именами David и выполнить обратное соединение с базовой таблицей для возврата экземпляра XML. Пример:  
  
```  
SELECT xCol   
FROM     T JOIN tblPropAuthor ON T.pk = tblPropAuthor.propPK  
WHERE    tblPropAuthor.propAuthor = 'David'  
```  
  
### <a name="example-solution-using-the-clr-streaming-table-valued-function"></a>Пример Решение, основанное на использовании потоковой функции CLR с табличным значением  
 Данное решение состоит из следующих шагов:  
  
1.  определение CLR-класса SqlReaderBase, реализующего интерфейс ISqlReader и формирующего потоковый возвращающий табличное значение выход путем применения выражения пути к экземпляру XML;  
  
2.  создание сборки и пользовательской функции языка Transact-SQL, запускающей класс CLR;  
  
3.  определение с помощью пользовательской функции триггеров вставки, обновления и удаления для обслуживания таблиц свойств.  
  
 Чтобы реализовать это решение, создайте сначала потоковую функцию CLR. `xml`Тип данных предоставляется как управляемый класс SQLXML в ADO.NET и поддерживает метод **CreateReader ()** , возвращающий XmlReader.  
  
> [!NOTE]  
>  В примере данного раздела используются классы XPathDocument и XPathNavigator, которые вынуждают программиста загрузить в память все XML-документы. Используя подобный код в своих приложениях для обработки нескольких крупных XML-документов, знайте, что он плохо масштабируется. Старайтесь свести к минимуму число операций выделения памяти и используйте во всех возможных случаях потоковые интерфейсы. Дополнительные сведения о производительности см. в разделе [Архитектура интеграции со средой CLR](../../database-engine/dev-guide/architecture-of-clr-integration.md).  
  
```  
public class c_streaming_xml_tvf {  
   public static ISqlReader streaming_xml_tvf   
(SqlXml xmlDoc, string pathExpression) {  
      return (new TestSqlReaderBase (xmlDoc, pathExpression));  
   }  
}  
  
// Class that implements ISqlReader  
public class TestSqlReaderBase : ISqlReader {  
XPathNodeIterator m_iterator;           
   public SqlChars FirstName;  
// Metadata for current resultset  
private SqlMetaData[] m_rgSqlMetaData;        
  
   public TestSqlReaderBase (SqlXml xmlDoc, string pathExpression) {     
      // Variables for XPath navigation  
      XPathDocument xDoc;  
      XPathNavigator xNav;  
      XPathExpression xPath;  
  
      // Set sql metadata  
      m_rgSqlMetaData = new SqlMetaData[1];  
      m_rgSqlMetaData[0] = new SqlMetaData ("FirstName",    
SqlDbType.NVarChar,50);     
  
      //Set up the Navigator  
      if (!xmlDoc.IsNull)  
          xDoc = new XPathDocument (xmlDoc.CreateReader());  
      else  
          xDoc = new XPathDocument ();  
      xNav = xDoc.CreateNavigator();  
      xPath = xNav.Compile (pathExpression);  
      m_iterator = xNav.Select(xPath);  
   }  
   public bool Read() {  
      bool moreRows = true;  
      if (moreRows = m_iterator.MoveNext())  
         FirstName = new SqlChars (m_iterator.Current.Value);  
      return moreRows;  
   }  
}  
```  
  
 Затем создайте сборку и пользовательскую функцию [!INCLUDE[tsql](../../includes/tsql-md.md)] с именем SQL_streaming_xml_tvf (не показана), соответствующую функции CLR streaming_xml_tvf. Пользовательская функция применяется для определения возвращающей табличное значение функции CLR_udf_XML2Table с целью создания набора строк:  
  
```  
create function CLR_udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (FK int, FirstName varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
   select @pk, FirstName   
   FROM   SQL_streaming_xml_tvf (@xCol, '/book/author/first-name')  
      return  
end  
```  
  
 Наконец, определите триггеры так, как показано в разделе «Создание триггеров для заполнения таблицы свойств», заменив при этом функцию udf_XML2Table функцией CLR_udf_XML2Table. Триггер вставки показан в следующем примере:  
  
```  
create trigger CLR_trg_docs_INS on T for insert  
as  
   declare @wantedXML xml  
   declare @FK int  
   select @wantedXML = xCol from inserted  
   select @FK = PK from inserted  
  
   insert into tblPropAuthor  
      select *  
   from    dbo.CLR_udf_XML2Table(@FK, @wantedXML)  
```  
  
 Триггер удаления идентичен версии, не использующей среду CLR. Однако триггер обновления просто заменяет функцию udf_XML2Table() функцией CLR_udf_XML2Table().  
  
## <a name="see-also"></a>См. также:  
 [Использование XML в вычисляемых столбцах](use-xml-in-computed-columns.md)  
  
  
