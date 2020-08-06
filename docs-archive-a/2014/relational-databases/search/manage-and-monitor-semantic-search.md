---
title: Управление семантическим поиском и наблюдение за ним | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16e3af1d37f177dfe6d4e0cb090e7b8b0a4988d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733762"
---
# <a name="manage-and-monitor-semantic-search"></a>Управление и наблюдение за семантическим поиском
  Описывается процесс семантического индексирования и задачи, связанные с наблюдением за индексами и управлением ими.  
  
##  <a name="how-to-check-the-status-of-semantic-indexing"></a><a name="HowToMonitorStatus"></a>Как проверить состояние семантического индексирования  
 **Завершен ли первый этап семантического индексирования?**  
 Запросите динамическое административное представление [sys.dm_fts_index_population (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) и проверьте столбцы **status** и **status_description**.  
  
 Первый этап индексирования включает заполнение полнотекстового индекса ключевых слов и семантического индекса ключевых фраз, а также извлечение данных о подобии документов.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 **Завершен ли второй этап семантического индексирования?**  
 Запросите динамическое административное представление [sys.dm_fts_semantic_similarity_population (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql) и проверьте столбцы **status** и **status_description**.  
  
 Второй этап индексирования включает заполнение семантического индекса подобия документов.  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="how-to-check-the-size-of-the-semantic-indexes"></a><a name="HowToCheckSize"></a>Как проверить размер семантических индексов  
 **Каков логический размер семантического индекса ключевых фраз или семантического индекса подобия документов?**  
 Запросите динамическое административное представление [sys.dm_db_fts_index_physical_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql).  
  
 Логический размер отображается в количестве страниц индекса.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 **Каков общий размер полнотекстового и семантического индексов для полнотекстового каталога?**  
 Запросите свойство **IndexSize** функции метаданных [FULLTEXTCATALOGPROPERTY (Transact-SQL)](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql).  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 **Сколько элементов проиндексированы в полнотекстовом и семантическом индексах для полнотекстового каталога?**  
 Запросите свойство **ItemCount** функции метаданных [FULLTEXTCATALOGPROPERTY (Transact-SQL)](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql).  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="how-to-force-the-population-of-the-semantic-indexes"></a><a name="HowToForcePopulation"></a>Как принудительно выполнить заполнение семантических индексов  
 Можно принудительно выполнить заполнение полнотекстового и семантического индексов с помощью предложений START/STOP/PAUSE или RESUME POPULATION с таким же синтаксисом и поведением, как описано для полнотекстовых индексов. Дополнительные сведения см. в разделах [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql) и [Заполнение полнотекстовых индексов](../indexes/indexes.md).  
  
 Поскольку семантическое индексирование зависит от полнотекстового индексирования, семантические индексы заполняются только после заполнения связанных полнотекстовых индексов.  
  
 **Пример. Запуск полного заполнения полнотекстового и семантического индексов**  
  
 В следующем примере запускается заполнение полнотекстового и семантического индексов путем изменения существующего полнотекстового индекса таблицы **Production.Document** в образце базы данных AdventureWorks2012.  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="how-to-disable-or-re-enable-semantic-indexing"></a><a name="HowToDisableIndexing"></a>Как отключить или повторно включить семантическое индексирование  
 Можно включить или отключить полнотекстовое или семантическое индексирование с помощью предложений ENABLE/DISABLE с таким же синтаксисом и поведением, как описано для полнотекстовых индексов. Дополнительные сведения см. в статье [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql).  
  
 Если семантическое индексирование отключено и приостановлено, запросы к семантическим данным продолжают успешно выполняться и возвращать ранее проиндексированные данные. Такое поведение не согласуется с поведением полнотекстового поиска.  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="phases-of-semantic-indexing"></a><a name="SemanticIndexing"></a>Фазы семантического индексирования  
 Для семантического поиска индексируются два типа данных для каждого столбца, по которому он включен.  
  
1.  **Ключевые фразы**  
  
2.  **Подобие документов**  
  
 Семантическое индексирование выполняется в два этапа совместно с полнотекстовым индексированием.  
  
1.  **Этап 1**. Полнотекстовый индекс ключевых слов и семантический индекс ключевых фраз заполняются параллельно и одновременно. Одновременно извлекаются данные, необходимые для индексирования подобия документов.  
  
2.  **Этап 2**. Затем заполняется семантический индекс подобия документов. Этот индекс зависит от обоих индексов, заполненных на предыдущем этапе.  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-semantic-indexes-are-not-populated"></a><a name="ProblemNotPopulated"></a>Проблема. семантические индексы не заполнены  
 **Заполнены ли связанные полнотекстовые индексы?**  
 Поскольку семантическое индексирование зависит от полнотекстового индексирования, семантические индексы заполняются только после заполнения связанных полнотекстовых индексов.  
  
 **Правильно ли установлены и настроены компоненты полнотекстового поиска и семантического поиска?**  
 Дополнительные сведения см. в разделе [Установка и настройка семантического поиска](install-and-configure-semantic-search.md).  
  
 **Не находится ли служба FDHOST в состоянии «недоступна» и нет ли других проблем, которые могли бы вызвать сбой полнотекстового индексирования?**  
 Дополнительные сведения см. в разделе [Устранение неполадок полнотекстового индексирования](troubleshoot-full-text-indexing.md).  
  
  
