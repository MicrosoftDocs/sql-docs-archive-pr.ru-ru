---
title: Укажите расположение целевого сервера&#39;s (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], location
ms.assetid: 511ff311-21f5-4f2f-839f-b4deee26ec98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 938528ab78f0f457cde69d8fd4d5432cc14a79b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666324"
---
# <a name="specify-a-target-server39s-location-sql-server-management-studio"></a>Определение расположения целевого сервера (SQL Server Management Studio)
  В этом разделе описано, как задать расположение целевого сервера в конфигурации администрирования нескольких серверов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Задание расположения целевого сервера с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Выполнение этого действие ведет к изменению реестра. Редактировать реестр вручную не рекомендуется, так как неуместные или неверные изменения могут серьезно нарушить конфигурацию системы. Пользоваться программой редактирования реестра должны только опытные пользователи. Дополнительные сведения см. в документации Microsoft Windows.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-specify-a-target-servers-location"></a>Задание расположения целевого сервера  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть главный сервер, на котором необходимо задать расположение целевого сервера.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  Щелкните правой кнопкой мыши целевой сервер и выберите пункт **Свойства**.  
  
4.  В окне **Расположение** введите расположение сервера, затем нажмите **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-specify-a-target-servers-location"></a>Задание расположения целевого сервера  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb ;  
    GO  
    -- enlists the current server into the AdventureWorks1 master server.   
    -- The location for the current server is Building 21, Room 309, Rack 5  
    EXEC dbo.sp_msx_enlist N'AdventureWorks2012',   
        N'Building 21, Room 309, Rack 5' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).  
  
  
