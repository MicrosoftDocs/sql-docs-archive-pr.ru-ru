---
title: Вывод значений круговой диаграммы в верхней части диаграммы (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed010eeaf3e4d581cce2f7242144c4f73ec2895b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654775"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>Вывод значений круговой диаграммы в верхней части диаграммы (построитель отчетов и службы SSRS)
  По умолчанию в круговых диаграммах первое значение набора данных отсчитывается с 90-го градуса от верхней части диаграммы. Можно указать, чтобы первое значение отсчитывалось от верхней части диаграммы.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>Отсчет значений круговой диаграммы от верхней части диаграммы  
  
1.  Щелкните круговую диаграмму.  
  
2.  Если панель **Свойства** не отображается, выберите на вкладке **Вид** пункт **Свойства**.  
  
3.  В области **Свойства** в разделе **настраиваемые атрибуты**измените значение **пиестартангле** с **0** на **270**.  
  
4.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Теперь первое значение круговой диаграммы отсчитывается от верхней части диаграммы.  
  
## <a name="see-also"></a>См. также:  
 [Форматирование построитель отчетов &#40;диаграммы и SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Круговые диаграммы (построитель отчетов и службы SSRS)](charts-report-builder-and-ssrs.md)  
  
  
