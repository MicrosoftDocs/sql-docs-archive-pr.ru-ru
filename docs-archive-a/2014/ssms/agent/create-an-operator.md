---
title: Создание оператора | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfe07042f9a4b8ac595ada8b86e7bad131032700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731378"
---
# <a name="create-an-operator"></a>Create an Operator
  В этом разделе описывается настройка пользователя для получения уведомлений о [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заданиях агента в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Создание оператора**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Режимы отправки уведомлений с помощью пейджера и команды **net send** будут удалены из агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
-   Обратите внимание, что для использования компонента Database Mail для отправки операторам уведомлений по электронной почте и на пейджер агент SQL Server необходимо настроить для использования компонента Database Mail. Дополнительные сведения см. в разделе [Назначить предупреждения для оператора](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Создавать операторов могут только члены предопределенной роли сервера **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-an-operator"></a>Создание оператора  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором необходимо создать оператора агента SQL Server.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Операторы** и выберите пункт **Создать оператора**.  
  
     На странице **Общие** диалогового окна **Создание оператора** доступны следующие параметры.  
  
     **имя**;  
     Изменить имя оператора.  
  
     **Enabled**  
     Разрешить оператор. Если он не включен, то уведомления оператору не отправляются.  
  
     **Имя для электронной почты**  
     Определяет адрес электронной почты оператора.  
  
     **Адрес для команды net send**  
     Задает адрес, используемый для **net send**.  
  
     **Имя для сообщения на пейджер**  
     Определяет адрес электронной почты пейджера оператора.  
  
     **Расписание работы для пейджера**  
     Указывает время, когда пейджер активен.  
  
     **Понедельник — воскресенье**  
     Выберите дни, когда пейджер активен.  
  
     **Начало рабочего дня**  
     Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет сообщения на пейджер.  
  
     **Конец рабочего дня**  
     Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перестает отправлять сообщения на пейджер.  
  
     На странице **Уведомления** диалогового окна **Создание оператора** доступны следующие параметры.  
  
     **Оповещения**  
     Просмотреть предупреждения в экземпляре.  
  
     **Задания**  
     Просмотреть задания в экземпляре.  
  
     **Список предупреждений**  
     Содержит список предупреждений в экземпляре.  
  
     **Список заданий**  
     Содержит список заданий в экземпляре.  
  
     **Электронных**  
     Уведомить этого оператора, используя электронную почту.  
  
     **Пейджер**  
     Уведомить этого оператора, отправив сообщение электронной почты на адрес пейджера.  
  
     **NET SEND**  
     Уведомить этого оператора, используя **net send**.  
  
4.  После завершения создания оператора нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-an-operator"></a>Создание оператора  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- sets up the operator information for user 'danwi.' The operator is enabled.   
    -- SQL Server Agent sends notifications by pager from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql).  
  
  
