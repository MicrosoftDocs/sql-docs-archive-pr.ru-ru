---
title: Диалоговое окно "Свойства оси" — "Параметры оси" (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.axisproperties.axisoptions.f1
- "10138"
ms.assetid: b276e210-7a12-48ae-971b-7dabae51df11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a94c4de6487d111417ef7ad3cee53a4172b5d275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664035"
---
# <a name="axis-properties-dialog-box-axis-options-report-builder-and-ssrs"></a>Диалоговое окно «Свойства оси» — «Параметры оси» (построитель отчетов и службы SSRS)
  Выберите **Параметры оси** в диалоговом окне **Свойства** **горизонтально** или вертикальной оси, чтобы определить внешний вид заданной оси диаграммы. В предыдущих версиях служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]на горизонтальной оси диаграммы по умолчанию отображались все метки. Однако в службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008 метки на диаграмме опускаются, чтобы изображение было понятнее, а метки не пересекались. Дополнительные сведения см. в разделе [Форматирование меток оси на диаграмме &#40;построитель отчетов и службы SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Варианты  
 **Включить разрывы шкалы**  
 Выберите данный параметр, чтобы разрешить диаграмме при необходимости изображать разрывы шкалы. Если данный параметр включен, то диаграмма будет автоматически вычислять, существует ли достаточная разница между верхней и нижней точкой в наборе данных, чтобы отобразить разрыв шкалы.  
  
 **Обратное направление**  
 Выберите этот параметр, чтобы изменить направление диаграммы на обратное. Например, по умолчанию на гистограммах ось Y отображается в левой части диаграммы, а категории располагаются слева направо. Если этот параметр выбран, ось Y отображается в правой части диаграммы, а категории — справа налево.  
  
 **Использовать чередование цветов**  
 Выберите этот параметр для добавления полосковых линий в диаграмму, затем выберите цвет или введите выражение. Полосовые линии — это затененные полосы в области диаграммы, создающие эффект чередующихся светлых и темных зон между линиями сетки. Эти полосовые линии полезны для выделения повторяющих тенденций на оси.  
  
 **Всегда включать ноль**  
 Выберите этот параметр, чтобы всегда включать ноль в шкалу на оси. Если данный параметр не включен, то на диаграмме не будет установлена метка для значения нуля на оси. Включение значения ноль полезно, если в набор данных входят нулевые или отрицательные значения.  
  
 **Скалярная ось**  
 Выберите данный параметр, чтобы набор значений оси отображался на непрерывной шкале. Например, если в наборе значений содержатся данные для января, марта и ноября, то на нескалярной оси будут отображены только эти месяцы, а на скалярной оси будут отображены все месяцы года.  
  
 **Использовать логарифмическую шкалу**  
 Выберите этот параметр, чтобы указать, что ось имеет логарифмическую шкалу. Этот параметр доступен только для оси Y, если на оси содержатся положительные числовые значения.  
  
 В поле введите основание логарифма, которое должно использоваться в случае, если для оси будет задано применение логарифмической шкалы. По умолчанию в диаграмме для логарифмической шкалы на оси используется основание 10. Этот параметр доступен только для оси Y, если ось является числовой.  
  
 **Минимальные**  
 Введите выражение или значение для минимального значения оси X. Если не указано, минимальное значение определяется данными, которые возвращает набор данных.  
  
 **Максимум**  
 Введите выражение или значение для максимального значения оси Y. Если не указано, максимальное значение определяется данными, возвращаемыми набором данных.  
  
 **Интервал**  
 Введите выражение или значение интервала между метками оси. Например, введите значение 1, чтобы вывести на оси все метки категорий. Введите значение 2, чтобы вывести на оси каждую вторую метку категории. При пропуске этого поля метки вычисляются автоматически на основе значений набора данных.  
  
 **Тип интервала**  
 Введите выражение или значение для типа указанного интервала. Например, если интервал должен быть равен двум дням, необходимо задать **2** как интервал и **Дни** как тип интервала.  
  
 **Боковые поля**  
 Введите выражение или выберите значение, чтобы добавить или удалить поле между элементами диаграммы и сторонами диаграммы. Если этот параметр равен **Auto**, боковые поля добавляются.  
  
## <a name="see-also"></a>См. также:  
 [Форматирование меток оси на построитель отчетов &#40;диаграммы и SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Диаграммы &#40;построитель отчетов и службы SSRS&#41;](report-design/charts-report-builder-and-ssrs.md)   
 [Форматирование цветов рядов на диаграмме &#40;построитель отчетов и SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Укажите интервал оси &#40;построитель отчетов и службы SSRS&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md)   
 [Форматирование меток оси в виде дат или валют &#40;построитель отчетов и SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Построение данных на вспомогательной оси &#40;построитель отчетов и SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)   
 [Спарклайны и гистограммы &#40;построитель отчетов и службы SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)   
 [Добавление или удаление полей из диаграммы (построитель отчетов и службы SSRS)](report-design/add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
  
