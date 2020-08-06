---
title: Добавление вторичной реплики к группе доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 6669dcce-85f9-495f-aadf-7f62cff4a9da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 498103a781641c72e166c6b11663f5248ae5ccfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655974"
---
# <a name="add-a-secondary-replica-to-an-availability-group-sql-server"></a>Добавление вторичной реплики к группе доступности (SQL Server)
  В этом разделе описано, как добавить вторичную реплику в существующую группу доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Перед началом работы**  
  
     [Требования и ограничения](#PrerequisitesRestrictions)  
  
     [Безопасность](#Security)  
  
-   **Добавление реплики с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Дальнейшие действия**  [После добавления вторичной реплики](#FollowUp)  
  
## <a name="before-you-begin"></a>Перед началом  
 Настоятельно рекомендуется прочитать этот раздел, прежде чем пытаться настроить свою первую группу доступности.  
  
##  <a name="prerequisites-and-restrictions"></a><a name="PrerequisitesRestrictions"></a> Требования и ограничения  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
 Дополнительные сведения см. в разделе [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="security"></a><a name="Security"></a> безопасность  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Добавление реплики**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните правой кнопкой группу доступности и выберите одну из следующих команд.  
  
    -   Чтобы запустить мастер добавления реплики в группу доступности, выберите команду **Добавить реплику** . Дополнительные сведения см. в разделе [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).  
  
    -   Либо выберите команду **Свойства** , чтобы открыть диалоговое окно **Свойства группы доступности** . Чтобы добавить реплику в этом диалоговом окне, выполните следующие действия.  
  
        1.  На панели **Реплики доступности** этого диалогового окна нажмите кнопку **Добавить** . Будет создана запись реплики с пустым полем «Экземпляр сервера».  
  
        2.  Введите имя экземпляра сервера, который соответствует обязательным условиям для размещения реплики доступности.  
  
         Чтобы добавить другие реплики, повторите предыдущие шаги. После завершения добавления реплик нажмите кнопку **ОК** для завершения операции.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Добавление реплики**  
  
1.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещена первичная реплика.  
  
2.  Добавьте новую вторичную реплику в группу доступности с помощью предложения ADD REPLICA ON инструкции ALTER AVAILABILITY GROUP. В предложении ADD REPLICA ON необходимо указать параметры ENDPOINT_URL, AVAILABILITY_MODE и FAILOVER_MODE. Другие параметры реплики (BACKUP_PRIORITY, SECONDARY_ROLE, PRIMARY_ROLE и SESSION_TIMEOUT) являются необязательными. Дополнительные сведения см. в разделе [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql).  
  
     Например, следующая инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] создает новую реплику в группе доступности `MyAG` в экземпляре сервера по умолчанию, размещенном на компьютере `COMPUTER04`, с URL-адресом конечной точки `TCP://COMPUTER04.Adventure-Works.com:5022'`. Данная реплика поддерживает переход на другой ресурс вручную и режим доступности «Asynchronous Commit».  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG ADD REPLICA ON 'COMPUTER04'   
       WITH (  
             ENDPOINT_URL = 'TCP://COMPUTER04.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
 **Добавление реплики**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором находится первичная реплика.  
  
2.  Используйте командлет **New-SqlAvailabilityReplica** .  
  
     Например, следующая команда добавляет реплику доступности в существующую группу доступности с именем `MyAg`. Данная реплика поддерживает переход на другой ресурс вручную и режим доступности «Asynchronous Commit». В роли вторичной эта реплика будет поддерживать соединения с доступом на чтение, позволяя разгрузить обработку только для чтения для этой реплики.  
  
    ```powershell
    $agPath = "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
    $endpointURL = "TCP://PrimaryServerName.domain.com:5022"  
    $failoverMode = "Manual"  
    $availabilityMode = "AsynchronousCommit"  
    $secondaryReadMode = "AllowAllConnections"  
  
    New-SqlAvailabilityReplica -Name SecondaryServer\Instance `   
    -EndpointUrl $endpointURL `   
    -FailoverMode $failoverMode `   
    -AvailabilityMode $availabilityMode `   
    -ConnectionModeInSecondaryRole $secondaryReadMode `   
    -Path $agPath  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-adding-a-secondary-replica"></a><a name="FollowUp"></a>Дальнейшие действия. После добавления вторичной реплики  
 Для добавления реплики в существующую группу доступности необходимо выполнить следующие шаги.  
  
1.  Подключитесь к экземпляру сервера, на котором должна быть размещена новая вторичная реплика доступности.  
  
2.  Присоедините новую вторичную реплику к группе доступности. Дополнительные сведения см. в разделе [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
3.  Для каждой базы данных в группе доступности создайте базу данных-получатель на экземпляре сервера, на котором размещается вторичная реплика. Дополнительные сведения см. в статье [Ручная подготовка базы данных-получателя для присоединения к группе доступности (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
4.  Присоедините все новые базы данных-получатели к группе доступности. Дополнительные сведения см. в статье [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
 **Управление репликой доступности**  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Удаление вторичной реплики из группы доступности (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Смена режима доступности для реплики доступности (SQL Server)](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Смена режима отработки отказа для реплики доступности (SQL Server)](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Изменение периода ожидания сеанса для реплики доступности (SQL Server)](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [Изменение периода ожидания сеанса для реплики доступности (SQL Server)](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql)   
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Создание и настройка групп доступности (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)   
 [Отслеживание групп доступности (Transact-SQL)](monitor-availability-groups-transact-sql.md)  
  
  
