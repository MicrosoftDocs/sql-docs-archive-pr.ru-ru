---
title: ЯЗЫК и FORMAT_STRING на FORMATED_VALUE | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7534ff5f-954e-47d4-a2ed-4b5b8ccb30e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba4aacbbd440da6048680054771c86c40ef96daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654525"
---
# <a name="language-and-format_string-on-formated_value"></a>Взаимодействие свойств LANGUAGE и FORMAT_STRING для построения свойства FORMATED_VALUE
  Свойство FORMATTED_VALUE основано на взаимодействии свойств ячейки VALUE, FORMAT_STRING и LANGUAGE. В этом разделе объясняется, как эти свойства взаимодействуют для построения свойства FORMATTED_VALUE.  
  
## <a name="value-format_string-language-properties"></a>Свойства VALUE, FORMAT_STRING, LANGUAGE  
 В следующей таблице описано, что представляют собой эти свойства. Эти сведения помогут сочетать указанные свойства.  
  
 Значение  
 Неформатированное значение ячейки.  
  
 FORMAT_STRING  
 Шаблон форматирования, применяемый к значению ячейки для создания свойства FORMATTED_VALUE  
  
 ЯЗЫК  
 Спецификация локали, применяемая вместе со свойством FORMAT_STRING для создания локализованной версии свойства FORMATTED_VALUE  
  
## <a name="formatted_value-constructed"></a>Построение свойства FORMATTED_VALUE  
 Свойство FORMATTED_VALUE строится с помощью значения свойства VALUE и применения шаблона формата, указанного в свойстве FORMAT_STRING для этого значения. Кроме того, если значением форматирования является `named formatting literal`, то спецификация свойства LANGUAGE изменяет вывод свойства FORMAT_STRING так, чтобы следовать языку значения «named formatting». Все значения «named formatting literal» определяются так, что их можно локализовать. Например, `"General Date"` является спецификацией, которую можно локализовать, в противоположность шаблону `"YYYY-MM-DD hh:nn:ss",` , в котором дата представлена так, как определено шаблоном, независимо от спецификации языка.  
  
 Если между шаблоном FORMAT_STRING и спецификацией LANGUAGE возникает конфликт, то шаблон FORMAT_STRING переопределяет спецификацию LANGUAGE. Например, если FORMAT_STRING="$ #0" и LANGUAGE=1034 (испанский), а VALUE=123.456, то FORMATTED_VALUE="$ 123" вместо FORMATTED_VALUE="€ 123" (ожидаемый формат в евро), так как значение шаблона формата переопределяет указанный языковой стандарт.  
  
