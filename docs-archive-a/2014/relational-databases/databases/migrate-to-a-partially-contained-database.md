---
title: Миграция на частично автономную базу данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, migrating to
ms.assetid: 90faac38-f79e-496d-b589-e8b2fe01c562
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6142d46dc0540e5998fa66d463538d1453a17d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751059"
---
# <a name="migrate-to-a-partially-contained-database"></a>Migrate to a Partially Contained Database
  В этом разделе описано, как подготовить к переходу на частично автономную модель базы данных, и приведены шаги по миграции.  
  
 **В этом разделе:**  
  
-   [Подготовка к миграции базы данных](#prepare)  
  
-   [Включение автономных баз данных](#enable)  
  
-   [Преобразование базы данных в частично автономную](#convert)  
  
-   [Миграция пользователей в пользователей автономной базы данных](#users)  
  
##  <a name="preparing-to-migrate-a-database"></a><a name="prepare"></a> Подготовка к миграции базы данных  
 Перед началом перевода базы данных в частичную автономную модель просмотрите следующие указания.  
  
-   Для этого потребуется понимание модели частично автономной базы данных. Дополнительные сведения см. в разделе [Contained Databases](contained-databases.md).  
  
-   Необходимо понимать риски, связанные с частично автономными базами данных. Дополнительные сведения см. в разделе [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md).  
  
-   Автономные базы данных не поддерживают репликацию, отслеживание измененных данных или отслеживание изменений. Убедитесь, что в базе данных не используются эти функции.  
  
-   Просмотрите список функций базы данных, которые изменились для частично автономных баз данных. Дополнительные сведения см. в разделе [Измененные функции (автономная база данных)](modified-features-contained-database.md).  
  
-   Выполнив запрос к представлению [sys.dm_db_uncontained_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) , найдите в базе данных неавтономные объекты или функции. Дополнительные сведения см. в разделе  
  
-   Мониторьте XEvent **database_uncontained_usage** , чтобы определить, когда используются неавтономные функции.  
  
##  <a name="enable-contained-databases"></a><a name="enable"></a> Включение автономных баз данных  
 Перед созданием автономных баз данных поддержка автономных баз данных должна быть включена на экземпляре [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
### <a name="enabling-contained-databases-using-transact-sql"></a>Включение автономных баз данных с помощью Transact-SQL  
 В следующем примере в экземпляре компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]создаются автономные базы данных.  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE ;  
GO  
```  
  
#### <a name="enabling-contained-databases-using-management-studio"></a>Включение автономных баз данных с помощью среды Management Studio  
 В следующем примере в экземпляре компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]создаются автономные базы данных.  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера и выберите пункт **Свойства**.  
  
2.  На странице **Расширенные** в разделе **Включение** установите параметр **Включить автономные базы данных** в значение **True**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="converting-a-database-to-partially-contained"></a><a name="convert"></a> Преобразование базы данных в частично автономную  
 База данных преобразуется в автономную путем изменения ее параметра **CONTAINMENT** .  
  
### <a name="converting-a-database-to-partially-contained-using-transact-sql"></a>Преобразование базы данных в частично автономную с помощью Transact-SQL  
 В следующем примере база данных показано преобразование `Accounting` в частично автономную базу данных.  
  
```sql  
USE [master]  
GO  
ALTER DATABASE [Accounting] SET CONTAINMENT = PARTIAL  
GO  
```  
  
### <a name="converting-a-database-to-partially-contained-using-management-studio"></a>Преобразование базы данных в частично автономную с помощью среды Management Studio  
 В следующем примере база данных преобразуется в частично автономную базу данных.  
  
1.  В обозревателе объектов разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных, которую нужно преобразовать, а затем выберите пункт **Свойства**.  
  
2.  На странице **Параметры** измените параметр **Тип вложения** на **Частичный**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="migrating-users-to-contained-database-users"></a><a name="users"></a> Миграция пользователей в пользователей автономной базы данных  
 В следующем примере выполняется миграция всех пользователей, основанных на имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в пользователей автономной базы данных с паролями. Этот пример исключает имена входа, которые не были включены. Этот пример должен выполняться в автономной базе данных.  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Автономные базы данных](contained-databases.md)   
 [sp_migrate_user_to_contained (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql)   
 [sys.dm_db_uncontained_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql)  
  
  
