---
title: SQLFetchScroll | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: rothja
ms.author: jroth
ms.openlocfilehash: eecf9714a97577ff490b642cee5b9c380333e40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657791"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
  Функция**SQLFetchScroll** возвращает приложению один набор строк данных. Размер набора строк задается с помощью функции [SQLSetStmtAttr](sqlsetstmtattr.md). Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает все определенные инструкции выборки (например, SQL_FETCH_RELATIVE) со следующими ограничениями.  
  
-   Если для инструкции определен однопроходный курсор, необходимо использовать инструкцию SQL_FETCH_NEXT, а попытки произвести выборку любым другим способом приведут к ошибке.  
  
-   Инструкция SQL_FETCH_BOOKMARK поддерживается только для статических курсоров и курсоров, управляемых набором ключей.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLFetchScroll улучшенных функций даты и времени  
 Значения результирующих столбцов типов даты-времени преобразуются, как описано в статье [преобразования из SQL в C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Поддержка функцией SQLFetchScroll больших определяемых пользователем типов CLR  
 Функция**SQLFetchScroll** поддерживает большие определяемые пользователем типы данных CLR. Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLFetchScroll](https://go.microsoft.com/fwlink/?LinkId=59343)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
