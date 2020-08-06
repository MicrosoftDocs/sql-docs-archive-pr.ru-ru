---
title: Допустимость значений NULL и сравнение логики с тремя значениями | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b8000c1c28d5a1d3d129b6e8d01c4ab2fbbbc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751171"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Допустимость значений NULL и трехзначная логика сравнения
  Знакомые с типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователи найдут сходную семантику и точность в пространстве имен `System.Data.SqlTypes` платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Однако существуют определенные различия. В этом разделе описаны самые важные из них.  
  
## <a name="null-values"></a>Значения NULL  
 Главное различие между типами данных среды CLR и типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заключается в том, что первые не допускают значений NULL, а вторые реализуют полную семантику NULL.  
  
 Значения NULL влияют на результаты сравнений. При сравнении двух значений x и y, если x или y имеет значение NULL, то результатом некоторых логических сравнений будет значение UNKNOWN, а не TRUE или FALSE.  
  
## <a name="sqlboolean-data-type"></a>Тип данных SqlBoolean  
 Пространство имен `System.Data.SqlTypes` вводит тип `SqlBoolean` для представления трехзначной логики. Сравнения каких-либо `SqlTypes` возвращают значения типа `SqlBoolean`. Значение UNKNOWN представлено значением NULL типа `SqlBoolean`. Свойства `IsTrue`, `IsFalse` и `IsNull` обеспечивают возможность проверки значения типа `SqlBoolean`.  
  
## <a name="operations-functions-and-null-values"></a>Операции, функции и значения NULL  
 Все арифметические операторы (+,-, \* ,/,%), битовые операторы (~, & и |) и большинство функций возвращают значение null, если любой из операндов или аргументов имеет `SqlTypes` значение null. Свойство `IsNull` всегда возвращает значение TRUE или FALSE.  
  
## <a name="precision"></a>Точность  
 Максимальные значения типов данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] отличаются от максимальных значений числовых типов и типов decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, типы данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] предполагают использование максимальной точности. Однако в среде CLR для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип `SqlDecimal` обеспечивает такую же максимальную точность и масштаб, а также такую же семантику, как и у типа данных decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="overflow-detection"></a>Обнаружение переполнений  
 В среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сложение двух очень больших чисел не может вызвать исключение. При этом если не использовался оператор проверки, возвращенный результат может «обернуться по кругу» и превратиться в отрицательное целое число. В `System.Data.SqlTypes` исключения возникают для всех ошибок переполнения и потери точности, а также для ошибок деления на ноль.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
