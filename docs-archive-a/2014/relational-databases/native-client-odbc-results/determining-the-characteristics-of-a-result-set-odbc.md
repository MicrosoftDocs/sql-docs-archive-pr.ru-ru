---
title: Определение характеристик результирующего набора (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], characteristics
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLDescribeCol function
- metadata [ODBC]
- SQLColAttribute function
- SQLNumResultCols function
ms.assetid: 90be414c-04b3-46c0-906b-ae7537989b7d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5957092cdddfbcbce904d9a6483914672565d337
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657755"
---
# <a name="determining-the-characteristics-of-a-result-set-odbc"></a>Определение характеристик результирующего набора (ODBC)
  Метаданные — это данные, описывающие другие данные. Например, метаданные результирующего набора описывают такие характеристики результирующего набора, как количество столбцов, типы данных в этих столбцах, их имена, точность и допустимость значений NULL.  
  
 ODBC сообщает метаданные приложениям с помощью функций каталога API-интерфейса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Драйвер ODBC для собственного клиента реализует многие функции каталога API ODBC в качестве вызовов к соответствующей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] процедуре каталога.  
  
 Метаданные требуются приложениям для большинства операций с результирующими наборами. Например, приложение использует тип данных столбца, чтобы определить, какую переменную привязывать к этому столбцу. Оно использует длину в байтах столбцов с символьными значениями, чтоб определить, сколько места потребуется для отображения данных из этого столбца. Способ определения метаданных для столбца зависит от типа приложения.  
  
 Вертикальные приложения обычно работают со стандартными таблицами и выполняют стандартные операции с этими таблицами. Поскольку метаданные результирующих наборов для таких приложений определяются даже до того, как приложение написано, и управляются разработчиком, они могут быть жестко запрограммированы в приложении. Например, если столбец идентификатора заказа определен в источник данных как 4-байтовое целое число, приложение может всегда привязывать 4-байтовые целые числа к этому столбцу. Если метаданные жестко запрограммированы в приложении, изменения в используемых приложением таблицах обычно подразумевают изменения в коде приложения.  
  
 В обычных приложениях, особенно приложениях, поддерживающих нерегламентируемые запросы, метаданные результирующих наборов обычно неизвестны до времени выполнения.  
  
 Чтобы определить характеристики результирующего набора, приложение может вызвать следующие функции.  
  
-   [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) , чтобы определить, сколько столбцов возвращает запрос.  
  
-   [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) или [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) для описания столбца в результирующем наборе.  
  
 Хорошо спроектированные приложения пишутся с предположением, что результирующий набор неизвестен, и используют для привязки столбцов в результирующем наборе данные, возвращаемые этими функциями. Приложение может вызвать эти функции в любое время после подготовки или выполнения инструкции. Однако для оптимальной производительности приложение должно вызывать **SQLColAttribute**, **SQLDescribeCol**и **SQLNumResultCols** после выполнения инструкции.  
  
 Можно выполнять несколько одновременных вызовов метаданных. Эти процедуры системного каталога, лежащие в основе реализаций API-интерфейса каталога ODBC, могут вызываться драйвером ODBC во время использования им статических серверных курсоров. Это позволяет приложениям одновременно обрабатывать несколько вызовов функций каталога ODBC.  
  
 Если приложение использует определенный набор метаданных более одного раза, может быть полезно кэшировать данные в закрытых переменных после их первого получения. Этот предотвращает последующие вызовы функций каталога ODBC для получения тех же данных, ради которых драйверу приходится многократно обращаться к серверу.  
  
## <a name="see-also"></a>См. также:  
 [Обработка результатов &#40;ODBC&#41;](processing-results-odbc.md)  
  
  