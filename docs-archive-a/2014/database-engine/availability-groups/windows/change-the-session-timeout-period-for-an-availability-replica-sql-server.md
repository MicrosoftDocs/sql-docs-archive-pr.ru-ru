---
title: Изменение периода ожидания сеанса для реплики доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], session timeout
- session timeout [SQL Server]
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 302ba4a2b0b72a70b05e563eb4085913074469eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750211"
---
# <a name="change-the-session-timeout-period-for-an-availability-replica-sql-server"></a>Изменение периода ожидания сеанса для реплики доступности (SQL Server)
  В этом разделе описывается настройка времени ожидания сеанса реплики доступности AlwaysOn при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Время ожидания сеанса — это свойство реплики, которое определяет, сколько секунд будет эта реплика доступности ждать отклика на команду ping, отправленную с подключенной реплики перед тем, как признать попытку подключения неудачной. По умолчанию реплика ожидает ответа на команду ping 10 секунд. Это свойство реплики применимо только к подключению данной вторичной реплики к первичной реплике группы доступности. Дополнительные сведения о периоде времени ожидания сеанса см. в разделе [Обзор групп доступности AlwaysOn (SQL Server)](overview-of-always-on-availability-groups-sql-server.md).  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Изменение времени ожидания с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
 Рекомендуется установить интервал времени ожидания в 10 секунд или более. При установке значения меньше 10 секунд возникает вероятность пропуска команды PING в сильно загруженной системе и вероятность ошибочного сообщения об ошибке.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Изменение значения времени ожидания сеанса для реплики доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните группу доступности, реплику которой нужно настроить.  
  
4.  Щелкните правой кнопкой мыши реплику доступности, которую нужно настроить, и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства реплики доступности** используйте поле **Время ожидания сеанса (в секундах)** , чтобы изменить число секунд, заданное в качестве времени ожидания для этой реплики.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение значения времени ожидания сеанса для реплики доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы*  
  
     MODIFY REPLICA ON '*имя_экземпляра*' WITH ( SESSION_TIMEOUT =*число_секунд* )  
  
     где *имя_группы* ― это имя группы доступности, *имя_экземпляра* ― это имя экземпляра сервера, где расположена реплика доступности, свойство которой необходимо изменить, а параметр *число_секунд* указывает количество секунд, которое реплика, будучи вторичной, будет ожидать до момента применения журнала к базам данных. Значение по умолчанию равно 0 секунд. Это означает, что время задержки равно 0.  
  
     В следующем примере, введенном на первичной реплике группы доступности `AccountsAG` , выполняется изменение значения времени ожидания сеанса на значение `15` секунд для реплики, размещенной на экземпляре сервера `INSTANCE09` .  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  

### <a name="to-change-the-session-timeout-period-for-an-availability-replica"></a>Изменение значения времени ожидания сеанса для реплики доступности
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором находится первичная реплика.  
  
2.  Используйте командлет `Set-SqlAvailabilityReplica` с параметром `SessionTimeout`, чтобы изменить число секунд времени ожидания сеанса для указанной реплики доступности.  
  
     Например, следующая команда задает период времени ожидания сеанса 15 секунд.  
  
    ```powershell
    Set-SqlAvailabilityReplica -SessionTimeout 15 -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
Сведения о настройке и использовании поставщика SQL Server PowerShell см. в разделе [поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md).
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
