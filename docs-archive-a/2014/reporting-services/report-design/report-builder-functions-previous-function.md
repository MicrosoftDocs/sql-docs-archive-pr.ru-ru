---
title: Функция Previous (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3891deec3f152cdf46da77a7f2d11d38387c5c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659417"
---
# <a name="previous-function-report-builder-and-ssrs"></a>Функция Previous (построитель отчетов и службы SSRS)
  Возвращает значение или значение статистического выражения для предыдущего экземпляра элемента внутри заданной области.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *expression*  
 (`Variant` или `Binary`) Выражение, используемое для идентификации данных, для которого необходимо получить предыдущее значение, например `Fields!Fieldname.Value` или `Sum(Fields!Fieldname.Value)`.  
  
 *область*  
 (`String`) Необязательно. Имя группы или области данных или значение null ( `Nothing` в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ), определяющее область, из которой извлекается предыдущее значение, заданное *выражением*.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает `Variant` или `Binary`.  
  
## <a name="remarks"></a>Remarks  
 Функция `Previous` возвращает предыдущее значение для выражения, которое вычисляется в указанной области после применения всех операций сортировки и фильтрации.  
  
 Если *выражение* не содержит статистического выражения, `Previous` функция по умолчанию использует текущую область для элемента отчета.  
  
 В группе подробностей используйте функцию `Previous`, чтобы задать ссылку на значение поля в предыдущем экземпляре строки детализации.  
  
> [!NOTE]  
>  `Previous`Функция поддерживает только ссылки на поля в группе подробностей. Например, для текстового поля в группе подробностей выражение `=Previous(Fields!Quantity.Value)` возвращает данные для поля `Quantity` из предыдущей строки. Это выражение в первой строке возвращает значение NULL (`Nothing` в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).  
  
 Если *выражение* содержит агрегатную функцию, которая использует область по умолчанию, выполняет `Previous` статистическую обработку данных в предыдущем экземпляре области, указанной в вызове агрегатной функции.  
  
 Если *выражение* содержит агрегатную функцию, задающую область, отличную от используемой по умолчанию, то параметром *области* для `Previous` функции должна быть область, включающая область, указанную в вызове агрегатной функции.  
  
 Функции, `Level` `InScope` `Aggregate` и `Previous` не могут использоваться в параметре *Expression*. Параметр *recursive* для агрегатных функций не поддерживается.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Description  
 Следующий пример кода, помещенный в строку данных по умолчанию для области данных, предоставляет значение для поля `LineTotal` в предыдущей строке.  
  
### <a name="code"></a>Код  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a>Description  
 В следующем примере показано выражение, вычисляющее сумму продаж в указанный день месяца и предыдущее значение в тот же день месяца в прошлом году. Выражение добавляется в ячейку строки, относящуюся к дочерней группе `GroupbyDay`. Ее родительской группой является `GroupbyMonth`, которая имеет родительскую группу `GroupbyYear`. Выражение отображает результаты для группы GroupbyDay (область по умолчанию) и затем для группы `GroupbyYear` (родитель родительской группы `GroupbyMonth`).  
  
 Рассмотрим для примера область данных с родительской группой `Year`и ее дочерней группой `Month`, у которой имеется дочерняя группа `Day` (три вложенных уровня). Выражение `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` в строке, связанной с группой `Day` , возвращает значение продаж в тот же день и в тот же месяц прошлого года.  
  
### <a name="code"></a>Код  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
