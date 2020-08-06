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
# <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="479df-102">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="479df-102">Microsoft Neural Network Algorithm</span></span>
  <span data-ttu-id="479df-103">В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] алгоритм нейронной сети объединяет каждое возможное состояние входного атрибута с каждым возможным состоянием прогнозируемого атрибута и использует обучающие данные для вычисления вероятностей.</span><span class="sxs-lookup"><span data-stu-id="479df-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm combines each possible state of the input attribute with each possible state of the predictable attribute, and uses the training data to calculate probabilities.</span></span> <span data-ttu-id="479df-104">Далее эти вероятности можно использовать для классификации или регрессии, а также для прогнозирования исхода прогнозируемого атрибута на основе входных атрибутов.</span><span class="sxs-lookup"><span data-stu-id="479df-104">You can later use these probabilities for classification or regression, and to predict an outcome of the predicted attribute, based on the input attributes.</span></span>  
  
 <span data-ttu-id="479df-105">В модели интеллектуального анализа данных, которая создается при помощи алгоритма нейронной сети [!INCLUDE[msCoName](../../includes/msconame-md.md)], может содержаться несколько сетей, что определяется количеством столбцов, используемых для входа и прогнозирования или только для прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="479df-105">A mining model that is constructed with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm can contain multiple networks, depending on the number of columns that are used for both input and prediction, or that are used only for prediction.</span></span> <span data-ttu-id="479df-106">Количество сетей, содержащихся в одной модели интеллектуального анализа данных, зависит от количества состояний, содержащихся во входных и прогнозируемых столбцах, используемых моделью интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="479df-106">The number of networks that a single mining model contains depends on the number of states that are contained by the input columns and predictable columns that the mining model uses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="479df-107">Пример</span><span class="sxs-lookup"><span data-stu-id="479df-107">Example</span></span>  
 <span data-ttu-id="479df-108">Алгоритм нейронной сети ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) полезен при анализе сложных входных данных, полученных, например в результате производственного или коммерческого процесса или бизнес-задач, для которых предоставляется значительный объем обучающих данных, но при этом затруднено образование производных правил при помощи других алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="479df-108">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm is useful for analyzing complex input data, such as from a manufacturing or commercial process, or business problems for which a significant quantity of training data is available but for which rules cannot be easily derived by using other algorithms.</span></span>  
  
 <span data-ttu-id="479df-109">Предлагаются следующие сценарии использования алгоритма нейронной сети ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ):</span><span class="sxs-lookup"><span data-stu-id="479df-109">Suggested scenarios for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm include the following:</span></span>  
  
-   <span data-ttu-id="479df-110">Анализ маркетинга и рекламы, например измерение эффективности прямой почтовой рассылки или рекламной кампании, проводимой по радио.</span><span class="sxs-lookup"><span data-stu-id="479df-110">Marketing and promotion analysis, such as measuring the success of a direct mail promotion or a radio advertising campaign.</span></span>  
  
-   <span data-ttu-id="479df-111">Прогнозирование изменений цен на акции, колебаний валютных курсов или других изменчивых финансовых данных из данных с предысторией.</span><span class="sxs-lookup"><span data-stu-id="479df-111">Predicting stock movement, currency fluctuation, or other highly fluid financial information from historical data.</span></span>  
  
-   <span data-ttu-id="479df-112">Анализ производственных и промышленных процессов.</span><span class="sxs-lookup"><span data-stu-id="479df-112">Analyzing manufacturing and industrial processes.</span></span>  
  
-   <span data-ttu-id="479df-113">Интеллектуальный анализ текста.</span><span class="sxs-lookup"><span data-stu-id="479df-113">Text mining.</span></span>  
  
