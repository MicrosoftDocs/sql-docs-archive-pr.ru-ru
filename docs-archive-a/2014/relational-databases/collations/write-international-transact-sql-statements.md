---
title: Написание инструкций Transact-SQL, адаптированных к международному использованию | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1888d1045e43e0a9839fd76a21c51500af63539a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668906"
---
# <a name="write-international-transact-sql-statements"></a>Написание инструкций Transact-SQL, адаптированных к международному использованию
  В базах данных и использующих их приложениях, в которых применяются инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , можно обеспечить большую степень языковой переносимости или поддержку нескольких языков при условии соблюдения следующих требований.  
  
-   Все элементы с типами данных `char`, `varchar` и `text` замените элементами с типами данных `nchar`, `nvarchar` и `nvarchar(max)`. Такая замена устраняет возможные проблемы с преобразованием кодовых страниц. Дополнительные сведения см. в статье [Collation and Unicode Support](collation-and-unicode-support.md).  
  
-   При выполнении сравнения и других операций со значениями месяцев и дней недели следует использовать числовые эквиваленты вместо строковых имен. При различных языковых настройках возвращаются различные названия месяцев и дней недели. Например, функция DATENAME(MONTH,GETDATE()) при выбранном английском (США) языке возвращает значение «May», при немецком — «Mai», а при французском — «mai». Вместо нее следует использовать функцию DATEPART(), в которой вместо названия месяца используется его номер. При выводе результирующих наборов пользователю лучше использовать названия из функции DATEPART(), так как они зачастую более информативны, чем числовое представление даты. Однако не следует кодировать какую-либо логику, зависящую от отображаемых названий на том или ином языке.  
  
-   При указании дат для сравнения либо ввода с помощью инструкций INSERT или UPDATE следует использовать константы, интерпретируемые одним и тем же образом для всех языковых настроек.  
  
    -   В приложениях ADO, OLE DB и ODBC следует использовать принятые в ODBC форматы отметок времени, даты и времени:  
  
         **{TS '** yyyy **-** _mm_ **-** _ддхх_**:**_mm_**:**_СС_[**.** _FFF_] **'}** Например: **{TS '** 1998 **-** 09 **-** 24 10 **:** 02 **:** 20 **'}**  
  
         **{ d'** _гггг_ **-** _мм_ **-** _дд_ **'}** , например: **{ d'** 1998**-** 09**-** 24 **'}**  
  
         **{t '** _чч_ **:** _мм_ **:** _СС_ **'}** , например: **{t '** 10:02:20 **'}**  
  
    -   В приложениях с использованием других прикладных программных API-интерфейсов, а также в скриптах языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , хранимых процедурах и триггерах следует использовать числовые строки без разделителей. Например, *yyyymmdd* в виде 19980924.  
  
    -   Приложения, использующие другие API-интерфейсы, [!INCLUDE[tsql](../../includes/tsql-md.md)] скрипты, хранимые процедуры и триггеры, должны использовать инструкцию CONVERT с параметром явного стиля для всех преобразований между типами данных,,,, `time` `date` `smalldate` `datetime` **datetime2**и `datetimeoffset` символьными строковыми типами данных. Например, следующая инструкция интерпретируется одинаково для любых настроек языка и формата даты в соединении:  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Дополнительные сведения см. в разделе [Функции CAST и CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
  