### <a name="examples"></a>Примеры  
 В следующих примерах показан вывод, полученный, когда свойство LANGUAGE использовалось совместно со свойством FORMAT_STRING.  
  
 В первом примере показано форматирование численных значений. Во втором примере показано форматирование значений даты и времени.  
  
 Для каждого примера дан код многомерного выражения.  
  
 `with`  
  
 `member measures.A as 5040, FORMAT_STRING="Currency"`  
  
 `member measures.B as measures.A, LANGUAGE=1034`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="$#,##0.00"`  
  
 `member measures.D as measures.A, FORMAT_STRING="Scientific"`  
  
 `member measures.E as measures.A, LANGUAGE=1034 , FORMAT_STRING="Scientific"`  
  
 `member measures.F as 0.5040, FORMAT_STRING="Percent"`  
  
 `member measures.G as measures.F, LANGUAGE=1034`  
  
 `member measures.H as 0, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.I as 59, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.J as 0, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `member measures.K as -312, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F, measures.G, measures.H, measures.I, measures.J, measures.K} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 Результаты в транспонированном виде выглядят следующим образом, если приведенный выше запрос многомерных выражений запускался с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] через сервер, а локаль клиента равна 1033:  
  
|Член|FORMATTED_VALUE|Объяснение|  
|------------|----------------------|-----------------|  
|A|$ 5 040,00|Свойство FORMAT_STRING имеет значение `Currency` , свойство LANGUAGE имеет значение `1033`, унаследованное от значения локали системы.|  
|B|€ 5 040,00|Свойство FORMAT_STRING имеет значение `Currency` (унаследованное из примера А), а свойству LANGUAGE явно задано значение `1034` (испанский), следовательно, используется знак евро, другой десятичный разделитель и другой разделитель групп разрядов.|  
|C|$ 5 040,00|Свойство FORMAT_STRING имеет значение `$#,##0.00` , переопределяющее значение Currency из примера А, а свойству LANGUAGE явно задано значение `1034` (испанский). Так как свойство FORMAT_STRING явно задает символ валюты $, свойство FORMATTED_VALUE представлено символом «$». Но так как `.` (точка) и `,` (запятая) являются заполнителями для десятичного разделителя и разделителя групп разрядов соответственно, то спецификация языкового стандарта влияет на них, создавая вывод, локализованный для десятичного разделителя и разделителей групп разрядов.|  
|D|5.04E+03|Свойство FORMAT_STRING имеет значение `Scientific` , свойство LANGUAGE имеет значение `1033`, унаследованное от значения локали системы, следовательно, десятичным разделителем является `.` (точка).|  
|E|5,04E+03|Свойство FORMAT_STRING имеет значение `Scientific` , а свойству LANGUAGE явно присвоено значение `1034,` , следовательно, десятичным разделителем является `,` (запятая).|  
|F|50,40 %|Свойство FORMAT_STRING имеет значение `Percent` , свойство LANGUAGE имеет значение `1033`, унаследованное от значения локали системы, следовательно, десятичным разделителем является `.` (точка).<br /><br /> Обратите внимание, что VALUE было изменено с 5040 на 0.5040.|  
|G|50,40 %|Свойство FORMAT_STRING имеет значение `Percent`, унаследованное из примера Е, а свойству LANGUAGE явно присвоено значение `1034` , следовательно, десятичным разделителем является `,` (запятая).<br /><br /> Обратите внимание, что VALUE было унаследовано из значения в примере Е.|  
|H|Нет|Свойство FORMAT_STRING имеет значение `YES/NO`, свойству VALUE присвоено значение 0, а свойству LANGUAGE явно задано значение `1034`. Так как нет отличия между английским "NO" и испанским "NO", пользователь не увидит отличий в значениях свойства FORMATTED_VALUE.|  
|I|SI|Свойство FORMAT_STRING имеет значение `YES/NO`, свойству VALUE присвоено значение 59, а свойству LANGUAGE явно присвоено значение `1034`. Как определено форматированием YES/NO, любое значение, отличное от нуля (0), является значением "YES", и, так как указан испанский язык, свойство FORMATTED_VALUE имеет значение "SI".|  
|J|Desactivado|Свойство FORMAT_STRING имеет значение `ON/OFF`, свойству VALUE присвоено значение 0, а свойству LANGUAGE явно присвоено значение `1034`. Как определено форматированием ON/OFF, любое значение, отличное от нуля (0), является значением "OFF", и, так как указан испанский язык, свойство FORMATTED_VALUE имеет значение "Desactivado".|  
|K|Activado|Свойство FORMAT_STRING имеет значение `ON/OFF`, свойству VALUE присвоено значение -312, а свойству LANGUAGE явно присвоено значение `1034`. Как определено форматированием ON/OFF, любое значение, отличное от нуля (0), является значением «ON», и, так как указан испанский язык, свойство FORMATTED_VALUE имеет значение «Activado».|  
  
 `with`  
  
 `member measures.A as 'CDate("1959-03-12 06:30")'`  
  
 `member measures.B as measures.A, FORMAT_STRING="Long Date"`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="General Date"`  
  
 `member measures.D as measures.A, LANGUAGE=1034, FORMAT_STRING="Long Date"`  
  
 `member measures.E as measures.A, LANGUAGE=1041 , FORMAT_STRING="General Date"`  
  
 `member measures.F as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Date"`  
  
 `member measures.G as measures.A, FORMAT_STRING="Long Time"`  
  
 `member measures.H as measures.A, FORMAT_STRING="Short Time"`  
  
 `member measures.I as measures.A, LANGUAGE=1034 , FORMAT_STRING="Long Time"`  
  
 `member measures.J as measures.A, LANGUAGE=1034 , FORMAT_STRING="Short Time"`  
  
 `member measures.K as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Time"`  
  
 `member measures.L as measures.A, LANGUAGE=1041 , FORMAT_STRING="Short Time"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F`  
  
 `, measures.G, measures.H, measures.I, measures.J, measures.K, measures.L} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 Результаты в транспонированном виде выглядят следующим образом, если приведенный выше запрос многомерных выражений запускался с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] через сервер, а локаль клиента равна 1033:  
  
|Член|FORMATTED_VALUE|Объяснение|  
|------------|----------------------|-----------------|  
|A|3/12/1959 6:30:00 AM|Свойству FORMAT_STRING явно присвоено значение `General Date` выражением CDate(). Свойство LANGUAGE имеет значение `1033` (английский), унаследованное от значения локали системы.|  
|B|Thursday, March 12, 1959|Свойству FORMAT_STRING явно присвоено значение `Long Date` . Свойство LANGUAGE имеет значение `1033` (английский), унаследованное от значения локали системы.|  
|C|12/03/1959 6:30:00|Свойству FORMAT_STRING явно присвоено значение `General Date` . Свойству LANGUAGE явно присвоено значение `1034` (испанский).<br /><br /> Обратите внимание, что месяц и день меняются местами, если сравнивать с американским стилем форматирования|  
|D|jueves, 12 de marzo de 1959|Свойству FORMAT_STRING явно присвоено значение `Long Date` . Свойству LANGUAGE явно присвоено значение `1034` (испанский).<br /><br /> Обратите внимание, что месяц и день недели написаны на испанском|  
|E|1959/03/12 6:30:00|Свойству FORMAT_STRING явно присвоено значение `General Date` . Свойству LANGUAGE явно присвоено значение `1041` (Японский).<br /><br /> Обратите внимание, что формат даты теперь выглядит как Год/Месяц/День Часы:Минуты:Секунды|  
|F|1959年3月12日|Свойству FORMAT_STRING явно присвоено значение `Long Date` . Свойству LANGUAGE явно присвоено значение `1041` (Японский).|  
|G|6:30:00|Свойству FORMAT_STRING явно присвоено значение `Long Time` . Свойство LANGUAGE имеет значение `1033` (английский), унаследованное от значения локали системы.|  
|H|06:30|Свойству FORMAT_STRING явно присвоено значение `Short Time` . Свойство LANGUAGE имеет значение `1033` (английский), унаследованное от значения локали системы.|  
|I|6:30:00|Свойству FORMAT_STRING явно присвоено значение `Long Time` . Свойству LANGUAGE явно присвоено значение `1034` (испанский).|  
|J|06:30|Свойству FORMAT_STRING явно присвоено значение `Short Time` . Свойству LANGUAGE явно присвоено значение `1034` (испанский).|  
|K|6:30:00|Свойству FORMAT_STRING явно присвоено значение `Long Time` . Свойству LANGUAGE явно присвоено значение `1041` (японский).|  
|L|06:30|Свойству FORMAT_STRING явно присвоено значение `Short Time` . Свойству LANGUAGE явно присвоено значение `1041` (японский).|  
  
## <a name="see-also"></a>См. также:  
 [FORMAT_STRING содержимого &#40;многомерных выражений&#41;](mdx-cell-properties-format-string-contents.md)   
 [Использование свойств ячеек &#40;&#41;многомерных выражений](mdx-cell-properties-using-cell-properties.md)   
 [Создание и использование значений свойств &#40;&#41;многомерных выражений](../../creating-and-using-property-values-mdx.md)   
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](mdx-query-fundamentals-analysis-services.md)  
  
  
