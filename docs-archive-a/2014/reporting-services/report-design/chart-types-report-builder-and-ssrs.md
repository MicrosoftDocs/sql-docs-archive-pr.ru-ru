---
title: Типы диаграмм (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10423"
ms.assetid: 57b00017-69ae-4e71-8d78-44744e208ac7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e578d8259a0b6fa4ad94b6889ecb6e96afdd7b67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667576"
---
# <a name="chart-types-report-builder-and-ssrs"></a>Типы диаграмм (построитель отчетов и службы SSRS)
  Важно выбрать тип диаграммы, подходящий для типа представляемых данных. От этого зависит, насколько успешно можно будет интерпретировать данные после их вывода на диаграмме. Например, если набор данных содержит количество точек данных, сравнимое с размером диаграммы, то может оказаться более успешным представление данных с использованием диаграммы с областями, графика или точечной диаграммы. Обсуждение темы, касающейся подготовки данных в зависимости от выбранного типа диаграммы, см. в разделе [Диаграммы (построитель отчетов и службы SSRS)](charts-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="choosing-a-chart-type"></a>Выбор типа диаграммы  
 Диаграмма каждого типа обладает уникальными характеристиками, позволяющими наилучшим образом представить визуально конкретный набор данных. Для отображения данных можно использовать диаграммы любого типа, но удобство чтения данных повышается, если применяется тип диаграммы, подходящий для конкретных данных, учитывая то, что должно быть показано в отчете. В следующей таблице собраны характеристики диаграммы, от которых зависит применимость диаграммы для конкретного набора данных.  
  
 Тип диаграммы можно изменить после ее создания. Дополнительные сведения см. в статье [Изменение типа диаграммы (построитель отчетов и службы SSRS)](change-a-chart-type-report-builder-and-ssrs.md).  
  
 Примеры многих из этих типов диаграмм доступны в качестве образцов отчетов. Дополнительные сведения о скачивании образцов отчетов см. в разделе [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [образцы отчетов построитель отчетов и конструктор отчетов](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
|Тип диаграммы|Отображение данных отношений|Отображение данных об акциях|Отображение линейных данных|Отображение многозначных данных|  
|----------------|------------------------|------------------------|-------------------------|-------------------------------|  
|[Диаграммы с областями (построитель отчетов и службы SSRS)](area-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Линейчатые диаграммы (построитель отчетов и службы SSRS)](bar-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Гистограммы](sparklines-and-data-bars-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Гистограммы (построитель отчетов и службы SSRS)](column-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Графики (построитель отчетов и службы SSRS)](line-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Круговые диаграммы (построитель отчетов и службы SSRS)](pie-charts-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")||||  
|[Полярные диаграммы (построитель отчетов и службы SSRS)](polar-charts-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")||||  
|[Диаграммы диапазонов (построитель отчетов и службы SSRS)](range-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")|![Доступно](../media/greencheck.gif "Доступно")|  
|[Точечные диаграммы (построитель отчетов и службы SSRS)](scatter-charts-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")||![Доступно](../media/greencheck.gif "Доступно")||  
|[Фигурные диаграммы (построитель отчетов и службы SSRS)](shape-charts-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")||||  
|[Спарклайны](sparklines-and-data-bars-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")|![Доступно](../media/greencheck.gif "Доступно")|![Доступно](../media/greencheck.gif "Доступно")|![Доступно](../media/greencheck.gif "Доступно")|  
|[Биржевые диаграммы (построитель отчетов и службы SSRS)](stock-charts-report-builder-and-ssrs.md)||![Доступно](../media/greencheck.gif "Доступно")||![Доступно](../media/greencheck.gif "Доступно")|  
  
## <a name="see-also"></a>См. также:  
 [Диаграммы &#40;построитель отчетов и службы SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Пустые и пустые точки данных в диаграммах &#40;построитель отчетов и SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Добавление диаграммы в отчет (построитель отчетов и службы SSRS)](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
  
