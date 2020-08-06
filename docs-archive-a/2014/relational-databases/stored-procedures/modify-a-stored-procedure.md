---
title: Изменение хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying stored procedures
- editing stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: 13396239-6100-48ce-aa34-461358d99c92
author: stevestein
ms.author: sstein
ms.openlocfilehash: 906f0e06650da505094d18774ce86dab53d53f38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728126"
---
# <a name="modify-a-stored-procedure"></a>Изменение хранимой процедуры
    
##  <a name="this-topic-describes-how-to-modify-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> В этом разделе описывается, как изменить хранимую процедуру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Перед началом работы**  [Ограничения](#Restrictions), [Безопасность](#Security)  
  
-   **Изменение хранимой процедуры с использованием:**  [среды SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] нельзя преобразовать в хранимые процедуры CLR, и наоборот.  
  
 Если предыдущее определение процедуры было создано с параметрами WITH ENCRYPTION или WITH RECOMPILE, эти параметры будут включены только в случае, если они указаны в инструкции ALTER PROCEDURE.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER PROCEDURE на процедуру.  
  
##  <a name="how-to-modify-a-stored-procedure"></a><a name="Procedures"></a> Изменение хранимой процедуры  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Изменение процедуры в среде Management Studio**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните **Хранимые процедуры**, щелкните правой кнопкой мыши изменяемую процедуру, затем выберите **Изменить**.  
  
4.  Изменение текста хранимой процедуры.  
  
5.  Для проверки синтаксиса выберите пункт **Выполнить анализ** в меню **Запрос**.  
  
6.  Чтобы сохранить изменения определения процедуры, в меню **Запрос** выберите пункт **Выполнить**.  
  
7.  Чтобы сохранить обновленное определение процедуры в качестве скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] , в меню **Файл** выберите команду **Сохранить как...** Можно принять предложенное имя файла или заменить его новым, после чего следует нажать кнопку **Сохранить**.  
  
> [!IMPORTANT]  
>  Проверяйте все данные, вводимые пользователем. Не включайте их в сценарий, не выполнив проверку. Никогда не выполняйте команду, построенную на основании непроверенных пользовательских входных данных.  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение процедуры в редакторе запросов**  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура. Также можно выбрать необходимую базу данных из списка доступных баз данных на панели инструментов. В данном примере выберите базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
3.  В меню **Файл** выберите команду **Создать запрос**.  
  
4.  Скопируйте и вставьте следующий пример в редактор запросов. В этом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
    ```  
  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
5.  В меню **Файл** выберите команду **Создать запрос**.  
  
6.  Скопируйте и вставьте следующий пример в редактор запросов. В следующем примере изменяется процедура `uspVendorAllInfo` . Предложение EXECUTE AS CALLER удаляется, и изменяется текст процедуры, чтобы возвращать только поставщиков, предлагающих конкретный товар. Содержимое результирующего набора определяется при помощи функций `LEFT` и `CASE`.  
  
    ```  
    ALTER PROCEDURE Purchasing.uspVendorAllInfo  
        @Product varchar(25)   
    AS  
        SET NOCOUNT ON;  
        SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
        'Rating' = CASE v.CreditRating   
            WHEN 1 THEN 'Superior'  
            WHEN 2 THEN 'Excellent'  
            WHEN 3 THEN 'Above average'  
            WHEN 4 THEN 'Average'  
            WHEN 5 THEN 'Below average'  
            ELSE 'No rating'  
            END  
        , Availability = CASE v.ActiveFlag  
            WHEN 1 THEN 'Yes'  
            ELSE 'No'  
            END  
        FROM Purchasing.Vendor AS v   
        INNER JOIN Purchasing.ProductVendor AS pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product AS p   
          ON pv.ProductID = p.ProductID   
        WHERE p.Name LIKE @Product  
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
7.  Чтобы сохранить изменения определения процедуры, в меню **Запрос** выберите пункт **Выполнить**.  
  
8.  Чтобы сохранить обновленное определение процедуры в качестве скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] , в меню **Файл** выберите команду **Сохранить как...** Можно принять предложенное имя файла или заменить его новым, после чего следует нажать кнопку **Сохранить**.  
  
9. Чтобы выполнить измененную хранимую процедуру, выполните следующий пример.  
  
    ```  
    EXEC Purchasing.uspVendorAllInfo N'LL Crankarm';  
    GO  
  
    ```  
  
## <a name="see-also"></a>См. также:  
 [ALTER PROCEDURE (Transact-SQL)](/sql/t-sql/statements/alter-procedure-transact-sql)  
  
  