-   <span data-ttu-id="479df-114">Любая прогнозирующая модель, которая анализирует сложные связи между большим количеством входных атрибутов и сравнительно малым количеством выходных атрибутов.</span><span class="sxs-lookup"><span data-stu-id="479df-114">Any prediction model that analyzes complex relationships between many inputs and relatively fewer outputs.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="479df-115">Принцип работы алгоритма</span><span class="sxs-lookup"><span data-stu-id="479df-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="479df-116">Алгоритм нейронной сети [!INCLUDE[msCoName](../../includes/msconame-md.md)] создает сеть, состоящую из двух или трех слоев нейронов.</span><span class="sxs-lookup"><span data-stu-id="479df-116">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates a network that is composed of up to three layers of neurons.</span></span> <span data-ttu-id="479df-117">Такими слоями являются входной слой, необязательный скрытый слой и выходной слой.</span><span class="sxs-lookup"><span data-stu-id="479df-117">These layers are an input layer, an optional hidden layer, and an output layer.</span></span>  
  
 <span data-ttu-id="479df-118">**Входной слой:** Входные нейроны определяют все значения входных атрибутов для модели интеллектуального анализа данных и их вероятности.</span><span class="sxs-lookup"><span data-stu-id="479df-118">**Input layer:** Input neurons define all the input attribute values for the data mining model, and their probabilities.</span></span>  
  
 <span data-ttu-id="479df-119">**Скрытый слой:** Скрытые нейроны получают входные данные из входных нейронов и предоставляют выходные данные выходным нейронам.</span><span class="sxs-lookup"><span data-stu-id="479df-119">**Hidden layer:** Hidden neurons receive inputs from input neurons and provide outputs to output neurons.</span></span> <span data-ttu-id="479df-120">В скрытом слое различным вероятностям входных атрибутов назначаются весовые коэффициенты.</span><span class="sxs-lookup"><span data-stu-id="479df-120">The hidden layer is where the various probabilities of the inputs are assigned weights.</span></span> <span data-ttu-id="479df-121">Весовой коэффициент описывает существенность или важность отдельного входного атрибута для скрытого нейрона.</span><span class="sxs-lookup"><span data-stu-id="479df-121">A weight describes the relevance or importance of a particular input to the hidden neuron.</span></span> <span data-ttu-id="479df-122">Чем больше весовой коэффициент, назначенный входному атрибуту, тем большую важность имеет его значение.</span><span class="sxs-lookup"><span data-stu-id="479df-122">The greater the weight that is assigned to an input, the more important the value of that input is.</span></span> <span data-ttu-id="479df-123">Весовые коэффициенты могут быть отрицательными. Входной атрибут с отрицательным коэффициентом препятствует, а не способствует наступлению выбранного результата.</span><span class="sxs-lookup"><span data-stu-id="479df-123">Weights can be negative, which means that the input can inhibit, rather than favor, a specific result.</span></span>  
  
 <span data-ttu-id="479df-124">**Выходной слой:** Выходные нейроны представляют значения прогнозируемых атрибутов для модели интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="479df-124">**Output layer:** Output neurons represent predictable attribute values for the data mining model.</span></span>  
  
 <span data-ttu-id="479df-125">Подробное объяснение процесса создания и оценки входного, скрытого и выходного слоев см. в разделе [Технический справочник по алгоритму нейронной сети (Майкрософт)](microsoft-neural-network-algorithm-technical-reference.md).</span><span class="sxs-lookup"><span data-stu-id="479df-125">For a detailed explanation of how the input, hidden, and output layers are constructed and scored, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-neural-network-models"></a><span data-ttu-id="479df-126">Данные, необходимые для моделей нейронной сети</span><span class="sxs-lookup"><span data-stu-id="479df-126">Data Required for Neural Network Models</span></span>  
 <span data-ttu-id="479df-127">Модель нейронной сети должна содержать ключевой столбец, один или несколько входных и прогнозируемых столбцов.</span><span class="sxs-lookup"><span data-stu-id="479df-127">A neural network model must contain a key column, one or more input columns, and one or more predictable columns.</span></span>  
  
 <span data-ttu-id="479df-128">Модели интеллектуального анализа данных, использующие алгоритм нейронной сети [!INCLUDE[msCoName](../../includes/msconame-md.md)] сильно зависят от значений, указанных для параметров, доступных в алгоритме.</span><span class="sxs-lookup"><span data-stu-id="479df-128">Data mining models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm are heavily influenced by the values that you specify for the parameters that are available to the algorithm.</span></span> <span data-ttu-id="479df-129">Эти параметры определяют порядок выборки данных, способ распределения или ожидаемого распределения данных в каждом столбце, а также условия, при которых вызывается выбор компонентов для ограничения значений, используемых в конечной модели.</span><span class="sxs-lookup"><span data-stu-id="479df-129">The parameters define how data is sampled, how data is distributed or expected to be distributed in each column, and when feature selection is invoked to limit the values that are used in the final model.</span></span>  
  
 <span data-ttu-id="479df-130">Дополнительные сведения о задании параметров для настройки поведения модели см. в разделе [Технический справочник по алгоритму нейронной сети (Майкрософт)](microsoft-neural-network-algorithm-technical-reference.md).</span><span class="sxs-lookup"><span data-stu-id="479df-130">For more information about setting parameters to customize model behavior, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-neural-network-model"></a><span data-ttu-id="479df-131">Просмотр модели нейронной сети</span><span class="sxs-lookup"><span data-stu-id="479df-131">Viewing a Neural Network Model</span></span>  
 <span data-ttu-id="479df-132">Для работы с данными и демонстрации корреляции между входами и выходами модели можно использовать **средство просмотра нейронных сетей (Майкрософт)**.</span><span class="sxs-lookup"><span data-stu-id="479df-132">To work with the data and see how the model correlates inputs with outputs, you can use the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="479df-133">С помощью этого средства просмотра можно применить фильтр по входным атрибутам и их значениям, чтобы получить графическое представление об их влиянии на выходные атрибуты.</span><span class="sxs-lookup"><span data-stu-id="479df-133">With this custom viewer, you can filter on input attributes and their values, and see graphs that show how they affect the outputs.</span></span> <span data-ttu-id="479df-134">Подсказки в средстве просмотра покажут вероятность и точность, связанные с каждой парой входных и выходных значений.</span><span class="sxs-lookup"><span data-stu-id="479df-134">The tooltips in the viewer show you the probability and lift associated with each pair of input and output values.</span></span> <span data-ttu-id="479df-135">Дополнительные сведения см. в разделе [Просмотр модели с помощью средства просмотра нейронных сетей (Майкрософт)](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="479df-135">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="479df-136">Просмотреть структуру модели проще всего с помощью **средства просмотра деревьев содержимого общего вида (Майкрософт)**.</span><span class="sxs-lookup"><span data-stu-id="479df-136">The easiest way to explore the structure of the model is to use the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="479df-137">Можно просмотреть входные и выходные атрибуты, а также сети, созданные моделью. Щелкнув любой узел, его можно развернуть и просмотреть статистику, связанную с узлами входного, выходного или скрытого слоя.</span><span class="sxs-lookup"><span data-stu-id="479df-137">You can view the inputs, outputs, and networks created by the model, and click on any node to expand it and see statistics related to the input, output, or hidden layer nodes.</span></span> <span data-ttu-id="479df-138">Дополнительные сведения см. в разделе [Просмотр модели в средстве просмотра деревьев содержимого общего вида (Майкрософт)](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="479df-138">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="479df-139">Создание прогнозов</span><span class="sxs-lookup"><span data-stu-id="479df-139">Creating Predictions</span></span>  
 <span data-ttu-id="479df-140">После обработки модели сеть и весовые коэффициенты, хранящиеся в каждом узле, можно использовать для составления прогнозов.</span><span class="sxs-lookup"><span data-stu-id="479df-140">After the model has been processed, you can use the network and the weights stored within each node to make predictions.</span></span> <span data-ttu-id="479df-141">Модель нейронной сети поддерживает регрессионный анализ, анализ взаимосвязей и классификационный анализ. Поэтому каждый прогноз может иметь различное значение.</span><span class="sxs-lookup"><span data-stu-id="479df-141">A neural network model supports regression, association, and classification analysis, Therefore, the meaning of each prediction might be different.</span></span> <span data-ttu-id="479df-142">Также можно запросить непосредственно модель, чтобы проверить обнаруженные взаимосвязи и получить связанную статистику.</span><span class="sxs-lookup"><span data-stu-id="479df-142">You can also query the model itself, to review the correlations that were found and retrieve related statistics.</span></span> <span data-ttu-id="479df-143">Примеры создания запросов к модели нейронной сети см. в разделе [Примеры запросов к модели нейронной сети](neural-network-model-query-examples.md).</span><span class="sxs-lookup"><span data-stu-id="479df-143">For examples of how to create queries against a neural network model, see [Neural Network Model Query Examples](neural-network-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="479df-144">Общие сведения о создании запроса к модели интеллектуального анализа данных см. в разделе [Запросы интеллектуального анализа данных](data-mining-queries.md).</span><span class="sxs-lookup"><span data-stu-id="479df-144">For general information about how to create a query on a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="479df-145">Remarks</span><span class="sxs-lookup"><span data-stu-id="479df-145">Remarks</span></span>  
  
-   <span data-ttu-id="479df-146">Не поддерживается детализация и измерения интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="479df-146">Does not support drillthrough or data mining dimensions.</span></span> <span data-ttu-id="479df-147">Это объясняется тем, что структура узлов в модели интеллектуального анализа данных не обязательно однозначно соответствует базовым данным.</span><span class="sxs-lookup"><span data-stu-id="479df-147">This is because the structure of the nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="479df-148">Не поддерживается создание моделей в формате языка разметки прогнозирующих моделей (PMML).</span><span class="sxs-lookup"><span data-stu-id="479df-148">Does not support the creation of models in Predictive Model Markup Language (PMML) format.</span></span>  
  
-   <span data-ttu-id="479df-149">Поддерживается использование моделей интеллектуального анализа OLAP.</span><span class="sxs-lookup"><span data-stu-id="479df-149">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="479df-150">Не поддерживается создание измерений интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="479df-150">Does not support the creation of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="479df-151">См. также:</span><span class="sxs-lookup"><span data-stu-id="479df-151">See Also</span></span>  
 <span data-ttu-id="479df-152">[Технический справочник по алгоритму нейронной сети (Майкрософт)](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="479df-152">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="479df-153">[Содержимое моделей интеллектуального анализа данных для моделей нейронных сетей &#40;Analysis Services — интеллектуальный анализ&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="479df-153">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="479df-154">[Примеры запросов к модели нейронной сети](neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="479df-154">[Neural Network Model Query Examples](neural-network-model-query-examples.md) </span></span>  
 [<span data-ttu-id="479df-155">Алгоритм логистической регрессии (Майкрософт)</span><span class="sxs-lookup"><span data-stu-id="479df-155">Microsoft Logistic Regression Algorithm</span></span>](microsoft-logistic-regression-algorithm.md)  
  
  