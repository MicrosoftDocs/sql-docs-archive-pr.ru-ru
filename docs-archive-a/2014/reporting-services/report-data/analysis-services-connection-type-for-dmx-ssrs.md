---
title: Тип соединения служб Analysis Services для расширений интеллектуального анализа данных (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], DMX
- Data Mining Prediction [Reporting Services]
- query view [Reporting Services]
- DMX [Reporting Services]
- design view [Reporting Services]
- data mining [Reporting Services]
- passing parameters [Reporting Services]
ms.assetid: 2de825e9-6d8a-4128-add0-da15dc6cea3e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c6d2c689689cde5c6c5ef4ffa8ab5c0e8737078
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654849"
---
# <a name="analysis-services-connection-type-for-dmx-ssrs"></a><span data-ttu-id="f7dc9-102">Тип соединения служб Analysis Services для расширений интеллектуального анализа данных (службы SSRS)</span><span class="sxs-lookup"><span data-stu-id="f7dc9-102">Analysis Services Connection Type for DMX (SSRS)</span></span>
  <span data-ttu-id="f7dc9-103">При создании набора данных по источнику данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] конструктор отчетов отображает конструктор запросов многомерных выражений, если обнаруживает допустимый куб.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-103">When you create a dataset using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source, Report Designer displays the Multidimensional Expression (MDX) query designer if it detects a valid cube.</span></span> <span data-ttu-id="f7dc9-104">Если куб не обнаружен, но доступна модель интеллектуального анализа данных, конструктор отчетов отображает конструктор запросов интеллектуального анализа данных (расширения интеллектуального анализа данных).</span><span class="sxs-lookup"><span data-stu-id="f7dc9-104">If no cube is detected, but a data mining model is available, Report Designer displays the Data Mining Extensions (DMX) query designer.</span></span> <span data-ttu-id="f7dc9-105">Для переключения между конструкторами MDX и DMX нажимайте кнопку **Расширения интеллектуального анализа данных командного типа** (![Переключение в режим DMX-запросов](../media/rsqdicon-commandtypedmx.gif "Переключение в режим языка DMX-запросов")) на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-105">To switch between the MDX and DMX designers, click the **Command Type DMX** (![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")) button on the toolbar.</span></span> <span data-ttu-id="f7dc9-106">Используйте конструктор DMX-запросов для интерактивного построения запроса расширений интеллектуального анализа данных с применением графических элементов.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-106">Use the DMX Query Designer to interactively build a DMX query using graphical elements.</span></span> <span data-ttu-id="f7dc9-107">Чтобы использовать конструктор DMX-запросов, указываемый источник данных должен уже иметь модель интеллектуального анализа данных, которая будет предоставлять данные.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-107">To use DMX Query Designer, the data source that you specify must already have a data mining model that provides the data.</span></span> <span data-ttu-id="f7dc9-108">Результаты запроса преобразуются в плоский набор строк, который используется в отчете.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-108">Query results are converted to a flattened rowset for use in the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7dc9-109">Перед конструированием отчета следует провести обучение модели.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-109">You must train your model before designing your report.</span></span> <span data-ttu-id="f7dc9-110">Дополнительные сведения см. в разделе [Решения интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span><span class="sxs-lookup"><span data-stu-id="f7dc9-110">For more information, see [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="design-mode"></a><span data-ttu-id="f7dc9-111">Режим конструктора</span><span class="sxs-lookup"><span data-stu-id="f7dc9-111">Design Mode</span></span>  
 <span data-ttu-id="f7dc9-112">Конструктор DMX-запросов открывается в режиме конструктора.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-112">The DMX query designer opens in Design mode.</span></span> <span data-ttu-id="f7dc9-113">В режиме конструктора доступна графическая область конструктора, используемая для выбора определенной модели интеллектуального анализа данных и входной таблицы, а также сетка, используемая для указания прогнозирующего запроса.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-113">Design mode includes a graphical design surface used for selecting a single data mining model and input table, and a grid used for specifying the prediction query.</span></span> <span data-ttu-id="f7dc9-114">Кроме того, существует два других режима конструктора DMX-запросов: режим запросов и режим результатов.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-114">There are two other modes in DMX query designer: Query mode and Result mode.</span></span> <span data-ttu-id="f7dc9-115">В режиме запросов сетка из режима конструктора заменяется панелью запросов, в которой можно вводить запросы расширений интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-115">In Query mode, the grid from Design mode is replaced with a Query pane, which you can use to type DMX queries.</span></span> <span data-ttu-id="f7dc9-116">В режиме результатов в сетке данных отображается результирующий набор, возвращенный запросом.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-116">In Result mode, the result set returned by the query appears in a data grid.</span></span>  
  
 <span data-ttu-id="f7dc9-117">Для изменения режимов конструктора DMX-запросов щелкните правой кнопкой мыши область конструктора и выберите **Проект**, **Запрос**или **Результат**.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-117">To change modes for the DMX query designer, right-click on the query design surface and select **Design**, **Query**, or **Result**.</span></span> <span data-ttu-id="f7dc9-118">Дополнительные сведения см. в разделах [Пользовательский интерфейс конструктора DMX-запросов служб Analysis Services](analysis-services-dmx-query-designer-user-interface.md) и [Получение данных из модели интеллектуального анализа данных (расширения интеллектуального анализа данных) (службы SSRS)](retrieve-data-from-a-data-mining-model-dmx-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="f7dc9-118">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md) and [Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md).</span></span>  
  
## <a name="designing-a-prediction-query"></a><span data-ttu-id="f7dc9-119">Проектирование прогнозирующего запроса</span><span class="sxs-lookup"><span data-stu-id="f7dc9-119">Designing a Prediction Query</span></span>  
 <span data-ttu-id="f7dc9-120">Панель "Конструктор запроса" режима конструктора содержит два окна: **Модель интеллектуального анализа данных** и **Выбор входных таблиц**.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-120">The Query Design pane of the Design mode contains two windows: **Mining Model** and **Select Input Table**.</span></span> <span data-ttu-id="f7dc9-121">Окно **Модель интеллектуального анализа данных** служит для выбора модели интеллектуального анализа, используемой в запросе.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-121">Use the **Mining Model** window to select the mining model to use in your query.</span></span> <span data-ttu-id="f7dc9-122">Окно **Выбор входной таблицы** служит для выбора таблицы, выступающей в качестве основы прогнозов.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-122">Use the **Select Input Table** window to select the table on which to base your predictions.</span></span> <span data-ttu-id="f7dc9-123">Если вместо входной таблицы нужно использовать одноэлементный запрос, щелкните правой кнопкой мыши панель конструктора запроса и выберите пункт **Одноэлементный запрос**.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-123">If you want to use a singleton query instead of an input table, right-click in the Query Design pane and select **Singleton Query**.</span></span> <span data-ttu-id="f7dc9-124">Окно **Выбор входной таблицы** заменяется окном **Ввод одноэлементного запроса** .</span><span class="sxs-lookup"><span data-stu-id="f7dc9-124">The **Select Input Table** window is replaced with a **Singleton Query Input** window.</span></span>  
  
 <span data-ttu-id="f7dc9-125">В режиме конструктора перенесите поля из окон **Модель интеллектуального анализа данных** и **Выбор входной таблицы** в столбец **Поле** панели сетки.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-125">In Design mode, drag fields from the **Mining Model** and **Select Input Table** windows to the **Field** column in the Grid pane.</span></span> <span data-ttu-id="f7dc9-126">Можно также заполнить оставшиеся столбцы, чтобы указать псевдоним, показать в результатах поле, сгруппировать поля и указать оператор для ограничения значения поля с учетом заданных критериев или с учетом аргумента.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-126">You can also fill in the remaining columns to specify an alias, to show the field in the results, to group fields together, and to specify an operator to restrict the field value to a given criteria or argument.</span></span> <span data-ttu-id="f7dc9-127">При работе в режиме запроса можно построить DMX-запрос, перетаскивая поля в панель запросов.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-127">If you are in Query mode, build the DMX query by dragging fields to the Query pane.</span></span>  
  
## <a name="using-parameters"></a><span data-ttu-id="f7dc9-128">Использование параметров</span><span class="sxs-lookup"><span data-stu-id="f7dc9-128">Using Parameters</span></span>  
 <span data-ttu-id="f7dc9-129">Можно передавать параметры отчетов параметру DMX-запросов.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-129">You can pass report parameters to a DMX query parameter.</span></span> <span data-ttu-id="f7dc9-130">Для этого следует добавить параметр в DMX-запрос, задать параметры запроса в диалоговом окне **Параметры запроса** и изменить связанные параметры отчета.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-130">To do this, you must add a parameter to your DMX query, define the query parameters in the **Query Parameters** dialog box, and then modify the associated report parameters.</span></span> <span data-ttu-id="f7dc9-131">Чтобы определить параметр запроса, нажмите кнопку **Параметры запроса** (![Значок диалогового окна "Параметры запроса"](../media/iconqueryparameter.gif "Значок диалогового окна "Параметры запроса"")) на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="f7dc9-131">To define a query parameter, click the **Query Parameters** (![Icon for the Query Parameters dialog box](../media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")) button on the toolbar.</span></span> <span data-ttu-id="f7dc9-132">Инструкции по заданию параметров в DMX-запросе см. в разделе [Определение параметров в конструкторе запросов многомерных выражений для служб Analysis Services (построитель отчетов и службы SSRS)](define-parameters-in-the-mdx-query-designer-for-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="f7dc9-132">To view instructions about defining parameters in a DMX query, see [Define Parameters in the MDX Query Designer for Analysis Services &#40;Report Builder and SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md).</span></span>  
  
 <span data-ttu-id="f7dc9-133">Дополнительные сведения об управлении связями между параметрами отчета и запроса см. в разделе [Связь параметра запроса с параметром отчета (построитель отчетов и службы SSRS)](associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="f7dc9-133">For more information about how to manage the relationship between report parameters and query parameters, see [Associate a Query Parameter with a Report Parameter &#40;Report Builder and SSRS&#41;](associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="f7dc9-134">Дополнительные сведения о параметрах см. в разделе [Параметры отчета (построитель отчетов и конструктор отчетов)](../report-design/report-parameters-report-builder-and-report-designer.md).</span><span class="sxs-lookup"><span data-stu-id="f7dc9-134">For more information about parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7dc9-135">См. также:</span><span class="sxs-lookup"><span data-stu-id="f7dc9-135">See Also</span></span>  
 <span data-ttu-id="f7dc9-136">[Решения для интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions) </span><span class="sxs-lookup"><span data-stu-id="f7dc9-136">[Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions) </span></span>  
 <span data-ttu-id="f7dc9-137">[Средства проектирования запросов в конструктор отчетов SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7dc9-137">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md) </span></span>  
 [<span data-ttu-id="f7dc9-138">Подключения данных, Источники данных и Строки подключения в службе Reporting Services</span><span class="sxs-lookup"><span data-stu-id="f7dc9-138">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  