---
title: Использование инструкции try.. Перехватывать хранимые процедуры, скомпилированные в собственном виде | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f730e70c-4f92-411d-9984-289e241e43ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d1f13a8fab6293eedc77a7ce93d86618a33d8c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732001"
---
# <a name="using-trycatch-in-natively-compiled-stored-procedures"></a>Использование блоков try..catch в хранимых процедурах, скомпилированных в собственном коде
  Внутри скомпилированной хранимой процедуры можно использовать блоки try..catch. Поддерживаются приведенные ниже конструкции.  
  
-   ERROR_LINE  
  
-   ERROR_MESSAGE  
  
-   ERROR_NUMBER  
  
-   ERROR_PROCEDURE  
  
-   ERROR_SEVERITY  
  
-   ERROR_STATE  
  
```sql  
CREATE PROCEDURE test_try_catch  
with native_compilation, schemabinding, execute as owner   
as  
begin atomic with (transaction isolation level = snapshot, language = N'us_english')  
  
  BEGIN TRY  
    -- generate error  
    declare @i int = 1,  
    @j int = 0  
    select @i/@j  
  END TRY  
  BEGIN CATCH  
    -- Execute error retrieval routine.  
    SELECT  
    ERROR_SEVERITY() AS ErrorSeverity  
    ,ERROR_STATE() AS ErrorState  
    ,ERROR_PROCEDURE() AS ErrorProcedure  
    ,ERROR_LINE() AS ErrorLine  
    ,ERROR_MESSAGE() AS ErrorMessage  
  END CATCH  
end  
go  
  
exec test_try_catch  
go  
```  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном коде хранимые процедуры](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
