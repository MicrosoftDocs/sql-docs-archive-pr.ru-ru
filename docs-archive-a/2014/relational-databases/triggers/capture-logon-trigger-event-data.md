---
title: Данные о захвате событий триггера входа | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
ms.openlocfilehash: b11323702d7468d07783b4d1c763dba691479d9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668169"
---
# <a name="capture-logon-trigger-event-data"></a>Захват данных событий триггера входа
  XML-данные о событиях LOGON для использования внутри триггеров входа могут быть захвачены с использованием функции [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) . Для события LOGON возвращается следующая схема данных событий:  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 Содержит `LOGON`.  
  
 `<PostTime>`  
 Содержит время запроса на установление сеанса.  
  
 `<SID>`  
 Содержит закодированный в base 64-битовый бинарный поток идентификационного номера безопасности (SID) для указанного имени входа.  
  
 `<ClientHost>`  
 Содержит имя узла клиента, с которого устанавливается подключение. Если имя сервера совпадает с именем клиента, то значение по умолчанию — «`<local_machine>`». Иначе значение равно IP-адресу клиента.  
  
 `<IsPooled>`  
 `1` , если соединение повторно используется с помощью пула соединений. В противном случае — значение `0`.  
  
  
