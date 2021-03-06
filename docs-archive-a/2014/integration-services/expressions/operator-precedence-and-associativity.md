---
title: Очередность и ассоциативность операторов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90ec23f9e961cbe4df291b9670c09e51d5d8704b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734374"
---
# <a name="operator-precedence-and-associativity"></a>Очередность и ассоциативность операторов
  Каждый оператор в наборе операторов, поддерживаемом средством оценки выражений, имеет назначенный приоритет в иерархии приоритетов и содержит направление, в котором производится его вычисление. Направление вычисления для оператора — это ассоциативность оператора. Операторы с более высоким приоритетом выполняются раньше операторов с более низким приоритетом. Если выполнение выражения предполагает наличие нескольких операторов, порядок выполнения этих операторов определяется их приоритетом. Порядок исполнения может существенно повлиять на результирующее значение. Некоторые операторы имеют одинаковый приоритет. Если выражение содержит несколько операторов с одинаковым приоритетом, то операторы выполняются направленно, слева направо или справа налево.  
  
 В следующей таблице представлен список операторов в порядке убывания приоритета. Операторы одного уровня имеют одинаковый приоритет.  
  
|Символ оператора|Тип операции|Ассоциативность|  
|---------------------|-----------------------|-------------------|  
|( )|Выражение|Слева направо|  
|–, !, ~|Унарный|Справа налево|  
|Приведения|Унарный|Справа налево|  
|*, / ,%|Мультипликативные|Слева направо|  
|+, –|Аддитивная|Слева направо|  
|\<, >, \<=, >=|Отношение|Слева направо|  
|==, !=|Равенство|Слева направо|  
|&|Побитовое И|Слева направо|  
|^|Побитовое исключающее ИЛИ|Слева направо|  
|&#124;|Побитовое ИЛИ|Слева направо|  
|&&|Логическое И|Слева направо|  
|&#124;&#124;|Логическое ИЛИ|Слева направо|  
|? , перечислены ниже.|Условное выражение|Справа налево|  
  
## <a name="see-also"></a>См. также:  
 [Операторы (выражение служб SSIS)](operators-ssis-expression.md)  
  
  
