---
title: Опрос серверов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6370e53083d2cf818e8c8b09752d49e092755a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665755"
---
# <a name="poll-servers"></a>Опрос серверов
  При использовании системы многосерверного администрирования целевые серверы периодически связываются с главным сервером для загрузки на него данных о выполненных заданиях и для получения новых заданий. Процесс взаимодействия с главным сервером называется *опросом сервера* и выполняется через равные *интервалы опроса.*  
  
## <a name="polling-intervals"></a>Интервалы опроса  
 Интервал опроса (равный по умолчанию одной минуте) определяет частоту, с которой целевой сервер будет связываться с главным сервером, чтобы загрузить инструкции и передать на него результаты выполнения задания.  
  
 Опрашивая главный сервер, целевой сервер считывает назначенные ему операции из таблицы **sysdownloadlist** базы данных **msdb** . Эти операции контролируют многосерверные задания и различные аспекты работы целевого сервера. Примерами таких операций могут служить удаление задания, вставка задания, запуск задания и обновление интервала опроса, заданного на целевом сервере.  
  
 Операции можно опубликовать в таблице **sysdownloadlist** двумя способами:  
  
-   явно, вызвав хранимую процедуру **sp_post_msx_operation** ;  
  
-   неявно, используя другие хранимые процедуры задания.  
  
 При изменении расписания выполнения многосерверного задания или шагов задания с помощью хранимых процедур задания или при использовании объектов SQL-DMO (SQL Distributed Management Objects) для контроля многосерверных заданий выполните после изменения следующую команду:  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 Это обеспечивает синхронизацию целевых серверов с текущим определением задания.  
  
 В следующих ситуациях явно публиковать операции не требуется:  
  
-   при использовании среды Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для контроля многосерверных заданий;  
  
-   при использовании хранимых процедур заданий, не изменяющих расписания выполнения заданий и шагов заданий.  
  
 **Принудительный опрос главного сервера целевым сервером**  
  
-   [Среда SQL Server Management Studio](force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [Управление событиями](manage-events.md)  
  
  
