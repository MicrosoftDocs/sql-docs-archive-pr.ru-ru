---
title: Реализация оператора CASE | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2f82db01-da7e-4a7d-8bc0-48b245e6f768
author: rothja
ms.author: jroth
ms.openlocfilehash: 27059cc09d5507bf2548b23b60f3c2f485c3fe36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738387"
---
# <a name="implementing-a-case-statement"></a>Реализация инструкции CASE
  Инструкции CASE не поддерживаются в скомпилированных в собственном коде хранимых процедурах. В следующем примере показан способ реализации функциональности инструкции CASE в скомпилированной в собственном коде хранимой процедуре.  
  
 В примерах используется табличная переменная для построения одного результирующего набора, который подходит для обработки лишь ограниченного количества строк, поскольку предусматривает создание дополнительных копий строк данных.  
  
 Необходимо проверить производительность этого временного решения, чтобы убедиться в том, что оно работает в соответствии с ожиданиями.  
  
```  
-- original query  
SELECT   
   SalesOrderID,   
   CASE (OnlineOrderFlag)   
   WHEN 1 THEN N'Order placed online by customer'  
   ELSE N'Order placed by sales person'  
   END  
FROM Sales.SalesOrderHeader_inmem  
  
--  workaround for CASE in natively compiled stored procedures  
--  use a table for the single resultset  
CREATE TYPE dbo.SOHOnlineOrderResult AS TABLE  
(  
   SalesOrderID uniqueidentifier not null index ix_SalesOrderID,  
     OrderFlag nvarchar(100) not null  
) with (memory_optimized=on)  
go  
  
-- natively compiled stored procedure that includes the query  
CREATE PROCEDURE dbo.usp_SOHOnlineOrderResult  
   WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
   AS BEGIN ATOMIC WITH  
      (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE=N'us_english')  
  
   -- table variable for creating the single resultset  
   DECLARE @result dbo.SOHOnlineOrderResult  
  
   -- CASE OnlineOrderFlag=1  
   INSERT @result   
   SELECT SalesOrderID, N'Order placed online by customer'  
      FROM Sales.SalesOrderHeader_inmem  
      WHERE OnlineOrderFlag=1  
  
   -- ELSE  
   INSERT @result   
   SELECT SalesOrderID, placed by sales person'  
      FROM Sales.SalesOrderHeader_inmem  
      WHERE OnlineOrderFlag!=1  
  
   -- return single resultset  
   SELECT SalesOrderID, OrderFlag FROM @result  
END  
GO  
  
EXEC dbo.usp_SOHOnlineOrderResult  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Конструкции языка Transact-SQL, не поддерживаемые в выполняющейся в памяти OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
