---
title: Алгоритм нейронной сети (Майкрософт) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 389df77299bbf357e1b8b0f0695f03a74420f786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654610"
---
# <a name="microsoft-neural-network-algorithm"></a>Microsoft Neural Network Algorithm
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] алгоритм нейронной сети объединяет каждое возможное состояние входного атрибута с каждым возможным состоянием прогнозируемого атрибута и использует обучающие данные для вычисления вероятностей. Далее эти вероятности можно использовать для классификации или регрессии, а также для прогнозирования исхода прогнозируемого атрибута на основе входных атрибутов.  
  
 В модели интеллектуального анализа данных, которая создается при помощи алгоритма нейронной сети [!INCLUDE[msCoName](../../includes/msconame-md.md)], может содержаться несколько сетей, что определяется количеством столбцов, используемых для входа и прогнозирования или только для прогнозирования. Количество сетей, содержащихся в одной модели интеллектуального анализа данных, зависит от количества состояний, содержащихся во входных и прогнозируемых столбцах, используемых моделью интеллектуального анализа данных.  
  
## <a name="example"></a>Пример  
 Алгоритм нейронной сети ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) полезен при анализе сложных входных данных, полученных, например в результате производственного или коммерческого процесса или бизнес-задач, для которых предоставляется значительный объем обучающих данных, но при этом затруднено образование производных правил при помощи других алгоритмов.  
  
 Предлагаются следующие сценарии использования алгоритма нейронной сети ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ):  
  
-   Анализ маркетинга и рекламы, например измерение эффективности прямой почтовой рассылки или рекламной кампании, проводимой по радио.  
  
-   Прогнозирование изменений цен на акции, колебаний валютных курсов или других изменчивых финансовых данных из данных с предысторией.  
  
-   Анализ производственных и промышленных процессов.  
  
-   Интеллектуальный анализ текста.  
  
-   Любая прогнозирующая модель, которая анализирует сложные связи между большим количеством входных атрибутов и сравнительно малым количеством выходных атрибутов.  
  
## <a name="how-the-algorithm-works"></a>Принцип работы алгоритма  
 Алгоритм нейронной сети [!INCLUDE[msCoName](../../includes/msconame-md.md)] создает сеть, состоящую из двух или трех слоев нейронов. Такими слоями являются входной слой, необязательный скрытый слой и выходной слой.  
  
 **Входной слой:** Входные нейроны определяют все значения входных атрибутов для модели интеллектуального анализа данных и их вероятности.  
  
 **Скрытый слой:** Скрытые нейроны получают входные данные из входных нейронов и предоставляют выходные данные выходным нейронам. В скрытом слое различным вероятностям входных атрибутов назначаются весовые коэффициенты. Весовой коэффициент описывает существенность или важность отдельного входного атрибута для скрытого нейрона. Чем больше весовой коэффициент, назначенный входному атрибуту, тем большую важность имеет его значение. Весовые коэффициенты могут быть отрицательными. Входной атрибут с отрицательным коэффициентом препятствует, а не способствует наступлению выбранного результата.  
  
 **Выходной слой:** Выходные нейроны представляют значения прогнозируемых атрибутов для модели интеллектуального анализа данных.  
  
 Подробное объяснение процесса создания и оценки входного, скрытого и выходного слоев см. в разделе [Технический справочник по алгоритму нейронной сети (Майкрософт)](microsoft-neural-network-algorithm-technical-reference.md).  
  
## <a name="data-required-for-neural-network-models"></a>Данные, необходимые для моделей нейронной сети  
 Модель нейронной сети должна содержать ключевой столбец, один или несколько входных и прогнозируемых столбцов.  
  
 Модели интеллектуального анализа данных, использующие алгоритм нейронной сети [!INCLUDE[msCoName](../../includes/msconame-md.md)] сильно зависят от значений, указанных для параметров, доступных в алгоритме. Эти параметры определяют порядок выборки данных, способ распределения или ожидаемого распределения данных в каждом столбце, а также условия, при которых вызывается выбор компонентов для ограничения значений, используемых в конечной модели.  
  
 Дополнительные сведения о задании параметров для настройки поведения модели см. в разделе [Технический справочник по алгоритму нейронной сети (Майкрософт)](microsoft-neural-network-algorithm-technical-reference.md).  
  
## <a name="viewing-a-neural-network-model"></a>Просмотр модели нейронной сети  
 Для работы с данными и демонстрации корреляции между входами и выходами модели можно использовать **средство просмотра нейронных сетей (Майкрософт)**. С помощью этого средства просмотра можно применить фильтр по входным атрибутам и их значениям, чтобы получить графическое представление об их влиянии на выходные атрибуты. Подсказки в средстве просмотра покажут вероятность и точность, связанные с каждой парой входных и выходных значений. Дополнительные сведения см. в разделе [Просмотр модели с помощью средства просмотра нейронных сетей (Майкрософт)](browse-a-model-using-the-microsoft-neural-network-viewer.md).  
  
 Просмотреть структуру модели проще всего с помощью **средства просмотра деревьев содержимого общего вида (Майкрософт)**. Можно просмотреть входные и выходные атрибуты, а также сети, созданные моделью. Щелкнув любой узел, его можно развернуть и просмотреть статистику, связанную с узлами входного, выходного или скрытого слоя. Дополнительные сведения см. в разделе [Просмотр модели в средстве просмотра деревьев содержимого общего вида (Майкрософт)](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
## <a name="creating-predictions"></a>Создание прогнозов  
 После обработки модели сеть и весовые коэффициенты, хранящиеся в каждом узле, можно использовать для составления прогнозов. Модель нейронной сети поддерживает регрессионный анализ, анализ взаимосвязей и классификационный анализ. Поэтому каждый прогноз может иметь различное значение. Также можно запросить непосредственно модель, чтобы проверить обнаруженные взаимосвязи и получить связанную статистику. Примеры создания запросов к модели нейронной сети см. в разделе [Примеры запросов к модели нейронной сети](neural-network-model-query-examples.md).  
  
 Общие сведения о создании запроса к модели интеллектуального анализа данных см. в разделе [Запросы интеллектуального анализа данных](data-mining-queries.md).  
  
## <a name="remarks"></a>Remarks  
  
-   Не поддерживается детализация и измерения интеллектуального анализа данных. Это объясняется тем, что структура узлов в модели интеллектуального анализа данных не обязательно однозначно соответствует базовым данным.  
  
-   Не поддерживается создание моделей в формате языка разметки прогнозирующих моделей (PMML).  
  
-   Поддерживается использование моделей интеллектуального анализа OLAP.  
  
-   Не поддерживается создание измерений интеллектуального анализа данных.  
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по алгоритму нейронной сети (Майкрософт)](microsoft-neural-network-algorithm-technical-reference.md)   
 [Содержимое моделей интеллектуального анализа данных для моделей нейронных сетей &#40;Analysis Services — интеллектуальный анализ&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Примеры запросов к модели нейронной сети](neural-network-model-query-examples.md)   
 [Алгоритм логистической регрессии (Майкрософт)](microsoft-logistic-regression-algorithm.md)  
  
  
