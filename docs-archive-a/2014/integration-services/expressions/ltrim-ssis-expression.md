---
title: LTRIM (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- LTRIM function
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 678d9d93eb1dcd7649d2085b651a08418bbcd6a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658912"
---
# <a name="ltrim-ssis-expression"></a>LTRIM (выражение служб SSIS)
  Возвращает символьное выражение после удаления начальных пробелов.  
  
> [!NOTE]  
>  Функция LTRIM не удаляет такие пробельные символы, как табуляция или перевод строки. Юникод обеспечивает элементы кода для множества различных типов пробелов, однако данная функция распознает только элемент кода 0x0020 в Юникоде. Если строки двухбайтовой кодировки (DBCS) преобразованы в Юникод, они могут включать пробелы, отличные от 0x0020. Тогда функция не в состоянии удалить такие пробелы. Для удаления всех типов пробелов можно использовать метод LTrim Microsoft Visual Basic .NET в скрипте, запускаемом из компонента скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LTRIM(character expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, из которого удаляются пробелы.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Функция LTRIM работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции LTRIM. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
 Функция LTRIM возвращает значение NULL, если аргумент принимает значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример удаляет начальные пробелы из строкового литерала. Возвращаемый результат — «Hello».  
  
```  
LTRIM("    Hello")  
```  
  
 Этот пример удаляет начальные пробелы из столбца **FirstName** .  
  
```  
LTRIM(FirstName)  
```  
  
 Этот пример удаляет начальные пробелы из переменной **FirstName** .  
  
```  
LTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>См. также:  
 [RTRIM (выражение служб SSIS)](trim-ssis-expression.md)   
 [TRIM (выражение служб SSIS)](trim-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
