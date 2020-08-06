---
title: Указание содержимого оси запроса (многомерные выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cellsets [MDX]
- query axis [MDX]
ms.assetid: c745ade0-738e-4a98-a3f0-3eabfd3eeba2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 28fd867b8f8caaf74e4dd704753c354368da2e89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734490"
---
# <a name="specifying-the-contents-of-a-query-axis-mdx"></a>Определение содержимого оси запроса (многомерные выражения)
  Оси запроса указывают границы набора ячеек, возвращаемого инструкцией многомерных выражений SELECT. Определение границ набора ячеек позволяет ограничить возвращаемые данные, видимые клиенту.  
  
 Для определения осей запроса используется инструкция `<SELECT query axis clause>` , связывающая набор с определенной осью запроса. Каждое значение в инструкции `<SELECT query axis clause>` определяет одну ось запроса. Число осей в наборе данных равно числу значений `<SELECT query axis clause>` в инструкции SELECT.  
  
## <a name="query-axis-syntax"></a>Синтаксис определения оси запроса  
 Для определения оси запроса в инструкции `<SELECT query axis clause>`используется следующий синтаксис:  
  
```  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression [ <SELECT dimension property list clause> ] [<HAVING clause>]  
   ON {  
      Integer_Expression |   
      AXIS( Integer_Expression ) |   
      {COLUMNS | ROWS | PAGES | SECTIONS | CHAPTERS}     
      }  
  
```  
  
 У каждой оси запроса есть номер: ноль (0) для оси x, 1 для оси y, 2 для оси z и т. д. В приведенном синтаксисе инструкции `<SELECT query axis clause>`значение `Integer_Expression` задает номер оси. В запросе многомерных выражений поддерживается до 128 осей, но очень редко в многомерных запросах встречается больше 5 осей. Для первых 5 осей можно использовать псевдонимы COLUMNS, ROWS, PAGES, SECTIONS и CHAPTERS.  
  
 В запросе многомерных выражений оси запроса не могут пропускаться. Это означает, что запрос, содержащий одну или несколько осей, не может не включать в себя промежуточные оси или оси с предыдущими номерами. Например, не может быть запроса с осью ROWS, но без оси COLUMNS, или с осями COLUMNS и PAGES без оси ROWS.  
  
 Можно, однако, указать предложение SELECT совсем без осей (то есть пустое предложение SELECT). В этом случае все измерения будут измерениями среза, а запрос многомерных выражений выберет только одну ячейку.  
  
 В приведенном выше синтаксисе оси запроса каждое значение `Set_Expression` указывает набор, определяющий содержимое оси запроса. Дополнительные сведения о наборах см. в разделе [Работа с элементами, кортежами и наборами (многомерные выражения)](working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="examples"></a>Примеры  
 Следующая простая инструкция SELECT возвращает меру Internet Sales Amount по оси столбцов и использует функцию MDX MEMBERS для возвращения всех элементов из иерархии «Календарь» в измерении «Дата» по осям строк:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 Два следующих запроса возвращают точно такие же результаты, но в них используются номера осей, а не псевдонимы:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON 0,  
{[Date].[Calendar].MEMBERS} ON 1  
FROM [Adventure Works]  
  
SELECT {[Measures].[Internet Sales Amount]} ON AXIS(0),  
{[Date].[Calendar].MEMBERS} ON AXIS(1)  
FROM [Adventure Works]  
  
```  
  
 Ключевое слово NON EMPTY, используемое до определения набора, представляет собой простой способ удаления пустых кортежей из осей. Например, в примерах, которые мы видели до сих пор, в Кубе нет данных с 2004 августа. Чтобы удалить все строки из набора ячеек, в которых отсутствуют данные во всех столбцах, просто добавьте NON EMPTY до набора по оси строк следующим образом:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 NON EMPTY можно использовать для всех осей в запросе. Сравните результаты следующих двух запросов, в первом из которых не используется NON EMPTY, а второй использует NON EMPTY на обеих осях:  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
SELECT NON EMPTY {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
```  
  
 Предложение HAVING можно использовать для фильтрации содержимого осей на основе определенного критерия. Этот метод менее гибкий по сравнению с другими, дающими те же результаты (например использованием функции FILTER), однако отличается большей простотой использования. Ниже приведен пример, возвращающий только даты, в которых значение Internet Sales Amount больше 15 000 долларов США:  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Date].MEMBERS}   
HAVING [Measures].[Internet Sales Amount]>15000  
ON ROWS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Определение содержимого оси среза (многомерные выражения)](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
