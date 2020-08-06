---
title: Дополнительные метаданные возвращающего табличное значение параметра | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), catalog functions to retrieve metadata
- table-valued parameters (ODBC), metadata
ms.assetid: 6c193188-5185-4373-9a0d-76cfc150c828
author: rothja
ms.author: jroth
ms.openlocfilehash: 9907b6bdbabcea427e5feffd14369e8aa718094f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667081"
---
# <a name="additional-table-valued-parameter-metadata"></a>Дополнительные метаданные возвращающего табличное значение параметра
  Чтобы получить метаданные для возвращающего табличное значение параметра, приложение вызывает SQLProcedureColumns. Для возвращающего табличное значение параметра SQLProcedureColumns возвращает одну строку. Добавлены два дополнительных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбца, SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME, для предоставления сведений о схеме и каталоге для табличных типов, связанных с параметрами, возвращающими табличное значение. В соответствии со спецификацией ODBC столбцы SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME находятся перед столбцами, зависящими от драйвера, добавленными в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и после всех столбцов, обязательных для ODBC.  
  
 В следующей таблице приводится список столбцов, имеющих отношение к возвращаемым табличное значение параметрам.  
  
|Имя столбца|Тип данных|Значения/комментарии|  
|-----------------|---------------|---------------------|  
|DATA_TYPE|Smallint, не NULL|SQL_SS_TABLE|  
|TYPE_NAME|WVarchar(128), не NULL|Имя типа возвращающего табличное значение параметра.|  
|COLUMN_SIZE|Целое число|NULL|  
|BUFFER_LENGTH|Целое число|0|  
|DECIMAL_DIGITS|Smallint|NULL|  
|NUM_PREC_RADIX|Smallint|NULL|  
|NULLABLE|Smallint, не NULL|SQL_NULLABLE|  
|ПРИМЕЧАНИЯ|Varchar|NULL|  
|COLUMN_DEF|WVarchar(4000)|NULL|  
|SQL_DATA_TYPE|Smallint, не NULL|SQL_SS_TABLE|  
|SQL_DATETIME_SUB|Smallint|NULL|  
|CHAR_OCTET_LENGTH|Целое число|NULL|  
|ORDINAL_POSITION|Integer, не NULL|Порядковый номер параметра.|  
|IS_NULLABLE|Varchar|"YES"|  
|SS_TYPE_CATALOG_NAME|WVarchar(128), не NULL|Каталог, содержащий определение табличного типа для возвращающего табличное значение параметра.|  
|SS_TYPE_SCHEMA_NAME|WVarchar(128), не NULL|Схема, содержащая определение табличного типа для возвращающего табличное значение параметра.|  
  
 Столбцы типа WVarchar в спецификации ODBC определяются как тип Varchar, но в действительности во всех последних драйверах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC возвращаются как WVarchar. Это изменение было сделано, когда к спецификации ODBC 3.5 была добавлена поддержка Юникода, но оно не описано.  
  
 Для получения дополнительных метаданных для возвращающих табличное значение параметров приложение использует функции каталога SQLColumns и SQLPrimaryKeys. Перед вызовом этих функций для возвращающих табличное значение параметров приложение должно присвоить атрибуту инструкции SQL_SOPT_SS_NAME_SCOPE значение SQL_SS_NAME_SCOPE_TABLE_TYPE. Оно указывает, что приложению требуются метаданные возвращающего табличное значение типа, а не таблицы. Затем приложение передает TYPE_NAME возвращающего табличное значение параметра в виде параметра *TableName* . SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME используются с параметрами *CatalogName* и *SchemaName* соответственно, чтобы найти каталог и схему для возвращающего табличное значение параметра. Когда приложение закончит получать метаданные для возвращающего табличное значение параметра, оно должно вновь присвоить SQL_SOPT_SS_NAME_SCOPE значение по умолчанию SQL_SS_NAME_SCOPE_TABLE.  
  
 Если SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE, то запросы к связанным серверам завершаются ошибкой. Вызовы SQLColumns или SQLPrimaryKeys с каталогом, содержащим серверный компонент, завершатся ошибкой.  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличное значение параметры &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
