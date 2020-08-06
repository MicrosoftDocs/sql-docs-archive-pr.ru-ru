---
title: Установка и изменение параметров сортировки для столбца | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8211569b6ce83faaec043e5eb527a60f0ddab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668917"
---
# <a name="set-or-change-the-column-collation"></a>Задание или изменение параметров сортировки столбца
  Для типов данных `char`, `varchar`, `text`, `nchar`, `nvarchar` и `ntext` параметры сортировки базы данных можно переопределить, указав другие параметры сортировки для определенного столбца таблицы одним из следующих способов.  
  
-   Предложением COLLATE в инструкциях [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) и [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql). Пример:  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Collation and Unicode Support](collation-and-unicode-support.md).  
  
-   Использование `Column.Collation` свойства в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] управляющих объектах (SMO).  
  
 Невозможно изменить параметры сортировки столбца, на который ссылаются:  
  
-   вычисляемый столбец;  
  
-   индекс;  
  
-   статистика распределения, созданная автоматически либо с помощью инструкции CREATE STATISTICS;  
  
-   ограничение CHECK;  
  
-   ограничение FOREIGN KEY.  
  
 При работе с базой данных **tempdb**предложение [COLLATE](/sql/t-sql/statements/collations) содержит параметр *database_default* , указывающий, что столбец, находящийся во временной таблице, использует параметры сортировки по умолчанию для текущей базы данных пользователя для соединения, а не параметра сортировки базы данных **tempdb**.  
  
## <a name="collations-and-text-columns"></a>Параметры сортировки и столбцы типа text  
 В столбце типа `text` можно добавлять или обновлять значения, имеющие параметры сортировки, отличные от кодовой страницы параметров сортировки по умолчанию для базы данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неявно преобразует значения в параметры сортировки столбца.  
  
## <a name="collations-and-tempdb"></a>Параметры сортировки и база данных tempdb  
 База данных **tempdb** создается каждый раз при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и имеет те же параметры сортировки по умолчанию, что и база данных **model** . Обычно они совпадают с параметрами сортировки экземпляра. Если при создании пользовательской базы данных указываются параметры сортировки, отличные от параметров сортировки базы данных **model**, то параметры сортировки пользовательской базы данных будут отличаться от базы данных **tempdb**. Все временные хранимые процедуры и временные таблицы создаются и сохраняются в базе данных **tempdb**. Это означает, что неявно столбцы временных таблиц и все константы, переменные и параметры хранимых процедур имеют параметры сортировки, отличные от сравниваемых объектов, создаваемых в постоянных таблицах и хранимых процедурах.  
  
 Это может привести к проблемам из-за различия параметров сортировки у объектов в пользовательских и системных базах данных. Например, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует параметры сортировки Latin1_General_CS_AS, выполняется следующая инструкция:  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 В рассматриваемой системе база данных **tempdb** использует параметры сортировки Latin1_General_CS_AS с кодовой страницей 1252, а база данных `TestDB` и столбец `TestPermTab.Col1` — параметры сортировки `Estonian_CS_AS` с кодовой страницей 1257. Пример:  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 Согласно предыдущему примеру, база данных **tempdb** использует параметры сортировки Latin1_General_CS_AS, а база данных `TestDB` и столбец `TestTab.Col1` параметры сортировки `Estonian_CS_AS` . Пример:  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 Поскольку база данных **tempdb** использует параметры сортировки сервера по умолчанию, а `TestPermTab.Col1` — другие параметры сортировки, SQL Server возвратит следующую ошибку: "Не удалось разрешить конфликт параметров сортировки между "Latin1_General_CI_AS_KS_WS" и "Estonian_CS_AS" в операции равенства".  
  
 Избавиться от этой ошибки можно одним из следующих способов:  
  
-   укажите, что столбец временной таблицы использует параметры сортировки по умолчанию пользовательской базы данных, а не базы данных **tempdb**. Это позволит таблице работать с аналогичными таблицами в разных базах данных, если это необходимо;  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   укажите правильные параметры сортировки в столбце `#TestTempTab` :  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Установка или изменение параметров сортировки сервера](set-or-change-the-server-collation.md)   
 [Установка и изменение параметров сортировки базы данных](set-or-change-the-database-collation.md)   
 [Поддержка параметров сортировки и Юникода](collation-and-unicode-support.md)  
  
  
