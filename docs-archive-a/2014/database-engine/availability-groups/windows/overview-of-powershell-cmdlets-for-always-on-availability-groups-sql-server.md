---
title: Общие сведения о командлетах PowerShell для группы доступности AlwaysOn (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], PowerShell cmdlets
- Availability Groups [SQL Server], about
- PowerShell [SQL Server], cmdlets
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6861abb3358df5e8c223d387b82e22de0f2a9d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656551"
---
# <a name="overview-of-powershell-cmdlets-for-alwayson-availability-groups-sql-server"></a>Обзор командлетов PowerShell для групп доступности AlwaysOn (SQL Server)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell ― это оболочка командной строки для задач и язык скриптов, разработанный специально для администрирования систем. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] содержит набор командлетов PowerShell для [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , которые позволяют развертывать, управлять и отслеживать группы доступности, реплики доступности и базы данных доступности.  
  
> [!NOTE]  
>  Командлет PowerShell может завершиться после успешного инициирования действия. Это не означает, что предписанное действие, например отработка отказа для группы доступности, завершено. При создании скрипта для некой последовательности действий может оказаться необходимым проверить состояние действий и подождать из завершения.  
  
 В этой теме описаны командлеты для следующих наборов задач.  
  
-   [Настройка экземпляра сервера для группы доступности AlwaysOn](#ConfiguringServerInstance)  
  
-   [Резервное копирование и восстановление баз данных и журналов транзакций](#BnRcmdlets)  
  
-   [Создание группы доступности и управление ею](#DeployManageAGs)  
  
-   [Создание прослушивателя группы доступности и управление им](#AGlisteners)  
  
-   [Создание реплики доступности и управление ею](#DeployManageARs)  
  
-   [Добавление базы данных доступности и управление ею](#DeployManageDbs)  
  
-   [Отслеживание работоспособности группы доступности](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  Список разделов [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] электронной документации по, в которых описывается использование командлетов для выполнения [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] задач, см. в разделе "связанные задачи" статьи [общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="configuring-a-server-instance-for-alwayson-availability-groups"></a><a name="ConfiguringServerInstance"></a>Настройка экземпляра сервера для группы доступности AlwaysOn  
  
|Командлеты|Описание|Поддерживается на|  
|-------------|-----------------|------------------|  
|`Disable-SqlAlwaysOn`|Отключает компонент [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для экземпляра сервера.|Экземпляр сервера, указанный параметром `Path`, `InputObject` или параметром `Name`. (Необходим выпуск [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с поддержкой [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].)|  
|`Enable-SqlAlwaysOn`|Включает [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в экземпляре [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , который поддерживает компонент [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] . Сведения о поддержке [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделе [Предварительные требования, ограничения и рекомендации для группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).|Любой выпуск [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с поддержкой [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].|  
|`New-SqlHadrEndPoint`|Создает новую конечную точку зеркального отображения базы данных на экземпляре сервера. Эта конечная точка необходима для перемещения данных между базой данных-источником и базой данных-получателем.|Любой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|`Set-SqlHadrEndpoint`|Изменяет свойства существующей конечной точки зеркального отображения базы данных, например имя, состояние и свойства проверки подлинности.|Экземпляр сервера, который поддерживает [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и в котором отсутствует конечная точка зеркального отображения базы данных|  
  
##  <a name="backing-up-and-restoring-databases-and-transaction-logs"></a><a name="BnRcmdlets"></a> Резервное копирование и восстановление баз данных и журналов транзакций  
  
|Командлеты|Описание|Поддерживается на|  
|-------------|-----------------|------------------|  
|`Backup-SqlDatabase`|Создает резервную копию данных или журнала.|Любая база данных, находящаяся в режиме «в сети» (для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]база данных на том экземпляре сервера, на котором размещена первичная реплика)|  
|`Restore-SqlDatabase`|Восстанавливает резервную копию.|Любой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]экземпляр сервера, на котором размещена вторичная реплика)<br /><br /> **&#42;&#42; важно &#42;&#42;** При подготовке базы данных-получателя необходимо использовать `-NoRecovery` параметр в каждой `Restore-SqlDatabase` команде.|  
  
 Дополнительные сведения об использовании этих командлетов для подготовки базы данных-получателя см. в разделе [Подготовка базы данных-получателя для присоединения к группе доступности (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
##  <a name="creating-and-managing-an-availability-group"></a><a name="DeployManageAGs"></a> Creating and Managing an Availability Group  
  
|Командлеты|Описание|Поддерживается на|  
|-------------|-----------------|------------------|  
|`New-SqlAvailabilityGroup`|Создает новую группу доступности.|Экземпляр сервера, в котором будет размещена первичная реплика|  
|`Remove-SqlAvailabilityGroup`|Удаляет группу доступности.|Экземпляр сервера с включенным компонентом HADR|  
|`Set-SqlAvailabilityGroup`|Устанавливает свойства группы доступности; включение и отключение режимов «в сети» и «вне сети» группы доступности|Экземпляр сервера, в котором размещена первичная реплика|  
|`Switch-SqlAvailabilityGroup`|Запускает одну из следующих форм отработки отказа.<br /><br /> Принудительная отработка отказа для группы доступности (возможна потеря данных).<br /><br /> Переход на другой ресурс группы доступности вручную.|Экземпляр сервера, на котором размещается целевая вторичная реплика|  
  
##  <a name="creating-and-managing-an-availability-group-listener"></a><a name="AGlisteners"></a> Creating and Managing an Availability Group Listener  
  
|Командлет|Описание|Поддерживается на|  
|------------|-----------------|------------------|  
|`New-SqlAvailabilityGroupListener`|Создает прослушиватель группы доступности и привязывает его к существующей группе доступности.|Экземпляр сервера, в котором размещена первичная реплика|  
|`Set-SqlAvailabilityGroupListener`|Изменяет порт существующего прослушивателя группы доступности.|Экземпляр сервера, в котором размещена первичная реплика|  
|`Add-SqlAvailabilityGroupListenerStaticIp`|Добавляет статический IP-адрес в конфигурацию существующего прослушивателя группы доступности. IP-адрес может быть адресом IPv4 с подсетью или адресом IPv6.|Экземпляр сервера, в котором размещена первичная реплика|  
  
##  <a name="creating-and-managing-an-availability-replica"></a><a name="DeployManageARs"></a> Creating and Managing an Availability Replica  
  
|Командлеты|Описание|Поддерживается на|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|Создает новую реплику доступности. Вы можете использовать параметр `-AsTemplate` для создания в памяти объекта реплики доступности для каждой новой реплики доступности.|Экземпляр сервера, в котором размещена первичная реплика|  
|`Join-SqlAvailabilityGroup`|Присоединяет вторичную реплику к группе доступности.|Экземпляр сервера, в котором размещена вторичная реплика|  
|**Remove-SqlAvailabilityReplica**|Удаляет реплику доступности.|Экземпляр сервера, в котором размещена первичная реплика|  
|`Set-SqlAvailabilityReplica`|Устанавливает свойства реплики доступности.|Экземпляр сервера, в котором размещена первичная реплика|  
  
##  <a name="adding-and-managing-an-availability-database"></a><a name="DeployManageDbs"></a> Adding and Managing an Availability Database  
  
|Командлеты|Описание|Поддерживается на|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|Добавляет базу данных в группу доступности на первичной реплике.<br /><br /> Присоединяет вторичную базу данных к группе доступности на вторичной реплике.|Любой экземпляр сервера, на котором размещается реплика доступности (поведение отличается для первичных и вторичных реплик)|  
|**Remove-SqlAvailabilityDatabase**|Удаляет базу данных из группы доступности на первичной реплике.<br /><br /> Удаляет локальную базу данных-получатель из локальной вторичной реплики на вторичной реплике.|Любой экземпляр сервера, на котором размещается реплика доступности (поведение отличается для первичных и вторичных реплик)|  
|`Resume-SqlAvailabilityDatabase`|Возобновляет перемещение данных для приостановленной базы данных доступности.|Экземпляр сервера, на котором была приостановлена база данных.|  
|`Suspend-SqlAvailabilityDatabase`|Приостанавливает перемещение данных в любой базе данных доступности.|Любой экземпляр сервера, на котором размещена реплика доступности.|  
  
##  <a name="monitoring-availability-group-health"></a><a name="MonitorTblshtAGs"></a> Monitoring Availability Group Health  
 Следующие командлеты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяют отслеживать работоспособность группы доступности, ее реплик и баз данных.  
  
> [!IMPORTANT]  
>  Для выполнения этих командлетов необходимо иметь разрешения CONNECT, VIEW SERVER STATE и VIEW ANY DEFINITION.  
  
|Командлет|Описание|Поддерживается на|  
|------------|-----------------|------------------|  
|`Test-SqlAvailabilityGroup`|Оценивает работоспособность группы доступности при помощи оценки состояния политик управления SQL Server.|Любой экземпляр сервера, на котором размещена реплика доступности.*|  
|`Test-SqlAvailabilityReplica`|Оценивает работоспособность реплик доступности при помощи оценки состояния политик управления SQL Server.|Любой экземпляр сервера, на котором размещена реплика доступности.*|  
|`Test-SqlDatabaseReplicaState`|Оценивает работоспособность базы данных доступности на всех присоединенных репликах доступности при помощи оценки состояния политик управления SQL Server.|Любой экземпляр сервера, на котором размещена реплика доступности.*|  
  
 * Чтобы просмотреть сведения обо всех репликах доступности в группе доступности, используйте экземпляр сервера, на котором размещена первичная реплика.  
  
 Дополнительные сведения см. в статье [Использование политик AlwaysOn для просмотра работоспособности группы доступности &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Получение справок по SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
  
