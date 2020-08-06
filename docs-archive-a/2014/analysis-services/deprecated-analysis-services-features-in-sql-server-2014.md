---
title: Устаревшие функции Analysis Services в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- deprecated features [Analysis Services]
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b3de78dfea70196e0c2855167e5ce2fda2369a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734573"
---
# <a name="deprecated-analysis-services-features-in-sql-server-2014"></a>Устаревшие функции служб Analysis Services в SQL Server 2014
  В этом разделе описаны устаревшие функции компонента [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , которые по-прежнему доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Эти функции будут удалены в следующем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Функции, не поддерживаемые в следующей версии SQL Server  
 Следующие функции компонента [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] не будут поддерживаться в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не используйте их при работе над новыми приложениями и как можно скорее измените приложения, в которых они в настоящее время используются.  
  
|Категория|Устаревшая функция|Замена|  
|--------------|------------------------|-----------------|  
|Функция многомерных выражений|CalculationPassValue, функция|Нет. Механизм OLAP управляет этапом вычисления. Эта функция больше не нужна.|  
|Функция многомерных выражений|CalculationCurrentPass, функция|Нет. Механизм OLAP управляет этапом вычисления. Эта функция больше не нужна.|  
|Многомерные выражения.|Подсказка оптимизатора запросов NON_EMPTY_BEHAVIOR была включена по умолчанию.|Подсказка оптимизатора запросов NON_EMPTY_BEHAVIOR будет отключена по умолчанию в будущем выпуске. При неправильном использовании подсказка оптимизации многомерного выражения может выдавать неверные результаты.|  
|Другое|Внутреннее свойство ячейки CELL_EVALUATION_LIST|Первоначально предоставлялся список вычисляемых формул, применимых к ячейке. В данном выпуске Analysis Services это свойство пусто.  Порядок вычисления теперь указывается в скрипте многомерных выражений. Дополнительные сведения см. в разделе [Основные сведения о порядке этапов и порядке вычисления &#40;многомерных выражениях&#41;](multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|  
|Объекты|Сборки COM|Использование сборок COM может представлять угрозу безопасности. Поддержка сборок COM будет удалена в будущем выпуске.|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Функции, не поддерживаемые в будущей версии SQL Server  
 Поддержка приведенных ниже функций компонента [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]будет сохранена, однако будет удалена в более поздней версии. (с какой именно версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , пока не определено).  
  
|Категория|Устаревшая функция|Замена|  
|--------------|------------------------|-----------------|  
|Многомерные модели|Удаленные секции|Нет. Вместо этого используйте локальные секции. Дополнительные сведения см. [в разделе Создание локальной секции и управление ей &#40;Analysis Services&#41;](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md) .|  
|Многомерные модели|Удаленные связанные группы мер|Удаленная связанная группа мер ― это связанная группа мер, которая использует источник данных на удаленном сервере. Возможность связанной группы мер использовать удаленный источник данных будет планово выведена из эксплуатации.<br /><br /> Замены для этой функции нет. Вместо нее рекомендуется использовать локальные связанные группы мер. Подробнее см. в разделе [Linked Measure Groups](multidimensional-models/linked-measure-groups.md) .|  
|Многомерные модели|Многомерная обратная запись|Нет. Если нужна возможность обратной записи, используйте обратную запись секции. Дополнительные сведения см. в разделе [Set Partition обратной записи](multidimensional-models/set-partition-writeback.md) .|  
|Многомерные модели|Связанные измерения|Нет. Можно скопировать измерения в другие модели, а не устанавливать связь с измерением из другой модели.|  
|MDX|Свойство Non_Empty_Behavior|Нет. При создании вычисляемого элемента ошибочное задание этого свойства увеличивает вероятность возврата неверных результатов. В последних оптимизациях ядра OLAP улучшены операции с наборами разреженных данных, что делает это свойство менее релевантным.|  
  
## <a name="see-also"></a>См. также:  
 [Analysis Services обратной совместимости](analysis-services-backward-compatibility.md)   
 [Неподдерживаемые функции служб Analysis Services в SQL Server 2014](discontinued-analysis-services-functionality-in-sql-server-2014.md)  
  
  
