---
title: Автоматизированное администрирование в организации | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8df3e34c2c70c81f9710ade0d6855446b930fb50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665769"
---
# <a name="automated-administration-across-an-enterprise"></a>Автоматизация администрирования в масштабах предприятия
   Автоматическое администрирование нескольких экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] называется *администрированием нескольких серверов*. Оно предназначено для выполнения следующих задач.  
  
-   Управления двумя или несколькими серверами.  
  
-   Планирования потоков данных между серверами предприятия для организации хранилищ данных.  
  
> [!NOTE]  
>  В рамках [!INCLUDE[msCoName](../../includes/msconame-md.md)] текущих усилий по уменьшению совокупной стоимости владения [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] появились две функции: метод управления серверами, называемый управлением на основе политик, и многосерверные запросы, использующие серверы конфигурации и группы серверов. Эти функции могут использоваться вместо или совместно с некоторыми функциями, описанными в этом разделе. Дополнительные сведения см. в статьях [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) и [Администрирование нескольких серверов с помощью центральных серверов управления](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).  
  
 Чтобы воспользоваться преимуществами администрирования нескольких серверов, необходимо иметь, по меньшей мере, один главный сервер и один целевой. Главный сервер распределяет задания целевым серверам и получает от них события. На главном сервере также хранится центральная копия определений заданий, выполняющихся на целевых серверах. Целевые серверы периодически подключаются к главному серверу для обновления расписаний своих заданий. Если на главном сервере имеется новое задание, то целевой сервер получает его. После завершения задания целевой сервер подключается к главному серверу и сообщает о состоянии его завершения.  
  
 На следующем рисунке показана связь между главным и целевыми серверами.  
  
 ![Настройка администрирования нескольких серверов](../../database-engine/media/multisvr.gif "Настройка администрирования нескольких серверов")  
  
 При администрировании серверов подразделений крупного предприятия можно определить:  
  
-   единое задание резервного копирования, разбитое на шаги;  
  
-   операторов, которые будут уведомлены в случае сбоя при резервном копировании;  
  
-   расписание выполнения для этого задания.  
  
 Один раз сохраните это задание резервного копирования на сервере, а затем прикрепите серверы подразделений как целевые. С этого момента все серверы подразделений выполняют одно и то же задание, хотя оно было определено всего один раз.  
  
> [!NOTE]  
>  Функции администрирования нескольких серверов предназначены для членов роли sysadmin. Тем не менее член роли sysadmin на целевом сервере не может изменить операции, которые главный сервер выполняет на целевом сервере. Такая мера предосторожности предохраняет шаги задания от случайного удаления, а операции на целевом сервере — от постороннего вмешательства.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Создание многосерверной среды](create-a-multiserver-environment.md)  
 Содержит сведения о создании главного и целевых серверов и управлении ими.  
  
 [Выбор правильной учетной записи службы агента SQL Server для многосерверной среды](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 Содержит сведения о влиянии использования неадминистративных учетных записей Windows или учетной записи Local System службы агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на многосерверное окружение.  
  
 [Установка параметров шифрования на целевых серверах](set-encryption-options-on-target-servers.md)  
 Содержит сведения о настройке подраздела реестра MsxEncryptChannelOptions агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на целевых серверах.  
  
 [Управление заданиями в масштабе предприятия](manage-jobs-across-an-enterprise.md)  
 Содержит сведения о проверке состояния задания, изменения для него целевых серверов, синхронизации времени на целевых серверах и опросе главных серверов о состоянии текущих заданий.  
  
 [Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 Содержит сведения об устранении неполадок многосерверных заданий, которые используют неверные учетные записи-посредники.  
  
 [Опрос серверов](poll-servers.md)  
 Содержит сведения о том, как явно или неявно заставить целевые серверы синхронизировать сведения о заданиях с главным сервером.  
  
 [Управление событиями](manage-events.md)  
 Содержит сведения о пересылке событий от целевых серверов к главному.  
  
 [Настройка автоматизированного администрирования в организации](tune-automated-administration-across-an-enterprise.md)  
 Содержит сведения о том, как автоматизированное администрирование в многосерверном окружении использует функции самонастройки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Обратная совместимость компонента ядра СУБД SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Регистрация серверов](../register-servers/register-servers.md)   
 [sp_add_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql)   
 [sp_delete_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql)   
 [sp_help_downloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql)   
 [sp_help_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql)   
 [sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql)   
 [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)   
 [sp_update_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql)   
 [dbo.sysжобсерверс &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql)   
 [sys.sysимена входа &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)   
 [dbo.sysтаржетсерверс &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
