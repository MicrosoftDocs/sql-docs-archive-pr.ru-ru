---
title: Неявные преобразования курсора (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: rothja
ms.author: jroth
ms.openlocfilehash: ff8350c71a853e39ff1d35a1f3fba6e8e1944934
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666559"
---
# <a name="implicit-cursor-conversions-odbc"></a>Неявные преобразования курсора (ODBC)
  Приложения могут запрашивать тип курсора через [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , а затем выполнять инструкцию SQL, которая не поддерживается серверными курсорами запрошенного типа. Вызов **SQLExecute** или **SQLExecDirect** возвращает SQL_SUCCESS_WITH_INFO и **SQLGetDiagRec** возвращает:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 Приложение может определить, какой тип курсора теперь используется, вызвав **SQLGetStmtOption** в значение SQL_CURSOR_TYPE. Преобразование типа курсора применяется только к одной инструкции. Следующие **SQLExecDirect** или **SQLExecute** будут выполняться с использованием параметров курсора исходной инструкции.  
  
## <a name="see-also"></a>См. также:  
 [Сведения о программировании курсора &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  
