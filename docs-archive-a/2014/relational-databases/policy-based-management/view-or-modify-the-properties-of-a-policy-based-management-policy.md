---
title: Просмотр или изменение свойств политики управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, modify policies
- Policy-Based Management, view policies
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: da2226d3049a84098eb8e561635161f73b71ab10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657696"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-policy"></a>Просмотр или изменение свойств политики управления на основе политик
  В этом разделе описывается просмотр и изменение свойств политики управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр или изменение свойств политики с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-all-policies-on-an-object"></a>Просмотр свойств всех политик в объекте  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер, базу данных или объект базы данных, укажите пункт **Политики** и выберите пункт **Просмотреть**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Просмотр политик —**_имя_объекта_, см. в статье [Диалоговое окно "Просмотр политик"](view-policies-dialog-box.md).  
  
2.  После завершения нажмите кнопку **Закрыть**.  
  
#### <a name="to-view-or-modify-a-specific-policys-properties"></a>Просмотр или изменение свойств отдельной политики  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, содержащий политику управления на основе политик, которую необходимо просмотреть или изменить.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните знак «плюс», чтобы развернуть папку **Политики** .  
  
5.  Щелкните правой кнопкой политику, свойства которой необходимо просмотреть или изменить, и выберите пункт **Свойства**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Открытие политики —**_имя_политики_, см. в статьях [Диалоговое окно "Создание новой политики" или "Открытие политики", страница "Общее"](../../integration-services/general-page-of-integration-services-designers-options.md) и [Диалоговое окно "Создание новой политики" или "Открытие политики", страница "Описание"](create-new-policy-or-open-policy-dialog-box-description-page.md).  
  
6.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-a-policys-properties"></a>Просмотр свойств политики  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 Дополнительные сведения см. в статье [syspolicy_policies (Transact-SQL)](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql).  
  
  
