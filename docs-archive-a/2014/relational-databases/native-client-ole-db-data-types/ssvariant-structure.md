---
title: Структура SSVARIANT | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: rothja
ms.author: jroth
ms.openlocfilehash: ed05eec7f9029519c04341380b8e43abc3d443bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656390"
---
# <a name="ssvariant-structure"></a>Структура SSVARIANT
  Структура `SSVARIANT`, определяемая в файле sqlncli.h, соответствует значению DBTYPE_SQLVARIANT в поставщике OLEDB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 `SSVARIANT` представляет собой избирательное соединение. В зависимости от значения элемента vt объект-получатель может определить, какой элемент следует считывать. Значения vt соответствуют типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, структура `SSVARIANT` может содержать любой тип SQL Server. Дополнительные сведения о структуре данных для стандартных типов OLE DB см. в статье об [индикаторах типа](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Remarks  
 Если DataTypeCompat==80, несколько подтипов `SSVARIANT` становятся строками. Например, следующие значения vt будут представлены в `SSVARIANT` в виде VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Если DateTypeCompat == 0, то эти типы будут представлены в собственном формате.  
  
 Дополнительные сведения о SSPROP_INIT_DATATYPECOMPATIBILITY см. в разделе [Использование ключевых слов строки подключения с SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Файл sqlncli.h содержит макросы для доступа к значениям variant, которые упрощают разыменование типов, входящих в структуру `SSVARIANT`. В качестве примера можно рассмотреть макрос V_SS_DATETIMEOFFSET, который можно использовать следующим образом:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Полный набор макросов доступа для каждого элемента структуры `SSVARIANT` см. в файле sqlncli.hi.  
  
 Следующая таблица описывает элементы структуры `SSVARIANT`.  
  
|Член|Индикатор типа OLE DB|Тип данных OLE DB|Значение vt|Комментарии|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Указывает тип значения, которое содержится в структуре `SSVARIANT`.|  
|bTinyIntVa|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|Поддерживает тип данных `tinyint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|Поддерживает тип данных `smallint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|Поддерживает тип данных `int`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|Поддерживает тип данных `bigint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|Поддерживает тип данных `real`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|Поддерживает тип данных `float`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|Поддерживает `money` типы данных и **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|Поддерживает тип данных `bit`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|Поддерживает тип данных `uniqueidentifier`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|Поддерживает тип данных `numeric`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|Поддерживает тип данных `date`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|Поддерживает типы данных `smalldatetime`, `datetime` и `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|Поддерживает тип данных `time`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *tTime2Val* ( `DBTIME2` )<br /><br /> *bScale* ( `BYTE` ) задает масштаб для значения *tTime2Val* .|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|Поддерживает тип данных `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* ( `BYTE` ) задает масштаб для значения *тсдататимевал* .|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|Поддерживает тип данных `datetimeoffset`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *тсодатетимеоффсетвал* ( `DBTIMESTAMPOFFSET` )<br /><br /> *bScale* ( `BYTE` ) задает масштаб для значения *тсодатетимеоффсетвал* .|  
|NCharVal|Отсутствует соответствующий индикатор типа OLE DB.|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|Поддерживает `nchar` типы данных и **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *сактуалленгс* ( `SHORT` ) задает фактическую длину строки, в которую *пвчнчарвал* Points. Не содержит завершающего нуля.<br /><br /> *смаксленгс* ( `SHORT` ) задает максимальную длину строки, в которую *пвчнчарвал* указывает.<br /><br /> Указатель *пвчнчарвал* ( `WCHAR` \* ) на строку.<br /><br /> Неиспользуемые элементы: *rgbReserved*, *dwReserved* и *pwchReserved*.|  
|CharVal|Отсутствует соответствующий индикатор типа OLE DB.|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|Поддерживает `char` типы данных и **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *сактуалленгс* ( `SHORT` ) задает фактическую длину строки, в которую *пччарвал* Points. Не содержит завершающего нуля.<br /><br /> *смаксленгс* ( `SHORT` ) задает максимальную длину строки, в которую *пччарвал* указывает.<br /><br /> Указатель *пччарвал* ( `CHAR` \* ) на строку.<br /><br /> Неиспользуемые элементы:<br /><br /> *rgbReserved*, *dwReserved* и *pwchReserved*.|  
|BinaryVal|Отсутствует соответствующий индикатор типа OLE DB.|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|Поддерживает `binary` типы данных и **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *сактуалленгс* ( `SHORT` ) задает фактическую длину данных, на которые указывает *пргббинаривал* .<br /><br /> *смаксленгс* ( `SHORT` ) задает максимальную длину данных, на которые указывает *пргббинаривал* .<br /><br /> *пргббинаривал* ( `BYTE` \* ) указатель на двоичные данные.<br /><br /> Неиспользуемый элемент: *dwReserved*.|  
|UnknownType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
|BLOBType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (OLE DB)](data-types-ole-db.md)  
  
  
