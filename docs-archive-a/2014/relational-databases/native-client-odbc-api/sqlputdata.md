---
title: SQLPutData | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: rothja
ms.author: jroth
ms.openlocfilehash: 31da9c21f9e4323a492a25629a979c66a4f7d365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668277"
---
# <a name="sqlputdata"></a>SQLPutData
  Следующие ограничения применяются при использовании SQLPutData для отправки более чем 65 535 байт данных (для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 4.21 a) или 400 КБ данных (для SQL Server версии 6,0 и более поздних) для столбца SQL_LONGVARCHAR ( `text` ), SQL_WLONGVARCHAR ( `ntext` ) или SQL_LONGVARBINARY ( `image` ):  
  
-   Параметр, на который указывает ссылка, может быть *insert_value* в инструкции INSERT.  
  
-   Параметр, на который указывает ссылка, может быть *выражением* в предложении SET инструкции UPDATE.  
  
 Отмена последовательности вызовов SQLPutData, предоставляющих данные в блоках на сервере, на котором выполняется, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приводит к частичному обновлению значения столбца при использовании версии 6,5 или более ранней. `text`Столбец, `ntext` или `image` , на который было дана ссылка при вызове SQLCancel, имеет значение промежуточного значения заполнителя.  
  
> [!NOTE]  
>  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает соединение с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранней.  
  
## <a name="diagnostics"></a>Диагностика  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Для SQLPutData существует один собственный клиент с конкретным кодом SQLSTATE:  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|22026|Строковые данные, несовпадение длины|Если длина данных в байтах для отправки была задана приложением, например с SQL_LEN_DATA_AT_EXEC (*n*), где *n* больше 0, общее число байтов, заданное приложением через SQLPutData, должно соответствовать указанной длине.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>Функция SQLPutData и параметры, возвращающие табличные значения  
 SQLPutData используется приложением при использовании привязки строк переменных с возвращающими табличные значения параметрами. Параметр *StrLen_Or_Ind* указывает, что драйвер готов к приему данных для следующей строки или строк данных возвращающего табличное значение параметра или что больше нет доступных строк:  
  
-   Значение, большее 0, указывает на доступность следующего набора значений строки.  
  
-   Значение 0 указывает, что строк для отправки больше нет.  
  
-   Значение меньше 0 является ошибочным и приводит к внесению в журнал диагностической записи со значением SQLState, равным HY090, и сообщением «Недопустимая длина строки или буфера».  
  
 Параметр *датаптр* игнорируется, но ему должно быть присвоено значение, отличное от NULL. Дополнительные сведения см. в разделе, посвященном TVP строке привязки в [Binding и передача данных значений параметров и столбцов, возвращающих](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)табличное значение.  
  
 Если *StrLen_Or_Ind* имеет любое значение, отличное от SQL_DEFAULT_PARAM или число от 0 до SQL_PARAMSET_SIZE (то есть параметр *ColumnSize* SQLBindParameter), это является ошибкой. Эта ошибка приводит к тому, что SQLPutData возвращает SQL_ERROR: SQLSTATE = HY090, "Недопустимая строка или длина буфера".  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Поддержка функции SQLPutData для улучшенных функций даты-времени  
 Значения параметров типов даты-времени преобразуются, как описано в статье [преобразования из C в SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Поддержка функции SQLPutData для больших определяемых пользователем типов данных CLR  
 Функция `SQLPutData` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLPutData](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
