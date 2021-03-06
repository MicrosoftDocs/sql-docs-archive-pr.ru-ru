---
title: Объект транспортного объекта SQL Server, брокера и DBM | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker / DBM Transport object
- SQLServer:Broker/DBM Transport
ms.assetid: eddb60b6-20a9-416c-adf3-4bc1687944fa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d44aa5b316a076f759d65a17f7e15c0a9ede786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667037"
---
# <a name="sql-server-broker-and-dbm-transport-object"></a>SQL Server, объект Broker и DBM Transport
  В объекте производительности **Broker/DBM Transport** содержатся счетчики производительности, сообщающие сведении о работе в сети служб Service Broker и зеркального отображения баз данных. В следующей таблице перечислены счетчики этого объекта.  
  
|Счетчик «SQL Server: Service Broker / транспорт зеркального отображения баз данных»|Описание|  
|------------------------------------------------|-----------------|  
|**Текущее число полученных байт**|Этот счетчик сообщает количество байт, считанных текущими запущенными транспортными операциями приема.|  
|**Текущее число отправленных байт**|Этот счетчик сообщает количество байт во фрагментах сообщений, которые в текущей момент посылаются по сети.|  
|**Текущее число отправленных фрагментов сообщений**|Этот счетчик сообщает общее число фрагментов сообщений, которые в текущей момент посылаются по сети.|  
|**Отправлено фрагментов сообщений P1/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 1, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P2/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 2, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P3/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 3, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P4/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 4, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P5/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 5, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P6/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 6, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P7/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 7, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P8/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 8, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P9/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 9, отправляемых по сети за одну секунду.|  
|**Отправлено фрагментов сообщений P10/с**|Этот счетчик содержит число фрагментов сообщений с приоритетом 10, отправляемых по сети за одну секунду.|  
|**Средний размер фрагмента отправляемого сообщения**|Этот счетчик сообщает средний размер фрагментов сообщений, посылаемых по сети.|  
|**Отправка фрагментов сообщений в сек.**|Этот счетчик сообщает число фрагментов сообщений всех приоритетов, посылаемых по сети за одну секунду.|  
|**Получение фрагментов сообщений в сек.**|Этот счетчик сообщает число фрагментов сообщений, принимаемых по сети за одну секунду.|  
|**Средний размер фрагмента получаемого сообщения**|Этот счетчик сообщает средний размер фрагментов сообщений, принимаемых по сети.|  
|**Число открытых соединений**|Этот счетчик сообщает число сетевых соединений, открытых на данный момент компонентом Service Broker.|  
|**Текущее число отложенных полученных байт**|Этот счетчик сообщает количество байт, содержащееся во фрагментах сообщений, принятых по сети, но еще не помещенных в очередь или не отмененных.|  
|**Текущее число отложенных отправленных байт**|Этот счетчик сообщает общее число байт во фрагментах сообщений, которые готовы к отправке по сети.|  
|**Текущее число отложенных полученных фрагментов**|Этот счетчик сообщает количество фрагментов сообщений, принятых по сети, но еще не помещенных в очередь или не отмененных.|  
|**Текущее число отложенных отправленных фрагментов**|Этот счетчик сообщает общее число фрагментов сообщений, готовых к отправке по сети.|  
|**Общее число полученных байт**|Этот счетчик сообщает общее число байт, принятых по сети конечными точками компонента Service Broker и зеркального отображения.|  
|**Получение байт в сек.**|Этот счетчик сообщает число байт, принимаемых по сети конечными точками компонента Service Broker и зеркального отображения за одну секунду.|  
|**Средняя длина получаемых данных**|Этот счетчик сообщает среднее число байт в транспортных операциях приема.|  
|**Получений данных в сек.**|Этот счетчик сообщает количество транспортных операций ввода-вывода по приему, выполняемых транспортным слоем Service Broker / зеркального отображения за одну секунду. Обратите внимание, что транспортная операция приема может содержать более одного фрагмента сообщения.|  
|**Общее число отправленных байт**|Этот счетчик сообщает общее число байтов, отправленных по сети конечными точками компонента Service Broker и зеркального отображения.|  
|**Отправка байт в сек.**|Этот счетчик сообщает число байтов, отправляемых по сети конечными точками компонента Service Broker и зеркального отображения за одну секунду.|  
|**Средняя длина отправляемых данных**|Этот счетчик сообщает среднее число байт для каждой транспортной операции отправки. Обратите внимание, что транспортная операция отправки может содержать более одного фрагмента сообщения.|  
|**Количество отправок данных в сек.**|Этот счетчик сообщает количество выполненных транспортных операций ввода-вывода по отправке за одну секунду. Обратите внимание, что транспортная операция отправки может содержать более одного фрагмента сообщения.|  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_broker_forwarded_messages (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-forwarded-messages-transact-sql)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](monitor-resource-usage-system-monitor.md)  
  
  
