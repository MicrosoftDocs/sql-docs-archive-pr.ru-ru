---
title: SQLSetDescRec | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescRec function
ms.assetid: 203d02a2-aa09-462b-a489-a2cdd6f6023b
author: rothja
ms.author: jroth
ms.openlocfilehash: f2a6c8084f092040a3fd4cccee50d6a3b940cc45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668263"
---
# <a name="sqlsetdescrec"></a>SQLSetDescRec
  В этом разделе обсуждаются функции SQLSetDescRec, характерные для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента.  
  
## <a name="sqlsetdescrec-and-table-valued-parameters"></a>Функция SQLSetDescRec и параметры, возвращающие табличное значение  
 SQLSetDescRec можно использовать для задания полей дескриптора для возвращающих табличное значение параметров и столбцов возвращающих табличное значение параметров. Столбцы возвращающих табличное значение параметров доступны только в том случае, когда в поле заголовка дескриптора SQL_SOPT_SS_PARAM_FOCUS задан порядковый номер записи, имеющей тип SQL_DESC_TYPE со значением SQL_SS_TABLE. Дополнительные сведения об атрибуте SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 В следующей таблице показано сопоставление между параметрами и полями дескриптора.  
  
|Параметр|Связанный атрибут для типов параметров, не являющихся табличными, включая столбцы возвращающих табличное значение параметров|Связанные атрибуты для возвращающих табличное значение параметров|  
|---------------|--------------------------------------------------------------------------------------------------------|----------------------------------------------------|  
|*Тип*|SQL_DESC_TYPE|SQL_SS_TABLE|  
|*Подтип*|Не учитывается|Для записей типа SQL_DATETIME и SQL_INTERVAL этот атрибут должен иметь значение SQL_DESC_DATETIME_INTERVAL_CODE.|  
|*Длина*|SQL_DESC_OCTET_LENGTH|Длина имени типа параметра, возвращающего табличное значение. Значение может быть равно SQL_NTS, если имя типа представляет собой строку, завершающуюся нулевым символом, или 0, если имя типа параметра, возвращающего табличное значение, не требуется.|  
|*Точность*|SQL_DESC_PRECISION|SQL_DESC_ARRAY_SIZE|  
|*Масштаб*|SQL_DESC_SCALE|Не используется. Значение этого параметра должно быть равно 0.|  
|*датаптр*|SQL_DESC_DATA_PTR в APD|SQL_CA_SS_TYPE_NAME<br /><br /> Этот параметр не является обязательным для вызова хранимых процедур; если он не требуется, можно задать значение NULL. Параметр должен быть задан для инструкций SQL, не являющихся вызовами процедур.<br /><br /> *Датаптр* также служит уникальным значением, которое приложение может использовать для обнаружения этого возвращающего табличное значение параметра, если используется привязка переменных строк.|  
|*стрингленгсптр*|SQL_DESC_OCTET_LENGTH_PTR|SQL_DESC_OCTET_LENGTH_PTR<br /><br /> Для параметра, возвращающего табличное значение, этот параметр равен числу строк для переноса или значению SQL_DATA_AT_EXEC. Это указатель на значение, которое содержит число строк для перемещения с помощью SQLExecDirect.|  
|*индикаторптр*|SQL_DESC_INDICATOR_PTR|SQL_DESC_INDICATOR_PTR|  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescrec-support-for-enhanced-date-and-time-features"></a>Поддержка методом SQLSetDescRec улучшенных функций даты и времени  
 Для типов даты и времени допускаются следующие значения.  
  
||*Тип*|*Подтип*|*Длина*|*Точность*|*Масштаб*|  
|-|------------|---------------|--------------|-----------------|-------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|Дата|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescrec-support-for-large-clr-udts"></a>Поддержка методом SQLSetDescRec больших определяемых пользователем типов в среде CLR  
 Функция `SQLSetDescRec` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [SQLSetDescRec](https://go.microsoft.com/fwlink/?LinkId=80704)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
