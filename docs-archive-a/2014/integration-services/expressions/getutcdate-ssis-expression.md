---
title: GETUTCDATE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f157ab5641e521a42cb3c96c96446b31de5dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732853"
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (выражение служб SSIS)
  Возвращает текущую дату системы в формате времени UTC (универсальное время, или время по Гринвичу), используя формат DT_DBTIMESTAMP. Функция GETUTCDATE не имеет аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>Аргументы  
 None  
  
## <a name="result-types"></a>Типы результата  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает год текущей даты времени в формате UTC.  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 Этот пример возвращает количество дней между датой в столбце **ModifiedDate** и текущей датой в формате UTC.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 Этот пример добавляет три месяца к текущей дате в формате UTC.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>См. также:  
 [GETDATE (выражение служб SSIS)](getdate-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
