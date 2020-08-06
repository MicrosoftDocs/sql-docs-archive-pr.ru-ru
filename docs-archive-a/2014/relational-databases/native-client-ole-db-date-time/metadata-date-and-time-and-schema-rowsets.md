---
title: Наборы строк даты, времени и схемы | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], schema rowsets
ms.assetid: 8c35e86f-0597-4ef4-b2b8-f643e53ed4c2
author: rothja
ms.author: jroth
ms.openlocfilehash: 71a54cd1d40101b48a0e02fc4b6a6343b04fe185
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739857"
---
# <a name="date-and-time-and-schema-rowsets"></a>Дата и время и наборы строк схемы
  В этом разделе содержатся сведения о наборе строк COLUMNS и о наборе строк PROCEDURE_PARAMETERS. Эти сведения относятся к усовершенствованиям даты и времени поставщика OLE DB, реализованного в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="columns-rowset"></a>COLUMNS, набор строк  
 Для типов даты-времени возвращаются значения следующих столбцов.  
  
|Тип столбца|DATA_TYPE|COLUMN_FLAGS, DBCOLUMFLAGS_SS_ISVARIABLESCALE|DATETIME_PRECISION|  
|-----------------|----------------|------------------------------------------------------|-------------------------|  
|Дата|DBTYPE_DBDATE|Очистить|0|  
|time|DBTYPE_DBTIME2|Присвойте параметру|0..7|  
|smalldatetime|DBTYPE_DBTIMESTAMP|Очистить|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|Очистить|3|  
|datetime2|DBTYPE_DBTIMESTAMP|Присвойте параметру|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|Присвойте параметру|0..7|  
  
 В параметре COLUMN_FLAGS флаг DBCOLUMNFLAGS_ISFIXEDLENGTH всегда имеет значение true для типов даты-времени, а следующие флаги всегда имеют значение false:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Значение остальных флагов (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE и DBCOLUMNFLAGS_WRITEUNKNOWN) может быть установлено в зависимости от того, каким образом определен столбец.  
  
 В параметре COLUMN_FLAGS появился новый флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE. Он дает приложениям возможность определять серверный тип столбцов, где значением DATA_TYPE является DBTYPE_DBTIMESTAMP. Кроме того, для определения типа сервера необходимо использовать DATETIME_PRECISION.  
  
 Флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE допустим только при соединении с сервером [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версией). DBCOLUMNFLAGS_SS_ISFIXEDSCALE остается неопределенным при соединении с серверами низкого уровня.  
  
## <a name="procedure_parameters-rowset"></a>Набор строк PROCEDURE_PARAMETERS  
 DATA_TYPE содержит те же значения, что и набор строк схемы COLUMNS, а TYPE_NAME содержит тип сервера.  
  
 Добавлен новый столбец SS_DATETIME_PRECISION. Он возвращает точность типа, как в столбце DATETIME_PRECISION, аналогично набору строк COLUMNS.  
  
## <a name="provider_types-rowset"></a>Набор строк PROVIDER_TYPES  
 Для типов даты-времени возвращаются следующие строки:  
  
|Тип -><br /><br /> Столбец|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_DBDATE|DBTYPE_DBTIME2|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMPOFFSET|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|scale|NULL|NULL|scale|scale|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|ДОСТУПНЫЙ ДЛЯ ПОИСКА|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|0|NULL|NULL|0|0|  
|MAXIMUM_SCALE|NULL|7|NULL|NULL|7|7|  
|Код GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE, если только не выполняется одно из следующих условий.<br /><br /> — Клиент, подключенный к серверу нижнего уровня.<br />— Свойство соединения с совместимостью типов данных задает уровень совместимости, равный 80.|VARIANT_TRUE, если только не выполняется одно из следующих условий.<br /><br /> — Клиент, подключенный к серверу нижнего уровня.<br />— Свойство соединения с совместимостью типов данных задает уровень совместимости, равный 80.|VARIANT_TRUE|  
|IS_FIXEDLENGTH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
  
 В OLE DB для числовых и десятичных типов определяются только значения MINIMUM_SCALE и MAXIMUM_SCALE, поэтому использование этих столбцов собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для типов time, datetime2 и datetimeoffset является нестандартным.  
  
## <a name="see-also"></a>См. также:  
 [Метаданные (OLE DB)](../../database-engine/dev-guide/metadata-ole-db.md)  
  
  
