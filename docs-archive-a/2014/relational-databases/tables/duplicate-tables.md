---
title: Дублирование таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 793a38416f86a5b43a3e3bb2420127d7acf2af1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657630"
---
# <a name="duplicate-tables"></a>Дублирование таблиц
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно создать копию существующей таблицы с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] , создав новую таблицу и скопировав в нее сведения о столбцах из существующей таблицы.  
  
> [!IMPORTANT]  
>  Эта операция дублирует только структуру таблицы. При этом не происходит дублирования строк таблицы.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Дублирование таблицы с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется разрешение CREATE TABLE в целевой базе данных.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-duplicate-a-table"></a>Дублирование таблицы  
  
1.  Убедитесь, что есть подключение к базе данных, в которой нужно создать таблицу, и эта база данных выбрана в обозревателе объектов.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши пункт **Таблицы** , а затем выберите **Создать таблицу**.  
  
3.  В обозревателе объектов щелкните правой кнопкой мыши таблицу, которую нужно скопировать, и выберите пункт **Конструктор**.  
  
4.  Выделите столбец из существующей таблицы и в меню **Правка** выберите **Копировать**.  
  
5.  Перейдите в новую таблицу и выберите первую строку.  
  
6.  В меню **Правка** выберите **Вставить**.  
  
7.  В меню **Файл** выберите пункт **Сохранить**_table name_.  
  
8.  В диалоговом окне **Выбор имени** введите имя новой таблицы и нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a>Дублирование таблицы в редакторе запросов  
  
1.  Убедитесь, что есть подключение к базе данных, в которой нужно создать таблицу, и эта база данных выбрана в обозревателе объектов.  
  
2.  Щелкните правой кнопкой таблицу, копию которой необходимо создать, выберите команду **Создать скрипт таблицы как**, укажите **CREATE для**и выберите вариант **Создать окно редактора запросов**.  
  
3.  Измените имя таблицы.  
  
4.  Удалите все столбцы, которые не требуются в новой таблице.  
  
5.  Нажмите кнопку **Выполнить**.  
  
  
