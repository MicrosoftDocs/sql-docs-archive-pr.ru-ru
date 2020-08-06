---
title: Обновление реплицируемых баз данных | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- merge replication database upgrades [SQL Server replication]
- replication [SQL Server], upgrading
- transactional replication, upgrading databases
- snapshot replication [SQL Server], upgrading databases
- upgrading replicated databases
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 326a94820876b40128428aac58e47c650ce122b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657859"
---
# <a name="upgrade-replicated-databases"></a>Обновление реплицируемых баз данных
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживает обновление реплицируемых баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущих версий, при этом на время обновления узла прекращать работу с другими узлами не требуется. Соблюдайте следующие правила, определяющие допустимые версии объектов репликации.  
  
-   Версия распространителя не должна быть ниже версии издателя (во многих случаях распространителем и издателем является один и тот же экземпляр).  
  
-   Версия издателя не должна превышать версию распространителя.  
  
-   Версия подписчика зависит от типа публикации следующим образом.  
  
    -   Подписчик на публикацию транзакций может иметь любую версию, отличающуюся от версии издателя, но не более, чем на две версии. Например, издатель [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] может работать с подписчиками [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], а издатель [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] — с подписчиками [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
    -   Версия подписчика на публикацию слиянием не должна превышать версию издателя.  
  
> [!NOTE]  
>  Этот раздел доступен в справочной документации по программе установки, а также в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ссылки на разделы, выделенные полужирным шрифтом в справке по установке, относятся к разделам, доступным только в электронной документации.  
  
## <a name="run-the-log-reader-agent-for-transactional-replication-before-upgrade"></a>Запуск агента чтения журнала для репликации транзакций перед обновлением  
 Перед обновлением до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]необходимо убедиться, что все зафиксированные транзакции из опубликованных таблиц были обработаны агентом чтения журнала. Чтобы это обеспечить, для каждой базы данных, содержащей публикации транзакций, необходимо выполнить следующие шаги.  
  
1.  Убедитесь, что в базе данных запущен агент чтения журнала. По умолчанию агент работает постоянно.  
  
2.  Остановите активность пользователей в опубликованных таблицах.  
  
3.  Подождите, пока агент чтения журнала не скопирует транзакции в базу данных распространителя, затем остановите агент.  
  
4.  Чтобы убедиться, что все транзакции были обработаны, выполните процедуру [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) . Результирующий набор от этой процедуры должен быть пустым.  
  
5.  Чтобы закрыть соединение процедуры sp_replcmds, выполните процедуру [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) .  
  
6.  Выполните обновление сервера до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
7.  Перезапустите агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и агент чтения журнала, если после обновления они не запустятся автоматически.  
  
## <a name="run-agents-for-merge-replication-after-upgrade"></a>Выполнение агентов для репликации слиянием после обновления  
 После обновления запустите агент моментальных снимков для каждой публикации слиянием и агент слияния для каждой подписки, чтобы обновить метаданные репликации. Применять новый моментальный снимок не требуется, потому что заново инициализировать подписки не нужно. Метаданные подписки обновляются при первом запуске агента слияния после обновления. Это означает, что база данных подписки может оставаться в сети в активном режиме во время обновления издателя.  
  
 Механизм репликации слиянием хранит метаданные публикации и подписки в нескольких системных таблицах баз данных публикации и подписки. При запуске агента моментальных снимков обновляются метаданные публикации, а при запуске агента слияния — метаданные подписки. Пользователь должен только сформировать моментальный снимок публикации. Если при публикации слиянием используются параметризованные фильтры, каждой секции также соответствует моментальный снимок. Обновлять эти секционированные снимки не требуется.  
  
 Для выполнения агентов можно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], монитор репликации и окно командной строки. Дополнительные сведения о выполнении агента моментальных снимков см. в следующих разделах.  
  
-   [Создание и применение исходного моментального снимка](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [Создание и применение исходного моментального снимка](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Replication Agent Executables Concepts](../../../2014/relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 Дополнительные сведения о выполнении агента слияния см. в следующих разделах.  
  
-   [Синхронизация подписки по запросу](../../../2014/relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Синхронизация принудительной подписки](../../../2014/relational-databases/replication/synchronize-a-push-subscription.md)  
  
 Если после обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в топологии, в которой используется репликация слиянием, необходимо использовать новые возможности, измените уровень совместимости всех публикаций.  
  
## <a name="upgrading-to-standard-workgroup-or-express-editions"></a>Обновление до выпусков Standard Edition, Workgroup Edition и Express Edition  
 Перед обновлением с одного выпуска [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] до другого проверьте, что используемые функции поддерживаются в выпуске, до которого производится обновление. Дополнительные сведения см. в разделе о репликации в [функциях, поддерживаемых Выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="web-synchronization-for-merge-replication"></a>Веб-синхронизация для репликации слиянием  
 Для использования веб-синхронизации репликации слиянием необходимо скопировать в виртуальный каталог служб IIS, используемый для синхронизации, прослушиватель репликации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (replisapi.dll). При настройке веб-синхронизации этот файл копируется в виртуальный каталог мастером настройки веб-синхронизации. Для обновления компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленных на сервере IIS, необходимо вручную скопировать библиотеку replisapi.dll из каталога COM в виртуальный каталог сервера IIS. Дополнительные сведения о конфигурации см. в статье [Настройка веб-синхронизации](../../../2014/relational-databases/replication/configure-web-synchronization.md).  
  
## <a name="restoring-a-replicated-database-from-an-earlier-version"></a>Восстановление из копии реплицированной базы данных из предыдущей версии  
 Чтобы обеспечить неизменность параметров репликации при восстановлении реплицированной базы данных, имеющей более раннюю версию, выполните восстановление на сервер и в базу данных, имеющих те же имена, что и у сервера или базы данных, для которых была сделана резервная копия.  
  
## <a name="see-also"></a>См. также:  
 [Вопросы и ответы об администрировании репликации](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)   
 [Обратная совместимость репликации](../../../2014/relational-databases/replication/replication-backward-compatibility.md)   
 [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Обновление до SQL Server 2014](upgrade-sql-server.md)  
  
  
