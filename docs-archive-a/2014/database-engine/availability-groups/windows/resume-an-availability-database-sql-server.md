---
title: Возобновление базы данных доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.resumedatamove.f1
helpviewer_keywords:
- Availability Groups [SQL Server], resuming a database
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], databases
ms.assetid: 20e9147b-e985-4caa-910e-fc4b38dbf9a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a2279940c2502a310e9dac4448bd6029b6e13dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740481"
---
# <a name="resume-an-availability-database-sql-server"></a>Возобновление базы данных доступности (SQL Server)
  В [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] можно возобновить выполнение приостановленной базы данных доступности с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Возобновление приостановленной базы данных переводит базу данных в состояние SYNCHRONIZING. Возобновление базы данных-источника возобновляет также все ее базы данных-получатели, которые были приостановлены в результате приостановки базы данных-источника. Если какая-либо база данных-получатель была приостановлена локально на экземпляре сервера, на котором размещена вторичная реплика, эта база данных-получатель должна быть возобновлена локально. Как только определенная база данных-получатель и соответствующая база данных-источник вместе переходят в состояние SYNCHRONIZING, возобновляется синхронизация данных для базы данных-получателя.  
  
> [!NOTE]  
>  Приостановка и возобновление базы данных-получателя AlwaysOn непосредственно не влияет на доступность базы данных-источника. Но приостановка базы данных-получателя может повлиять на избыточность и возможности отработки отказа для базы данных-источника, эти возможности снижены до тех пор, пока не будет возобновлена база данных-получатель. Этим она отличается от зеркального отображения базы данных, где состояние зеркального отображения приостанавливается как в зеркальной базе данных, так и в основной базе данных, до тех пор пока не возобновится зеркальное отображение. Приостановка базы данных-источника AlwaysOn приостанавливает перемещение данных для всех соответствующих баз данных-получателей, функции избыточности и отработки отказа для этой базы данных не работают до тех пор, пока работа базы данных-источника не будет возобновлена.  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Возобновление базы данных-получателя с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Команда RESUME возвращается сразу после принятия репликой, в которой размещена целевая база данных, но фактическое возобновление базы данных происходит асинхронно.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором расположена возобновляемая база данных.  
  
-   Группа доступности должна быть в сети.  
  
-   База данных-источник должна быть в сети и доступна.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Возобновление базы данных-получателя**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена реплика доступности, для которой нужно возобновить базу данных, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Разверните группу доступности.  
  
4.  Разверните узел **Базы данных доступности** , щелкните правой кнопкой мыши базу данных и нажмите кнопку **Возобновить перемещение данных**.  
  
5.  В диалоговом окне **Возобновление перемещения данных** нажмите кнопку **ОК**.  
  
> [!NOTE]  
>  Чтобы возобновить дополнительные базы данных данной реплики, повторите шаги 4 и 5 для каждой базы данных.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Возобновление базы данных-получателя, приостановленной локально**  
  
1.  Подключитесь к экземпляру сервера, на котором размещена вторичная реплика, базу данных которой нужно возобновить.  
  
2.  Возобновите базу данных-получатель с помощью следующей инструкции [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr):  
  
     ALTER DATABASE *database_name* задать HADR Resume  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  

### <a name="to-resume-a-secondary-database"></a>Возобновление базы данных-получателя
  
1.  Измените папку (`cd`) на экземпляр сервера, на котором размещена реплика, базу данных которой нужно возобновить. Дополнительные сведения см. в подразделе [Предварительные условия](#Prerequisites)ранее в этом разделе.  
  
2.  Для возобновления группы доступности воспользуйтесь командлетом **Resume-SqlAvailabilityDatabase** .  
  
     Например, следующая команда возобновляет синхронизацию данных для базы данных доступности `MyDb3` в группе доступности `MyAg`.  
  
    ```powershell
    Resume-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Приостановка базы данных доступности (SQL Server)](suspend-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
