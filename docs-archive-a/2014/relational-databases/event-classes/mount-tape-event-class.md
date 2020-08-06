---
title: Класс событий Mount Tape | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Mount Tape event class
ms.assetid: 4c595e0a-d968-47d3-a84f-9b6857342671
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8298df4bfd0eaa91cf788fedbffe4e9b2a1389de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665353"
---
# <a name="mount-tape-event-class"></a>Mount Tape, класс событий
  Класс событий Mount Tape происходит при получении запроса на монтирование ленты. Используйте данный класс событий для отслеживания запросов монтирования ленты и их успешного или неуспешного завершения.  
  
## <a name="mount-tape-event-class-data-columns"></a>Столбцы данных класса событий Mount Tape  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данный столбец заполняется значениями, переданными приложением.|10|Да|  
|ClientProcessID|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для указанного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|имя_базы_данных|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|Duration|`bigint`|Длительность события (в микросекундах).|13|Да|  
|EndTime|`datetime`|Для событий запроса на подключение — время ожидания подключения, если этот срок истек; в противном случае — время самого события (в этом случае StartTime содержит время соответствующего запроса на подключение).|15|Да|  
|EventClass|`int`|Тип события = 195.|27|Нет|  
|EventSequence|`int`|Порядковый номер указанного события в запросе.|51|Нет|  
|EventSubClass|`int`|Тип подкласса события.<br /><br /> 1 = запрос подключения ленты<br /><br /> 2 = завершение подключения ленты<br /><br /> 3 = Отмена подключения ленты.|21|Да|  
|GroupID|`int`|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LoginName|`nvarchar`|Имя учетной записи пользователя (имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа безопасности или [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетные данные входа Windows в формате домен \\ *имя_пользователя*).|11|Да|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|ServerName|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|TextData|`ntext`|*имя физического устройства* [ ( *имя логического устройства* ) ]. Имя логического устройства отображается только в том случае, если оно определено в представлении каталога sys.backup_devices.|1|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Резервное копирование и восстановление баз данных SQL Server](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
