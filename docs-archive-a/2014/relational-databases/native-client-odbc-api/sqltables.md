---
title: SQLTables | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: rothja
ms.author: jroth
ms.openlocfilehash: bad60aa102a7771935e37ac963e6fa0d3cb2fd57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664168"
---
# <a name="sqltables"></a>SQLTables
  SQLTables может выполняться на статическом серверном курсоре. Попытка выполнить SQLTables для обновляемого (динамического или ключевого набора ключей) курсора возвратит SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 SQLTables сообщает таблицы из всех баз данных, если параметр *CatalogName* имеет значение SQL_ALL_CATALOGS и все остальные параметры содержат значения по умолчанию (указатели NULL).  
  
 Чтобы сообщать о доступных каталогах, схемах и табличных типах, SQLTables позволяет использовать пустые строки (указатели в виде байтов нулевой длины). Пустые строки не являются значениями по умолчанию (указатели NULL).  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
 SQLTables возвращает сведения обо всех таблицах, имена которых совпадают с *TableName* и принадлежат текущему пользователю.  
  
## <a name="sqltables-and-table-valued-parameters"></a>Функция SQLTables и возвращающие табличное значение параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLTables возвращает сведения о табличных типах. Значение TABLE_TYPE, возвращаемое для табличного типа в столбце 4 результирующего набора, возвращаемого функцией SQLTables, — это ТАБЛИЧный тип. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Таблицы, представления и синонимы имеют общее пространство имен, отличающееся от пространства имен табличных типов. Хотя таблица и представление не могут иметь одинаковое имя, в одном каталоге и схеме можно иметь таблицу и табличный тип с одинаковым именем.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="example"></a>Пример  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLTables](https://go.microsoft.com/fwlink/?LinkId=59374)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
