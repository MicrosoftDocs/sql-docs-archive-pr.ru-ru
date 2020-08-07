---
title: Установка и настройка семантического поиска | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], installing
- semantic search [SQL Server], configuring
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d95e0bb2adf3bacf7057b881ab2e85afd50feef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733793"
---
# <a name="install-and-configure-semantic-search"></a>Установка и настройка семантического поиска
  Описывает компоненты, необходимые для статистического семантического поиска, и способы их установки и проверки.  
  
## <a name="installing-semantic-search"></a>Установка семантического поиска  
  
###  <a name="how-to-check-whether-semantic-search-is-installed"></a><a name="HowToCheckInstalled"></a>Как проверить, установлен ли семантический поиск  
 Отправьте запрос к свойству **IsFullTextInstalled** функции метаданных [SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql).  
  
 Возвращаемое значение 1 указывает, что установлен компонент Full-Text Search и семантический поиск. Возвращаемое значение 0 указывает, что они не установлены.  
  
```sql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="how-to-install-semantic-search"></a><a name="BasicsSemanticSearch"></a>Руководство. Установка семантического поиска  
 Чтобы установить семантический поиск, выберите пункт **Полнотекстовые и семантические извлечения для поиска** на странице **Устанавливаемые средства** во время установки.  
  
 Статистический семантический поиск зависит от полнотекстового поиска. Эти два дополнительных компонента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливаются совместно.  
  
## <a name="installing-or-removing-the-semantic-language-statistics-database"></a>Установка или удаление базы данных семантической статистики языка  
 Средства семантического поиска имеют дополнительную внешнюю зависимость; речь идет о базе данных семантической статистики языка. Эта база данных содержит статистические языковые модели, необходимые для семантического поиска. Каждая база данных статистики семантики языка содержит языковые модели для всех языков, поддерживаемых семантическим индексированием.  
  
###  <a name="how-to-check-whether-the-semantic-language-statistics-database-is-installed"></a><a name="HowToCheckDatabase"></a>Как проверить, установлена ли база данных Семантическая статистика языка  
 Отправьте запрос в представление каталога [sys.fulltext_semantic_language_statistics_database (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql).  
  
 Если для экземпляра установлена и зарегистрирована база данных семантической статистики языка, то результаты запроса содержат единственную строку сведений о базе данных.  
  
```vb  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="how-to-install-attach-and-register-the-semantic-language-statistics-database"></a><a name="HowToInstallModel"></a>Как установить, присоединить и зарегистрировать базу данных Семантическая статистика языка  
 База данных семантической статистики языка не устанавливается программой установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы установить базу данных семантической статистики языка как необходимый компонент для семантического индексирования, выполните следующие задачи:  
  
 **1. Установите базу данных семантической статистики языка.**  
 1.  Найдите базу данных семантической статистики языка на установочном носителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или загрузите её из Интернета.  
  
    -   Найдите пакет установщика Windows с именем файла **SemanticLanguageDatabase.msi** на установочном носителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Выберите 32-разрядную или 64-разрядную версию пакета установщика с учетом целевой системы. Имя папки, содержащей файл, обозначает 32-разрядную или 64-разрядную версию файла; само имя файла остается одинаковым для обеих версий.  
  
    -   Загрузить пакет установщика из [Microsoft?? SQL Server?? 2014 Семантическая статистика языка](https://go.microsoft.com/fwlink/?LinkID=296743) страница в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] центре загрузки.  
  
2.  Запустите пакет установщика Windows **SemanticLanguageDatabase.msi** , чтобы извлечь базу данных и файл журнала.  
  
     Предусмотрена возможность изменить каталог назначения (не обязательно). По умолчанию установщик извлекает файлы в папку с именем **базы данных семантического языка Майкрософт** в папке 32-bit или 64-bit Program Files. Файл MSI содержит файл базы данных и файл журнала в сжатом виде.  
  
3.  Переместите извлеченный файл базы данных и файл журнала в подходящее расположение в файловой системе.  
  
     Если оставить эти файлы на месте, невозможно будет извлечь еще одну копию базы данных для другого экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Файлу базы данных и файлу журнала при извлечении базы данных семантической статистики языка назначаются ограниченные разрешения в расположении по умолчанию в файловой системе. В результате, если вы перейдете из расположения по умолчанию, у вас может не оказаться разрешения на присоединение базы данных. Если при попытке присоединить базу данных возникает ошибка, переместите файлы или проверьте и исправьте разрешения файловой системы соответствующим образом.  
  
 **2. Присоедините базу данных семантической статистики языка.**  
 Присоедините базу данных к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] или вызвав инструкцию [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) с синтаксисом **FOR ATTACH**. Дополнительные сведения см. в разделе [Присоединение и отсоединение базы данных (SQL Server)](../databases/database-detach-and-attach-sql-server.md).  
  
 По умолчанию база данных имеет имя **semanticsdb**. При присоединении можно присвоить базе данных другое имя (необязательно). Это имя необходимо предоставить при регистрации базы данных в следующем шаге.  
  
