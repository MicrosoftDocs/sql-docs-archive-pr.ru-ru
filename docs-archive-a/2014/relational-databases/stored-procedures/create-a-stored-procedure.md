---
title: Создание хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- new stored procedures
- stored procedures [SQL Server], creating
- creating stored procedures
ms.assetid: 76e8a6ba-1381-4620-b356-4311e1331ca7
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6781840e6a6c84773f40a6cd0557ccb79b676eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667618"
---
# <a name="create-a-stored-procedure"></a>Создание хранимой процедуры
  В этом разделе описывается, как можно создать хранимую процедуру [!INCLUDE[tsql](../../includes/tsql-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с использованием инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE PROCEDURE.  
  
##  <a name="Top"></a>   
-   **Перед началом работы**  [Разрешения](#Permissions)  
  
-   **Создание процедуры с использованием:**  [среды SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для выполнения этой инструкции требуется разрешение CREATE PROCEDURE в отношении базы данных и разрешение ALTER в отношении схемы, в которой создается процедура.  
  
##  <a name="how-to-create-a-stored-procedure"></a><a name="Procedures"></a> Создание хранимой процедуры  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Создание процедуры в обозревателе объектов**  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и узел **Программирование**.  
  
3.  Щелкните правой кнопкой мыши элемент **Хранимые процедуры**и выберите пункт **Создать хранимую процедуру**.  
  
4.  В меню **Запрос** выберите пункт **Указать значения для параметров шаблона**.  
  
5.  В диалоговом окне **Задание значений для параметров шаблона** введите для показанных параметров следующие значения.  
  
    |Параметр|Значение|  
    |---------------|-----------|  
    |Автор|*Ваше имя*|  
    |Дата создания|*Сегодняшняя дата*|  
    |Описание|Возвращает данные о сотрудниках.|  
    |Procedure_name|HumanResources.uspGetEmployeesTest|  
    |@Param1|@LastName|  
    |@Datatype_For_Param1|`nvarchar`(50)|  
    |Default_Value_For_Param1|NULL|  
    |@Param2|@FirstName|  
    |@Datatype_For_Param2|`nvarchar`(50)|  
    |Default_Value_For_Param2|NULL|  
  
6.  Нажмите кнопку **ОК**.  
  
7.  В **редакторе запросов**замените инструкцию SELECT следующей инструкцией:  
  
    ```sql  
    SELECT FirstName, LastName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory  
    WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    ```  
  
8.  Для проверки синтаксиса выберите пункт **Выполнить анализ** в меню **Запрос**. Если возвращается сообщение об ошибке, сравните инструкции с приведенными выше и при необходимости внесите исправления.  
  
9. Чтобы создать процедуру, в меню **Запрос** выберите пункт **Выполнить**. Процедура создается как объект в базе данных.  
  
10. Чтобы увидеть процедуру в обозревателе объектов, щелкните правой кнопкой мыши элемент **Хранимые процедуры** и выберите пункт **Обновить**.  
  
11. Чтобы выполнить процедуру, в обозревателе объектов щелкните правой кнопкой мыши имя хранимой процедуры **HumanResources.uspGetEmployeesTest** и выберите пункт **Выполнение хранимой процедуры**.  
  
12. В окне **Выполнение процедуры** введите Margheim в качестве значения для параметра @LastName и Diane в качестве значения для параметра @FirstName.  
  
> [!WARNING]  
>  Проверяйте все данные, вводимые пользователем. Не включайте их в сценарий, не выполнив проверку. Никогда не выполняйте команду, построенную на основании непроверенных пользовательских входных данных.  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Создание процедуры в редакторе запросов**  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В данном примере создается та же хранимая процедура, что и раньше, но с другим именем процедуры.  
  
    ```sql
    USE AdventureWorks2012;  
    GO  
    CREATE PROCEDURE HumanResources.uspGetEmployeesTest2   
        @LastName nvarchar(50),   
        @FirstName nvarchar(50)   
    AS
  
        SET NOCOUNT ON;  
        SELECT FirstName, LastName, Department  
        FROM HumanResources.vEmployeeDepartmentHistory  
        WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    GO
    ```  
  
4.  Чтобы выполнить процедуру, скопируйте следующий пример в окно создаваемого запроса и нажмите кнопку **Выполнить**. Показаны различные методы задания значений параметров.  
  
    ```sql
    EXECUTE HumanResources.uspGetEmployeesTest2 N'Ackerman', N'Pilar';  
    -- Or  
    EXEC HumanResources.uspGetEmployeesTest2 @LastName = N'Ackerman', @FirstName = N'Pilar';  
    GO  
    -- Or  
    EXECUTE HumanResources.uspGetEmployeesTest2 @FirstName = N'Pilar', @LastName = N'Ackerman';  
    GO
    ```  
  
## <a name="see-also"></a>См. также:  
 [CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql)  
  