---
title: Удаление базы данных-получателя из группы доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.unjoindb.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], databases
ms.assetid: 4e51a570-58d7-4f01-9390-4198f3602576
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1c3de0afd73b46ae5594d26d1763f5bd78483efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657317"
---
# <a name="remove-a-secondary-database-from-an-availability-group-sql-server"></a>Удаление базы данных-получателя из группы доступности (SQL Server)
  В этом разделе описывается удаление базы данных-получателя из группы доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Удаление базы данных-получателя с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Дальнейшие действия**  [После удаления базы данных-получателя из группы доступности](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a>   
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> Требования и ограничения  
  
-   Эта задача поддерживается только на вторичных репликах. Необходимо подключиться к экземпляру сервера, размещающему вторичную реплику, из которой удаляется база данных.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Удаление базы данных-получателя из группы доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, размещающему вторичную реплику, из которой требуется удалить одну или несколько баз данных-получателей, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Выберите группу доступности и разверните узел **Базы данных доступности** .  
  
4.  Этот шаг зависит от того, удаляется несколько баз данных или только одна база данных.  
  
    -   Чтобы удалить несколько баз данных, используйте панель **Подробности обозревателя объектов** , чтобы просмотреть и выбрать базы данных, которые требуется удалить. Дополнительные сведения см. в разделе [Использование раздела "Подробности обозревателя объектов" для мониторинга групп доступности (среда SQL Server Management Studio)](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Чтобы удалить одну базу данных, выберите ее в **обозревателе объектов** или на панели **Подробности обозревателя объектов** .  
  
5.  Щелкните правой кнопкой мыши выбранную базу данных или базы данных и выберите в контекстном меню команду **Удалить базу данных-получателя** .  
  
6.  В диалоговом окне **Удаление базы данных из группы доступности** нажмите кнопку **ОК**, чтобы удалить все выбранные базы данных. Если все перечисленные базы данных удалять не нужно, нажмите кнопку **Отмена**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Удаление базы данных-получателя из группы доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится дополнительная реплика.  
  
2.  Используйте предложение [SET HADR в инструкции ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) следующим образом:  
  
     ALTER DATABASE *имя_базы_данных* SET HADR OFF  
  
     где *имя_базы_данных* ― имя базы данных-получателя, удаляемой из группы доступности, к которой она относится.  
  
     В следующем примере локальная база данных-получатель *MyDb2* удаляется из соответствующей группы доступности.  
  
    ```sql
    ALTER DATABASE MyDb2 SET HADR OFF;  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
 **Удаление базы данных-получателя из группы доступности**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором размещается вторичная реплика.  
  
2.  Используйте командлет **Remove-SqlAvailabilityDatabase** , указав имя базы данных доступности, которую требуется удалить из группы доступности. Когда установлено подключение к экземпляру сервера, на котором находится вторичная реплика, из группы доступности удаляется только локальная база данных-получатель.  
  
     Например, следующая команда удаляет базу данных-получатель `MyDb8` из вторичной реплики, размещенной на экземпляре сервера `SecondaryComputer\Instance`. Синхронизация данных для удаленных баз данных-получателей прекращается. Эта команда не влияет на базу данных-источник и на любые другие базы данных-получатели.  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\SecondaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb8  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-database-from-an-availability-group"></a><a name="FollowUp"></a>Дальнейшие действия. После удаления базы данных-получателя из группы доступности  
 После удаления базы данных-получателя она перестает входить в группу доступности, кроме того, из группы доступности удаляются все сведения об этой базе данных-получателе. Удаленная база данных-получатель переводится в состояние RESTORING.  
  
> [!TIP]  
>  В течение некоторого времени после удаления базы данных-получателя можно перезапустить синхронизацию данных AlwaysOn в базе данных, повторно присоединив ее к группе доступности. Дополнительные сведения см. в статье [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
 В этот момент поступить с удаленной базой данных-получателем можно следующим образом.  
  
-   Если эта база данных-получатель больше не нужна, ее можно удалить.  
  
     Дополнительные сведения см. в разделе [DROP DATABASE (Transact-SQL)](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) или [Удаление базы данных](../../../relational-databases/databases/delete-a-database.md).  
  
-   Если после удаления базы данных-получателя из группы доступности она еще может понадобиться, ее можно восстановить. Однако при восстановлении удаленной базы данных-получателя в режиме «в сети» окажутся две разные базы данных с одним именем. Необходимо обеспечить, чтобы клиенты могли получить доступ только к текущей базе данных-источнику.  
  
     Дополнительные сведения см. в разделе [Восстановление базы данных без восстановления данных (Transact-SQL)](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Удаление базы данных-источника из группы доступности (SQL Server)](remove-a-primary-database-from-an-availability-group-sql-server.md)  
