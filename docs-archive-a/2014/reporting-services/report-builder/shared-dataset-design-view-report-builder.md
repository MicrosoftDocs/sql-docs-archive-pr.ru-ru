---
title: Представление конструктора общих наборов данных (построитель отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47c502da-d163-45d9-bf04-0849e5ba7929
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a3c34b984ab3aca5bbd6313d088695f22ef2255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657028"
---
# <a name="shared-dataset-design-view-report-builder"></a><span data-ttu-id="278b9-102">Представление конструктора общих наборов данных (построитель отчетов)</span><span class="sxs-lookup"><span data-stu-id="278b9-102">Shared Dataset Design View (Report Builder)</span></span>
  <span data-ttu-id="278b9-103">В окне конструктора общих наборов данных создаются запросы к наборам данных, которые будут доступны другим пользователям.</span><span class="sxs-lookup"><span data-stu-id="278b9-103">The Shared Dataset Design window helps you create a dataset query that you can share with others.</span></span> <span data-ttu-id="278b9-104">Окно позволяет выбрать общий источник данных, указать свойства для общего набора данных и создать запрос в конструкторе запросов.</span><span class="sxs-lookup"><span data-stu-id="278b9-104">The window lets you select a shared data source, specify properties for the shared dataset, and create a query in the query designer.</span></span>  
  
 <span data-ttu-id="278b9-105">![rs_SharedDatasetDesignMode](../media/rs-shareddatasetdesignmode.gif "rs_SharedDatasetDesignMode")</span><span class="sxs-lookup"><span data-stu-id="278b9-105">![rs_SharedDatasetDesignMode](../media/rs-shareddatasetdesignmode.gif "rs_SharedDatasetDesignMode")</span></span>  
  
 <span data-ttu-id="278b9-106">Дополнительные сведения о работе с данными в отчете см. в разделе [Добавление данных в отчет &#40;построитель отчетов и SSRS&#41;](../report-data/report-datasets-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="278b9-106">For more information about working with data in a report, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md).</span></span>  
  
##  <a name="the-ribbon"></a><a name="Ribbon"></a><span data-ttu-id="278b9-107">Лента</span><span class="sxs-lookup"><span data-stu-id="278b9-107">The Ribbon</span></span>  
 <span data-ttu-id="278b9-108">Лента предназначена для быстрого доступа к командам, необходимым для выполнения задачи.</span><span class="sxs-lookup"><span data-stu-id="278b9-108">The Ribbon helps you quickly find the commands that you need to complete a task.</span></span> <span data-ttu-id="278b9-109">Команды организованы в следующие логические группы: подключение, набор данных и конструктор запросов.</span><span class="sxs-lookup"><span data-stu-id="278b9-109">Commands are organized into the following logical groups: Connection, Dataset, and Query Designer.</span></span>  
  
### <a name="connection"></a><span data-ttu-id="278b9-110">Соединение</span><span class="sxs-lookup"><span data-stu-id="278b9-110">Connection</span></span>  
 <span data-ttu-id="278b9-111">Используйте кнопку **Выбрать** в группе «Соединение» для выбора общего источника данных в отчете или нахождения общего источника данных на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="278b9-111">Use the **Select** button in the Connection group to select a shared data source in your report, or browse to a shared data source on the report server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="278b9-112">Общий набор данных должен быть основан на общем источнике данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-112">A shared dataset must be based on a shared data source.</span></span> <span data-ttu-id="278b9-113">Если необходимый источник данных недоступен, его необходимо создать на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="278b9-113">If the data source that you need is not available, you must create one on the report server.</span></span> <span data-ttu-id="278b9-114">Дополнительные сведения см. в разделе [Создание, удаление или изменение общего источника данных &#40;диспетчер отчетов&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) в документации Reporting Services [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [электронной документации](https://go.microsoft.com/fwlink/?linkid=121312)по.</span><span class="sxs-lookup"><span data-stu-id="278b9-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="278b9-115">Дополнительные сведения см. в разделе [Подключения к данным, источники данных и строки подключения](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="278b9-115">For more information, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
### <a name="dataset"></a><span data-ttu-id="278b9-116">Набор данных</span><span class="sxs-lookup"><span data-stu-id="278b9-116">Dataset</span></span>  
 <span data-ttu-id="278b9-117">Кнопка **Параметры набора** служит для изменения свойств общего набора данных,</span><span class="sxs-lookup"><span data-stu-id="278b9-117">Use the **Set Options** button to set shared dataset properties.</span></span> <span data-ttu-id="278b9-118">следующие основные параметры.</span><span class="sxs-lookup"><span data-stu-id="278b9-118">These include the following:</span></span>  
  
-   <span data-ttu-id="278b9-119">Поля.</span><span class="sxs-lookup"><span data-stu-id="278b9-119">Fields.</span></span> <span data-ttu-id="278b9-120">В коллекции полей можно добавлять или изменять поля.</span><span class="sxs-lookup"><span data-stu-id="278b9-120">You can add a field or edit a field in the field collection.</span></span>  
  
-   <span data-ttu-id="278b9-121">Параметры данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-121">Data options.</span></span> <span data-ttu-id="278b9-122">Можно задать параметры, влияющие на критерии сопоставления и порядок сортировки, например учет регистра и параметры сортировки.</span><span class="sxs-lookup"><span data-stu-id="278b9-122">You can set options that affect match criteria and sort order, such as case sensitivity and collation.</span></span>  
  
-   <span data-ttu-id="278b9-123">Фильтры.</span><span class="sxs-lookup"><span data-stu-id="278b9-123">Filters.</span></span> <span data-ttu-id="278b9-124">Можно определить фильтры, которые ограничат данные в отчете после их извлечения с помощью подключения к данным.</span><span class="sxs-lookup"><span data-stu-id="278b9-124">You can define filters that limit the data in a report after it is retrieved from the data connection.</span></span>  
  
-   <span data-ttu-id="278b9-125">Параметры.</span><span class="sxs-lookup"><span data-stu-id="278b9-125">Parameters.</span></span> <span data-ttu-id="278b9-126">Можно добавить параметр или изменить свойства параметра.</span><span class="sxs-lookup"><span data-stu-id="278b9-126">You can add a parameter or edit parameter options.</span></span> <span data-ttu-id="278b9-127">Например, можно задать значение по умолчанию для каждого параметра так, чтобы можно было создавать план обновления кэша для этого общего набора данных на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="278b9-127">For example, you can specify a default value for each parameter so that you can create a cache refresh plan for this shared dataset on the report server.</span></span>  
  
 <span data-ttu-id="278b9-128">Задаваемые значения становятся частью определения общего набора данных на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="278b9-128">The values that you set become part of the shared dataset definition on the report server.</span></span> <span data-ttu-id="278b9-129">Когда автора отчета включает общий набор данных в отчет, заданные параметры применяются к этому экземпляру набора данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-129">When a report author includes this shared dataset in a report, the options that you specify apply to that dataset instance.</span></span>  
  
 <span data-ttu-id="278b9-130">После добавления к отчету общего набора данных разработчик отчета может переопределить следующее: параметры сортировки, учет регистра, учет диакритических знаков, учет японской азбуки, учет ширины, подытоги.</span><span class="sxs-lookup"><span data-stu-id="278b9-130">After a shared dataset is added to a report, a report author can override the following options: collation, case sensitivity, accent sensitivity, kanatype sensitivity, width sensitivity, subtotals.</span></span> <span data-ttu-id="278b9-131">Авторы также могут создавать дополнительные фильтры наборов данных для ограничения данных в отчете.</span><span class="sxs-lookup"><span data-stu-id="278b9-131">They can also create additional dataset filters to limit the data in the report.</span></span>  
  
 <span data-ttu-id="278b9-132">Дополнительные сведения см. в разделе [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="278b9-132">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="278b9-133">Дополнительные сведения о планах обновления кэша см. в разделе [Общие наборы данных кэша &#40;SSRS&#41;](../report-server/cache-shared-datasets-ssrs.md) в документации по Reporting Services в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [электронной](https://go.microsoft.com/fwlink/?linkid=121312)документации по.</span><span class="sxs-lookup"><span data-stu-id="278b9-133">For more information about cache refresh plans, see [Cache Shared Datasets &#40;SSRS&#41;](../report-server/cache-shared-datasets-ssrs.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
### <a name="query-designer"></a><span data-ttu-id="278b9-134">Конструктор запросов</span><span class="sxs-lookup"><span data-stu-id="278b9-134">Query Designer</span></span>  
 <span data-ttu-id="278b9-135">С помощью панели инструментов конструктора запросов создаются запросы, указывающие, какие данные следует извлечь с помощью подключения к данным.</span><span class="sxs-lookup"><span data-stu-id="278b9-135">Use the query designer toolbar to help build a query that specifies which data to retrieve from the data connection.</span></span> <span data-ttu-id="278b9-136">Отображаемая панель инструментов зависит от конструктора запросов, который связан с типом источника данных из подключения к данным.</span><span class="sxs-lookup"><span data-stu-id="278b9-136">The toolbar that you see depends on the query designer that is associated with the data source type from the data connection.</span></span>  
  
 <span data-ttu-id="278b9-137">Дополнительные сведения см. в разделе, который соответствует типу источника данных в статье [Добавление данных из внешних источников данных &#40;служб SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) и [конструкторы запросов &#40;построитель отчетов&#41;](../query-designers-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="278b9-137">For more information, see the topic that corresponds to the data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) and [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md).</span></span>  
  

  
##  <a name="the-query-designer-surface"></a><a name="DesignSurface"></a><span data-ttu-id="278b9-138">Область конструктора запросов</span><span class="sxs-lookup"><span data-stu-id="278b9-138">The Query Designer Surface</span></span>  
 <span data-ttu-id="278b9-139">С помощью конструктора запросов создаются запросы с использованием синтаксиса, который является требованием внешнего источника данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-139">A query designer helps you to build a query in the syntax that is required by the external data source.</span></span>  
  
 <span data-ttu-id="278b9-140">Некоторые типы источников данных предоставляют графический конструктор запросов, который можно использовать для просмотра метаданных во внешнем источнике данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-140">Some data source types provide a graphical query designer that you can use to explore the metadata on an external data source.</span></span> <span data-ttu-id="278b9-141">Можно перетаскивать имена в интерактивном режиме из панели метаданных в область конструктора запросов или в интерактивном режиме выбирать необходимые имена.</span><span class="sxs-lookup"><span data-stu-id="278b9-141">You can interactively drag names from the metadata pane to the query design surface, or interactively select the names to use.</span></span>  
  
 <span data-ttu-id="278b9-142">Некоторые типы источников данных поддерживают текстовый конструктор запросов, который можно использовать для вставки запросов, созданных в других средствах, таких как среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="278b9-142">Some data source types support a text-based query designer that you can use to paste in queries that you have created in other tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="278b9-143">Каждый тип источника данных имеет особые требования к запросу, который будет выполняться относительно внешнего источника данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-143">Each data source type has specific requirements for the query that will work against the external data source.</span></span> <span data-ttu-id="278b9-144">Дополнительные сведения см. в разделе, который соответствует типу источника данных в статье [Добавление данных из внешних источников данных &#40;службы ssrs&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) и [Источники данных, ПОДДЕРЖИВАЕМЫЕ Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) в документации по Reporting Services в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [электронной](https://go.microsoft.com/fwlink/?linkid=121312)документации по.</span><span class="sxs-lookup"><span data-stu-id="278b9-144">For more information, see the topic that corresponds to the data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) and [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  

  
##  <a name="viewing-query-results"></a><a name="Results"></a><span data-ttu-id="278b9-145">Просмотр результатов запроса</span><span class="sxs-lookup"><span data-stu-id="278b9-145">Viewing Query Results</span></span>  
 <span data-ttu-id="278b9-146">В конструкторе общего набора данных пользователь создает запрос, который будет извлекать данные во время обработки отчета с помощью подключения к данным.</span><span class="sxs-lookup"><span data-stu-id="278b9-146">In shared dataset design view, you are building a query that will retrieve data from the data connection when the report is processed.</span></span>  
  
 <span data-ttu-id="278b9-147">Выполните запрос, чтобы с помощью подключения к данным открыть образец данных и убедиться, что запрос возвращает необходимый тип данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-147">Run the query to see example data from the data connection to verify that the query returns the type of data that you expect.</span></span> <span data-ttu-id="278b9-148">Столбцы в результирующем наборе берутся из метаданных для схем данных, с которыми установлено подключение.</span><span class="sxs-lookup"><span data-stu-id="278b9-148">The columns in the result set come from the metadata for data schemas from the data connection.</span></span> <span data-ttu-id="278b9-149">Имена столбцов образуют коллекцию полей набора данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-149">The column names become the dataset field collection.</span></span> <span data-ttu-id="278b9-150">Значения данных, отображаемые в результирующем наборе запроса, являются данными времени разработки.</span><span class="sxs-lookup"><span data-stu-id="278b9-150">The values of the data that you see in the query result set is design time data.</span></span> <span data-ttu-id="278b9-151">После сохранения общего набора данных в качестве определения общего набора данных на сервере отчетов сохраняется только текст запроса.</span><span class="sxs-lookup"><span data-stu-id="278b9-151">After you save the shared dataset as a shared dataset definition on the report server, only the query text is saved.</span></span> <span data-ttu-id="278b9-152">Данные в результирующем наборе запроса не сохраняются.</span><span class="sxs-lookup"><span data-stu-id="278b9-152">The data in the query result set is not saved.</span></span>  
  
 <span data-ttu-id="278b9-153">Когда автор отчета добавляет этот набор данных к отчету, добавляется указатель на определение набора данных на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="278b9-153">When a report author adds this shared dataset to a report, a pointer to the dataset definition on the report server is added.</span></span> <span data-ttu-id="278b9-154">В отчете коллекция полей набора данных появляется на панели данных отчета.</span><span class="sxs-lookup"><span data-stu-id="278b9-154">In the report, the dataset field collection appears in the Report Data pane.</span></span> <span data-ttu-id="278b9-155">Текст запроса недоступен.</span><span class="sxs-lookup"><span data-stu-id="278b9-155">The query text is not available.</span></span>  
  
 <span data-ttu-id="278b9-156">Учетные данные, используемые для выполнения запроса, отделены от учетных данных, используемых для просмотра отчета или выполнения отчета с сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="278b9-156">The credentials that you use to run a query are separate from the credentials that are used to preview a report or to run a report from the report server.</span></span> <span data-ttu-id="278b9-157">Дополнительные сведения см. в разделе [Указание учетных данных в построителе отчетов](../specify-credentials-in-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="278b9-157">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
### <a name="running-a-report-with-parameters"></a><span data-ttu-id="278b9-158">Запуск отчета с параметрами</span><span class="sxs-lookup"><span data-stu-id="278b9-158">Running a Report with Parameters</span></span>  
 <span data-ttu-id="278b9-159">Если запрос включает переменные запроса, параметры набора данных создаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="278b9-159">When your query includes query variables, dataset parameters are created automatically for you.</span></span> <span data-ttu-id="278b9-160">В свою очередь после завершения построения запроса к набору данных параметры отчета, заданные для параметров набора данных, создаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="278b9-160">In turn, when you finish building the dataset query, report parameters that are set to dataset parameters are created automatically.</span></span>  
  
 <span data-ttu-id="278b9-161">Если отчет содержит параметры, то все они должны иметь значения по умолчанию, чтобы была возможность запуска отчета автоматически.</span><span class="sxs-lookup"><span data-stu-id="278b9-161">If a report contains parameters, all the parameters must have default values before the report can run automatically.</span></span> <span data-ttu-id="278b9-162">Если параметр не имеет значения по умолчанию, то для него необходимо выбрать значение при запуске отчета, после чего нажать кнопку **Просмотреть отчет** на вкладке **Выполнение** .</span><span class="sxs-lookup"><span data-stu-id="278b9-162">If a parameter does not have a default value, when you run the report you must choose a value for the parameter, and then click **View Report** on the **Run** tab.</span></span>  
  
 <span data-ttu-id="278b9-163">Дополнительные сведения см. в разделе [Параметры отчета (построитель отчетов и конструктор отчетов)](../report-design/report-parameters-report-builder-and-report-designer.md).</span><span class="sxs-lookup"><span data-stu-id="278b9-163">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  

  
##  <a name="saving-the-shared-dataset"></a><a name="Save"></a> <span data-ttu-id="278b9-164">Сохранение общего набора данных</span><span class="sxs-lookup"><span data-stu-id="278b9-164">Saving the Shared Dataset</span></span>  
 <span data-ttu-id="278b9-165">Чтобы сохранить созданный запрос, на кнопке **Построитель отчетов** щелкните **Сохранить** или **Сохранить как**.</span><span class="sxs-lookup"><span data-stu-id="278b9-165">To save the query that you built, on the **Report Builder** button, click **Save** or **Save As**.</span></span> <span data-ttu-id="278b9-166">Перейдите в соответствующую папку на сервере отчетов и сохраните определение общего набора данных.</span><span class="sxs-lookup"><span data-stu-id="278b9-166">Navigate to the appropriate folder on the report server and save the shared dataset definition.</span></span> <span data-ttu-id="278b9-167">Общий набор данных будет доступен для других пользователей только после его сохранения на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="278b9-167">The shared dataset is not available to others until you save it to the report server.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="278b9-168">См. также:</span><span class="sxs-lookup"><span data-stu-id="278b9-168">See Also</span></span>  
 <span data-ttu-id="278b9-169">[Добавление данных в построитель отчетов &#40;отчетов и SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="278b9-169">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="278b9-170">[Фильтрация, группировка и сортировка данных &#40;построитель отчетов и SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="278b9-170">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="278b9-171">Параметры отчета (построитель отчетов и конструктор отчетов)</span><span class="sxs-lookup"><span data-stu-id="278b9-171">Report Parameters &#40;Report Builder and Report Designer&#41;</span></span>](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
  