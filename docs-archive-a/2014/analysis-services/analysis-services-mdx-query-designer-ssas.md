---
title: Конструктор запросов многомерных выражений Analysis Services (SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.asmdxquerydes.f1
ms.assetid: a2fb0b79-802a-4dac-bd9a-32dfe2e8c4d4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 98c08da8e7caaba268346075a3bb3e9e8e5dc3c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656913"
---
# <a name="analysis-services-mdx-query-designer-ssas"></a><span data-ttu-id="ff9cc-102">Конструктор многомерных запросов служб Analysis Services (службы SSAS)</span><span class="sxs-lookup"><span data-stu-id="ff9cc-102">Analysis Services MDX Query Designer (SSAS)</span></span>
  <span data-ttu-id="ff9cc-103">Конструктор запросов многомерных выражений Analysis Services предоставляет графические пользовательские интерфейсы, помогающие создавать запросы многомерных выражений для [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] источника данных.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-103">The Analysis Services Multidimensional Expression (MDX) query designer provides a graphical user interfaces to help you create MDX queries for a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="ff9cc-104">Графический конструктор запросов многомерных выражений имеет два режима: режим конструктора и режим запросов.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-104">The MDX graphical query designer has two modes: design mode and query mode.</span></span> <span data-ttu-id="ff9cc-105">В каждом режиме есть панель метаданных, из которой можно перетаскивать элементы с выбранного куба для построения запроса многомерных выражений, который возвращает нужные данные.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-105">Each mode provides a metadata pane from which you can drag members from the selected cubes to build an MDX query that retrieves the data you want to use.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ff9cc-106">При создании и выполнении запросов пользователи получают доступ к источникам данных.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="ff9cc-107">Следует предоставить минимальные разрешения на источники данных, например разрешение только на чтение.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>  
>   
>  <span data-ttu-id="ff9cc-108">При выполнении запроса для соединения с источником данных используются учетные данные текущего пользователя, а не указанные на странице «Сведения об олицетворении».</span><span class="sxs-lookup"><span data-stu-id="ff9cc-108">The credentials of the current user, not the credentials specified in the Impersonation Information page, are used to connect to the data source when a query is executed.</span></span>  
  
 <span data-ttu-id="ff9cc-109">В следующих разделах описываются кнопки панели инструментов и области конструктора запросов для каждого режима работы графического конструктора запросов.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-109">The following sections describe the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>  
  
## <a name="graphical-mdx-query-designer-in-design-mode"></a><span data-ttu-id="ff9cc-110">Графический конструктор запросов многомерных выражений: режим конструктора</span><span class="sxs-lookup"><span data-stu-id="ff9cc-110">Graphical MDX Query Designer in Design Mode</span></span>  
 <span data-ttu-id="ff9cc-111">При изменении запроса многомерных выражений графический конструктор запросов многомерных выражений откроется в режиме конструктора.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-111">When you edit an MDX query, the graphical MDX query designer opens in Design mode.</span></span>  
  
 <span data-ttu-id="ff9cc-112">На следующем рисунке отмечены панели в режиме конструктора.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-112">The following figure labels the panes for Design mode.</span></span>  
  
 <span data-ttu-id="ff9cc-113">![Конструктор запросов многомерных выражений служб Analysis Services, режим конструктора](media/rsqd-dsawas-mdx-designmode.gif "Конструктор запросов многомерных выражений служб Analysis Services, режим конструктора")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-113">![Analysis Services MDX query designer, design view](media/rsqd-dsawas-mdx-designmode.gif "Analysis Services MDX query designer, design view")</span></span>  
  
 <span data-ttu-id="ff9cc-114">В следующей таблице перечисляются панели, доступные в этом режиме.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-114">The following table lists the panes in this mode:</span></span>  
  
|<span data-ttu-id="ff9cc-115">Панель</span><span class="sxs-lookup"><span data-stu-id="ff9cc-115">Pane</span></span>|<span data-ttu-id="ff9cc-116">Компонент</span><span class="sxs-lookup"><span data-stu-id="ff9cc-116">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="ff9cc-117">Кнопка "Выбрать куб" (**...**)</span><span class="sxs-lookup"><span data-stu-id="ff9cc-117">Select Cube button (**...**)</span></span>|<span data-ttu-id="ff9cc-118">Отображает куб, выбранный в настоящий момент.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-118">Displays the currently selected cube.</span></span>|  
|<span data-ttu-id="ff9cc-119">Панель «Метаданные»</span><span class="sxs-lookup"><span data-stu-id="ff9cc-119">Metadata pane</span></span>|<span data-ttu-id="ff9cc-120">Отображает список мер в иерархическом порядке, ключевые показатели эффективности (KPIs) и измерения, определенные для выбранного куба.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-120">Displays a hierarchical list of measures, Key Performance Indicators (KPIs), and dimensions defined on the selected cube.</span></span>|  
|<span data-ttu-id="ff9cc-121">Панель «Вычисляемые элементы»</span><span class="sxs-lookup"><span data-stu-id="ff9cc-121">Calculated Members pane</span></span>|<span data-ttu-id="ff9cc-122">Отображает вычисляемые элементы, определенные на данный момент и доступные для использования в запросе.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-122">Displays the currently defined calculated members available for use in the query.</span></span>|  
|<span data-ttu-id="ff9cc-123">Панель «Фильтр»</span><span class="sxs-lookup"><span data-stu-id="ff9cc-123">Filter pane</span></span>|<span data-ttu-id="ff9cc-124">Используется для выбора измерений и связанных иерархий для фильтрации данных в источнике и ограничения возвращаемых данных.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-124">Use to choose dimensions and related hierarchies to filter data at the source and limit data returned.</span></span>|  
|<span data-ttu-id="ff9cc-125">Панель «Данные»</span><span class="sxs-lookup"><span data-stu-id="ff9cc-125">Data pane</span></span>|<span data-ttu-id="ff9cc-126">Отображает заголовки столбцов для результирующего набора в ходе перетаскивания элементов с панели «Метаданные» и панели «Вычисляемые элементы».</span><span class="sxs-lookup"><span data-stu-id="ff9cc-126">Displays the column headings for the result set as you drag items from the Metadata pane and the Calculated Members pane.</span></span> <span data-ttu-id="ff9cc-127">Автоматически обновляет результирующий набор, если выбрана кнопка **Автовыполнение** .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-127">Automatically updates the result set if the **AutoExecute** button is selected.</span></span>|  
  
 <span data-ttu-id="ff9cc-128">Можно перетаскивать измерения, меры и ключевые показатели эффективности с панели «Метаданные», а вычисляемые элементы с панели «Вычисляемые элементы» на панель «Данные».</span><span class="sxs-lookup"><span data-stu-id="ff9cc-128">You can drag dimensions, measures, and KPIs from the Metadata pane, and calculated members from the Calculated Member pane, onto the Data pane.</span></span> <span data-ttu-id="ff9cc-129">На панели «Фильтр» можно выбрать измерения и относящиеся к ним иерархии, а также задать критерии фильтра для ограничения данных, доступных запросу.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-129">In the Filter pane, you can select dimensions and related hierarchies, and set filter expressions to limit the data available to query.</span></span> <span data-ttu-id="ff9cc-130">При выборе переключателя **Автовыполнение** (![Автоматическое выполнение запроса](media/rsqdicon-autoexecute.gif "Автоматическое выполнение запроса")) на панели инструментов конструктор запросов выполняет запрос каждый раз при помещении объекта метаданных на панель "Данные".</span><span class="sxs-lookup"><span data-stu-id="ff9cc-130">If the **AutoExecute** (![AutoExecute the query](media/rsqdicon-autoexecute.gif "AutoExecute the query")) toggle button on the toolbar is selected, the query designer runs the query every time that you drop a metadata object onto the Data pane.</span></span> <span data-ttu-id="ff9cc-131">Запрос можно выполнить вручную, нажав кнопку **Запуск** (![Выполнение запроса](media/rsqdicon-run.gif "Выполнить запрос")) на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-131">You can manually run the query using the **Run** (![Run the query](media/rsqdicon-run.gif "Run the query")) button on the toolbar.</span></span>  
  
 <span data-ttu-id="ff9cc-132">При создании запроса многомерных выражений в данном режиме следующие дополнительные свойства автоматически включаются в запрос:</span><span class="sxs-lookup"><span data-stu-id="ff9cc-132">When you create an MDX query in this mode, the following additional properties are automatically included in the query:</span></span>  
  
 <span data-ttu-id="ff9cc-133">**Свойства элемента** MEMBER_CAPTION, MEMBER_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff9cc-133">**Member Properties** MEMBER_CAPTION, MEMBER_UNIQUE_NAME</span></span>  
  
 <span data-ttu-id="ff9cc-134">**Свойства ячейки** VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="ff9cc-134">**Cell Properties** VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS</span></span>  
  
 <span data-ttu-id="ff9cc-135">Чтобы включить собственные дополнительные свойства, необходимо вручную изменить запрос многомерных выражений в режиме запроса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-135">To specify your own additional properties, you must manually edit the MDX query in Query mode.</span></span>  
  
 <span data-ttu-id="ff9cc-136">Импорт запроса многомерных выражений из файла не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-136">Importing an .mdx query from a file is not supported.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff9cc-137">Дополнительные сведения о многомерных выражениях и общие сведения о конструкторе запросов многомерных выражений см. в разделе "Редактор запросов многомерных выражений (службы Analysis Services — многомерные данные)" [электронной документации по SQL Server](https://go.microsoft.com/fwlink/?linkid=98335).</span><span class="sxs-lookup"><span data-stu-id="ff9cc-137">For more information about MDX and general information about the MDX query designer, see "MDX Query Editor (Analysis Services - Multidimensional Data)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335).</span></span>  
  
### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a><span data-ttu-id="ff9cc-138">Панель инструментов графического конструктора запросов многомерных выражений в режиме конструктора</span><span class="sxs-lookup"><span data-stu-id="ff9cc-138">Graphical MDX Query Designer Toolbar in Design Mode</span></span>  
 <span data-ttu-id="ff9cc-139">Панель инструментов конструктора запросов содержит кнопки, которые помогают создавать запросы многомерных выражений с помощью графического интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-139">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="ff9cc-140">В следующей таблице перечислены кнопки и их функции.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-140">The following table lists the buttons and their functions.</span></span>  
  
|<span data-ttu-id="ff9cc-141">Кнопка</span><span class="sxs-lookup"><span data-stu-id="ff9cc-141">Button</span></span>|<span data-ttu-id="ff9cc-142">Описание</span><span class="sxs-lookup"><span data-stu-id="ff9cc-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ff9cc-143">**Редактировать как текст**</span><span class="sxs-lookup"><span data-stu-id="ff9cc-143">**Edit As Text**</span></span>|<span data-ttu-id="ff9cc-144">Не включено для данного типа источника данных.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-144">Not enabled for this data source type.</span></span>|  
|<span data-ttu-id="ff9cc-145">**Импорт**</span><span class="sxs-lookup"><span data-stu-id="ff9cc-145">**Import**</span></span>|<span data-ttu-id="ff9cc-146">Импортировать существующий запрос из файла определения отчета (RDL), расположенного в файловой системе.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-146">Import an existing query from a report definition (.rdl) file on the file system.</span></span>|  
|<span data-ttu-id="ff9cc-147">![Переключение в режим запросов многомерных выражений](media/rsqdicon-commandtypemdx.gif "Переключение в режим запросов многомерных выражений")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-147">![Change to MDX query view](media/rsqdicon-commandtypemdx.gif "Change to MDX query view")</span></span>|<span data-ttu-id="ff9cc-148">Перейти к многомерному выражению командного типа.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-148">Switch to Command Type MDX.</span></span>|  
|<span data-ttu-id="ff9cc-149">![Обновление результирующих данных](media/rsqdicon-refresh.gif "Обновление результирующих данных")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-149">![Refresh result data](media/rsqdicon-refresh.gif "Refresh result data")</span></span>|<span data-ttu-id="ff9cc-150">Обновление метаданных из источника данных.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-150">Refresh metadata from the data source.</span></span>|  
|<span data-ttu-id="ff9cc-151">![Добавление вычисляемого элемента](media/rsqdicon-addcalculatedmember.gif "Добавить вычисляемый элемент")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-151">![Add calculated member](media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="ff9cc-152">Отображение диалогового окна **Построитель вычисляемых элементов** .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-152">Display the **Calculated Member Builder** dialog box.</span></span>|  
|<span data-ttu-id="ff9cc-153">![Переключатель для просмотра пустых ячеек](media/rsqdicon-showemptycells.gif "Переключатель для просмотра пустых ячеек")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-153">![Toggle for show empty cells](media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="ff9cc-154">Переключение между отображением и скрытием пустых ячеек на панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="ff9cc-154">Toggle between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="ff9cc-155">(Это эквивалентно использованию предложения NON EMPTY в многомерном выражении).</span><span class="sxs-lookup"><span data-stu-id="ff9cc-155">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|  
|<span data-ttu-id="ff9cc-156">![Автоматическое выполнение запроса](media/rsqdicon-autoexecute.gif "Автоматическое выполнение запроса")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-156">![AutoExecute the query](media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="ff9cc-157">Автоматически выполнять запрос и отображать результат при каждом изменении.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-157">Automatically run the query and show the result every time a change is made.</span></span> <span data-ttu-id="ff9cc-158">Результаты отображаются в панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="ff9cc-158">Results are shown in the Data pane.</span></span>|  
|<span data-ttu-id="ff9cc-159">![Кнопка отображения агрегатов](media/rsqdicon-showaggregations.gif "Кнопка "Показать агрегаты"")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-159">![Show Aggregations button](media/rsqdicon-showaggregations.gif "Show Aggregations button")</span></span>|<span data-ttu-id="ff9cc-160">Показать статистические выражения на панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="ff9cc-160">Show aggregations in the Data pane.</span></span>|  
|<span data-ttu-id="ff9cc-161">![Удалить](media/rsqdicon-delete.gif "DELETE")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-161">![Delete](media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="ff9cc-162">Удалить выбранный на панель «Данные» столбец из запроса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-162">Delete the selected column in the Data pane from the query.</span></span>|  
|<span data-ttu-id="ff9cc-163">![Значок диалогового окна "Параметры запроса"](media/iconqueryparameter.gif "Значок диалогового окна "Параметры запроса"")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-163">![Icon for the Query Parameters dialog box](media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="ff9cc-164">Отображает диалоговое окно **Параметры запроса** .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-164">Display the **Query Parameters** dialog box.</span></span> <span data-ttu-id="ff9cc-165">При указании значений для параметра запроса автоматически создается параметр с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-165">When you specify values for a query parameter, a parameter with the same name is automatically created.</span></span>|  
|<span data-ttu-id="ff9cc-166">![Кнопка "Подготовить запрос"](media/rsqdicon-preparequery.gif "Кнопка "Подготовить запрос"")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-166">![Prepare Query button](media/rsqdicon-preparequery.gif "Prepare Query button")</span></span>|<span data-ttu-id="ff9cc-167">Подготовить запрос.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-167">Prepare the query.</span></span>|  
|<span data-ttu-id="ff9cc-168">![Выполнить запрос](media/rsqdicon-run.gif "Выполнить запрос")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-168">![Run the query](media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="ff9cc-169">Выполнить запрос и показать результаты на панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="ff9cc-169">Run the query and display the results in the Data pane.</span></span>|  
|<span data-ttu-id="ff9cc-170">![Отмена запроса](media/rsqdicon-cancel.gif "Отмена запроса")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-170">![Cancel the query](media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="ff9cc-171">Отмена запроса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-171">Cancel the query.</span></span>|  
|<span data-ttu-id="ff9cc-172">![Перейти в режим конструктора](media/rsqdicon-designmode.gif "Перейти в режим конструктора")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-172">![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="ff9cc-173">Переключение между режимом конструктора и режимом запроса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-173">Toggle between Design mode and Query mode.</span></span>|  
  
## <a name="graphical-mdx-query-designer-in-query-mode"></a><span data-ttu-id="ff9cc-174">Графический конструктор запросов многомерных выражений: режим запроса</span><span class="sxs-lookup"><span data-stu-id="ff9cc-174">Graphical MDX Query Designer in Query Mode</span></span>  
 <span data-ttu-id="ff9cc-175">Для переключения графического конструктора запросов в режим **запроса** нажмите кнопку **Режим конструктора** на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-175">To change the graphical query designer to **Query** mode, click the **Design Mode** button on the toolbar.</span></span>  
  
 <span data-ttu-id="ff9cc-176">На следующем рисунке показаны метки панелей режима запроса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-176">The following figure labels the panes for Query mode.</span></span>  
  
 <span data-ttu-id="ff9cc-177">![Конструктор запросов многомерных выражений служб Analysis Services, режим запроса](media/rsqd-dsawas-mdx-querymode.gif "Конструктор запросов многомерных выражений служб Analysis Services, режим запроса")</span><span class="sxs-lookup"><span data-stu-id="ff9cc-177">![Analysis Services MDX query designer, query view](media/rsqd-dsawas-mdx-querymode.gif "Analysis Services MDX query designer, query view")</span></span>  
  
 <span data-ttu-id="ff9cc-178">В следующей таблице перечисляются панели, доступные в этом режиме.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-178">The following table lists the panes in this mode:</span></span>  
  
|<span data-ttu-id="ff9cc-179">Панель</span><span class="sxs-lookup"><span data-stu-id="ff9cc-179">Pane</span></span>|<span data-ttu-id="ff9cc-180">Компонент</span><span class="sxs-lookup"><span data-stu-id="ff9cc-180">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="ff9cc-181">Кнопка "Выбрать куб" (**...**)</span><span class="sxs-lookup"><span data-stu-id="ff9cc-181">Select Cube button (**...**)</span></span>|<span data-ttu-id="ff9cc-182">Отображает куб, выбранный в настоящий момент.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-182">Displays the currently selected cube.</span></span>|  
|<span data-ttu-id="ff9cc-183">Панель Метаданные/Функции/Шаблоны</span><span class="sxs-lookup"><span data-stu-id="ff9cc-183">Metadata/Functions/Templates pane</span></span>|<span data-ttu-id="ff9cc-184">Отображает меры в иерархическом списке, ключевые показатели эффективности и измерения, определенные для выбранного куба.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-184">Displays a hierarchical list of measures, KPIs, and dimensions defined on the selected cube.</span></span>|  
|<span data-ttu-id="ff9cc-185">Панель запросов</span><span class="sxs-lookup"><span data-stu-id="ff9cc-185">Query pane</span></span>|<span data-ttu-id="ff9cc-186">Отображает текст запроса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-186">Displays the query text.</span></span>|  
|<span data-ttu-id="ff9cc-187">Панель результатов</span><span class="sxs-lookup"><span data-stu-id="ff9cc-187">Result pane</span></span>|<span data-ttu-id="ff9cc-188">Отображает результаты выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-188">Displays the results of running the query.</span></span>|  
  
 <span data-ttu-id="ff9cc-189">Панель «Метаданные» содержит вкладки **Метаданные**, **Функции**и **Шаблоны**.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-189">The Metadata pane displays tabs for **Metadata**, **Functions**, and **Templates**.</span></span> <span data-ttu-id="ff9cc-190">Можно перетащить измерения, иерархии, ключевые показатели эффективности и меры с вкладки **Метаданные** на панель запросов многомерных выражений.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-190">From the **Metadata** tab, you can drag dimensions, hierarchies, KPIs, and measures onto the MDX Query pane.</span></span> <span data-ttu-id="ff9cc-191">Функции можно перетащить с вкладки **Функции** на панель запросов многомерных выражений.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-191">From the **Functions** tab, you can drag functions onto the MDX Query pane.</span></span> <span data-ttu-id="ff9cc-192">Шаблоны многомерных выражений можно добавить на панель запросов многомерных выражений с вкладки **Шаблоны** .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-192">From the **Templates** tab, you can add MDX templates to the MDX Query pane.</span></span> <span data-ttu-id="ff9cc-193">После выполнения запроса на панели результатов отображаются результаты запроса многомерных выражений.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-193">When you execute the query, the Result pane displays the results for the MDX query.</span></span>  
  
 <span data-ttu-id="ff9cc-194">Запрос многомерных выражений по умолчанию, сформированный в режиме конструктора, можно расширить, включив дополнительные свойства элементов и ячеек.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-194">You can extend the default MDX query generated in Design mode to include additional member properties and cell properties.</span></span> <span data-ttu-id="ff9cc-195">После выполнения запроса следующие значения не будут отражены в результирующем наборе.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-195">When you run the query, these values do not appear in the result set.</span></span> <span data-ttu-id="ff9cc-196">Однако они передаются обратно с коллекцией полей набора данных, и эти значения можно использовать.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-196">However, they are passed back with the dataset field collection and you can use these values.</span></span>  
  
### <a name="graphical-query-designer-toolbar-in-query-mode"></a><span data-ttu-id="ff9cc-197">Панель инструментов графического конструктора запросов многомерных выражений в режиме запроса</span><span class="sxs-lookup"><span data-stu-id="ff9cc-197">Graphical Query Designer Toolbar in Query Mode</span></span>  
 <span data-ttu-id="ff9cc-198">Панель инструментов конструктора запросов содержит кнопки, которые помогают создавать запросы многомерных выражений с помощью графического интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-198">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span>  
  
 <span data-ttu-id="ff9cc-199">Кнопки на панели инструментов в режиме конструктора ничем не отличаются от кнопок в режиме запроса, однако в режиме запроса недоступны следующие кнопки.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-199">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>  
  
-   <span data-ttu-id="ff9cc-200">**Редактировать как текст**</span><span class="sxs-lookup"><span data-stu-id="ff9cc-200">**Edit As Text**</span></span>  
  
-   <span data-ttu-id="ff9cc-201">**Добавить вычисляемый элемент** (![Добавить вычисляемый элемент](media/rsqdicon-addcalculatedmember.gif "Добавить вычисляемый элемент"))</span><span class="sxs-lookup"><span data-stu-id="ff9cc-201">**Add Calculated Member** (![Add calculated member](media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>  
  
-   <span data-ttu-id="ff9cc-202">**Показывать пустые ячейки** (![Переключатель для просмотра пустых ячеек](media/rsqdicon-showemptycells.gif "Переключатель для просмотра пустых ячеек"))</span><span class="sxs-lookup"><span data-stu-id="ff9cc-202">**Show Empty Cells** (![Toggle for show empty cells](media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>  
  
-   <span data-ttu-id="ff9cc-203">**AutoExecute** (![Автоматическое выполнение запроса](media/rsqdicon-autoexecute.gif "Автоматическое выполнение запроса"))</span><span class="sxs-lookup"><span data-stu-id="ff9cc-203">**AutoExecute** (![AutoExecute the query](media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>  
  
-   <span data-ttu-id="ff9cc-204">**Показать агрегаты** (![Кнопка отображения агрегатов](media/rsqdicon-showaggregations.gif "Кнопка "Показать агрегаты""))</span><span class="sxs-lookup"><span data-stu-id="ff9cc-204">**Show Aggregations** (![Show Aggregations button](media/rsqdicon-showaggregations.gif "Show Aggregations button"))</span></span>  
  
  