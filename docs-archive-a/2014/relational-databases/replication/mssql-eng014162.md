---
title: MSSQL_ENG014162 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014162 error
ms.assetid: a15eef3f-219f-45d3-8286-6a864c85a723
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 78c6eb13087a7f7d5b2711af4484df7a384d7835
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668809"
---
# <a name="mssql_eng014162"></a>MSSQL_ENG014162
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14162|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Задан порог [%s:%s] для публикации [%s]. Убедитесь в том, что агент слияния запущен и соответствует предъявляемому требованию.|  
  
## <a name="explanation"></a>Объяснение  
 При репликации можно включить предупреждения для ряда условий. Сюда входит превышение определенного промежутка времени, необходимого для синхронизации изменений между издателем и подписчиком слияния. Для соединений по локальной сети и коммутируемых соединений можно указать разные значения времени.  
  
 Когда предупреждение включается при помощи монитора репликации или процедуры [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), необходимо указать пороговое значение, определяющее, в какой момент выдается предупреждение. При достижении или превышении порогового значения предупреждение отображается в мониторе репликации, а в журнал событий Windows записывается событие. Достижение порогового значения также может приводить к выдаче предупреждения агента SQL Server. Дополнительные сведения см. в статьях [Настройка пороговых значений и предупреждений в мониторе репликации](monitor/set-thresholds-and-warnings-in-replication-monitor.md). и [Наблюдение за репликацией программным образом](monitoring-replication.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Если подписка превышает пороговое значение промежутка времени, необходимо определить, является ли это проблемой производительности системы или свидетельствует о необходимости изменить пороговое значение. После настройки репликации разработайте базовый уровень производительности, позволяющий определить работу репликации при рабочей нагрузке, типичной для ваших приложений и топологии. Включите в базовый уровень продолжительность синхронизации, чтобы правильно выбрать подходящее пороговое значение.  
  
 Если пороговое значение выбрано верно, но превышение порогового значения все же наблюдается, то нужно определить, где в системе находится узкое место по производительности. Дополнительные сведения о мониторинге и устранении неполадок, влияющих на производительность репликации, см. в следующих разделах:  
  
-   [Наблюдение за производительностью с помощью монитора репликации](monitor/monitor-performance-with-replication-monitor.md) (в частности, раздел "Просмотр подробных сведений о производительности синхронизации для репликации слиянием").  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  