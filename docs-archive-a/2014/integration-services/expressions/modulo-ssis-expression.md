---
title: (Остаток от деления) (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e23152fca9c9f2c7c3ac11490a56b03d1a1f9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658913"
---
# <a name="modulo-ssis-expression"></a>(Остаток от деления) (выражение служб SSIS)
  Вычисляет целочисленный остаток после деления первого числового выражения на второе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dividend % divisor  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *dividend*  
 Делимое числовое выражение. *dividend* может быть любым допустимым числовым выражением. Дополнительные сведения см. в разделе [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Числовое выражение, на которое делится делимое. *divisor* может быть любым допустимым числовым выражением, отличным от нуля.  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Remarks  
 Оба выражения должны соответствовать целочисленному типу данных со знаком или без знака.  
  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
 Нулевой остаток от деления — недопустимый аргумент.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример вычисляет модули из двух числовых литералов. Результат 3.  
  
```  
42 % 13  
```  
  
 Этот пример вычисляет модуль от столбца **SalesQuota** и числового литерала.  
  
```  
SalesQuota % 12  
```  
  
 Этот пример вычисляет модуль из двух числовых переменных **Sales$** и **Month**. Переменная **Sales$** должна быть заключена в квадратные скобки, так как имя включает символ $. Дополнительные сведения см. в разделе [Идентификаторы (службы SSIS)](identifiers-ssis.md).  
  
```  
@[Sales$] % @Month  
```  
  
 Этот пример использует оператор остатка от деления, чтобы определить, является ли значение переменной **Value** четным или нечетным, и использует оператор условия, чтобы вернуть строку, описывающую результат. Дополнительные сведения см. в разделе [? : (условный) (выражение служб SSIS)](conditional-ssis-expression.md).  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](operators-ssis-expression.md)  
  
  
