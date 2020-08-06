---
title: Установка параметров индекса | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- ALLOW_ROW_LOCKS option
- SORT_IN_TEMPDB option
- DROP_EXISTING clause
- large data, indexes
- PAD_INDEX
- STATISTICS_NORECOMPUTE
- MAXDOP index option, setting
- index options [SQL Server]
- MAXDOP index option
- IGNORE_DUP_KEY option
- ALLOW_PAGE_LOCKS option
- ONLINE
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9f2d7f0bbbf0d152d3f510ae9ddbe3168634ef96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739962"
---
# <a name="set-index-options"></a>Установка параметров индекса
  В этом разделе описывается процесс изменения свойств индекса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Изменение свойств индекса различными средствами.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   К индексу с помощью предложения SET в инструкции ALTER INDEX немедленно применяются следующие параметры: ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY и STATISTICS_NORECOMPUTE.  
  
-   Следующие параметры индекса можно установить при перестройке индекса с помощью инструкции ALTER INDEX REBUILD или CREATE INDEX WITH DROP_EXISTING: PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP и DROP_EXISTING (только для CREATE INDEX).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER для таблицы или представления.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-the-properties-of-an-index-in-table-designer"></a>Изменение свойств индекса при помощи конструктора таблиц.  
  
1.  В обозревателе объектов щелкните значок плюса, чтобы развернуть базу данных, содержащую таблицу, в которой необходимо изменить свойства индекса.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните правой кнопкой мыши таблицу, в которой необходимо изменить свойства индекса, а затем выберите пункт **Проект**.  
  
4.  В меню **Конструктор таблиц** выберите пункт **Индексы и ключи**.  
  
5.  Выберите индекс, свойства которого необходимо изменить. Его свойства отобразятся в основной сетке.  
  
6.  Измените значения любого или всех свойств, чтобы внести изменения в индекс.  
  
7.  Щелкните **Закрыть**.  
  
8.  В меню **Файл** выберите пункт **Сохранить**_имя_таблицы_.  
  
#### <a name="to-modify-the-properties-of-an-index-in-object-explorer"></a>Изменение свойств индекса при помощи обозревателя объектов.  
  
1.  В обозревателе объектов щелкните значок плюса, чтобы развернуть базу данных, содержащую таблицу, в которой необходимо изменить свойства индекса.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните значок плюса (+), чтобы развернуть таблицу, в которой необходимо изменить свойства индекса.  
  
4.  Чтобы развернуть папку **Индексы** , щелкните знак «плюс» (+).  
  
5.  Щелкните правой кнопкой мыши индекс, свойства которого требуется изменить, и выберите пункт **Свойства**.  
  
6.  В разделе **Выбор страницы**щелкните **Параметры**.  
  
7.  Измените значения любого или всех свойств, чтобы внести изменения в индекс.  
  
8.  Чтобы добавить столбец индекса, удалить или изменить его позицию, выберите страницу **Общие** в диалоговом окне **Свойства индекса ―**  _имя_индекса_. Дополнительные сведения см. в разделе [Index Properties F1 Help](index-properties-f1-help.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-see-the-properties-of-all-the-indexes-in-a-table"></a>Просмотр свойств всех индексов в таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### <a name="to-set-the-properties-of-an-index"></a>Задание свойств индекса  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующие примеры в окно запроса и нажмите кнопку **Выполнить**.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 Дополнительные сведения см. в разделе [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql).  
  
  
