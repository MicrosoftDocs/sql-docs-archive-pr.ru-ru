---
title: Обработка результатов (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a22e9d7280f88de7799c31d2d0611e5299043d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738294"
---
# <a name="process-results-odbc"></a>Обработка результатов (ODBC)
    
### <a name="to-process-results"></a>Обработка результатов  
  
1.  Получите сведения о результирующем наборе.  
  
2.  Если используются привязанные столбцы, вызовите функцию [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) для каждого столбца, чтобы привязать буфер программы к столбцу.  
  
3.  Для каждой строки в результирующем наборе сделайте следующее.  
  
    -   Вызовите функцию [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401), чтобы получить следующую строку.  
  
    -   Если используются привязанные столбцы, используйте данные, теперь доступные в привязанных буферах столбцов.  
  
    -   Если используются непривязанные столбцы, вызовите функцию [SQLGetData](../native-client-odbc-api/sqlgetdata.md) один или несколько раз, чтобы получить данные для непривязанных столбцов после последнего привязанного столбца. Вызовы функции `SQLGetData` должны следовать по возрастанию номера столбца.  
  
    -   Получение данных из столбца типа text или image производится многократным вызовом функции `SQLGetData`.  
  
4.  Когда функция [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) указывает конец результирующего набора, возвращая SQL_NO_DATA, вызовите функцию [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md), чтобы определить, доступен ли другой результирующий набор.  
  
    -   Если вернулось значение SQL_SUCCESS, то доступен другой результирующий набор.  
  
    -   Если вернулось значение SQL_NO_DATA, то больше нет результирующих наборов.  
  
    -   Если вернулось значение SQL_SUCCESS_WITH_INFO или SQL_ERROR, вызовом функции [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) определите, есть ли выходные данные от инструкции PRINT или RAISERROR.  
  
         Если в качестве выходных параметров используются привязанные параметры инструкции или возвращаемое значение хранимой процедуры, используйте данные, имеющиеся в буферах привязанного параметра. Кроме того, если используются привязанные параметры, при каждом вызове функции [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) или [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) инструкция SQL будет выполняться *S* раз, где *S* — количество элементов в массиве привязанных параметров. Это значит, что придется обработать *S* наборов результатов, каждый из которых содержит все результирующие наборы, выходные параметры и коды возврата, обычно возвращаемые при исполнении отдельной инструкции SQL.  
  
    > [!NOTE]  
    >  Если результирующий набор содержит вычисляемые строки, каждая вычисляемая строка доступна как отдельный результирующий набор. Эти вычисляемые результирующие наборы находятся среди обычных строк, разбивая их на несколько результирующих наборов.  
  
5.  Можно также вызвать функцию [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) с SQL_UNBIND, чтобы освободить все буферы связанных столбцов.  
  
6.  Если есть еще один результирующий набор, перейдите к шагу 1.  
  
> [!NOTE]  
>  Чтобы отменить обработку результирующего набора прежде, чем функция [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) вернет значение SQL_NO_DATA, вызовите функцию [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).  
  
## <a name="see-also"></a>См. также:  
 [Разделы руководства по обработке результатов &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  