```sql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 В этих образцах кода предполагается, что вы переместили базу данных из расположения по умолчанию в новое место хранения.  
  
 **3. Зарегистрируйте базу данных статистики семантики языка.**  
 Вызовите хранимую процедуру [sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) и укажите имя, присвоенное базе данных при присоединении.  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  
  
###  <a name="how-to-unregister-detach-and-remove-the-semantic-language-statistics-database"></a><a name="HowToUnregister"></a>Как отменить регистрацию, отсоединить и удалить базу данных Семантическая статистика языка  
 **Отмените регистрацию базы данных семантической статистики языка.**  
 Вызовите хранимую процедуру [sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql). Необходимость предоставлять имя базы данных отсутствует, поскольку экземпляр может иметь только одну базу данных семантической статистики языка.  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 **Отсоедините базу данных семантической статистики языка.**  
 Вызовите хранимую процедуру [sp_detach_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) и укажите имя базы данных.  
  
```sql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 **Удалите базу данных семантической статистики языка.**  
 После отмены регистрации и отсоединения базы данных можно просто удалить файл базы данных. Программы удаления не существует, отсутствует пункт в списке **Программы и компоненты** на панели управления.  
  
###  <a name="requirements-and-restrictions-for-installing-and-removing-the-semantic-language-statistics-database"></a><a name="reqinstall"></a>Требования и ограничения для установки и удаления базы данных Семантическая статистика языка  
  
-   Вы можете присоединить и зарегистрировать только одну базу данных статистики семантики языка для экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
     Для каждого экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на одном компьютере требуется отдельная физическая копия базы данных семантической статистики языка. Присоедините по одной копии к каждому экземпляру.  
  
-   Нельзя отсоединить действительную базу данных статистики семантики языка и заменить ее произвольной базой данных с тем же именем. Это приведет к сбоям активного или последующего заполнения индекса.  
  
-   База данных статистики семантики языка доступна только для чтения. Вы не можете настраивать эту базу данных. Если содержимое этой базы данных будет изменено каким-то образом, то результаты будущего семантического индексирования станут недетерминированными. Чтобы восстановить исходное состояние данных, можно удалить измененную базу данных, загрузить и прикрепить новую неизмененную копию базы данных.  
  
-   Имеется возможность отключить или удалить базу данных статистики семантики языка. При наличии активных операций индексирования, имеющих блокировки чтения в базе данных, операция отсоединения или удаления завершится ошибкой или истечет время ожидания. Это согласуется с существующим поведением. Операции семантического индексирования после удаления базы данных будут оканчиваться неудачей.  
  
## <a name="installing-optional-support-for-newer-document-types"></a>Установка дополнительной поддержки для новых типов документов  
  
###  <a name="how-to-install-the-latest-filters-for-microsoft-office-and-other-microsoft-document-types"></a><a name="office"></a>Как установить последние фильтры для Microsoft Office и других типов документов Майкрософт  
 Этот выпуск [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливает самые последние средства разбиения по словам и парадигматические модули [!INCLUDE[msCoName](../../../includes/msconame-md.md)] , но не устанавливает последние фильтры для документов [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office и других типов документов [!INCLUDE[msCoName](../../../includes/msconame-md.md)] . Эти фильтры необходимы для индексирования документов, созданных в последних версиях программ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office и других приложениях [!INCLUDE[msCoName](../../../includes/msconame-md.md)] . Чтобы загрузить последние фильтры, см. раздел [Пакеты фильтров Microsoft Office 2010](https://www.microsoft.com/download/details.aspx?id=17062).  
  
  
