---
title: Смена режима доступности для реплики доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1636f3ea86e083e47276423b120dbc8d3744d387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750227"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a>Смена режима доступности для реплики доступности (SQL Server)
  В этом разделе описывается изменение режима доступности для реплики доступности в группе доступности AlwaysOn в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell. Режим доступности — это свойство реплики, которое определяет, происходит в ней синхронная или асинхронная фиксация. *Режим асинхронной фиксации* увеличивает производительность за счет средств высокого уровня доступности и поддерживает только принудительный переход на другой ресурс вручную (с возможной потерей данных), который обычно называется *принудительной отработкой отказа*. *Режим синхронной фиксации* обеспечивает высокий уровень доступности за счет производительности и после завершения синхронизации вторичной реплики поддерживает как автоматическую отработку отказа, так и отработку отказа вручную.  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Изменение режима доступности для группы доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните группу доступности, реплику которой нужно изменить.  
  
4.  Щелкните правой кнопкой мыши реплику и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства реплики доступности** измените режим доступности для этой реплики с помощью раскрывающегося списка **Режим доступности** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение режима доступности для группы доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* MODIFY REPLICA ON '*имя_сервера*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     } )  
  
     где *group_name* — имя группы доступности, а *server_name* — имя экземпляра сервера, на котором размещена изменяемая реплика.  
  
    > [!NOTE]  
    >  FAILOVER_MODE = AUTOMATIC поддерживается, только если указан параметр AVAILABILITY_MODE = SYNCHRONOUS_COMMIT.  
  
     В следующем примере, введенном на первичной реплике группы доступности `AccountsAG` , выполняется изменение режимов доступности и отработки отказа на синхронную фиксацию и автоматический переход на другой ресурс соответственно для реплики, размещенной на экземпляре сервера `INSTANCE09` .  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell

### <a name="to-change-the-availability-mode-of-an-availability-group"></a>Изменение режима доступности для группы доступности
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором находится первичная реплика.  
  
2.  Используйте командлет `Set-SqlAvailabilityReplica` с параметром `AvailabilityMode`. Дополнительно можно использовать параметр `FailoverMode`.  
  
     Например, следующая команда изменяет реплику `MyReplica` в группе доступности `MyAg` , устанавливая использование режима доступности с синхронной фиксацией и поддержку автоматического перехода на другой ресурс.  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
Сведения о настройке и использовании поставщика SQL Server PowerShell см. в разделе [поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md).
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Режимы доступности (группы доступности AlwaysOn)](availability-modes-always-on-availability-groups.md)   
 [Отказоустойчивость и режимы отработки отказа &#40;группы доступности AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md)  
