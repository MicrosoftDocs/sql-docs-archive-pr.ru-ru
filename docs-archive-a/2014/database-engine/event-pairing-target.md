---
title: Целевой объект связывания событий | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- pairing target [SQL Server extended events]
- event pairing target
- targets [SQL Server extended events], pairing target
ms.assetid: 3c87dcfb-543a-4bd8-a73d-1390bdf4ffa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a1a6beb1c6996e6e12f16c4555fd9dfcab97617d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732942"
---
# <a name="event-pairing-target"></a>Цель «Попарное разбиение событий»
  Цель «Попарное разбиение событий» устанавливает соответствие между двумя событиями с помощью одного или нескольких столбцов данных, присутствующих в каждом событии. Многие события возникают попарно, например получение и снятие блокировки. После выделения пары событий оба эти события отбрасываются. Исключение парных наборов позволяет легко обнаруживать наличие не снятых блокировок.  
  
 С помощью фильтрации на уровне события цель «Попарное разбиение событий» может использоваться только для сбора событий, не соответствующих заранее установленным условиям.  
  
 При использовании цели «Попарное разбиение событий» разрешается выбирать два сопоставляемых события и последовательность столбцов, предназначенных для установки соответствия. Все столбцы такой последовательности должны иметь одинаковый тип.  
  
 В следующей таблице описаны доступные параметры настройки попарного разбиения событий.  
  
|Параметр|Допустимые значения|Описание|  
|------------|--------------------|-----------------|  
|begin_event|Имя любого события, присутствующего в текущем сеансе.|Имя события, определяющее начальное событие в парной последовательности.|  
|end_event|Имя любого события, присутствующего в текущем сеансе.|Имя события, определяющее завершающее событие в парной последовательности.|  
|begin_matching_columns|Упорядоченный список имен столбцов с разделителями-запятыми.|Столбцы, по которым выполняется установка соответствия.|  
|end_matching_columns|Упорядоченный список имен столбцов с разделителями-запятыми.|Столбцы, по которым выполняется установка соответствия.|  
|begin_matching_actions|Упорядоченный список действий с разделителями-запятыми.|Действия, по которым выполняется установка соответствия.|  
|end_matching_actions|Упорядоченный список действий с разделителями-запятыми.|Действия, по которым выполняется установка соответствия.|  
|respond_to_memory_pressure|Принимает одно из следующих значений:<br /><br /> 0 = не отвечать;<br /><br /> 1 = прекратить добавлять новые несвязанные события к списку при нехватке памяти.|Реакция цели на события памяти. Если значение равно 1, а сервер испытывает недостаток памяти, сохраненные данные о непарных событиях удаляются.|  
|max_orphans||Указывает общее количество непарных событий, которые будут собраны в целевом объекте. После достижения этого предела непарные события удаляются по принципу «первым пришел, первым ушел» (FIFO). По умолчанию равно 10,000.|  
  
 Все данные, связанные с событием, собираются и хранятся для будущей установки соответствия. Кроме того, также собираются данные, добавленные действиями. Собранные данные события хранятся в памяти, а следовательно, их объем ограничен. Это ограничение зависит от объема памяти и активности системы. В качестве параметра указывается не максимальный объем памяти, а объем доступных системных ресурсов. При их недостатке сохраненные непарные события удаляются. Если непарное событие удаляется, соответствующее ему событие появится как непарное.  
  
 Цель «Попарное разбиение событий» сериализует непарные события в формате XML. Этот формат не соответствует ни одной схеме. Он содержит только два типа элементов. **\<unpaired>** Элемент является корнем, за которым следует один. **\<event>** элемент для каждого непарного события, которое в настоящее время отслеживается. **\<event>** Элемент содержит один атрибут, который содержит имя непарного события.  
  
## <a name="adding-the-target-to-a-session"></a>Добавление цели к сеансу  
 Для добавления цели попарного разбиения событий в сеанс расширенных событий следует использовать одну из следующих инструкций при создании или изменении сеанса события:  
  
```  
ADD TARGET package0.pair_matching   
```  
  
 После этого необходимо использовать инструкцию SET для определения начального и конечного событий и выбора действий и столбцов для сопоставления. В следующем примере показан образец синтаксиса для сопоставления пар событий sqlserver.lock_acquired и sqlserver.lock_released.  
  
```  
   ( SET begin_event = 'sqlserver.lock_acquired',  
      begin_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
      end_event = 'sqlserver.lock_released',  
      end_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
   respond_to_memory_pressure = 1)  
```  
  
 Дополнительные сведения см. в разделе [Определение запросов, удерживающих блокировки](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md).  
  
## <a name="reviewing-the-target-output"></a>Просмотр целевого вывода  
 Для просмотра результата цели попарного разбиения событий можно воспользоваться следующим запросом, заменив параметр *session_name* на имя сеанса события.  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 В следующем примере показан выходной формат цели «Попарное разбиение событий».  
  
```  
<unpaired truncated = "0" matchedCount = "[matched count]" memoryPressureDroppedCount = " [lost count]">  
    <event name  = "[event name]" package = "[package]" id= "[event ID value]" version = "[event version]">  
    <data name = "[column name]">   
    <type name = "[column type]" package = "[type package]" />   
    <value>[column value]</value>  
    <text value>[text value]</text>>  
        </data>  
    </event>  
</unpaired>  
```  
  
## <a name="see-also"></a>См. также:  
 [Цели расширенных событий SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
