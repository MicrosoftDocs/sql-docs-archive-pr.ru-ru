---
title: Определение таблиц и столбцов определяемого пользователем типа | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: aa9596629ed8b4877b1793fa0c56956c52989499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669430"
---
# <a name="defining-udt-tables-and-columns"></a>Определение таблиц и столбцов определяемых пользователем типов
  После регистрации в базе данных сборки, содержащей определение определяемого пользователем типа (UDT) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ее можно использовать в определении столбца.  
  
## <a name="creating-tables-with-udts"></a>Создание таблиц с использованием определяемых пользователем типов  
 Не существует специального синтаксиса для создания в таблице столбца определяемого пользователем типа. Можно использовать в определении столбца имя определяемого пользователем типа, как если бы он был одним из внутренних типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следующая инструкция CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] создает таблицу с именем **points**и столбцом с именем **ID,** который определен как `int` столбец идентификаторов и является первичным ключом для таблицы. Второй столбец называется **PointValue**и имеет тип данных **Point**. В этом примере используется имя схемы **dbo**. Обратите внимание, что требуется иметь соответствующие разрешения на указание имени схемы. Если имя схемы опущено, используется схема по умолчанию для пользователя базы данных.  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Создание индексов по столбцам определяемых пользователем типов  
 Существует два параметра для индексирования столбца определяемого пользователем типа:  
  
-   Индекс полного значения. В этом случае, если определяемый пользователем тип поддерживает двоичный режим упорядочивания, можно создать индекс для всего столбца определяемого пользователем типа при помощи инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX.  
  
-   Индекс выражений определяемого пользователем типа. Можно создать индексы материализованных вычисляемых столбцов при помощи выражений определяемого пользователем типа. Выражение определяемого пользователем типа может быть полем, методом или свойством определяемого пользователем типа. Выражение должно быть детерминированным и не осуществлять доступ к данным.  
  
 Дополнительные сведения см. в статьях [определяемые пользователем типы данных CLR](clr-user-defined-types.md) и [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
## <a name="see-also"></a>См. также:  
 [Работа с определяемыми пользователем типами в SQL Server](working-with-user-defined-types-in-sql-server.md)  
  
  
