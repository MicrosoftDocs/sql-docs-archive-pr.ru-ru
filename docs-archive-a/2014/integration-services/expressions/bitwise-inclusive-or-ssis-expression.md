---
title: '| (битовое включающее ИЛИ) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '| (bitwise inclusive OR)'
- bitwise inclusive OR (|)
ms.assetid: 4dce9eb2-3680-4adc-81a3-816ea52cef49
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 73d64886b433ffe5b4e06dc4870bbca06b2a53dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666184"
---
# <a name="-bitwise-inclusive-or-ssis-expression"></a>| (битовое включающее ИЛИ) (выражение служб SSIS)
  Выполняет побитовую операцию ИЛИ для двух целочисленных значений. Она сравнивает каждый бит первого операнда с соответствующим битом второго операнда. Если какой-либо из битов равен 1, соответствующий бит результата равен 1. В противном случае соответствующий бит результата равен нулю (0).  
  
 Оба условия должны относиться либо к целым числам со знаком, либо к беззнаковым целым числам.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
integer_expression1 | integer_expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *integer_expression1, integer_expression2*  
 Любое допустимое выражение: либо целое число со знаком, либо беззнаковое целое число. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Remarks  
 Если значение любого из условий — NULL, то результат выражения тоже будет NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В данном примере выполняется операция битового ИЛИ над переменными **NumberA** и **NumberB**. **NumberA** содержит 3 (00000011) а **NumberB** содержит 9 (00001001).  
  
```  
@NumberA | @NumberB  
```  
  
 Результат устанавливается в 11 (00001011).  
  
 00000011  
  
 00001001  
  
 ----------\-  
  
 00001011  
  
 В данном примере выполняется операция побитового ИЛИ над столбцами **ReorderPoint** и **SafetyStockLevel** .  
  
```  
ReorderPoint | SafetyStockLevel  
```  
  
 Если **ReorderPoint** имеет значение 10, а **SafetyStockLevel** — 8, результат вычисления выражения равен 10 (00001010).  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001010  
  
 В данном примере выполняется операция побитового ИЛИ над двумя целочисленными значениями.  
  
```  
3 | 5   
```  
  
 Значение устанавливается равным 7 (00000111).  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000111  
  
## <a name="see-also"></a>См. также:  
 [&#124;&#124; (логическое ИЛИ) (выражение служб SSIS)](logical-or-ssis-expression.md)   
 [^ (битовое исключающее ИЛИ) (выражение служб SSIS)](bitwise-exclusive-or-ssis-expression.md)   
 [Очередность и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](operators-ssis-expression.md)  
  
  
