---
title: Вкладка диаграммы кластеризации последовательностей (средство просмотра моделей интеллектуального анализа данных) Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.diagrams.f1
ms.assetid: 4b705397-9af4-4678-9eda-149bc5d762fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4c100b7a8d38f7ef1b8920017cff009cfc91d62c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665603"
---
# <a name="sequence-clustering-cluster-diagram-tab-mining-model-viewer"></a>Вкладка «Диаграмма кластеров кластеризации последовательностей» (средство просмотра моделей интеллектуального анализа данных)
  Вкладка **Диаграмма кластеров** в **средстве просмотра деревьев содержимого общего вида (Майкрософт)** содержит графическое представление всех кластеров, содержащихся в модели кластеризации последовательностей.  
  
 Используйте представление модели кластеризации последовательностей для детализации из каждого кластера к соответствующим вариантам, если режим детализации включен. Можно также назначить описательные имена кластерам и изменить переменную заливки для доступа к распределению значений с первого взгляда  
  
 **Дополнительные сведения:** [Алгоритм кластеризации последовательностей (Майкрософт)](data-mining/microsoft-sequence-clustering-algorithm.md), [Просмотр модели с помощью средства просмотра кластеризации последовательностей (Майкрософт)](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Варианты  
 **Обновить содержимое средства просмотра**  
 Перезагрузить модель интеллектуального анализа данных в средстве просмотра.  
  
 **Модель интеллектуального анализа данных**  
 Выберите для просмотра модель интеллектуального анализа данных, содержащуюся в текущей структуре интеллектуального анализа данных. Модель интеллектуального анализа данных открывается в связанном средстве просмотра.  
  
 **Зритель**  
 Выберите средство просмотра для обзора выбранной модели интеллектуального анализа данных. Можно использовать пользовательское средство просмотра или **средство просмотра деревьев содержимого общего вида (Майкрософт)**. Также можно использовать подключаемые модули просмотра, если они доступны.  
  
 **Увеличить масштаб**  
 Увеличить диаграмму для получения более подробного представления кластеров.  
  
 **Уменьшить масштаб**  
 Уменьшить масштабы диаграммы, чтобы увидеть все кластеры в модели.  
  
 **Копировать представление диаграммы**  
 Копировать видимую часть диаграммы в буфер обмена.  
  
 **Копировать весь граф**  
 Копировать всю диаграмму в буфер обмена.  
  
 **Подобрать масштаб диаграммы по размеру окна**  
 Уменьшить диаграмму, чтобы она полностью помещалась на экране.  
  
 **Найти узел**  
 Используйте диалоговое окно **Найти узел** для фильтрации кластеров в диаграмме и упрощения поиска нужных узлов. Дополнительные сведения см. в разделе [Диалоговое окно "Найти узел" (средство просмотра моделей интеллектуального анализа данных)](find-node-dialog-box-mining-model-viewer.md).  
  
 Обратите внимание, что в этом контексте выполняется поиск только имени кластера, а не атрибутов внутри кластера; этот параметр наиболее полезен, если кластеру назначены описательные имена. Имена кластерам можно назначать в средстве просмотра, щелкая правой кнопкой мыши каждый кластер и выбирая пункт **Переименовать**.  
  
 **Улучшить макет**  
 Переупорядочить кластеры в диаграмме для улучшения макета.  
  
 **Плотность**  
 Вид линейной диаграммы плотности и значения в ней зависят от атрибута, выбранного в поле **Переменная заливки**.  
  
-   Если не выбраны никакие состояния атрибута в качестве переменной заливки, плотность заливки, примененная к каждому кластеру, по умолчанию представляет поддержку кластера в сравнении с общим заполнением вариантов.  
  
-   После выбора атрибута для **Переменной заливки**необходимо также выбрать значение **Состояние** . В результате линейная диаграмма плотности обновляется, чтобы показать вероятность состояния. Можно навести указатель мыши на любой кластер, чтобы увидеть вероятность выбранного состояния для этого кластера.  
  
 **Переменная заливки**  
 Выберите атрибут из модели интеллектуального анализа данных для заливки диаграммы кластеров.  
  
 **Состояние**  
 Выберите состояние, которое соответствует **Переменной заливки**. Например, если нужно просмотреть последовательности, которые содержат определенный продукт, можно выбрать столбец [Product] в качестве атрибута для **Переменной заливки**и конкретное название продукта как значение **Состояние** .  
  
 **Ссылки**  
 Линии на диаграмме показывают взаимосвязи между кластерами последовательностей. Количество ссылок, отображаемых в средстве просмотра, можно настроить, перемещая ползунок справа от кластеров. При движении ползунка вниз отображаются только самые прочные связи.  
  
## <a name="see-also"></a>См. также:  
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Средства просмотра моделей интеллектуального анализа &#40;конструктор моделей интеллектуального анализа данных&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Средства просмотра моделей интеллектуального анализа данных](data-mining/data-mining-model-viewers.md)  
  
  