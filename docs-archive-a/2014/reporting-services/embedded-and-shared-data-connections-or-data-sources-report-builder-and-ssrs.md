---
title: Внедренные и общие подключения к данным или источники данных (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- embedded data sources
- shared data sources
- data sources
ms.assetid: f417782c-b85a-4c4d-8a40-839176daba56
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a4b4020665e74377c048cb4be9c0cbddf97b2728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735065"
---
# <a name="embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs"></a><span data-ttu-id="0a183-102">Внедренные и общие подключения к данным или источники данных (построитель отчетов и службы SSRS)</span><span class="sxs-lookup"><span data-stu-id="0a183-102">Embedded and Shared Data Connections or Data Sources (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0a183-103">Отчеты используют подключения к данным для получения данных об отчете при выполнении запросов или при обработке отчета.</span><span class="sxs-lookup"><span data-stu-id="0a183-103">Reports use data connections to retrieve data for a report when a query runs or when the report is processed.</span></span> <span data-ttu-id="0a183-104">Подключение можно выбрать из списка встроенных типов подключений: к реляционной базе данных, к многомерной базе данных, веб-службе или некоторым другим источникам данных.</span><span class="sxs-lookup"><span data-stu-id="0a183-104">You choose from a list of built-in data connection types to connect to a relational database, a multidimensional database, a Web service, or some other source of data.</span></span> <span data-ttu-id="0a183-105">При описании подключений к данным используются следующие термины.</span><span class="sxs-lookup"><span data-stu-id="0a183-105">The following terms are used when describing data connections.</span></span>  
  
-   <span data-ttu-id="0a183-106">**Подключение к данным.**</span><span class="sxs-lookup"><span data-stu-id="0a183-106">**Data connection.**</span></span> <span data-ttu-id="0a183-107">Также называется *источником данных*.</span><span class="sxs-lookup"><span data-stu-id="0a183-107">Also known as a *data source*.</span></span> <span data-ttu-id="0a183-108">У подключения к данным есть имя и свойства подключения, зависящие от типа подключения.</span><span class="sxs-lookup"><span data-stu-id="0a183-108">A data connection includes a name and connection properties that are dependent on the connection type.</span></span> <span data-ttu-id="0a183-109">В соответствии с требованиями безопасности подключение к данным не содержит в себе учетных данных.</span><span class="sxs-lookup"><span data-stu-id="0a183-109">By design, a data connection does not include credentials.</span></span> <span data-ttu-id="0a183-110">Подключение к данным не определяет, какие данные будут извлекаться из внешнего источника данных.</span><span class="sxs-lookup"><span data-stu-id="0a183-110">A data connection does not specify which data to retrieve from the external data source.</span></span> <span data-ttu-id="0a183-111">Для этого при создании набора данных задается запрос.</span><span class="sxs-lookup"><span data-stu-id="0a183-111">To do that, you specify a query when you create a dataset.</span></span>  
  
-   <span data-ttu-id="0a183-112">**Определение источника данных.**</span><span class="sxs-lookup"><span data-stu-id="0a183-112">**Data source definition.**</span></span> <span data-ttu-id="0a183-113">Файл, содержащий XML-представление источника данных отчетов.</span><span class="sxs-lookup"><span data-stu-id="0a183-113">A file that contains the XML representation of a report data source.</span></span> <span data-ttu-id="0a183-114">При публикации отчета его источники данных сохраняются на сервере отчетов или сайте SharePoint в виде определений источников данных независимо от определения отчета.</span><span class="sxs-lookup"><span data-stu-id="0a183-114">When a report is published, its data sources are saved on the report server or SharePoint site as data source definitions, independently from the report definition.</span></span> <span data-ttu-id="0a183-115">Например, администратор сервера отчетов может обновить строку подключения или учетные данные.</span><span class="sxs-lookup"><span data-stu-id="0a183-115">For example, a report server administrator might update the connection string or credentials.</span></span> <span data-ttu-id="0a183-116">Собственный формат сервера отчетов для этого файла — RDS.</span><span class="sxs-lookup"><span data-stu-id="0a183-116">On a native report server, the file type is .rds.</span></span> <span data-ttu-id="0a183-117">На сайте SharePoint этот файл сохраняется в формате RSDS.</span><span class="sxs-lookup"><span data-stu-id="0a183-117">On a SharePoint site, the file type is .rsds.</span></span>  
  
-   <span data-ttu-id="0a183-118">**Строка подключения.**</span><span class="sxs-lookup"><span data-stu-id="0a183-118">**Connection string.**</span></span> <span data-ttu-id="0a183-119">Строка подключения — это строковая версия свойств подключения, необходимых для подключения к источнику данных.</span><span class="sxs-lookup"><span data-stu-id="0a183-119">A connection string is a string version of the connection properties that are needed to connect to a data source.</span></span> <span data-ttu-id="0a183-120">Свойства подключения различаются в зависимости от типа подключения к данным.</span><span class="sxs-lookup"><span data-stu-id="0a183-120">Connection properties differ based on data connection type.</span></span> <span data-ttu-id="0a183-121">Примеры см. в разделе [Подключения к данным, источники данных и строки подключения](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="0a183-121">For examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
-   <span data-ttu-id="0a183-122">**Общий источник данных.**</span><span class="sxs-lookup"><span data-stu-id="0a183-122">**Shared data source.**</span></span> <span data-ttu-id="0a183-123">Источник данных, доступный на сервере отчетов или на сайте SharePoint, который может использоваться в нескольких отчетах.</span><span class="sxs-lookup"><span data-stu-id="0a183-123">A data source that is available on a report server or SharePoint site to be used by multiple reports.</span></span>  
  
-   <span data-ttu-id="0a183-124">**Внедренный источник данных.**</span><span class="sxs-lookup"><span data-stu-id="0a183-124">**Embedded data source.**</span></span> <span data-ttu-id="0a183-125">Также называется *источником данных, связанных с отчетом*.</span><span class="sxs-lookup"><span data-stu-id="0a183-125">Also known as a *report-specific data source*.</span></span> <span data-ttu-id="0a183-126">Источник данных, определенный в отчете и используемый только этим отчетом.</span><span class="sxs-lookup"><span data-stu-id="0a183-126">A data source that is defined in a report and used only by that report.</span></span>  
  
-   <span data-ttu-id="0a183-127">**Информации.**</span><span class="sxs-lookup"><span data-stu-id="0a183-127">**Credentials.**</span></span> <span data-ttu-id="0a183-128">.   Учетные данные — это сведения для проверки подлинности, которые необходимы для получения доступа к внешним данным.</span><span class="sxs-lookup"><span data-stu-id="0a183-128">Credentials are the authentication information that must be provided to allow you access to external data.</span></span>  
  
 <span data-ttu-id="0a183-129">Различие между общими и внедренными источниками данных состоит в способе создания, хранения и управления.</span><span class="sxs-lookup"><span data-stu-id="0a183-129">The difference between the embedded and shared data sources is in how they are created, stored, and managed.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
## <a name="shared-data-sources"></a><span data-ttu-id="0a183-130">Общие источники данных</span><span class="sxs-lookup"><span data-stu-id="0a183-130">Shared Data Sources</span></span>  
 <span data-ttu-id="0a183-131">Применение общего источника данных рекомендовано в тех случаях, когда источник данных используется часто.</span><span class="sxs-lookup"><span data-stu-id="0a183-131">Shared data sources are useful when you have data sources that you use often.</span></span> <span data-ttu-id="0a183-132">Рекомендуется использовать общие источники данных (если возможно).</span><span class="sxs-lookup"><span data-stu-id="0a183-132">It is recommended that you use shared data sources as much as possible.</span></span> <span data-ttu-id="0a183-133">Они облегчают управление отчетами и доступом к ним, а также помогают обеспечить безопасность отчетов и источников данных.</span><span class="sxs-lookup"><span data-stu-id="0a183-133">They make reports and report access easier to manage, and help to keep reports and the data sources they access more secure.</span></span> <span data-ttu-id="0a183-134">Необходимый общий источник данных должен создать системный администратор.</span><span class="sxs-lookup"><span data-stu-id="0a183-134">If you need a shared data source, ask your system administrator to create one for you.</span></span>  
  
 <span data-ttu-id="0a183-135">В построителе отчетов невозможно создать общий источник данных.</span><span class="sxs-lookup"><span data-stu-id="0a183-135">In Report Builder, you cannot create a shared data source.</span></span> <span data-ttu-id="0a183-136">Перейдите на сервер отчетов и выберите расположенный на нем общий источник данных.</span><span class="sxs-lookup"><span data-stu-id="0a183-136">You can browse to and select a shared data source from the report server.</span></span> <span data-ttu-id="0a183-137">Дополнительные сведения см. в разделе [Подключения к данным, источники данных и строки подключения](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="0a183-137">For more information, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="0a183-138">В конструкторе отчетов нельзя перейти к общему источнику данных на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="0a183-138">In Report Designer, you cannot browse to a shared data source on the report server.</span></span> <span data-ttu-id="0a183-139">Можно создать общий источник данных как часть проекта в обозревателе решений и решить, будет ли он развернут на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="0a183-139">You can create shared data sources as part of a project in Solution Explorer and choose whether to deploy them to a report server.</span></span> <span data-ttu-id="0a183-140">Этот источник данных можно также использовать локально, поскольку имеются различия в учетных данных, необходимых для обращения к локальному компьютеру и к серверу отчетов.</span><span class="sxs-lookup"><span data-stu-id="0a183-140">You might choose to use them locally only because of differences in credentials required from your computer or from the report server.</span></span> <span data-ttu-id="0a183-141">Дополнительные сведения см. в разделе [Подключения данных, источники данных и строки подключения в службе Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span><span class="sxs-lookup"><span data-stu-id="0a183-141">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="0a183-142">Следующий значок обозначает элемент общего источника данных в иерархии папок сервера отчетов: ![значок общего источника данных](media/hlp-16datasource.png "Значок общего источника данных")</span><span class="sxs-lookup"><span data-stu-id="0a183-142">The following icon indicates a shared data source item in the report server folder hierarchy: ![Shared data source icon](media/hlp-16datasource.png "Shared data source icon")</span></span>  
  
## <a name="embedded-data-sources"></a><span data-ttu-id="0a183-143">Внедренные источники данных</span><span class="sxs-lookup"><span data-stu-id="0a183-143">Embedded Data Sources</span></span>  
 <span data-ttu-id="0a183-144">Внедренный источник данных представляет собой подключение к данным, которое сохраняется в определении отчета.</span><span class="sxs-lookup"><span data-stu-id="0a183-144">An embedded data source is a data connection that is saved in the report definition.</span></span> <span data-ttu-id="0a183-145">Эти сведения могут использоваться только тем отчетом, в который они внедрены.</span><span class="sxs-lookup"><span data-stu-id="0a183-145">Embedded data source connection information can be used only by the report in which it is embedded.</span></span> <span data-ttu-id="0a183-146">Внедренные источники данных определяются и управляются с помощью диалогового окна **Свойства источника данных** .</span><span class="sxs-lookup"><span data-stu-id="0a183-146">To define and manage embedded data sources, use the **Data Source Properties** dialog box.</span></span>  
  
##  <a name="comparing-embedded-and-shared-data-sources"></a><a name="Comparing"></a><span data-ttu-id="0a183-147">Сравнение внедренных и общих источников данных</span><span class="sxs-lookup"><span data-stu-id="0a183-147">Comparing Embedded and Shared Data Sources</span></span>  
 <span data-ttu-id="0a183-148">В следующей таблице приведены все различия между внедренными и общими источниками данных.</span><span class="sxs-lookup"><span data-stu-id="0a183-148">The following table summarizes the differences between embedded and shared data sources:</span></span>  
  
|<span data-ttu-id="0a183-149">Описание</span><span class="sxs-lookup"><span data-stu-id="0a183-149">Description</span></span>|<span data-ttu-id="0a183-150">Внедренный</span><span class="sxs-lookup"><span data-stu-id="0a183-150">Embedded</span></span><br /><br /> <span data-ttu-id="0a183-151">Источник данных</span><span class="sxs-lookup"><span data-stu-id="0a183-151">Data Source</span></span>|<span data-ttu-id="0a183-152">Совмещаемая блокировка</span><span class="sxs-lookup"><span data-stu-id="0a183-152">Shared</span></span><br /><br /> <span data-ttu-id="0a183-153">Источник данных</span><span class="sxs-lookup"><span data-stu-id="0a183-153">Data Source</span></span>|  
|-----------------|------------------------------|----------------------------|  
|<span data-ttu-id="0a183-154">Подключение к данным внедрено в определение отчета.</span><span class="sxs-lookup"><span data-stu-id="0a183-154">Data connection is embedded in the report definition.</span></span>|<span data-ttu-id="0a183-155">![Доступно](media/greencheck.gif "Доступно")</span><span class="sxs-lookup"><span data-stu-id="0a183-155">![Available](media/greencheck.gif "Available")</span></span>||  
|<span data-ttu-id="0a183-156">Указатель на подключение к данным на сервере ответов внедрен в определение отчета.</span><span class="sxs-lookup"><span data-stu-id="0a183-156">Pointer to the data connection on the report server is embedded in the report definition.</span></span>||<span data-ttu-id="0a183-157">![Доступно](media/greencheck.gif "Доступно")</span><span class="sxs-lookup"><span data-stu-id="0a183-157">![Available](media/greencheck.gif "Available")</span></span>|  
|<span data-ttu-id="0a183-158">Управляется на сервере отчетов</span><span class="sxs-lookup"><span data-stu-id="0a183-158">Managed on the report server</span></span>|<span data-ttu-id="0a183-159">![Доступно](media/greencheck.gif "Доступно")</span><span class="sxs-lookup"><span data-stu-id="0a183-159">![Available](media/greencheck.gif "Available")</span></span>|<span data-ttu-id="0a183-160">![Доступно](media/greencheck.gif "Доступно")</span><span class="sxs-lookup"><span data-stu-id="0a183-160">![Available](media/greencheck.gif "Available")</span></span>|  
|<span data-ttu-id="0a183-161">Необходим для общих наборов данных</span><span class="sxs-lookup"><span data-stu-id="0a183-161">Required for shared datasets</span></span>||<span data-ttu-id="0a183-162">![Доступно](media/greencheck.gif "Доступно")</span><span class="sxs-lookup"><span data-stu-id="0a183-162">![Available](media/greencheck.gif "Available")</span></span>|  
|<span data-ttu-id="0a183-163">Необходим для компонентов</span><span class="sxs-lookup"><span data-stu-id="0a183-163">Required for components</span></span>||<span data-ttu-id="0a183-164">![Доступно](media/greencheck.gif "Доступно")</span><span class="sxs-lookup"><span data-stu-id="0a183-164">![Available](media/greencheck.gif "Available")</span></span>|  
  
## <a name="data-source-credentials"></a><span data-ttu-id="0a183-165">Учетные данные источника данных</span><span class="sxs-lookup"><span data-stu-id="0a183-165">Data Source Credentials</span></span>  
 <span data-ttu-id="0a183-166">Учетные данные используются для создания внедренного источника данных, для запуска запроса, а также для извлечения данных в процессе обработки отчета.</span><span class="sxs-lookup"><span data-stu-id="0a183-166">Credentials are used to create an embedded data source, to run a query, or to retrieve data during report processing.</span></span> <span data-ttu-id="0a183-167">Владелец источника данных определяет тип учетных данных, которые необходимо использовать для получения доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="0a183-167">The owner of the data source determines the type of credentials that you must use to access the data.</span></span> <span data-ttu-id="0a183-168">Учетные данные управляются независимо от подключения к данным на сервере отчетов, на сайте SharePoint или на локальном компьютере в среде создания отчетов.</span><span class="sxs-lookup"><span data-stu-id="0a183-168">Credentials are managed independently from the data connection on a report server, a SharePoint site, or on a local computer in a report authoring environment.</span></span> <span data-ttu-id="0a183-169">В зависимости от типа источника данных учетные данные могут быть сохранены или настроены таким образом, чтобы их должен был вводить самостоятельно каждый пользователь.</span><span class="sxs-lookup"><span data-stu-id="0a183-169">Depending on the type of data source, credentials can be saved to avoid prompting or set to prompt each user.</span></span> <span data-ttu-id="0a183-170">Необходимые учетные данные могут отличаться в зависимости от того, производится ли подключение к источнику данных с локального компьютера или с сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="0a183-170">The credentials that you need might differ depending on whether you are connecting to the data source from your computer or from the report server.</span></span> <span data-ttu-id="0a183-171">Дополнительные сведения см. [в разделе Указание учетных данных в построитель отчетов](../../2014/reporting-services/specify-credentials-in-report-builder.md) и [подключения к данным, источники данных и строки подключения в Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span><span class="sxs-lookup"><span data-stu-id="0a183-171">For more information, see [Specify Credentials in Report Builder](../../2014/reporting-services/specify-credentials-in-report-builder.md) and [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a183-172">См. также:</span><span class="sxs-lookup"><span data-stu-id="0a183-172">See Also</span></span>  
 <span data-ttu-id="0a183-173">[Добавление данных в построитель отчетов &#40;отчетов и SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a183-173">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="0a183-174">[Основные понятия разработки отчетов &#40;построитель отчетов и службы SSRS&#41;](report-design/report-authoring-concepts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a183-174">[Report Authoring Concepts &#40;Report Builder and SSRS&#41;](report-design/report-authoring-concepts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0a183-175">[Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="0a183-175">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="0a183-176">[Добавление и проверка подключения к данным или источника данных &#40;построитель отчетов и служб SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a183-176">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0a183-177">Внедренные и общие наборы данных (построитель отчетов и службы SSRS)</span><span class="sxs-lookup"><span data-stu-id="0a183-177">Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)  
  
  