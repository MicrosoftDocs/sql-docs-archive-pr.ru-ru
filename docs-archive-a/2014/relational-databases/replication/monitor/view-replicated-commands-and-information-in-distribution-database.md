---
title: Просмотр реплицированных команд и другой информации в базе данных распространителя (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb5850277d685f2ecf6471fa4bf9814579b2843e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750704"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a>Просмотр реплицированных команд и другой информации в базе данных распространителя (программирование репликации на языке Transact-SQL)
  Если используется репликация транзакций, команды транзакций хранятся в базе данных распространителя, пока агент распространителя не передаст их всем подписчикам или пока агент распространителя на подписчике не получит изменения по запросу. Эти ждущие команды в базе данных распространителя можно просматривать программным способом с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Хранимые процедуры репликации (Transact-SQL)](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql).  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>Просмотр реплицируемых команд из всех публикаций транзакций в базе данных распространителя  
  
1.  В базе данных на распространителе выполните процедуру [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>Просмотр реплицируемых команд в базе данных распространителя из определенной статьи или определенной базы данных, опубликованной с помощью репликации транзакций  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)(необязательно). Укажите ** \@ публикацию** и ** \@ статью**. Запомните значение параметра **article id** в результирующем наборе.  
  
2.  В базе данных на распространителе выполните процедуру [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql). Используемых Укажите идентификатор статьи из шага 2 для ** \@ article_id**. Используемых Укажите идентификатор базы данных публикации для ** \@ publisher_database_id**, которую можно получить из столбца **database_id** представления каталога [sys. databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией программным образом](../monitoring-replication.md)  
  
  
