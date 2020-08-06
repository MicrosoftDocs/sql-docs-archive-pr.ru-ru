---
title: Создание резервных копий реплицируемых баз данных и восстановление из них | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- backups [SQL Server replication]
- administering replication, restoring
- backing up replicated databases
- backups [SQL Server replication], about backups
- restoring replicated databases [SQL Server replication]
- recovery [SQL Server replication], about recovery
- restoring databases [SQL Server], replicated databases
- backing up databases [SQL Server], replicated databases
- restoring [SQL Server replication], about restoring
- recovery [SQL Server replication]
- replication [SQL Server], administering
- distribution databases [SQL Server replication], backing up
- restoring [SQL Server replication]
- administering replication, backing up
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e91505bacf67f7f4628bd1b3f6b2cc78a6bc4c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664879"
---
# <a name="back-up-and-restore-replicated-databases"></a>Создание резервных копий реплицируемых баз данных и восстановление из них
  Реплицированные базы данных требуют особого внимания к резервному копированию и восстановлению данных. В данном разделе содержится вводные сведения и ссылки на дополнительные сведения о стратегиях резервного копирования и восстановления для различных типов репликации.  
  
 Служба репликации поддерживает восстановление реплицированной базы данных на том же сервере и в той же базе данных, где была создана ее резервная копия. Если восстановить резервную копию реплицированной базы данных на другом сервере или в другой базе данных, то станет невозможным сохранение настроек репликации. В этом случае после восстановления из резервной копии потребуется повторно создать все публикации и подписки.  
  
> [!NOTE]  
>  Реплицируемую базу данных можно восстановить на резервном сервере при использовании доставки журналов. Дополнительные сведения см. в статье [Репликация и доставка журналов (SQL Server)](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).  
  
 Необходимо регулярно выполнять резервное копирование реплицируемых баз данных и связанных с ними системных баз данных. Выполняйте резервное копирование следующих баз данных:  
  
-   База данных публикаций на издателе.  
  
-   База данных распространителя на распространителе.  
  
-   База данных подписок на каждом подписчике.  
  
-   Системные базы данных **master** и **msdb** на издателе, распространителе и на всех подписчиках. Резервные копии этих баз данных и копия соответствующей базы данных репликации должны быть сделаны одновременно. Например, создавайте резервную копию баз данных **master** и **msdb** на издателе одновременно с резервной копией базы данных публикаций. Если база данных публикаций восстановлена, убедитесь, что базы данных **master** и **msdb** согласованы с базой данных публикаций по настройке и конфигурации репликации.  
  
 Если резервное копирование журналов выполняется регулярно, любые изменения, касающиеся репликации, будут заноситься в резервные копии журнала. Если не выполняется резервное копирование журналов, то необходимо выполнить это резервное копирование при каждом изменении настройки, относящейся к репликации. Дополнительные сведения см. в статье [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md).  
  
## <a name="backup-and-restore-strategies"></a>Стратегии резервного копирования и восстановления  
 Стратегии для резервного копирования и восстановления каждого узла в топологии репликации различаются в соответствии с используемым типом репликации. Сведения о стратегиях резервного копирования и восстановления для каждого типа репликации см. в следующих разделах:  
  
-   [Стратегии резервного копирования и восстановления для моментальных снимков и репликации транзакций](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)  
  
-   [Стратегии резервного копирования и восстановления для репликации слиянием](strategies-for-backing-up-and-restoring-merge-replication.md)  
  
 В состав любой стратегии восстановления всегда должно входить сохранение текущего скрипта настроек репликации в безопасном расположении. В случае отказа сервера или необходимости создания тестовой среды можно изменить скрипт, изменив ссылки имен серверов, после чего он может использоваться для восстановления настроек репликации. В дополнение к созданию скрипта текущих настроек репликации нужно создать скрипт включения и отключения репликации. Сведения о создании скриптов для объектов репликации см. в разделе [Scripting Replication](../scripting-replication.md).  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление баз данных SQL Server](../../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Best Practices for Replication Administration](best-practices-for-replication-administration.md)  
  
  
