---
title: Прокрутка и выборка строк | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 97586f82ddddb79581b0f9c027aa60d7822b472c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739899"
---
# <a name="scrolling-and-fetching-rows"></a>Прокрутка и выборка строк
  Чтобы можно было использовать прокручиваемый курсор в приложение ODBC, необходимо выполнить следующие действия.  
  
-   Установите возможности курсора с помощью [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Откройте курсор с помощью **SQLExecute** или **SQLExecDirect**.  
  
-   Прокрутите и извлеките строки с помощью **SQLFetch** или [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).  
  
 Одновременно **SQLFetch** и **склфетчсролл** могут получать блоки строк за раз. Число возвращаемых строк задается с помощью **SQLSetStmtAttr** для установки параметра SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Приложения ODBC могут использовать **SQLFetch** для выборки однопроходного курсора.  
  
 **SQLFetchScroll** используется для прокрутки курсора. **SQLFetchScroll** поддерживает выборку следующих, предыдущих, первых и последних наборов строк в дополнение к относительным выборам (получение строк набора строк *n* из начала текущего набора строк) и абсолютная выборка (выборка набора строк, начиная со строки *n*). Если *n* является отрицательным в абсолютной выборки, строки учитываются с конца результирующего набора. Абсолютная выборка строки -1 означает, что будет возвращен набор строк, начинающийся с последней строки результирующего набора.  
  
 Приложения, использующие **SQLFetchScroll** только для возможностей блочных курсоров, таких как отчеты, скорее всего, будут проходить через результирующий набор один раз, используя только параметр для выборки следующего набора строк. С другой стороны, приложения на основе экрана могут воспользоваться всеми возможностями **SQLFetchScroll**. Если приложение устанавливает размер набора строк равным количеству строк, отображаемым на экране, и привязывает буферы экрана к результирующему набору, он может перевести операции полосы прокрутки непосредственно в вызовы **SQLFetchScroll**.  
  
|Операция полосы прокрутки|Параметр прокрутки SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|На страницу вверх|SQL_FETCH_PRIOR|  
|На страницу вниз|SQL_FETCH_NEXT|  
|На строку вверх|SQL_FETCH_RELATIVE с Фетчоффсет, равным-1|  
|На строку вниз|SQL_FETCH_RELATIVE с FetchOffset, равным 1|  
|Ползунок вверх|SQL_FETCH_FIRST|  
|Ползунок вниз|SQL_FETCH_LAST|  
|Случайное положение ползунка|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание закладок строк в ODBC](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Использование курсоров &#40;ODBC&#41;](using-cursors-odbc.md)  
  
  
