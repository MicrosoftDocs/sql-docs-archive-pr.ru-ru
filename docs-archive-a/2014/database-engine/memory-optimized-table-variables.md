---
title: Оптимизированные для памяти табличные переменные | Документация Майкрософт
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: bd102e95-53e2-4da6-9b8b-0e4f02d286d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: bec720c53c257240ee92274a6391ebc3f17faa25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665098"
---
# <a name="memory-optimized-table-variables"></a>Переменные оптимизированной для памяти таблицы
  Помимо оптимизированных для памяти таблиц (которые повышают эффективность доступа к данным) и скомпилированных в собственном коде хранимых процедур (которые повышают эффективность обработки запросов и выполнения бизнес-логики) [!INCLUDE[hek_2](../includes/hek-2-md.md)] также использует третий тип объекта: оптимизированный для памяти табличный тип. Табличная переменная, созданная с использованием оптимизированного для памяти табличного типа, является оптимизированной для памяти табличной переменной.  
  
 Оптимизированные для памяти табличные переменные обеспечивают следующие преимущества, если сравнивать их с дисковыми табличными переменными.  
  
-   Переменные хранятся только в памяти. Доступ к данным более эффективен, поскольку оптимизированный для памяти табличный тип использует такой же алгоритм и структуры данных, что и оптимизированные для памяти таблицы, особенно когда переменные используются в скомпилированных в собственном коде хранимых процедурах.  
  
-   С оптимизированными для памяти табличными переменными tempdb не используется. Табличные переменные не хранятся в базе данных tempdb и не потребляют ее ресурсы.  
  
 Типичные сценарии использования оптимизированных для памяти табличных переменных.  
  
-   Хранение промежуточных результатов и создание единого результирующего набора для нескольких запросов в скомпилированных в собственном коде хранимых процедурах.  
  
-   Передача параметров с табличными значениями в скомпилированные в собственном коде и интерпретируемые хранимые процедуры.  
  
-   Замена находящихся на диске табличных переменных и в некоторых случаях таблиц #temp, которые являются локальными по отношению к хранимой процедуре. Это особенно полезно, если база данных tempdb часто используется в системе.  
  
