---
title: Установка параметров курсора (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: rothja
ms.author: jroth
ms.openlocfilehash: 877c2596c87ce50295a15912493661c6dd4e0305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739866"
---
# <a name="set-cursor-options-odbc"></a>Указание параметров курсора (ODBC)
  Чтобы задать параметры курсора, вызовите [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать или [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) , чтобы получить параметры инструкции, управляющие поведением курсора.  
  
|*Attribute (XElement Dynamic Property)* (Attribute (динамическое свойство XElement))|Что определяет|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|Однопроходный, статический, динамический или управляемый набором ключей тип курсора|  
|SQL_ATTR_CONCURRENCY|Параметр управления параллелизмом – только для чтения, блокирующий, оптимистичный с использованием отметок времени или оптимистичный с использованием значений|  
|SQL_ATTR_ROW_ARRAY_SIZE|Количество строк, получаемых в каждой выборке|  
|SQL_ATTR_CURSOR_SENSITIVITY|Курсор, который отображает или не отображает обновления строк курсора, выполняемые в других соединениях|  
|SQL_ATTR_CURSOR_SCROLLABLE|Курсор, который может прокручиваться вперед и назад|  
  
 Значения по умолчанию для этих атрибутов (однопроходный, только для чтения, размер набора строк, равный 1) не используют серверные курсоры. Для использования серверных курсоров по крайней мере одному из этих атрибутов должно быть задано значение, отличное от значения по умолчанию, а выполняемая инструкция должна быть единственной инструкцией SELECT или хранимой процедурой, содержащей единственную инструкцию SELECT. При использовании серверных курсоров инструкции SELECT не могут использовать предложения, не поддерживаемые серверными курсорами: ВЫЧИСЛЕНие, ВЫЧИСЛЕНие по, для просмотра и в.  
  
 Используемым типом курсора можно управлять, установив SQL_ATTR_CURSOR_TYPE и SQL_ATTR_CONCURRENCY или установив SQL_ATTR_CURSOR_SENSITIVITY и SQL_ATTR_CURSOR_SCROLLABLE. Не следует смешивать два метода задания режима работы курсоров.  
  
## <a name="example"></a>Пример  
 В следующем образце выделяется дескриптор инструкции, устанавливается динамический тип курсора и оптимистический параллелизм с управлением версиями строк, а затем выполняется инструкция SELECT.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>Пример  
 В следующем образце выделяется дескриптор инструкции, устанавливается прокручиваемый, чувствительный курсор, а затем выполняется инструкция SELECT.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции по выполнению запросов &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
