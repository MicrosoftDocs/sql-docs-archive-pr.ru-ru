---
title: Метаданные параметров и наборов строк | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- metadata [OLE DB]
ms.assetid: 31b318a4-20e7-4db0-b367-eb9938859029
author: rothja
ms.author: jroth
ms.openlocfilehash: f3bddb4d83a8904b3def70853fe1e6614dd48d9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730634"
---
# <a name="parameter-and-rowset-metadata"></a>Метаданные параметров и наборов строк
  В этом разделе приведены сведения о следующем типе и элементах типа, связанных с усовершенствованиями даты и времени OLE DB.  
  
-   Структура DBBINDING  
  
-   `ICommandWithParameters::GetParameterInfo`  
  
-   `ICommandWithParameters::SetParameterInfo`  
  
-   `IColumnsRowset::GetColumnsRowset`  
  
-   `IColumnsInfo::GetColumnInfo`  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Следующие сведения возвращаются в структуре DBPARAMINFO с помощью *prgParamInfo*:  
  
|Тип параметра|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|Дата|DBTYPE_DBDATE|6|10|0|Очистить|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Присвойте параметру|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Очистить|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Очистить|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21.27|0..7|Присвойте параметру|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28.34|0..7|Присвойте параметру|  
  
 Обратите внимание, что в некоторых случаях диапазоны значений не являются непрерывными. Это следствие добавления десятичной запятой, когда точность в долях секунды выше нуля.  
  
 Параметр DBPARAMFLAGS_SS_ISVARIABLESCALE допустим только при соединении с сервером [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версией). DBPARAMFLAGS_SS_ISVARIABLESCALE никогда не задается при соединении с серверами низкого уровня.  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>Метод ICommandWithParameters::SetParameterInfo и неявные типы параметров  
 Сведения, предоставленные в структуре DBPARAMBINDINFO, должны соответствовать следующим требованиям.  
  
|*pwszDataSourceType*<br /><br /> (зависит от поставщика)|*pwszDataSourceType*<br /><br /> (OLE DB, обычный)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|Не учитывается|  
|Дата|DBTYPE_DBDATE|6|Не учитывается|  
||DBTYPE_DBTIME|10|Не учитывается|  
|time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|Не учитывается|  
|DATETIME||16|Не учитывается|  
|datetime2 или DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 Параметр *bPrecision* не учитывается.  
  
 Значение «DBPARAMFLAGS_SS_ISVARIABLESCALE» не учитывается при отправке данных на сервер. Приложения могут принудительно использовать унаследованные типы потоков табличных данных за счет применения имен типов «`datetime`» и «`smalldatetime`», характерных для поставщика. При подключении к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] серверам (или более поздней версии) `datetime2` будет использоваться формат "", и при необходимости произойдет неявное преобразование сервера, если имя типа — " `datetime2` " или "DBTYPE_DBTIMESTAMP". *bScale* игнорируется, если используются имена типов " `datetime` " или "", определенные поставщиком `smalldatetime` . В противном случае аппикатионс должен убедиться, что *bScale* задан правильно. Приложения, обновленные с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощью MDAC и Native Client с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , используют "DBTYPE_DBTIMESTAMP", будут завершаться ошибкой, если они не устанавливают *bScale* правильно. При соединении с экземплярами сервера версии ниже [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] значение параметра *bScale*, отличное от 0 или 3 с именем "DBTYPE_DBTIMESTAMP", является ошибкой. В этом случае будет возвращено E_FAIL.  
  
 Если ICommandWithParameters:: SetParameterInfo не вызывается, поставщик имплес тип сервера из типа привязки, как указано в IAccessor:: CreateAccessor следующим образом:  
  
|Тип привязки|*pwszDataSourceType*<br /><br /> (зависит от поставщика)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|Дата|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Функция `IColumnsRowset::GetColumnsRowset` возвращает следующие столбцы.  
  
|Тип столбца|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS, DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|Дата|DBTYPE_DBDATE|6|10|0|Очистить|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Присвойте параметру|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Очистить|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Очистить|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Присвойте параметру|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Присвойте параметру|  
  
 В DBCOLUMN_FLAGS, DBCOLUMNFLAGS_ISFIXEDLENGTH всегда имеет значение TRUE для типов даты-времени, а следующие флаги всегда имеют значение FALSE.  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Остальные флаги (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE и DBCOLUMNFLAGS_WRITEUNKNOWN) можно задать в зависимости от того, как определен столбец, а также от фактического запроса.  
  
 В DBCOLUMN_FLAGS новый флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE внедрен, чтобы приложения могли определять тип сервера столбцов, где DBCOLUMN_TYPE является DBTYPE_DBTIMESTAMP. Также должен использоваться флаг DBCOLUMN_SCALE или DBCOLUMN_DATETIMEPRECISION для указания типа сервера.  
  
 Флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE допустим только при соединении с сервером [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версией). При соединении с серверами низкого уровня флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE остается неопределенным.  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 Структура DBCOLUMNINFO возвращает следующие данные.  
  
|Тип параметра|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|Дата|DBTYPE_DBDATE|6|10|0|Очистить|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|Присвойте параметру|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Очистить|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Очистить|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Присвойте параметру|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Присвойте параметру|  
  
 В *dwFlags* флаг DBCOLUMNFLAGS_ISFIXEDLENGTH всегда имеет значение TRUE для типов даты и времени, а следующие флаги всегда имеют значение FALSE:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 Остальные флаги (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE и DBCOLUMNFLAGS_WRITEUNKNOWN) можно задавать.  
  
 В *dwFlags* предусмотрен новый флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE, чтобы приложения могли определять тип сервера столбцов, где *wType* является DBTYPE_DBTIMESTAMP. Кроме того, для определения типа сервера необходимо использовать *bScale*.  
  
## <a name="see-also"></a>См. также:  
 [Метаданные (OLE DB)](../../database-engine/dev-guide/metadata-ole-db.md)  
  
  
