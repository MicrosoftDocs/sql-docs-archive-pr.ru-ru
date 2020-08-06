---
title: Удаление прослушивателя группы доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 057b9c137cb4d8bbbdd03be61df600f7e59b264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657318"
---
# <a name="remove-an-availability-group-listener-sql-server"></a>Удаление прослушивателя группы доступности (SQL Server)
  В этом разделе описывается удаление прослушивателя группы доступности из группы доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Удаление прослушивателя с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
 Перед удалением прослушивателя группы доступности рекомендуется убедиться, что он не используется никакими приложениями.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Удаление прослушивателя группы доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и щелкните имя сервера, чтобы развернуть его дерево.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Разверните узел группы доступности и разверните узел **Прослушиватели группы доступности** .  
  
4.  Правой кнопкой щелкните прослушиватель, который необходимо удалить, и выберите команду **Удалить** .  
  
5.  Откроется диалоговое окно **Удаление прослушивателя из группы доступности** . Дополнительные сведения см. в подразделе [Удаление прослушивателя из группы доступности](#AgListenerPropertiesDialog)далее в этом разделе.  
  
###  <a name="remove-listener-from-availability-group-dialog-box"></a><a name="AgListenerPropertiesDialog"></a>Удалить прослушиватель из группы доступности (диалоговое окно)  
 **имя**;  
 Имя удаляемого прослушивателя.  
  
 **Результат**  
 Отображает ссылку **Успешно** или **Ошибка**, которую можно щелкнуть для получения дополнительных сведений.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Удаление прослушивателя группы доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *group_name* удалить прослушиватель **" *`dns_name`* "**  
  
     где *group_name* — имя группы доступности, а *dns_name* — DNS-имя прослушивателя группы доступности.  
  
     В следующем примере выполняется удаление прослушивателя группы доступности `AccountsAG` . Имя DNS — AccountsAG_Listener.  
  
    ```sql
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER 'AccountsAG_Listener';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
 **Удаление прослушивателя группы доступности**  
  
1.  Установите значение по умолчанию (`cd`) равным серверу экземпляра, на котором размещена первичная реплика.  
  
2.  Для удаления прослушивателя используйте встроенный командлет `Remove-Item`. Например, следующая команда удаляет прослушиватель с именем `MyListener` из группы доступности с именем `MyAg`.  
  
    ```powershell
    Remove-Item SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Просмотр свойств прослушивателя группы доступности (SQL Server)](view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md)  
