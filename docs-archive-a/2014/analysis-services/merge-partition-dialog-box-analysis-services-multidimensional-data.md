---
title: Диалоговое окно «слияние секции» (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1978c187bfb5097d286f78650b5bda6645c7a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667459"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Слияние секций» (службы Analysis Services — многомерные данные)
  Диалоговое окно **Слияние секций** в среде **SQL Server Management Studio** позволяет объединять секции для группы мер в кубе. Для вывода диалогового окна **Слияние секций** щелкните правой кнопкой мыши папку "Секции" в **обозревателе объектов** и выберите команду **Слияние секций** из контекстного меню.  
  
## <a name="options"></a>Варианты  
 **Server**  
 Выберите имя экземпляра службы Analysis Services, содержащего нужную секцию.  
  
 **имя**;  
 Выберите имя существующей секции для использования в качестве секции назначения.  
  
 **Папка**  
 Выводит имя папки, содержащей секцию назначения, если секция, выбранная в поле «Имя», не использует папку, установленную по умолчанию для данного экземпляра служб Analysis Services.  
  
 **Исходные секции**  
 Выводит сетку с исходными секциями, которые можно объединить в секцию назначения.  
  
> [!NOTE]  
>  Объединять можно только секции в одной группе мер с одной статистической схемой.  
  
 Сетка содержит следующие столбцы:  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Объединить**|Выберите, чтобы выполнить слияние исходной секции с секцией назначения.|  
|**Имя секции**|Отображает имя исходной секции.|  
|**Последняя обработка**|Выводит дату и время последней обработки исходной секции.|  
  
## <a name="see-also"></a>См. также:  
 [Секции &#40;Analysis Services многомерных данных&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Объединение секций в службах Analysis Services (службы SSAS — многомерные данные)](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
