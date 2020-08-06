---
title: Диалоговое окно «Фильтр набора данных» или «фильтр модели» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9602174-b7e2-4e16-8ded-dfd8eb9264d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa796cd8cb23894c059deba411b3e1d6676e3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733318"
---
# <a name="data-set-filter-or-model-filter-dialog-box"></a>Диалоговое окно "Фильтр набора данных" или "Фильтр модели"
  Это диалоговое окно позволяет создавать фильтры, которые можно применить к набору данных.  Набор данных может быть внешним набором данных, используемых для проверки, или данными варианта для модели интеллектуального анализа данных. Имя диалогового окна изменяется в зависимости от того, предназначен ли фильтр для внешнего набора данных или для модели интеллектуального анализа данных.  
  
 Если к новому набору данных применяется фильтр, модель интеллектуального анализа данных оценивается с помощью только тех вариантов набора данных, которые удовлетворяют заданным критериям. Если фильтр применяется к самой модели интеллектуального анализа данных, обучение и проверка модели осуществляется с помощью только тех вариантов существующего набора проверочных данных, которые удовлетворяют критериям фильтрации.  
  
-   Вызвать диалоговое окно **Фильтр набора данных** можно с вкладки **Выбор входа** конструктора **Диаграмма точности интеллектуального анализа данных** .  
  
-   Диалоговое окно **Фильтр модели** можно вызвать с вкладки **Модели интеллектуального анализа данных** конструктора интеллектуального анализа данных.  
  
-   Сетка **Условия** содержит столбцы, в которых можно указать имя таблицы или столбца, оператор и целевые значения. Использование этой сетки является, по сути, созданием предложения WHERE.  
  
> [!TIP]  
>   Чтобы проверить точность на подмножестве исходных обучающих данных, можно добавить представление источников данных, используемое для определения обучающего набора, в виде внешних проверочных данных, после чего добавить условия в сетке **Фильтр набора данных** .  
  
 **Дополнительные сведения:** [Тестирование и проверка (интеллектуальный анализ данных)](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Варианты  
 **Условия**  
 Отображает имена таблиц, за которыми следуют имена столбцов с условиями.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**И (или)**|Выберите оператор для соединения нескольких условий.|  
|**Столбец структуры интеллектуального анализа данных**|Нажмите, чтобы выбрать источник данных, затем щелкните последующие строки сетки, чтобы добавить столбцы из источника данных.<br /><br /> В первой строке сетки указано представление источника данных. После того как выбрано представление источника данных, в поле **Столбец структуры интеллектуального анализа данных** отображается значок таблицы, а в поле **Значение** отображается сочетание всех критериев, определенных для этого источника данных.<br /><br /> После выбора источника данных поле **Столбец структуры интеллектуального анализа данных** содержит раскрывающийся список отдельных столбцов этого источника данных.|  
|**Оператор**|Выберите оператор из списка.|  
|**Значение**|Для таблиц в поле **Значение** отображается сочетание всех фильтров, применяемых к источнику данных. Можно также нажать кнопку Построить **(...)** справа от текстового поля, чтобы открыть диалоговое окно **Фильтр** и построить условие.|  
  
 **Выражение**  
 Отображает набор критериев, построенных с помощью сетки.  
  
 **Изменить запрос**  
 Меняет режим изменения фильтра, позволяя вводить критерий фильтра непосредственно в текстовое поле **Выражение** .  
  
> [!NOTE]  
>  После внесения изменений в критерий фильтра вручную вы не сможете вернуться в режим правки сетки даже после сохранения выражения в поле **критерий фильтра** на вкладке **Выбор входа** . Если требуется построить выражение с помощью сетки, необходимо удалить существующее выражение фильтра и начать заново.  
  
 **Сбросить изменения запроса**  
 Восстанавливает прежнее состояние сетки и отменяет все изменения, внесенные в критерий фильтра.  
  
## <a name="see-also"></a>См. также:  
 [Задачи тестирования и проверки и инструкции &#40;&#41;интеллектуального анализа данных](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Конструктор диаграмм точности интеллектуального анализа &#40;&#41;интеллектуального анализа данных](mining-accuracy-chart-designer-data-mining.md)  
  
  