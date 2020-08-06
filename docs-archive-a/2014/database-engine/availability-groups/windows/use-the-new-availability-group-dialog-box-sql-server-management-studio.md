---
title: Использование диалогового окна "Создание группы доступности" (SQL Server Management Studio) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 1b0a6421-fbd4-4bb4-87ca-657f4782c433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 811710051089dfeb402e59bf1b7f45d05c84d925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657897"
---
# <a name="use-the-new-availability-group-dialog-box-sql-server-management-studio"></a>Используйте диалоговое окно «Создание группы доступности» (SQL Server Management Studio)
  Данный раздел содержит сведения об использовании диалогового окна **Новая группа доступности** в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] для создания группы доступности AlwaysOn в экземплярах [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , которые включены для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. *Группа доступности* определяет набор пользовательских баз данных, которые будут действовать при сбое как единое целое, и набор партнеров по обеспечению отработки отказа, называемых *репликами доступности*и поддерживающих отработку отказа.  
  
> [!NOTE]  
>  Базовые сведения о группах доступности см. в разделе [Обзор групп доступности AlwaysOn (SQL Server)](overview-of-always-on-availability-groups-sql-server.md).  
  

> [!NOTE]  
>  Дополнительные сведения о других способах создания группы доступности см. в подразделе [Связанные задачи](#RelatedTasks)далее в этом разделе.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
 Настоятельно рекомендуется прочитать этот раздел, прежде чем пытаться настроить свою первую группу доступности.  
  
###  <a name="prerequisites"></a><a name="PrerequisitesRestrictions"></a> Предварительные требования  
  
-   Перед созданием группы доступности необходимо, чтобы экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на которых находятся реплики доступности, были расположены на различных узлах одной отказоустойчивой кластеризации Windows Server (WSFC). Кроме того, убедитесь, что каждый из экземпляров сервера включен для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и соответствует всем другим обязательным условиям [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] . Для получения дополнительных сведений настоятельно рекомендуется изучить раздел [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   До создания группы доступности убедитесь, что на каждом экземпляре сервера, на котором будет размещаться реплика доступности, имеется полностью работоспособная конечная точка зеркального отображения базы данных. Дополнительные сведения см. в разделе [Конечная точка зеркального отображения базы данных (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
-   Для использования диалогового окна **Создание группы доступности** необходимы сведения об именах экземпляров сервера, в которых будут размещаться реплики доступности. Также необходимы сведения об именах всех баз данных, которые требуется добавить к новой группе доступности, а также нужно убедиться, что эти базы данных соответствуют необходимым условиям и ограничениям баз данных доступности, описанным в статье [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md). Если ввести недопустимые значения, новая группа доступности не будет работать.  
  
###  <a name="limitations"></a><a name="Limitations"></a> Ограничения  
 Диалоговое окно **Создание группы доступности** нельзя использовать для выполнения следующих задач:  
  
-   Создание прослушивателя группы доступности.  
  
-   Присоединение дополнительных реплик к группе доступности.  
  
-   Выполнение синхронизации начальных данных.  
  
 Дополнительные сведения об этих задачах конфигурации см. в разделе [Дальнейшие действия. После создания группы доступности](#FollowUp) далее в этом разделе.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется членство в фиксированной роли сервера **sysadmin** и одно из разрешений: CREATE AVAILABILITY GROUP, ALTER ANY AVAILABILITY GROUP или CONTROL SERVER.  
  
##  <a name="using-the-new-availability-group-dialog-box-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование диалогового окна «Создание группы доступности» (SQL Server Management Studio)  
 **Создание группы доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и щелкните имя сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** .  
  
3.  Щелкните правой кнопкой мыши узел **Группы доступности** , а затем выберите команду **Создание группы доступности** .  
  
4.  Эта команда открывает диалоговое окно **Создание группы доступности** .  
  
5.  На странице **Общие** введите имя новой группы доступности в поле **Имя группы доступности** . Имя должно быть допустимым идентификатором SQL Server и являться уникальным во всех группах доступности в кластере WSFC. Максимальная длина имени группы доступности составляет 128 символов.  
  
6.  В сетке **Базы данных доступности** щелкните **Добавить** и введите имя локальной базы данных, которая должна принадлежать группе доступности. Повторите это действие для каждой добавляемой базы данных. При нажатии **ОК**в диалоговом окне будет выполнена проверка соответствия указанной базы данных предварительным требованиям для включения в группу доступности. Дополнительные сведения об этих предварительных требованиях см. в статье [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).  
  
7.  В сетке **Базы данных доступности** щелкните **Добавить** и введите имя экземпляра сервера для размещения вторичной реплики. В диалоговом окне не будут выполняться попытки подключения к этим экземплярам. При указании неправильного имени сервера вторичная реплика будет добавлена, но к ней нельзя будет подключиться.  
  
    > [!TIP]  
    >  Если реплика была добавлена, и не удается подключиться к экземпляру сервера, можно удалить эту реплику и добавить новую. Дополнительные сведения см. в разделах [Удаление вторичной реплики из группы доступности (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md) и [Добавление вторичной реплики к группе доступности (SQL Server)](add-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
8.  На панели **Выбор страницы** диалогового окна щелкните **Настройки резервного копирования**. Затем на странице **Настройки резервного копирования** укажите местоположение для резервного копирования в роли реплики и задайте приоритеты резервного копирования для всех экземпляров серверов, на которых будет размещаться реплика доступности для этой группы доступности. Дополнительные сведения см. в разделе [Свойства группы доступности. Создание группы доступности (страница настроек резервного копирования)](availability-group-properties-new-availability-group-backup-preferences-page.md).  
  
9. Чтобы создать группу доступности, нажмите кнопку **ОК**. После этого в диалоговом окне будет выполнена проверка соответствия указанных баз данных предварительным требованиям.  
  
     Чтобы выйти из диалогового окна без создания группы доступности, нажмите кнопку **Отмена**.  
  
##  <a name="follow-up-after-using-the-new-availability-group-dialog-box-to-create-an-availability-group"></a><a name="FollowUp"></a> Дальнейшие действия. После использования диалогового окна "Создание группы доступности" для создания группы доступности  
  
-   Потребуется поочередное подключение ко всем экземплярам сервера, на которых размещается вторичная реплика для группы доступности, и выполнение следующих действий:  
  
    1.  Присоединение новой вторичной реплики к группе доступности. Дополнительные сведения см. в разделе [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
    2.  Восстановление текущих резервных копий всех баз данных-источников и их журналов транзакций (с помощью инструкции RESTORE WITH NORECOVERY). Дополнительные сведения см. в статье [Ручная подготовка базы данных-получателя для присоединения к группе доступности (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
    3.  Все новые подготовленные базы данных-получатели немедленно присоединяются к группе доступности. Дополнительные сведения см. в статье [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
-   Для новой группы доступности рекомендуется создать прослушиватель группы доступности. Для этого необходимо подключиться к экземпляру сервера, на котором размещена текущая первичная реплика. Дополнительные сведения см. в разделе [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
 **Настройка свойств группы доступности и реплики**  
  
-   [Смена режима доступности для реплики доступности (SQL Server)](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Смена режима отработки отказа для реплики доступности (SQL Server)](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Настройка гибкой политики отработки отказа для обеспечения контроля над автоматическим переходом на другой ресурс (группы доступности AlwaysOn)](configure-flexible-automatic-failover-policy.md)  
  
-   [Укажите URL-адрес конечной точки при добавлении или изменении реплики доступности (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Настройка резервного копирования в репликах доступности (SQL Server)](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Настройка маршрутизации только для чтения в группе доступности (SQL Server)](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Изменение периода ожидания сеанса для реплики доступности (SQL Server)](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Завершение настройки группы доступности**  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Другие способы создания группы доступности**  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Создание группы доступности (Transact-SQL)](create-an-availability-group-transact-sql.md)  
  
-   [Создание группы доступности (SQL Server PowerShell)](../../../powershell/sql-server-powershell.md)  
  
 **Включение функции «Группы доступности AlwaysOn»**  
  
-   [Включение и отключение групп доступности AlwaysOn (SQL Server)](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **Настройка конечной точки зеркального отображения базы данных**  
  
-   [Создание конечной точки зеркального отображения базы данных для группы доступности AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Использование сертификатов для конечной точки зеркального отображения базы данных (Transact-SQL)](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [Укажите URL-адрес конечной точки при добавлении или изменении реплики доступности (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Устранение неполадок с конфигурацией групп доступности AlwaysOn**  
  
-   [Устранение неполадок при группы доступности AlwaysOn конфигурации (SQL Server)](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Устранение неполадок при &#40;операции добавления файла группы доступности AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> См. также  
  
-   [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Конечная точка зеркального отображения базы данных (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md)   
 [Предварительные требования, ограничения и рекомендации для группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
