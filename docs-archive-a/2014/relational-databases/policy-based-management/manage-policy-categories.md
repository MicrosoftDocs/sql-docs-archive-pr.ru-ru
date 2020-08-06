---
title: Управление категориями политик | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.policycategories.f1
ms.assetid: d188a819-731f-4029-98aa-780d3299a0ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 168d05dd88286263da1dca5456a2c6072e946786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657717"
---
# <a name="manage-policy-categories"></a>Управление категориями политики
  В этом разделе описывается применение любой политики или всех доступных политик в категории ко всему экземпляру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для применения политик категории к экземпляру SQL Server используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Если при использовании [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]флажок **Обязательные подписки базы данных** не установлен, каждую категорию политики будет необходимо индивидуально применить к каждому участку сервера, например базам данных или таблицам.  
  
-   Если указать несуществующую категорию политики, то во время выполнения хранимой процедуры будет создана новая категория политики и подписка будет обязательной для всех баз данных. Если затем очистить обязательную подписку для новой категории, то подписка будет применяться только к базе данных, указанной в аргументе *target_object*. Дополнительные сведения об изменении параметра обязательной подписки см. в разделе [sp_syspolicy_update_policy_category (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Эта хранимая процедура выполняется в контексте текущего владельца хранимой процедуры.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a>Применение политик категории к экземпляру SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, к которому нужно применить политики категории.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните правой кнопкой мыши элемент **Управление политиками** и выберите пункт **Управление категориями**.  
  
     В диалоговом окне **Управление категориями политики** доступны следующие данные.  
  
     **Название**  
     Имя категории политики.  
  
     **Обязательные подписки базы данных**  
     Заставляет все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применять политики из категории политики.  
  
4.  Установите или снимите флажки в разделе **Обязательные подписки базы данных** , чтобы применить ту или иную категорию политики к экземпляру SQL Server.  
  
5.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a>Применение политик категории к экземпляру SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb;  
    GO  
    -- configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
    EXEC dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
    , @target_object = N'AdventureWorks2012'  
    , @policy_category = N'Table Naming Policies';  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_syspolicy_add_policy_category_subscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql).  
  
  
