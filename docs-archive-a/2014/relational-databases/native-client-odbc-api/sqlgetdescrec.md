---
title: SQLGetDescRec | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
author: rothja
ms.author: jroth
ms.openlocfilehash: 11e0e43b5c9cec15627b7f32ebe51fc28d74786c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656389"
---
# <a name="sqlgetdescrec"></a>SQLGetDescRec
  В этом разделе обсуждаются функции SQLGetDescRec, характерные для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента.  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a>Функция SQLGetDescRec и возвращающие табличные значения параметры  
 SQLGetDescRec можно использовать для получения значений атрибутов возвращающих табличное значение параметров и столбцов возвращающих табличное значение параметров. Параметр *рекнумбер* параметра SQLGetDescRec соответствует параметру *параметернумбер* SQLBindParameter.  
  
 Столбцы возвращающих табличное значение параметров доступны только в том случае, когда в поле заголовка дескриптора SQL_SOPT_SS_PARAM_FOCUS задан порядковый номер записи, имеющей тип SQL_DESC_TYPE со значением SQL_SS_TABLE. Дополнительные сведения о SQL_SOPT_SS_PARAM_FOCUS о см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 SQLGetDescRec возвращает следующие данные:  
  
|Параметр|Возвращающий табличное значение параметр|Столбцы возвращающих табличные значения параметров и других параметров|  
|---------------|-----------------------------|----------------------------------------------------------|  
|*имя*;|Имя параметра для вызова хранимой процедуры; в противном случае строка длины 0.|Имя столбца возвращающих табличные значения параметров.|  
|*типептр*|SQL_DESC_TYPE. Для возвращающих табличные значения параметров — SQL_SS_TABLE.|SQL_DESC_TYPE|  
|*субтипептр*|Не определено.|SQL_DESC_DATETIME_INTERVAL_CODE (для записей типа SQL_DATETIME или SQL_INTERVAL).|  
|*ленгсптр*|0|SQL_DESC_OCTET_LENGTH|  
|*преЦисионптр*|0|SQL_DESC_PRECISION|  
|*скалептр*|0|SQL_DESC_SCALE|  
|*нуллаблептр*|1|SQL_DESC_NULLABLE|  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLGetDescRec улучшенных функций даты и времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*типептр*|*субтипептр*|*ленгсптр*|*преЦисионптр*|*скалептр*|  
|-|---------------|------------------|-----------------|--------------------|----------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|Дата|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a>Поддержка функцией SQLGetDescRec больших определяемых пользователем типов (UDT) среды CLR  
 Функция `SQLGetDescRec` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [SQLGetDescRec](https://go.microsoft.com/fwlink/?LinkId=80707)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