-   Табличные переменные могут использоваться для имитации курсоров из скомпилированных в собственном коде хранимых процедур, что может помочь обойти ограничения контактной зоны в скомпилированных в собственном коде хранимых процедурах.  
  
 Как и оптимизированные для памяти таблицы, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] создает библиотеку DLL для каждого оптимизированного для памяти табличного типа. (Компиляция вызывается при создании оптимизированного для памяти табличного типа, а не при использовании для создания оптимизированных для памяти табличных переменных.) Эта библиотека DLL включает функции для доступа к индексам и получения данных из табличных переменных. При объявлении оптимизированной для памяти табличной переменной на основе табличного типа создается экземпляр структур таблицы и индекса, соответствующий табличному типу в пользовательском сеансе. После этого табличную переменную можно использовать таким же образом, как и записанные на диск табличные переменные. Можно вставлять, обновлять и удалять строки в табличной переменной, а также использовать переменные в запросах [!INCLUDE[tsql](../includes/tsql-md.md)] . Кроме того, можно передавать переменные, скомпилированные в собственном коде, и интерпретированные хранимые процедуры в качестве параметров с табличными значениями (TVP).  
  
 В следующем примере показан оптимизированный для памяти табличный тип из образца выполняющейся в памяти OLTP на основе AdventureWorks ([пример SQL Server 2014 в памяти OLTP](https://msftdbprodsamples.codeplex.com/releases/view/114491)).  
  
```sql
CREATE TYPE Sales.SalesOrderDetailType_inmem
   AS TABLE
(
   OrderQty         smallint   NOT NULL,
   ProductID        int        NOT NULL,

   SpecialOfferID   int        NOT NULL
      INDEX  IX_SpecialOfferID  NONCLUSTERED,

   LocalID          int        NOT NULL,

   INDEX IX_ProductID HASH (ProductID)
      WITH ( BUCKET_COUNT = 8 )
)
WITH ( MEMORY_OPTIMIZED = ON );
```  
  
 Пример показывает, что синтаксис оптимизированных для памяти табличных типов похож на дисковые табличные типы, за исключением следующих случаев.  
  
-   `MEMORY_OPTIMIZED=ON` указывает, что табличный тип является оптимизированным для памяти.  
  
-   Тип должен иметь по крайней мере один индекс. Как и в случае с оптимизированными для памяти таблицами, можно использовать хэш-индексы и некластеризованные индексы.  
  
     Для хэш-индекса число контейнеров должно быть примерно в два раза больше числа ожидаемых уникальных ключей индекса. Дополнительные сведения см. в разделе [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).  
  
-   Тип данных и ограничения для оптимизированных для памяти таблиц также применяются к оптимизированным для памяти табличным типам. Например, ограничения по умолчанию в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] поддерживаются, а ограничения CHECK — нет.  
  
 Как и оптимизированные для памяти таблицы, оптимизированные для памяти табличные  
  
-   Не поддерживают параллельные планы.  
  
-   Должна помещаться в памяти и не использует дисковые ресурсы.  
  
 Записанные на диск табличные переменные существуют в tempdb. Оптимизированные для памяти табличные переменные существуют в пользовательской базе данных, однако они не используют хранение и не восстанавливаются.  
  
 Нельзя создать переменную оптимизированной для памяти таблицы с помощью встроенного синтаксиса. В отличие от дисковых табличных переменных сначала необходимо создать тип.  
  
## <a name="table-valued-parameters"></a>Параметры, возвращающие табличные значения  
 В следующем примере скрипта объявляется табличная переменная в качестве оптимизированного для памяти табличного типа `Sales.SalesOrderDetailType_inmem`, выполняется вставка трех строк в переменную и передача переменной в качестве возвращающего табличное значение параметра в `Sales.usp_InsertSalesOrder_inmem`.  
  
```sql  
DECLARE @od Sales.SalesOrderDetailType_inmem,  
  @SalesOrderID uniqueidentifier,  
  @DueDate datetime2 = SYSDATETIME()  
  
INSERT @od (LocalID, ProductID, OrderQty, SpecialOfferID) VALUES  
  (1, 888, 2, 1),  
  (2, 450, 13, 1),  
  (3, 841, 1, 1)  
  
EXEC Sales.usp_InsertSalesOrder_inmem  
  @SalesOrderID = @SalesOrderID,  
  @DueDate = @DueDate,  
 @OnlineOrderFlag = 1,  
  @SalesOrderDetails = @od  
```  
  
 Оптимизированные для памяти табличные типы можно использовать в качестве параметров с табличными значениями хранимых процедур; клиенты могут обращаться к ним по ссылке так же, как и к записанным на диск табличным типам и TVP. Таким образом, вызов хранимых процедур с оптимизированными для памяти, возвращающими табличное значение параметрами и компилируемых в собственном коде хранимых процедур работает так же, как и вызов интерпретируемых хранимых процедур с записанными на диск, возвращающими табличное значение параметрами.  
  
## <a name="temp-table-replacement"></a>Замена таблицы #temp  
 В следующем примере показаны оптимизированные для памяти табличные типы и табличные переменные в качестве замены таблиц #temp, которые являются локальными по отношению к хранимой процедуре.  
  
```sql  
-- Using SQL procedure and temp table  
CREATE TABLE #tempTable (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
  
CREATE PROCEDURE sqlProc  
AS  
BEGIN  
  TRUNCATE TABLE #tempTable  
  
  INSERT #tempTable VALUES (1)  
  INSERT #tempTable VALUES (2)  
  INSERT #tempTable VALUES (3)  
  SELECT * FROM #tempTable  
END  
GO  
  
-- Using natively compiled stored procedure and table variable  
CREATE TYPE TT AS TABLE (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
GO  
  
CREATE PROCEDURE NCSPProc  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @tableVariable TT  
  INSERT @tableVariable VALUES (1)  
  INSERT @tableVariable VALUES (2)  
  INSERT @tableVariable VALUES (3)  
  SELECT c FROM @tableVariable  
END  
GO  
```  
  
## <a name="creating-a-single-result-set"></a>Создание одного результирующего набора  
 В следующем примере показано, как сохранить промежуточные результаты и создать единый результирующий набор для нескольких запросов в компилируемых в собственном коде хранимых процедурах. В примере вычисляется соединение `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`.  
  
```sql  
CREATE DATABASE hk  
GO  
ALTER DATABASE hk ADD FILEGROUP hk_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE hk ADD FILE( NAME = 'hk_mod' , FILENAME = 'c:\data\hk_mod') TO FILEGROUP hk_mod;  
  
USE hk  
GO  
  
CREATE TYPE tab1 AS TABLE (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON)  
  
CREATE TABLE dbo.t1 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
CREATE TABLE dbo.t2 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
  
INSERT INTO dbo.t1 VALUES (1), (2)  
INSERT INTO dbo.t2 VALUES (3), (4)  
GO  
  
CREATE PROCEDURE dbo.p1  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS  
  BEGIN ATOMIC WITH ( TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english' )  
  
    DECLARE @t dbo.tab1  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t1;  
  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t2;  
  
    SELECT c1 FROM @t;  
  END  
GO  
  
EXEC dbo.p1  
GO  
```  
  
## <a name="memory-consumption-for-table-variables"></a>Потребление памяти для табличных переменных  
 Потребление памяти для табличных переменных такое же, как для таблиц, оптимизированных для памяти, за исключением некластеризованных индексов. При вставке большого количества строк в переменные таблиц, оптимизированных для памяти, с некластеризованными индексами, если ключи индексов при этом большие, переменные этих таблиц занимают непропорционально большое количество памяти. Некластеризованные индексы для больших табличных переменных требуют пропорционально больше памяти, необходимой при одинаковом количестве строк, вставляемых в таблицу (больше памяти для страниц индекса), чем некластеризованный индекс.  
  
 Память для табличных переменных состоит из пула ресурсов регулятора ресурсов базы данных.  
  
 В отличие от оптимизированных для памяти таблиц, память, потребляемая табличными переменными (включая удаленные строки), освобождается, когда табличная переменная покидает область действия.  
  
 Память учитывается как часть одного потребителя памяти PGPOOL базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка Transact-SQL для выполняющейся в памяти OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  