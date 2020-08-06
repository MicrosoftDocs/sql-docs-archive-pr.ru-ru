---
title: Изменение учетной записи-посредника агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], modifying
- modifying SQL Server Agent proxy
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f86793a8ddcc6fe8f981d6b367d2178c5a794ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658054"
---
# <a name="modify-a-sql-server-agent-proxy"></a>Modify a SQL Server Agent Proxy
  В этом разделе описывается изменение [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи-посредника агента в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Изменение учетной записи-посредника агента SQL Server с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Учетные записи-посредники агента[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют учетные данные для хранения сведений об учетных записях пользователей Windows. Указанный в учетных данных пользователь должен иметь разрешение «Вход в систему в качестве пакетного задания» на компьютере, где запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет действительность доступа к подсистеме учетной записи-посредника и предоставляет ей доступ при каждом выполнении шага задания. Если учетная запись-посредник больше не имеет доступа к подсистеме, шаг задания завершается ошибкой. В противном случае агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] олицетворяет пользователя, указанного в учетной записи-посреднике, и запускает шаг задания.  
  
-   Если имени входа пользователя предоставлен доступ к учетной записи-посреднику или пользователь принадлежит к любой роли с доступом к учетной записи-посреднику, то он может использовать учетную запись-посредник в шаге задания.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Создавать, изменять или удалять учетные записи-посредники могут только члены предопределенной роли сервера **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a>Изменение учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий учетную запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которую необходимо изменить.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Учетные записи-посредники** .  
  
4.  Щелкните знак "плюс", чтобы развернуть узел подсистемы, содержащий учетную запись-посредник (например, **Скрипт ActiveX**).  
  
5.  Щелкните правой кнопкой мыши учетную запись-посредник, которую требуется изменить, и выберите пункт **Свойства**.  
  
6.  В диалоговом окне**Свойства учетной записи-посредника** _proxy_name_внесите необходимые изменения в учетную запись-посредник. Дополнительные сведения о параметрах данного диалогового окна см. в разделе [Создание учетной записи-посредника агента SQL Server](create-a-sql-server-agent-proxy.md).  
  
7.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a>Изменение учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_update_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql).  
  
  
