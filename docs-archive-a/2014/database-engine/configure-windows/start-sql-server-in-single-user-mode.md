---
title: Запуск SQL Server в однопользовательском режиме | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server, single-user mode
- single-user mode [SQL Server]
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b2600524da45f9a81f155432397cee2e7e876274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655344"
---
# <a name="start-sql-server-in-single-user-mode"></a>Запуск SQL Server в однопользовательском режиме
  При определенных обстоятельствах экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нужно запустить в однопользовательском режиме (используется **параметр запуска -m**). Например, может понадобиться изменить параметры конфигурации сервера, восстановить поврежденную базу данных master или другую системную базу данных. Для обоих этих действий необходим запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме.  
  
 После запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме каждый член локальной группы администраторов на компьютере сможет подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от имени члена предопределенной роли сервера sysadmin. Дополнительные сведения см. в статье [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 При запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме необходимо обратить внимание на следующее:  
  
-   Только один пользователь может подключиться к серверу.  
  
-   Процесс CHECKPOINT не выполняется. По умолчанию он автоматически выполняется при запуске.  
  
> [!NOTE]  
>  Перед подключением к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме остановите службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В противном случае служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать соединение, тем самым блокируя его  
  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается в однопользовательском режиме, среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] может подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обозреватель объектов в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] может вызвать ошибку, так как для некоторых операций ему необходимо одновременно несколько соединений. Чтобы управлять [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме, выполняйте инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , подключаясь только через редактор запросов в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], или используйте [программу sqlcmd](../../tools/sqlcmd-utility.md).  
  
 При использовании параметра **-m** с **sqlcmd** или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] можно ограничить соединения с указанным клиентским приложением. Например, **-m "sqlcmd"** ограничивает соединения с одним соединением, и это соединение должно идентифицироваться как клиентская программа **sqlcmd** . Этот параметр следует использовать, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается в однопользовательском режиме, а единственное доступное соединение занято неизвестным клиентским приложением. Чтобы подключиться с помощью редактора запросов в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], используйте **-m"Microsoft SQL Server Management Studio - Query"** .  
  
> [!IMPORTANT]  
>  Не используйте этот параметр как средство безопасности. Клиентское приложение предоставляет имя клиентского приложения и может указать ложное имя в составе строки подключения.  
  
## <a name="note-for-clustered-installations"></a>Примечание для кластеризованной установки  
 Когда при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в кластерной среде выполняется запуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме, DLL-библиотека ресурсов кластера использует доступное соединение, блокируя тем самым любые другие подключения к серверу. В таком состоянии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] попытка перевести ресурс агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режим «в сети», может привести к переходу ресурса SQL на другой узел, если этот ресурс настроен с учетом группы.  
  
 Для решения этой проблемы используется следующая процедура.  
  
1.  Удалите параметр запуска -m из дополнительных свойств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Переведите ресурс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режим «вне сети».  
  
3.  С текущего узла владельца этой группы выполните в командной строке следующую команду:  
    net start MSSQLSERVER /m.  
  
4.  Уточните у администратора кластера или с помощью консоли управления отказоустойчивым кластером, остается ли ресурс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме «вне сети».  
  
5.  Подключитесь к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используя теперь следующую команду, и выполните необходимую операцию: SQLCMD -E -S\<servername>.  
  
6.  После завершения операции закройте командную строку и переведите SQL и другие ресурсы обратно в режим «в сети», обратившись к администратору кластера.  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка или приостановка службы агента SQL Server](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Диагностическое соединение для администраторов баз данных](diagnostic-connection-for-database-administrators.md)   
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)   
 [CHECKPOINT (Transact-SQL)](/sql/t-sql/language-elements/checkpoint-transact-sql)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Параметры запуска службы Database Engine](database-engine-service-startup-options.md)  
  
  
