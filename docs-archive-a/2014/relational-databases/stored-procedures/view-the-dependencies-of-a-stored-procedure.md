---
title: Просмотр зависимостей хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 790684035d2db3b697fb8b718c96182eda8f1186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669367"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a><span data-ttu-id="9f943-102">Просмотр зависимостей хранимой процедуры</span><span class="sxs-lookup"><span data-stu-id="9f943-102">View the Dependencies of a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-view-stored-procedure-dependencies-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="9f943-103">В этом разделе описывается, как просмотреть зависимости хранимой процедуры [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f943-103">This topic describes how to view stored procedure dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="9f943-104">**Перед началом работы**  [Безопасность](#Security)</span><span class="sxs-lookup"><span data-stu-id="9f943-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="9f943-105">**Просмотр зависимостей хранимой процедуры с использованием:**  [среды SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="9f943-105">**To view the dependencies of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9f943-106">Перед началом</span><span class="sxs-lookup"><span data-stu-id="9f943-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9f943-107">безопасность</span><span class="sxs-lookup"><span data-stu-id="9f943-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9f943-108">Permissions</span><span class="sxs-lookup"><span data-stu-id="9f943-108">Permissions</span></span>  
 <span data-ttu-id="9f943-109">Системная функция: `sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="9f943-109">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="9f943-110">Необходимо разрешение CONTROL на упоминаемую сущность и разрешение SELECT на представление sys.dm_sql_referencing_entities.</span><span class="sxs-lookup"><span data-stu-id="9f943-110">Requires CONTROL permission on the referenced entity and SELECT permission on sys.dm_sql_referencing_entities.</span></span> <span data-ttu-id="9f943-111">Если упоминаемая сущность является функцией секционирования, необходимо разрешение CONTROL на базу данных.</span><span class="sxs-lookup"><span data-stu-id="9f943-111">When the referenced entity is a partition function, CONTROL permission on the database is required.</span></span> <span data-ttu-id="9f943-112">Разрешение SELECT по умолчанию предоставляется роли public.</span><span class="sxs-lookup"><span data-stu-id="9f943-112">By default, SELECT permission is granted to public.</span></span>  
  
 <span data-ttu-id="9f943-113">Системная функция: `sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="9f943-113">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="9f943-114">Требует разрешения SELECT для функции sys.dm_sql_referenced_entities и разрешения VIEW DEFINITION для ссылающейся сущности.</span><span class="sxs-lookup"><span data-stu-id="9f943-114">Requires SELECT permission on sys.dm_sql_referenced_entities and VIEW DEFINITION permission on the referencing entity.</span></span> <span data-ttu-id="9f943-115">Разрешение SELECT по умолчанию предоставляется роли public.</span><span class="sxs-lookup"><span data-stu-id="9f943-115">By default, SELECT permission is granted to public.</span></span> <span data-ttu-id="9f943-116">Требует разрешения VIEW DEFINITION для базы данных, либо, если ссылающаяся сущность является триггером DDL уровня базы данных, разрешения ALTER DATABASE DDL TRIGGER.</span><span class="sxs-lookup"><span data-stu-id="9f943-116">Requires VIEW DEFINITION permission on the database or ALTER DATABASE DDL TRIGGER permission on the database when the referencing entity is a database-level DDL trigger.</span></span> <span data-ttu-id="9f943-117">Если указанный модуль является триггером DDL уровня сервера, то требуется разрешение VIEW ANY DEFINITION на уровне сервера.</span><span class="sxs-lookup"><span data-stu-id="9f943-117">Requires VIEW ANY DEFINITION permission on the server when the referencing entity is a server-level DDL trigger.</span></span>  
  
 <span data-ttu-id="9f943-118">Представление каталога объектов: `sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="9f943-118">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="9f943-119">Необходимо разрешение VIEW DEFINITION в базе данных и разрешение SELECT на представление sys.sql_expression_dependencies в базе данных.</span><span class="sxs-lookup"><span data-stu-id="9f943-119">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="9f943-120">По умолчанию разрешение SELECT предоставляется только членам предопределенной роли базы данных db_owner.</span><span class="sxs-lookup"><span data-stu-id="9f943-120">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="9f943-121">Если разрешения SELECT и VIEW DEFINITION предоставлены другому пользователю, он может просматривать все зависимости в базе данных.</span><span class="sxs-lookup"><span data-stu-id="9f943-121">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="how-to-view-the-dependencies-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="9f943-122">Просмотр зависимостей хранимой процедуры</span><span class="sxs-lookup"><span data-stu-id="9f943-122">How to View the Dependencies of a Stored Procedure</span></span>  
 <span data-ttu-id="9f943-123">Можно использовать один из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="9f943-123">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="9f943-124">Среда SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9f943-124">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="9f943-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9f943-125">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9f943-126">Использование среды SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9f943-126">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9f943-127">**Просмотр зависимостей процедуры в обозревателе объектов**</span><span class="sxs-lookup"><span data-stu-id="9f943-127">**To view the dependencies of a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="9f943-128">В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.</span><span class="sxs-lookup"><span data-stu-id="9f943-128">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9f943-129">Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.</span><span class="sxs-lookup"><span data-stu-id="9f943-129">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="9f943-130">Разверните узел **Хранимые процедуры**, щелкните процедуру правой кнопкой мыши и выберите пункт **Просмотреть зависимости**.</span><span class="sxs-lookup"><span data-stu-id="9f943-130">Expand **Stored Procedures**, right-click the procedure and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="9f943-131">Просмотрите список объектов, находящихся в зависимости от процедуры.</span><span class="sxs-lookup"><span data-stu-id="9f943-131">View the list of objects that depend on the procedure.</span></span>  
  
5.  <span data-ttu-id="9f943-132">Просмотрите список объектов, от которых зависит данная процедура.</span><span class="sxs-lookup"><span data-stu-id="9f943-132">View the list of objects on which the procedure depends.</span></span>  
  
6.  <span data-ttu-id="9f943-133">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="9f943-133">Click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9f943-134">Использование Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9f943-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="9f943-135">**Просмотр зависимостей процедуры в редакторе запросов**</span><span class="sxs-lookup"><span data-stu-id="9f943-135">**To view the dependencies of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="9f943-136">Системная функция: `sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="9f943-136">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="9f943-137">Эта функция используется для отображения объектов, зависящих от процедуры.</span><span class="sxs-lookup"><span data-stu-id="9f943-137">This function is used to display the objects that depend on a procedure.</span></span>  
  
1.  <span data-ttu-id="9f943-138">В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.</span><span class="sxs-lookup"><span data-stu-id="9f943-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9f943-139">Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.</span><span class="sxs-lookup"><span data-stu-id="9f943-139">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="9f943-140">Выберите команду **Создать запрос** в меню **Файл** .</span><span class="sxs-lookup"><span data-stu-id="9f943-140">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="9f943-141">Скопируйте и вставьте следующие примеры в редактор запросов.</span><span class="sxs-lookup"><span data-stu-id="9f943-141">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="9f943-142">В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.</span><span class="sxs-lookup"><span data-stu-id="9f943-142">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="9f943-143">После того как процедура будет создана, во втором примере будет использована функция sys.dm_sql_referencing_entities для отображения объектов, зависящих от процедуры.</span><span class="sxs-lookup"><span data-stu-id="9f943-143">After the procedure is created, the second example uses the sys.dm_sql_referencing_entities function to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 <span data-ttu-id="9f943-144">Системная функция: `sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="9f943-144">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="9f943-145">Эта функция используется для отображения объектов, от которых зависит процедура.</span><span class="sxs-lookup"><span data-stu-id="9f943-145">This function is used to display the objects a procedure depends on.</span></span>  
  
1.  <span data-ttu-id="9f943-146">В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.</span><span class="sxs-lookup"><span data-stu-id="9f943-146">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9f943-147">Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.</span><span class="sxs-lookup"><span data-stu-id="9f943-147">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="9f943-148">Выберите команду **Создать запрос** в меню **Файл** .</span><span class="sxs-lookup"><span data-stu-id="9f943-148">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="9f943-149">Скопируйте и вставьте следующие примеры в редактор запросов.</span><span class="sxs-lookup"><span data-stu-id="9f943-149">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="9f943-150">В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.</span><span class="sxs-lookup"><span data-stu-id="9f943-150">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="9f943-151">После того как процедура будет создана, во втором примере будет использована функция sys.dm_sql_referencing_entities для отображения объектов, зависящих от процедуры.</span><span class="sxs-lookup"><span data-stu-id="9f943-151">After the procedure is created, the second example uses the sys.dm_sql_referenced_entities function to display the objects that the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 <span data-ttu-id="9f943-152">Представление каталога объектов: `sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="9f943-152">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="9f943-153">Это представление можно использовать для отображения объектов, от которых зависит процедура или которые зависят от процедуры.</span><span class="sxs-lookup"><span data-stu-id="9f943-153">This view can be used to display objects that a procedure depends on or that depend on a procedure.</span></span>  
  
 <span data-ttu-id="9f943-154">Отображение объектов зависит от процедуры.</span><span class="sxs-lookup"><span data-stu-id="9f943-154">Displaying the objects that depend on a procedure.</span></span>  
 1.  <span data-ttu-id="9f943-155">В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.</span><span class="sxs-lookup"><span data-stu-id="9f943-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9f943-156">Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.</span><span class="sxs-lookup"><span data-stu-id="9f943-156">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="9f943-157">Выберите команду **Создать запрос** в меню **Файл** .</span><span class="sxs-lookup"><span data-stu-id="9f943-157">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="9f943-158">Скопируйте и вставьте следующие примеры в редактор запросов.</span><span class="sxs-lookup"><span data-stu-id="9f943-158">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="9f943-159">В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.</span><span class="sxs-lookup"><span data-stu-id="9f943-159">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="9f943-160">После того как процедура будет создана, во втором примере будет использовано представление sys.sql_expression_dependencies для отображения объектов, зависящих от процедуры.</span><span class="sxs-lookup"><span data-stu-id="9f943-160">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 <span data-ttu-id="9f943-161">Отображение объектов, от которых зависит процедура.</span><span class="sxs-lookup"><span data-stu-id="9f943-161">Displaying the objects a procedure depends on.</span></span>  
 1.  <span data-ttu-id="9f943-162">В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.</span><span class="sxs-lookup"><span data-stu-id="9f943-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9f943-163">Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.</span><span class="sxs-lookup"><span data-stu-id="9f943-163">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="9f943-164">Выберите команду **Создать запрос** в меню **Файл** .</span><span class="sxs-lookup"><span data-stu-id="9f943-164">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="9f943-165">Скопируйте и вставьте следующие примеры в редактор запросов.</span><span class="sxs-lookup"><span data-stu-id="9f943-165">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="9f943-166">В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.</span><span class="sxs-lookup"><span data-stu-id="9f943-166">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="9f943-167">После того как процедура будет создана, во втором примере будет использовано представление sys.sql_expression_dependencies для отображения объектов, от которых зависит процедура.</span><span class="sxs-lookup"><span data-stu-id="9f943-167">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9f943-168">См. также:</span><span class="sxs-lookup"><span data-stu-id="9f943-168">See Also</span></span>  
 <span data-ttu-id="9f943-169">[Изменение имени хранимой процедуры](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9f943-169">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="9f943-170">[sys.dm_sql_referencing_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f943-170">[sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span></span>  
 <span data-ttu-id="9f943-171">[sys.dm_sql_referenced_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f943-171">[sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span></span>  
 [<span data-ttu-id="9f943-172">sys.sql_expression_dependencies (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9f943-172">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
