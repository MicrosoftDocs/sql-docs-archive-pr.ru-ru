---
title: Выделение маркера оператора | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: rothja
ms.author: jroth
ms.openlocfilehash: fac0802b474f38f6a6c314dd727fa335d14598d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750883"
---
# <a name="allocating-a-statement-handle"></a>Выделение дескриптора инструкции
  Прежде чем приложение сможет выполнить инструкцию, оно должно выделить дескриптор инструкции. Для этого вызывается **функцию SQLAllocHandle** с параметром *параметром handletype* , для которого задано значение SQL_HANDLE_STMT и *инпусандле* указывает на маркер подключения.  
  
 Атрибуты инструкции представляют собой характеристики дескриптора инструкции. Атрибуты образца инструкции могут включать закладки и курсор для использования с результирующим набором инструкции. Атрибуты инструкции задаются с помощью [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md), а их текущие параметры извлекаются с использованием [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md). Приложению не обязательно устанавливать атрибуты инструкции, все они имеют значения по умолчанию, а некоторые зависят от драйвера.  
  
 При использовании некоторых инструкций ODBC и параметров соединения следует соблюдать осторожность. Вызов [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с *параметром fOption* , установленным в значение SQL_ATTR_LOGIN_TIMEOUT, определяет время ожидания приложения при попытке соединения, при ожидании установления соединения (0 указывает бесконечное время ожидания). Сайты с низким временем ответа могут задать большее значение, чтобы дать приложению достаточно времени для установления соединения. Тем не менее этот интервал должен быть достаточно низким, чтобы дать пользователю ответ в том случае, если драйвер не может установить соединение.  
  
 Вызов **SQLSetStmtAttr** с *параметром fOption* , установленным в значение SQL_ATTR_QUERY_TIMEOUT задает интервал времени ожидания запроса для защиты сервера и пользователя от длительных запросов.  
  
 Вызов **SQLSetStmtAttr** с *параметром fOption* , для которого задано значение SQL_ATTR_MAX_LENGTH ограничивает объем данных **текста** и **изображений** , которые может получить отдельная инструкция. Вызов **SQLSetStmtAttr** с *параметром fOption* , установленным в SQL_ATTR_MAX_ROWS, также ограничивает набор строк первыми *n* строками, если это требуется для всего приложения. Обратите внимание, что по значению SQL_ATTR_MAX_ROWS драйвер выполняет инструкцию SET ROWCOUNT на сервере. Это влияет на все [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции, включая триггеры и обновления.  
  
 Соблюдайте осторожность при установке этих параметров. Лучше, если все дескрипторы инструкций в дескрипторе соединения будут иметь одинаковые значения SQL_ATTR_MAX_LENGTH и SQL_ATTR_MAX_ROWS. Если драйвер переключается с одного дескриптора инструкции на другой с разными значениями этих параметров, то он должен для изменения значений формировать соответствующие инструкции SET TEXTSIZE и SET ROWCOUNT. Драйвер не может поместить эти инструкции в один пакет как пользовательские инструкции SQL, поскольку пользовательские инструкции SQL могут содержать инструкцию, которая должна быть первой в пакете. Драйвер должен отправлять инструкции SET TEXTSIZE и SET ROWCOUNT в отдельных пакетах, что приводит к появлению дополнительного обращения к серверу.  
  
## <a name="see-also"></a>См. также:  
 [Выполняя запросы &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
