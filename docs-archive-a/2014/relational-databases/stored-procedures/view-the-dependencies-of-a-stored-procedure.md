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
# <a name="view-the-dependencies-of-a-stored-procedure"></a>Просмотр зависимостей хранимой процедуры
    
##  <a name="this-topic-describes-how-to-view-stored-procedure-dependencies-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> В этом разделе описывается, как просмотреть зависимости хранимой процедуры [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Перед началом работы**  [Безопасность](#Security)  
  
-   **Просмотр зависимостей хранимой процедуры с использованием:**  [среды SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Системная функция: `sys.dm_sql_referencing_entities`  
 Необходимо разрешение CONTROL на упоминаемую сущность и разрешение SELECT на представление sys.dm_sql_referencing_entities. Если упоминаемая сущность является функцией секционирования, необходимо разрешение CONTROL на базу данных. Разрешение SELECT по умолчанию предоставляется роли public.  
  
 Системная функция: `sys.dm_sql_referenced_entities`  
 Требует разрешения SELECT для функции sys.dm_sql_referenced_entities и разрешения VIEW DEFINITION для ссылающейся сущности. Разрешение SELECT по умолчанию предоставляется роли public. Требует разрешения VIEW DEFINITION для базы данных, либо, если ссылающаяся сущность является триггером DDL уровня базы данных, разрешения ALTER DATABASE DDL TRIGGER. Если указанный модуль является триггером DDL уровня сервера, то требуется разрешение VIEW ANY DEFINITION на уровне сервера.  
  
 Представление каталога объектов: `sys.sql_expression_dependencies`  
 Необходимо разрешение VIEW DEFINITION в базе данных и разрешение SELECT на представление sys.sql_expression_dependencies в базе данных. По умолчанию разрешение SELECT предоставляется только членам предопределенной роли базы данных db_owner. Если разрешения SELECT и VIEW DEFINITION предоставлены другому пользователю, он может просматривать все зависимости в базе данных.  
  
##  <a name="how-to-view-the-dependencies-of-a-stored-procedure"></a><a name="Procedures"></a> Просмотр зависимостей хранимой процедуры  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр зависимостей процедуры в обозревателе объектов**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните узел **Хранимые процедуры**, щелкните процедуру правой кнопкой мыши и выберите пункт **Просмотреть зависимости**.  
  
4.  Просмотрите список объектов, находящихся в зависимости от процедуры.  
  
5.  Просмотрите список объектов, от которых зависит данная процедура.  
  
6.  Нажмите кнопку **ОК**.  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр зависимостей процедуры в редакторе запросов**  
  
 Системная функция: `sys.dm_sql_referencing_entities`  
 Эта функция используется для отображения объектов, зависящих от процедуры.  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.  
  
3.  Выберите команду **Создать запрос** в меню **Файл** .  
  
4.  Скопируйте и вставьте следующие примеры в редактор запросов. В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  После того как процедура будет создана, во втором примере будет использована функция sys.dm_sql_referencing_entities для отображения объектов, зависящих от процедуры.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 Системная функция: `sys.dm_sql_referenced_entities`  
 Эта функция используется для отображения объектов, от которых зависит процедура.  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.  
  
3.  Выберите команду **Создать запрос** в меню **Файл** .  
  
4.  Скопируйте и вставьте следующие примеры в редактор запросов. В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  После того как процедура будет создана, во втором примере будет использована функция sys.dm_sql_referencing_entities для отображения объектов, зависящих от процедуры.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 Представление каталога объектов: `sys.sql_expression_dependencies`  
 Это представление можно использовать для отображения объектов, от которых зависит процедура или которые зависят от процедуры.  
  
 Отображение объектов зависит от процедуры.  
 1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.  
  
3.  Выберите команду **Создать запрос** в меню **Файл** .  
  
4.  Скопируйте и вставьте следующие примеры в редактор запросов. В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  После того как процедура будет создана, во втором примере будет использовано представление sys.sql_expression_dependencies для отображения объектов, зависящих от процедуры.  
  
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
  
 Отображение объектов, от которых зависит процедура.  
 1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.  
  
3.  Выберите команду **Создать запрос** в меню **Файл** .  
  
4.  Скопируйте и вставьте следующие примеры в редактор запросов. В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  После того как процедура будет создана, во втором примере будет использовано представление sys.sql_expression_dependencies для отображения объектов, от которых зависит процедура.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Изменение имени хранимой процедуры](rename-a-stored-procedure.md)   
 [sys.dm_sql_referencing_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)   
 [sys.dm_sql_referenced_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)   
 [sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
