---
title: MSSQLSERVER_1793 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54172adb957c3cbc1dbc221d1cae2a583830a1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731669"
---
# <a name="mssqlserver_1793"></a>MSSQLSERVER_1793
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1793|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|FILESTREAM_BASEDATA_NEED_SAME_PARTITION|  
|Текст сообщения|Не удается удалить «%.*ls», поскольку для данных FILESTREAM не указана схема секционирования.|  
  
## <a name="explanation"></a>Объяснение  
 Это сообщение возникает при попытке удалить кластеризованный индекс для таблицы, которая содержит данные FILESTREAM, указав предложение **MOVE TO** для базовых данных, но не указав предложение **FILESTREAM_ON** для данных FILESTREAM.  
  
## <a name="user-action"></a>Действие пользователя  
 При удалении кластеризованного индекса для таблицы, которая содержит данные FILESTREAM, используйте один из следующих вариантов.  
  
-   Укажите оба предложения: **MOVE TO** для базовых данных и **FILESTREAM_ON** для данных FILESTREAM.  
  
-   Не указывайте ни одно из предложений **MOVE TO** для базовых данных или **FILESTREAM_ON** для данных FILESTREAM.  
  
 Следующий пример заканчивается ошибкой, потому что схема секционирования указана для базовых данных, но не указана для данных FILESTREAM.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
 Следующий пример завершается успешно, так как для базовых данных указано предложение **MOVE TO**, а для данных FILESTREAM — предложение **FILESTREAM_ON**.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
 Следующий пример также завершается успешно, так как не указано ни одно из предложений: **MOVE TO** для базовых данных или **FILESTREAM_ON** для данных FILESTREAM.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
  
