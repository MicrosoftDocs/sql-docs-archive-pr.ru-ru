---
title: SQLSpecialColumns | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: rothja
ms.author: jroth
ms.openlocfilehash: c36ff73606e95ed7ee5e713b81acf7c177a42563
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664177"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
  При запросе идентификаторов строк (*идентифиертипе* SQL_BEST_ROWID) **SQLSpecialColumns** возвращает пустой результирующий набор (без строк данных) для запрошенной области, отличной от SQL_SCOPE_CURROW. Сформированный результирующий набор определяет, что столбцы допустимы только внутри этой области.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает псевдостолбцы для идентификаторов. Результирующий набор **SQLSpecialColumns** будет обозначать все столбцы как SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** может выполняться для статического курсора. Попытка выполнить **SQLSpecialColumns** на обновляемом (управляемом набором ключей или динамическом) методе возвращает SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLSpecialColumns улучшенных функций работы с данными в формате даты-времени  
 Сведения о значениях, возвращаемых для столбцов DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH и DECIMAL_DIGTS для типов даты и времени см. в разделе [метаданные каталога](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные общие сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLSpecialColumns определяемых пользователем типов больших данных CLR  
 **SQLSpecialColumns** поддерживает большие определяемые пользователем типы данных CLR (UDT). Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLSpecialColumns](https://go.microsoft.com/fwlink/?LinkId=59371)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
