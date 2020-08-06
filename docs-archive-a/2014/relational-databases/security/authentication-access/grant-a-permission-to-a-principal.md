---
title: Предоставление разрешения для субъекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Grant permission to a principal
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4256d62bdeac2d79c51e5f3792c991e0e3b15096
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750632"
---
# <a name="grant-a-permission-to-a-principal"></a>Предоставление разрешения для участника
  В данном разделе содержатся инструкции по предоставлению разрешения участнику [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Предоставление разрешения участнику с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Рассмотрим следующие рекомендации, которые упростят управление разрешениями.  
  
-   Предоставляйте разрешения ролям, а не отдельным именам входа или пользователям. Когда один пользователь заменяет другого, удалите уходящего пользователя из роли и добавьте в нее нового. Все разрешения, связанные с ролью, автоматически становятся доступными для нового пользователя. Если нескольким лицам в организации нужны одинаковые разрешения, то добавление их в одну роль предоставит им одинаковые разрешения.  
  
-   Поместите сходные защищаемые объекты (таблицы, представления и процедуры) в одну схему, а затем предоставьте этой схеме разрешения. Например, схема платежной ведомости может содержать несколько таблиц, представлений и хранимых процедур. Предоставляя доступ к схеме, можно сразу предоставить все разрешения, необходимые для осуществления расчетов. Дополнительные сведения о защищаемых объектах, которым можно предоставлять разрешения, см. в разделе [Securables](../securables.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Лицо, предоставляющее разрешение (или участник, указанный с аргументом AS), должны иметь либо само разрешение с аргументом GRANT OPTION, либо разрешение более высокого уровня, которое включает в себя предоставленное разрешение. Члены предопределенной роли сервера **sysadmin** могут предоставлять любые разрешения.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-grant-permission-to-a-principal"></a>Предоставление разрешения участнику  
  
1.  В обозревателе объектов разверните базу данных, содержащую объект, которому необходимо предоставить разрешение.  
  
    > [!NOTE]  
    >  Как правило, эти действия используются для предоставления разрешений хранимым процедурам, но их можно использовать и для добавления разрешений таблицам, представлениям, функциям, сборкам и другим защищаемым объектам. Дополнительные сведения см. в разделе [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql).  
  
2.  Разверните папку **Программирование** .  
  
3.  Разверните папку **Хранимые процедуры** .  
  
4.  Щелкните правой кнопкой мыши хранимую процедуру и выберите **Свойства**.  
  
5.  В диалоговом окне **Свойства хранимой процедуры —**_stored_procedure_name_ в разделе Выбор страницы выберите **разрешения**. Данная страница используется для добавления пользователей или ролей к хранимым процедурам и для назначения разрешений этим пользователям и ролям.  
  
6.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-grant-permission-to-a-principal"></a>Предоставление разрешения участнику  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 Дополнительные сведения см. в статьях [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) и [Разрешения объекта GRANT (Transact-SQL)](/sql/t-sql/statements/grant-object-permissions-transact-sql).  
  
## <a name="see-also"></a>См. также:  
 [Участники (компонент Database Engine)](principals-database-engine.md)  
  
  
