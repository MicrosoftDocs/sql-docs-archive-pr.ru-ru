---
title: Изменение представлений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- views [SQL Server], modifying
- modifying views
- renaming views
ms.assetid: 2d3c14dc-43e5-4324-b8fb-f2692d330b16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10cf9ecc860d8f9b46a06ac679b0f1a8241000bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664077"
---
# <a name="modify-views"></a>Изменение представлений
  После определения представления это определение можно изменить в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] без удаления и повторного создания представления с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Изменение представления с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Изменение представлений не влияет ни на какие зависимые объекты, например хранимые процедуры или триггеры, до тех пор пока определение представления не будет изменено таким образом, что зависимый объект станет недопустимым.  
  
-   При изменении текущего представления с помощью инструкции ALTER VIEW компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] осуществляет монопольную блокировку схемы представления. Если блокировка предоставлена, и с представлением в настоящий момент не работает ни один пользователь, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] удаляет все копии представления из кэша процедур. Существующие планы, ссылающиеся на представление, остаются в кэше, но при обращении к ним выполняется повторная компиляция.  
  
-   Инструкцию ALTER VIEW можно выполнять для индексированных представлений, однако она удаляет все индексы представления.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для выполнения инструкции ALTER VIEW необходимо как минимум разрешение ALTER на объект.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-view"></a>Изменение представления  
  
1.  В **обозревателе объектов**щелкните знак «плюс» рядом с базой данных, в которой содержится представление, а затем щелкните знак «плюс» рядом с папкой **Представления** .  
  
2.  Щелкните правой кнопкой мыши представление, которое нужно изменить, и выберите пункт **Конструктор**.  
  
3.  На панели диаграмм конструктора запросов внесите изменения в представление одним из следующих способов.  
  
    1.  Установите или снимите флажки элементов, которые необходимо добавить или удалить.  
  
    2.  Щелкните правой кнопкой мыши на панели диаграмм, выберите **Добавить таблицу…** , а затем выберите дополнительные столбцы, которые необходимо добавить к представлению, в диалоговом окне **Добавить таблицу**.  
  
    3.  Щелкните правой кнопкой мыши строку заголовка таблицы, которую необходимо удалить, и выберите **Удалить**.  
  
4.  В меню **Файл** выберите пункт **Сохранить**_view name_.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-modify-a-view"></a>Изменение представления  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере сначала создается представление, а затем оно изменяется с помощью инструкции ALTER VIEW. Предложение WHERE добавляется к определению представления.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    -- Create a view.  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
  
    -- Modify the view by adding a WHERE clause to limit the rows returned.  
    ALTER VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID  
    WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;   
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [ALTER VIEW (Transact-SQL)](/sql/t-sql/statements/alter-view-transact-sql).  
  
  
