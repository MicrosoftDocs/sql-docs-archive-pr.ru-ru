---
title: Пользовательский интерфейс конструктора запросов SAP NetWeaver BI (построитель отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10014"
- sql12.rtp.rptdesigner.dataview.sapbwquerydesigner.f1
helpviewer_keywords:
- data sources [Reporting Services], SAP NetWeaver Business Intelligence
- SAP NetWeaver Business Intelligence [Reporting Services], query designer
- query designers [Reporting Services]
ms.assetid: 102da66e-ca31-41aa-ab4b-c9b5ab752a72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c1bd7293021a1a755c8189f354af7a54f7e4737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657021"
---
# <a name="sap-netweaver-bi-query-designer-user-interface"></a><span data-ttu-id="52984-102">Пользовательский интерфейс конструктора запросов BI SAP NetWeaver</span><span class="sxs-lookup"><span data-stu-id="52984-102">SAP NetWeaver BI Query Designer User Interface</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="52984-103">предоставляют графический конструктор запросов, предназначенный для построения запросов многомерных выражений к источнику данных SAP NetWeaver® Business Intelligence.</span><span class="sxs-lookup"><span data-stu-id="52984-103">provides a graphical query designer for building Multidimensional Expression (MDX) queries for a SAP NetWeaver® Business Intelligence data source.</span></span> <span data-ttu-id="52984-104">Графический конструктор запросов многомерных выражений имеет два режима: режим конструктора и режим запросов.</span><span class="sxs-lookup"><span data-stu-id="52984-104">The MDX graphical query designer has two modes: Design mode and Query mode.</span></span> <span data-ttu-id="52984-105">В каждом режиме имеется панель «Метаданные», из которой можно перетащить элементы из InfoCube, MultiProvider или запроса с поддержкой веб-доступа, определенного на источнике данных, для построения запроса многомерных выражений, получающего данные при обработке отчета.</span><span class="sxs-lookup"><span data-stu-id="52984-105">Each mode provides a Metadata pane from which you can drag members from an InfoCube, MultiProvider, or Web-enabled query defined on the data source to build an MDX query that retrieves data when the report is processed.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="52984-106">При создании и выполнении запросов пользователи получают доступ к источникам данных.</span><span class="sxs-lookup"><span data-stu-id="52984-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="52984-107">Следует предоставить минимальные разрешения на источники данных, например разрешение только на чтение.</span><span class="sxs-lookup"><span data-stu-id="52984-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="52984-108">Дополнительные сведения о работе с многомерными источниками данных SAP см. в разделе [Тип соединения SAP NetWeaver BI (службы SSRS)](sap-netweaver-bi-connection-type-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="52984-108">For more information about working with a SAP multidimensional data source, see [SAP NetWeaver BI Connection Type &#40;SSRS&#41;](sap-netweaver-bi-connection-type-ssrs.md).</span></span>

 <span data-ttu-id="52984-109">В этом разделе описываются кнопки панели инструментов и области конструктора запросов для каждого режима работы графического конструктора запросов.</span><span class="sxs-lookup"><span data-stu-id="52984-109">This section describes the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>

## <a name="graphical-query-designer-in-design-mode"></a><span data-ttu-id="52984-110">Графический конструктор запросов в режиме конструктора</span><span class="sxs-lookup"><span data-stu-id="52984-110">Graphical Query Designer in Design Mode</span></span>
 <span data-ttu-id="52984-111">При изменении запроса набора данных, в котором используется источник данных [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] , графический конструктор запросов открывается в режиме конструктора.</span><span class="sxs-lookup"><span data-stu-id="52984-111">When you edit a dataset query that uses a [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source, the graphical query designer opens in the Design mode.</span></span> <span data-ttu-id="52984-112">На следующем рисунке отмечены панели в режиме конструктора.</span><span class="sxs-lookup"><span data-stu-id="52984-112">The following figure labels the panes for Design mode.</span></span>

 <span data-ttu-id="52984-113">![Конструктор запросов с использованием многомерных выражений в режиме конструктора](../media/rsqd-dssapbw-mdx-designmode.gif "Конструктор запросов с использованием многомерных выражений в режиме конструктора")</span><span class="sxs-lookup"><span data-stu-id="52984-113">![Query Designer using MDX in Design Mode](../media/rsqd-dssapbw-mdx-designmode.gif "Query Designer using MDX in Design Mode")</span></span>

 <span data-ttu-id="52984-114">В следующей таблице приводится список панелей в этом режиме.</span><span class="sxs-lookup"><span data-stu-id="52984-114">The following table lists the panes in this mode.</span></span>

|<span data-ttu-id="52984-115">Панель</span><span class="sxs-lookup"><span data-stu-id="52984-115">Pane</span></span>|<span data-ttu-id="52984-116">Компонент</span><span class="sxs-lookup"><span data-stu-id="52984-116">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="52984-117">Кнопка «Выбрать куб»</span><span class="sxs-lookup"><span data-stu-id="52984-117">Select Cube button</span></span>|<span data-ttu-id="52984-118">Отображается текущий выбранный InfoCube, MultiProvider или запрос с поддержкой веб-доступа.</span><span class="sxs-lookup"><span data-stu-id="52984-118">Displays the currently selected InfoCube, MultiProvider, or Web-enabled query.</span></span>|
|<span data-ttu-id="52984-119">Панель «Метаданные»</span><span class="sxs-lookup"><span data-stu-id="52984-119">Metadata pane</span></span>|<span data-ttu-id="52984-120">Отображается иерархический список InfoCube, MultiProvider и запросов.</span><span class="sxs-lookup"><span data-stu-id="52984-120">Displays a hierarchical list of InfoCubes, MultiProviders, and queries.</span></span> <span data-ttu-id="52984-121">Запросы, созданные в источнике данных, появляются под соответствующим кубом.</span><span class="sxs-lookup"><span data-stu-id="52984-121">Queries created at the data source may appear under the corresponding cube.</span></span>|
|<span data-ttu-id="52984-122">Панель «Вычисляемые элементы»</span><span class="sxs-lookup"><span data-stu-id="52984-122">Calculated Members pane</span></span>|<span data-ttu-id="52984-123">Отображает вычисляемые элементы, определенные на данный момент и доступные для использования в запросе.</span><span class="sxs-lookup"><span data-stu-id="52984-123">Displays the currently defined calculated members available for use in the query.</span></span>|
|<span data-ttu-id="52984-124">Панель «Данные»</span><span class="sxs-lookup"><span data-stu-id="52984-124">Data pane</span></span>|<span data-ttu-id="52984-125">Отображает результаты выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="52984-125">Displays the results of running the query.</span></span>|

 <span data-ttu-id="52984-126">На панель «Данные» можно перетаскивать измерения и ключевые элементы с панели «Метаданные» и вычисляемые элементы с панели «Вычисляемые элементы».</span><span class="sxs-lookup"><span data-stu-id="52984-126">You can drag dimensions and key figures from the Metadata pane, and calculated members from the Calculated Member pane onto the Data pane.</span></span> <span data-ttu-id="52984-127">Если переключатель **Автовыполнение** на панели инструментов включен, конструктор запросов выполняет запрос каждый раз при перетаскивании объекта в область «Данные».</span><span class="sxs-lookup"><span data-stu-id="52984-127">If the **AutoExecute** toggle button on the toolbar is on, the query designer runs the query every time you drop an object onto the Data pane.</span></span> <span data-ttu-id="52984-128">Если переключатель **Автовыполнение** выключен, конструктор запросов не выполняет запрос при любых изменениях в панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="52984-128">If **AutoExecute** is off, the query designer does not run the query as you make changes to the Data pane.</span></span> <span data-ttu-id="52984-129">Запрос можно выполнить вручную, нажав кнопку **Запуск** на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="52984-129">You can manually run the query using the **Run** button on the toolbar.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a><span data-ttu-id="52984-130">Панель инструментов графического конструктора запросов в режиме конструктора</span><span class="sxs-lookup"><span data-stu-id="52984-130">Toolbar for the Graphical Query Designer in Design Mode Toolbar</span></span>
 <span data-ttu-id="52984-131">Панель инструментов конструктора запросов содержит кнопки, которые помогают создавать запросы многомерных выражений с помощью графического интерфейса.</span><span class="sxs-lookup"><span data-stu-id="52984-131">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="52984-132">В следующей таблице перечислены кнопки и описаны их функции.</span><span class="sxs-lookup"><span data-stu-id="52984-132">The following table describes the buttons and their functions.</span></span>

|<span data-ttu-id="52984-133">Кнопка</span><span class="sxs-lookup"><span data-stu-id="52984-133">Button</span></span>|<span data-ttu-id="52984-134">Description</span><span class="sxs-lookup"><span data-stu-id="52984-134">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="52984-135">**Редактировать как текст**</span><span class="sxs-lookup"><span data-stu-id="52984-135">**Edit As Text**</span></span>|<span data-ttu-id="52984-136">Переключиться из текстового конструктора запросов в графический и обратно.</span><span class="sxs-lookup"><span data-stu-id="52984-136">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="52984-137">Недоступен для этого типа источника данных.</span><span class="sxs-lookup"><span data-stu-id="52984-137">Not available for this data source type.</span></span>|
|<span data-ttu-id="52984-138">**Импорт**</span><span class="sxs-lookup"><span data-stu-id="52984-138">**Import**</span></span>|<span data-ttu-id="52984-139">Импортировать существующий запрос из файла определения отчета (RDL), расположенного в файловой системе.</span><span class="sxs-lookup"><span data-stu-id="52984-139">Import an existing query from a report definition (.rdl) file on the file system.</span></span> <span data-ttu-id="52984-140">Дополнительные сведения см. в разделе [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="52984-140">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|
|<span data-ttu-id="52984-141">![Обновление полей набора данных](../media/rsqdicon-refreshfields.gif "Обновление полей набора данных")</span><span class="sxs-lookup"><span data-stu-id="52984-141">![Refresh dataset fields](../media/rsqdicon-refreshfields.gif "Refresh dataset fields")</span></span>|<span data-ttu-id="52984-142">Обновление метаданных из источника данных.</span><span class="sxs-lookup"><span data-stu-id="52984-142">Refresh metadata from the data source.</span></span>|
|<span data-ttu-id="52984-143">![Добавление вычисляемого элемента](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Добавить вычисляемый элемент")</span><span class="sxs-lookup"><span data-stu-id="52984-143">![Add calculated member](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="52984-144">Отображение диалогового окна **Построитель вычисляемых элементов** .</span><span class="sxs-lookup"><span data-stu-id="52984-144">Display the **Calculated Member Builder** dialog box.</span></span>|
|<span data-ttu-id="52984-145">![Переключатель для отображения пустых ячеек](../../analysis-services/media/rsqdicon-showemptycells.gif "Переключатель для просмотра пустых ячеек")</span><span class="sxs-lookup"><span data-stu-id="52984-145">![Toggle for show empty cells](../../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="52984-146">Переключение между режимами отображения и скрытия пустых ячеек в панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="52984-146">Switch between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="52984-147">(Это эквивалентно использованию предложения NON EMPTY в многомерном выражении).</span><span class="sxs-lookup"><span data-stu-id="52984-147">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|
|<span data-ttu-id="52984-148">![Автоматическое выполнение запроса](../../analysis-services/media/rsqdicon-autoexecute.gif "Автоматическое выполнение запроса")</span><span class="sxs-lookup"><span data-stu-id="52984-148">![AutoExecute the query](../../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="52984-149">Автоматическое выполнение запроса и вывод результатов после каждого изменения, например после удаления столбца на панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="52984-149">Automatically run the query and show the result every time a change is made, for example, deleting a column in the Data pane.</span></span> <span data-ttu-id="52984-150">Результаты отображаются в панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="52984-150">Results are shown in the Data pane.</span></span>|
|<span data-ttu-id="52984-151">![Удаление](../../analysis-services/media/rsqdicon-delete.gif "DELETE")</span><span class="sxs-lookup"><span data-stu-id="52984-151">![Delete](../../analysis-services/media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="52984-152">Удалить выбранный на панель «Данные» столбец из запроса.</span><span class="sxs-lookup"><span data-stu-id="52984-152">Delete the selected column in the Data pane from the query.</span></span>|
|<span data-ttu-id="52984-153">![Значок диалогового окна "Параметры запроса"](../../analysis-services/media/iconqueryparameter.gif "Значок диалогового окна "Параметры запроса"")</span><span class="sxs-lookup"><span data-stu-id="52984-153">![Icon for the Query Parameters dialog box](../../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="52984-154">Отобразить диалоговое окно **Переменные** .</span><span class="sxs-lookup"><span data-stu-id="52984-154">Display the **Variables** dialog box.</span></span> <span data-ttu-id="52984-155">Эта кнопка включена, только если выбранный куб является кубом запроса (так как переменные поддерживаются только в кубах запросов).</span><span class="sxs-lookup"><span data-stu-id="52984-155">This button is enabled only when the selected cube is a Query cube (because only query cubes support variables).</span></span> <span data-ttu-id="52984-156">При присвоении переменной значения по умолчанию создается соответствующий параметр в отчете.</span><span class="sxs-lookup"><span data-stu-id="52984-156">When you assign a default value to a variable, a corresponding report parameter is created.</span></span>|
|<span data-ttu-id="52984-157">![Выполнить запрос](../../analysis-services/media/rsqdicon-run.gif "Выполнить запрос")</span><span class="sxs-lookup"><span data-stu-id="52984-157">![Run the query](../../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="52984-158">Выполнить запрос и показать результаты на панели «Данные».</span><span class="sxs-lookup"><span data-stu-id="52984-158">Run the query and display the results in the Data pane.</span></span>|
|<span data-ttu-id="52984-159">![Отмена запроса](../../analysis-services/media/rsqdicon-cancel.gif "Отмена запроса")</span><span class="sxs-lookup"><span data-stu-id="52984-159">![Cancel the query](../../analysis-services/media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="52984-160">Отмена запроса.</span><span class="sxs-lookup"><span data-stu-id="52984-160">Cancel the query.</span></span>|
|<span data-ttu-id="52984-161">![Перейти в режим конструктора](../../analysis-services/media/rsqdicon-designmode.gif "Перейти в режим конструктора")</span><span class="sxs-lookup"><span data-stu-id="52984-161">![Switch to Design mode](../../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="52984-162">Переключение между режимом конструктора и режимом запросов.</span><span class="sxs-lookup"><span data-stu-id="52984-162">Switch between Design mode and Query mode.</span></span>|

## <a name="graphical-query-designer-in-query-mode"></a><span data-ttu-id="52984-163">Графический конструктор запросов в режиме запросов</span><span class="sxs-lookup"><span data-stu-id="52984-163">Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="52984-164">Для переключения графического конструктора запросов в режим запросов щелкните переключатель **Режим конструктора** на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="52984-164">To change the graphical query designer to Query mode, click the **Design Mode** toggle button on the toolbar.</span></span>

 <span data-ttu-id="52984-165">На следующем рисунке показаны части конструктора запросов в режиме запросов.</span><span class="sxs-lookup"><span data-stu-id="52984-165">The following figure indicates the parts of the query designer in Query mode.</span></span>

 <span data-ttu-id="52984-166">![Конструктор запросов многомерных выражений SAP BW в режиме запроса](../media/rsqd-dssapbw-mdx-querymode.gif "Конструктор запросов многомерных выражений SAP BW в режиме запроса")</span><span class="sxs-lookup"><span data-stu-id="52984-166">![SAP BW MDX query designer in query view](../media/rsqd-dssapbw-mdx-querymode.gif "SAP BW MDX query designer in query view")</span></span>

 <span data-ttu-id="52984-167">В следующей таблице описываются функции каждой панели.</span><span class="sxs-lookup"><span data-stu-id="52984-167">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="52984-168">Панель</span><span class="sxs-lookup"><span data-stu-id="52984-168">Pane</span></span>|<span data-ttu-id="52984-169">Компонент</span><span class="sxs-lookup"><span data-stu-id="52984-169">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="52984-170">Кнопка «Выбрать куб»</span><span class="sxs-lookup"><span data-stu-id="52984-170">Select Cube button</span></span>|<span data-ttu-id="52984-171">Отображает текущий выбранный InfoCube, MultiProvider или другой куб.</span><span class="sxs-lookup"><span data-stu-id="52984-171">Displays the currently selected InfoCube, MultiProvider, or other cube.</span></span>|
|<span data-ttu-id="52984-172">Панель «Метаданные/Функции»</span><span class="sxs-lookup"><span data-stu-id="52984-172">Metadata/Functions pane</span></span>|<span data-ttu-id="52984-173">Отображает окно с вкладками, содержащее список доступных метаданных и функций, которые можно использовать при создании текста запроса.</span><span class="sxs-lookup"><span data-stu-id="52984-173">Displays a tabbed window that shows a list of available metadata or functions that can be used to build the query text.</span></span>|
|<span data-ttu-id="52984-174">Панель «Переменные»</span><span class="sxs-lookup"><span data-stu-id="52984-174">Variables pane</span></span>|<span data-ttu-id="52984-175">Отображает определенные в настоящее время переменные, которые можно использовать в запросе.</span><span class="sxs-lookup"><span data-stu-id="52984-175">Displays the currently defined variables available for use in the query.</span></span>|
|<span data-ttu-id="52984-176">Панель запросов</span><span class="sxs-lookup"><span data-stu-id="52984-176">Query pane</span></span>|<span data-ttu-id="52984-177">Отображает текст текущего запроса.</span><span class="sxs-lookup"><span data-stu-id="52984-177">Displays the current query text.</span></span>|
|<span data-ttu-id="52984-178">Панель результатов</span><span class="sxs-lookup"><span data-stu-id="52984-178">Result pane</span></span>|<span data-ttu-id="52984-179">Отображает результаты запроса.</span><span class="sxs-lookup"><span data-stu-id="52984-179">Displays the results of the query.</span></span>|

 <span data-ttu-id="52984-180">С панели «Метаданные» можно перетаскивать ключевые элементы и измерения с вкладки **Метаданные** на панель запроса многомерных выражений. Техническое имя метаданных вставляется в то место, где находится курсор.</span><span class="sxs-lookup"><span data-stu-id="52984-180">From the Metadata pane, you can drag key figures and dimensions from the **Metadata** tab onto the MDX Query pane; the technical name for the metadata is inserted at the cursor.</span></span> <span data-ttu-id="52984-181">Функции можно перетаскивать в панель «Запросы многомерных выражений» с вкладки **Функции** .</span><span class="sxs-lookup"><span data-stu-id="52984-181">You can drag functions from the **Functions** tab onto the MDX Query pane.</span></span> <span data-ttu-id="52984-182">При выполнении запроса в панели «Результат» отображаются результаты текущего запроса многомерных выражений.</span><span class="sxs-lookup"><span data-stu-id="52984-182">When you execute the query, the Result pane displays the results for the current MDX query.</span></span>

 <span data-ttu-id="52984-183">Если выбранный куб является запросом с поддержкой веб-доступа, будет предложено задать статические значения по умолчанию для существующих переменных.</span><span class="sxs-lookup"><span data-stu-id="52984-183">If your selected cube is a Web-enabled query, you will be prompted to set static default values for the existing variables.</span></span> <span data-ttu-id="52984-184">После этого можно будет перетащить переменные на панель запроса многомерных выражений.</span><span class="sxs-lookup"><span data-stu-id="52984-184">You can then drag variables onto the MDX Query pane.</span></span>

 <span data-ttu-id="52984-185">На панелях метаданных и переменных выводятся понятные имена.</span><span class="sxs-lookup"><span data-stu-id="52984-185">The Metadata and Variable panes display friendly names.</span></span> <span data-ttu-id="52984-186">При перетаскивании объектов на панель запроса многомерных выражений выводятся технические имена, необходимые источнику данных, введенному в запрос многомерных выражений.</span><span class="sxs-lookup"><span data-stu-id="52984-186">When you drop the objects onto the MDX Query pane, you see the technical names needed by the data source entered into the MDX query.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a><span data-ttu-id="52984-187">Панель инструментов графического конструктора запросов в режиме запросов</span><span class="sxs-lookup"><span data-stu-id="52984-187">Toolbar for the Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="52984-188">Панель инструментов конструктора запросов содержит кнопки, которые помогают создавать запросы многомерных выражений с помощью графического интерфейса.</span><span class="sxs-lookup"><span data-stu-id="52984-188">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="52984-189">Кнопки на панели инструментов в режиме конструктора ничем не отличаются от кнопок в режиме запроса, однако в режиме запроса недоступны следующие кнопки.</span><span class="sxs-lookup"><span data-stu-id="52984-189">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>

-   <span data-ttu-id="52984-190">**Редактировать как текст**</span><span class="sxs-lookup"><span data-stu-id="52984-190">**Edit As Text**</span></span>

-   <span data-ttu-id="52984-191">**Добавить вычисляемый элемент** (![Добавить вычисляемый элемент](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Добавить вычисляемый элемент"))</span><span class="sxs-lookup"><span data-stu-id="52984-191">**Add Calculated Member** (![Add calculated member](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>

-   <span data-ttu-id="52984-192">**Показывать пустые ячейки** (![Переключатель для просмотра пустых ячеек](../../analysis-services/media/rsqdicon-showemptycells.gif "Переключатель для просмотра пустых ячеек"))</span><span class="sxs-lookup"><span data-stu-id="52984-192">**Show Empty Cells** (![Toggle for show empty cells](../../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>

-   <span data-ttu-id="52984-193">**AutoExecute** (![Автоматическое выполнение запроса](../../analysis-services/media/rsqdicon-autoexecute.gif "Автоматическое выполнение запроса"))</span><span class="sxs-lookup"><span data-stu-id="52984-193">**AutoExecute** (![AutoExecute the query](../../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>

-   <span data-ttu-id="52984-194">**Удалить** (![Удаление](../../analysis-services/media/rsqdicon-delete.gif "DELETE"))</span><span class="sxs-lookup"><span data-stu-id="52984-194">**Delete** (![Delete](../../analysis-services/media/rsqdicon-delete.gif "Delete"))</span></span>

## <a name="see-also"></a><span data-ttu-id="52984-195">См. также:</span><span class="sxs-lookup"><span data-stu-id="52984-195">See Also</span></span>
 <span data-ttu-id="52984-196">[Создание общего набора данных или внедренного набора данных &#40;построитель отчетов и SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) [файл конфигурации RSReportDesigner](../report-server/rsreportdesigner-configuration-file.md)</span><span class="sxs-lookup"><span data-stu-id="52984-196">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) [RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md)</span></span>

