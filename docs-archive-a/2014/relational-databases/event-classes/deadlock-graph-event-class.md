---
title: Класс событий Deadlock Graph | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Deadlock Graph event class
ms.assetid: 20f92233-c912-4382-8993-8e2e23d03fbe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 078e125136643958a1cd9203d07f632c3023a9de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668882"
---
# <a name="deadlock-graph-event-class"></a>Deadlock Graph, класс событий
  Класс событий **Deadlock Graph** предоставляет XML-описание взаимоблокировки. Этот класс происходит одновременно с классом событий **Lock:Deadlock** .  
  
## <a name="deadlock-graph-event-class-data-columns"></a>Столбцы данных класса событий Deadlock Graph  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Тип события = 148.|27|нет|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|нет|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский. Значение всегда равно 1 для этого события.|60|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо имя входа безопасности [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате "ДОМЕН\имя_пользователя"). Это значение всегда равно системному пользователю для данного события.|11|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере. Это значение всегда равно идентификатору безопасности пользователя системы для данного события.|41|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время обнаружения взаимоблокировки.|14|Да|  
|**TextData**|**ntext**|XML-описание взаимоблокировки.|1|Да|  
|**TransactionID**|**bigint**|Не используется.|4|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Класс событий Lock:Deadlock](lock-deadlock-event-class.md)  
  
  
