---
title: Удаление вторичной реплики из группы доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removesecondaryar.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3f2b35ec9cf27f2f7b23714a41665f2709837a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657314"
---
# <a name="remove-a-secondary-replica-from-an-availability-group-sql-server"></a>Удаление вторичной реплики из группы доступности (SQL Server)
  В этом разделе описывается удаление вторичной реплики из группы доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Удаление вторичной реплики с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Дальнейшие действия.**  [После удаления вторичной реплики](#PostBestPractices)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Эта задача поддерживается только в первичной реплике.  
  
-   Из группы доступности может быть удалена только вторичная реплика.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо иметь подключение к экземпляру сервера, на котором размещена первичная реплика группы доступности.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Удаление вторичной реплики**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Выберите группу доступности и разверните узел **Реплики доступности** .  
  
4.  Этот шаг имеет следующие различия в зависимости от того, удаляется одна или несколько реплик.  
  
    -   Чтобы удалить несколько реплик, используйте область **Подробности** обозревателя объектов, чтобы просмотреть и выбрать реплики для удаления. Дополнительные сведения см. в разделе [Использование раздела "Подробности обозревателя объектов" для мониторинга групп доступности (среда SQL Server Management Studio)](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Чтобы удалить одну реплику, выберите ее на панели **Обозреватель объектов** или на панели **Подробности обозревателя объектов** .  
  
5.  Щелкните правой кнопкой мыши выбранную вторичную реплику или реплики и выберите в контекстном меню команду **Удалить из группы доступности** .  
  
6.  Чтобы удалить все перечисленные вторичные реплики, в диалоговом окне **Удаление вторичных реплик из группы доступности** нажмите кнопку **ОК**. Если все перечисленные группы доступности удалять не нужно, нажмите кнопку **Отмена**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Удаление вторичной реплики**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* REMOVE REPLICA ON "*имя_экземпляра*" [,...*n*],  
  
     где *имя_группы* — имя группы доступности, а *имя_экземпляра* — экземпляр сервера, на котором размещена вторичная реплика.  
  
     В следующем примере удаляется вторичная реплика из группы доступности *MyAG* . Целевая вторичная реплика расположена на экземпляре сервера с именем *HADR_INSTANCE* на компьютере *COMPUTER02*.  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
 **Удаление вторичной реплики**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором находится первичная реплика.  
  
2.  Используйте командлет **Remove-SqlAvailabilityReplica** .  
  
     Например, следующая команда удаляет реплику доступности на сервере `MyReplica` из группы доступности с именем `MyAg`.  Эта команда должна выполняться на экземпляре сервера, на котором размещена первичная реплика группы доступности.  
  
    ```powershell
    Remove-SqlAvailabilityReplica -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-replica"></a><a name="PostBestPractices"></a> Дальнейшие действия. После удаления вторичной реплики  
 Если была выбрана реплика, которая в данный момент недоступна, ее удаление произойдет в момент перехода в режим «в сети».  
  
 Удаление реплики прекращает поступление в нее данных. После того, как вторичная реплика подтверждает, что она была удалена из глобального хранилища, реплика удаляет параметры группы доступности из своих баз данных, которые остаются на экземпляре локального сервера в состоянии RECOVERING.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Добавление вторичной реплики в группу доступности &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)   
 [Удаление группы доступности (SQL Server)](remove-an-availability-group-sql-server.md)  
