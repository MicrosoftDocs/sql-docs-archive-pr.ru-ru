---
title: Сопоставление типов данных XSD с типами данных XPath (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
author: rothja
ms.author: jroth
ms.openlocfilehash: a4a3bd0b100dd935b5cea0d9ee4565633a9cb80e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667650"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>Сопоставление типов данных XSD с типами данных XPath (SQLXML 4.0)
  Если запрос XPath выполняется для схемы XSD, а тип XSD задан в атрибуте `xsd:type`, то XPath использует заданный тип данных при обработке запроса.  
  
 Тип данных XPath для узла выводится из типа данных XSD в схеме, как показано в следующей таблице. (Узел EmployeeID используется в демонстрационных целях.)  
  
|Тип данных XSD|Тип данных XDR|Эквивалентный<br /><br /> тип данных XPath|SQL Server<br /><br /> преобразование не используется|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|`Base64Binary`<br /><br /> `HexBinary`|`None`<br /><br /> `bin.base64bin.hex`|`Not applicable`|Нет<br /><br /> EmployeeID|  
|`Boolean`|`boolean`|`boolean`|CONVERT(bit, EmployeeID)|  
|`Decimal, integer, float, byte, short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong`|`number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8`|`number`|CONVERT(float(53), EmployeeID)|  
|`id, idref, idrefsentity, entities, notation, nmtoken, nmtokens, DateTime, string, AnyURI`|`id, idref, idrefsentity, entities, enumeration, notation, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid`|`string`|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|`decimal`|`fixed14.4`|`Not applicable (There is no data type in XPath that is equivalent to the fixed14.4 XDR data type.)`|CONVERT(money, EmployeeID)|  
|`date`|`date`|`string`|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|`time`|`time`<br /><br /> `time.tz`|`string`|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  
