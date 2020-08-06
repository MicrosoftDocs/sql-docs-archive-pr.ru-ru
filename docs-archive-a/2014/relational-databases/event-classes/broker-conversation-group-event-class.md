---
title: Класс событий Broker:Conversation Group | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Conversation Group event class
ms.assetid: 6595bef6-9d40-42eb-a934-735622dd23fb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 00fa44abc6d9d374a99fc92e9b3e86f719afc07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664901"
---
# <a name="brokerconversation-group-event-class"></a>Broker:Conversation Group, класс событий
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует событие **Broker:Conversation Group** , когда компонент Service Broker создает новую или удаляет существующую группу сообщений.  
  
## <a name="brokerconversation-group-event-class-data-columns"></a>Класс событий «Broker:Conversation Group»  
  
|Столбец данных|Тип|Description|Номер столбца|Фильтруемый|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|`int`|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|`int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**EventClass**|`int`|Тип захваченного класса событий. В случае класса событий **Broker:Conversation Group** это значение всегда равно **136**.|27|Нет|  
|**EventSequence**|`int`|Порядковый номер этого события.|51|нет|  
|**EventSubClass**|`nvarchar`|Тип подкласса событий, предоставляющий дополнительные сведения о каждом классе события. Данный столбец может содержать следующие значения.<br /><br /> **Create** (создать). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создал новую группу сообщений.<br /><br /> **Drop**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удалил группу сообщений.|21|Да|  
|**GUID**|`uniqueidentifier`|Идентификатор группы сообщений, которую описывает данное событие.|54|нет|  
|**HostName**|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|нет|  
|**LoginSid**|`image`|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|`nvarchar`|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**ServerName**|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемого трассировке.|26|нет|  
|**SPID**|`int`|Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**StartTime**|`datetime`|Время начала события, если доступно.|14|Да|  
|**TransactionID**|`bigint`|Назначенный системой идентификатор транзакции.|4|нет|  
  
  
