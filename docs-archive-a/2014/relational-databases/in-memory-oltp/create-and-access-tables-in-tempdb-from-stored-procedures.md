---
title: Создание таблиц в базе данных TempDB и доступ к ним из хранимых процедур, скомпилированных в собственном режиме | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
author: rothja
ms.author: jroth
ms.openlocfilehash: a0bd2b4863cc3c257cd260bf381ebb3b890af219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749904"
---
# <a name="creating-and-accessing-tables-in-tempdb-from-natively-compiled-stored-procedures"></a>Создание и обращение к таблицам в базе данных TempDB из скомпилированных в собственном коде хранимых процедур
  Создание и обращение к таблицам в базе данных TempDB из скомпилированных в собственном коде хранимых процедур не поддерживается. Вместо этого используйте табличные типы и табличные переменные. Пример:  
  
```sql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = 'english'  
)  
  -- declare table variables for the list of orders   
  DECLARE @Input dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @Input SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## <a name="see-also"></a>См. также:  
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Конструкции языка Transact-SQL, не поддерживаемые в выполняющейся в памяти OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
