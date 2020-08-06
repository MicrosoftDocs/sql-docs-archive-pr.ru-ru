---
title: Изменения в работе функций Analysis Services в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4fa6e5f28202c80ed8b80e16a67b0e77cf4d10fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656870"
---
# <a name="behavior-changes-to-analysis-services-features-in-sql-server-2014"></a><span data-ttu-id="ac2ba-102">Изменение работы функций служб Analysis Services в SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="ac2ba-102">Behavior Changes to Analysis Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="ac2ba-103">В этом разделе описаны изменения работы функций [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для табличной модели, многомерной модели, модели анализа данных и развертываний [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ac2ba-103">This topic describes behavior changes in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] for multidimensional, tabular, data mining, and [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] deployments.</span></span> <span data-ttu-id="ac2ba-104">Изменения в работе касаются того, как функциональные возможности работают или взаимодействуют в текущей версии в сравнении с предыдущими версиями SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-104">Behavior changes affect how features work or interact in the current version as compared to earlier versions of SQL Server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2ba-105">Напротив, критическое изменение — это изменение, которое препятствует работе модели данных или приложения, интегрированного с [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ac2ba-105">In contrast, a breaking change is one that prevents a data model or application integrated with [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] from running.</span></span> <span data-ttu-id="ac2ba-106">Дополнительные сведения см. в разделе [Breaking Changes to Analysis Services Features in SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-106">To learn more, see [Breaking Changes to Analysis Services Features in SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="ac2ba-107">В этом разделе.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-107">In this Topic:</span></span>  
  
-   [<span data-ttu-id="ac2ba-108">Изменения в работе SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="ac2ba-108">Behavior Changes in SQL Server 2014</span></span>](#bkmk_sql2014)  
  
-   [<span data-ttu-id="ac2ba-109">Изменения в поведении SQL Server 2012 SP1</span><span class="sxs-lookup"><span data-stu-id="ac2ba-109">Behavior Changes in SQL Server 2012 SP1</span></span>](#bkmk_sql2012sp1)  
  
-   [<span data-ttu-id="ac2ba-110">Изменения в поведении SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="ac2ba-110">Behavior Changes in SQL Server 2012</span></span>](#bkmk_sql2012)  
  
##  <a name="behavior-changes-in-sssql14"></a><a name="bkmk_sql2014"></a><span data-ttu-id="ac2ba-111">Изменения в работе[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac2ba-111">Behavior Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="ac2ba-112">В этом выпуске не произошло никаких новых изменений работы функций в рамках табличной модели, многомерной модели, модели анализа данных и функциональных возможностей [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] , о которых было объявлено.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-112">There are no new behavior changes announced for tabular, multidimensional, data mining, or [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] features in this release.</span></span>  <span data-ttu-id="ac2ba-113">Тем не менее, так как версия  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] аналогична версиям [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] и [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] , то для вашего удобства здесь приведены изменения работы функций для обоих предыдущих выпусков на тот случай, если вы осуществили обновление [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac2ba-113">However, because  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] is so similar to the [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] and [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] versions, behavior changes from both prior releases are provided here as a convenience in case you're upgrading from [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
##  <a name="behavior-changes-in-sssql11sp1"></a><a name="bkmk_sql2012sp1"></a><span data-ttu-id="ac2ba-114">Изменения в работе[!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac2ba-114">Behavior Changes in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]</span></span>  
 <span data-ttu-id="ac2ba-115">В этом разделе документированы изменения работы функций [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac2ba-115">This section documents the behavior changes reported for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].</span></span> <span data-ttu-id="ac2ba-116">Эти изменения также применяются к [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac2ba-116">These changes also apply to [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
|<span data-ttu-id="ac2ba-117">Проблема</span><span class="sxs-lookup"><span data-stu-id="ac2ba-117">Issue</span></span>|<span data-ttu-id="ac2ba-118">Описание</span><span class="sxs-lookup"><span data-stu-id="ac2ba-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac2ba-119">Книги SQL Server 2008 R2 PowerPivot не обновляются автоматически и не обновляют модели, если используются в SQL Server 2012 PowerPivot с пакетом обновления 1 (SP1) для SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-119">SQL Server 2008 R2 PowerPivot workbooks will not silently upgrade and refresh the models when they are used in SQL Server 2012 SP1 PowerPivot for SharePoint 2013.</span></span> <span data-ttu-id="ac2ba-120">Поэтому плановые обновления данных не будут действовать для книг SQL Server 2008 R2 PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-120">Therefore Scheduled data refreshes will not work for SQL Server 2008 R2 PowerPivot workbooks.</span></span>|<span data-ttu-id="ac2ba-121">Книги 2008 R2 открываются в [!INCLUDE[ssGeminiShortvnext](../includes/ssgeminishortvnext-md.md)], однако плановые обновления не выполняются.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-121">The 2008 R2 workbooks will open in [!INCLUDE[ssGeminiShortvnext](../includes/ssgeminishortvnext-md.md)], however scheduled refreshes will not work.</span></span> <span data-ttu-id="ac2ba-122">При просмотре журнала обновления обнаруживается сообщение об ошибке следующего вида:</span><span class="sxs-lookup"><span data-stu-id="ac2ba-122">If you review the refresh history you will see an error message similar to the following:</span></span><br /> <span data-ttu-id="ac2ba-123">"Книга содержит неподдерживаемую модель PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-123">"The workbook contains an unsupported PowerPivot model.</span></span> <span data-ttu-id="ac2ba-124">Модель PowerPivot в книге представлена в формате SQL Server 2008 R2 PowerPivot для Excel 2010.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-124">The PowerPivot model in the workbook is in the SQL Server 2008 R2 PowerPivot for Excel 2010 format.</span></span> <span data-ttu-id="ac2ba-125">Поддерживаются следующие модели PowerPivot:</span><span class="sxs-lookup"><span data-stu-id="ac2ba-125">Supported PowerPivot models are the following:</span></span> <br /><span data-ttu-id="ac2ba-126">SQL Server 2012 PowerPivot для Excel 2010,</span><span class="sxs-lookup"><span data-stu-id="ac2ba-126">SQL Server 2012 PowerPivot for Excel 2010</span></span><br /><span data-ttu-id="ac2ba-127">SQL Server 2012 PowerPivot для Excel 2013 "</span><span class="sxs-lookup"><span data-stu-id="ac2ba-127">SQL Server 2012 PowerPivot for Excel 2013"</span></span><br /><br /> <span data-ttu-id="ac2ba-128">**Обновление книги:** плановые обновления не будут действовать, пока книга не будет обновлена до книги версии 2012.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-128">**How to upgrade a workbook:** The scheduled refreshes will not work until you upgrade the workbook to a 2012 workbook.</span></span> <span data-ttu-id="ac2ba-129">Для обновления книги и содержащейся в ней модели выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-129">To upgrade the workbook and model it contains, complete one of the following:</span></span><br /><br /> <span data-ttu-id="ac2ba-130">Загрузите и откройте книгу в Microsoft Excel 2010 с помощью установленной надстройки SQL Server 2012 PowerPivot для Excel.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-130">Download and open the workbook in Microsoft Excel 2010 with the SQL Server 2012 PowerPivot for Excel add-in installed.</span></span> <span data-ttu-id="ac2ba-131">Затем сохраните книгу и повторно опубликуйте ее на сервере SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-131">Then save the workbook and republish it to the SharePoint server.</span></span><br /><br /> <span data-ttu-id="ac2ba-132">Загрузите и откройте книгу в Microsoft Excel 2013.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-132">Download and open the workbook in Microsoft Excel 2013.</span></span> <span data-ttu-id="ac2ba-133">Затем сохраните книгу и повторно опубликуйте ее на сервере SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-133">Then save the workbook and republish it to the SharePoint server.</span></span><br /><br /> <br /><br /> <span data-ttu-id="ac2ba-134">Дополнительные сведения об обновлении книги см. в разделе [обновление книг и запланированное обновление данных &#40;SharePoint 2013&#41;](instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-134">For more information on workbook upgrade, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).</span></span>|  
|<span data-ttu-id="ac2ba-135">Изменения в организации работы DAX [ALL Function](/dax/all-function-dax).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-135">Behavior change in DAX [ALL Function](/dax/all-function-dax).</span></span>|<span data-ttu-id="ac2ba-136">До выхода версии [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)], если был задан столбец [Date] в окне «Пометить как таблицу дат» для использования в логике операций со временем и этот столбец [Date] передан в качестве аргумента в функцию ALL для использования в свою очередь в качестве фильтра в функции CALCULATE, пропускаются все фильтры для всех столбцов в таблице независимо от того, имеется ли какой-либо срез в столбце дат.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-136">Prior to [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)], if you specify a [Date] column in Mark as Date Table, for use in time-intelligence, and that [Date] column is passed as an argument to the ALL function, in-turn, passed as a filter to a CALCULATE function, all filters for all columns in the table are ignored, regardless of any slicer on the date column.</span></span><br /><br /> <span data-ttu-id="ac2ba-137">например следующие.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-137">For example,</span></span><br /><br /> `= CALCULATE (<expression>, ALL (DateTable[Date]))`<br /><br /> <span data-ttu-id="ac2ba-138">До выхода версии [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]все фильтры пропускались для всех столбцов DateTable независимо от того, передавался ли столбец [Date] в качестве аргумента в функцию ALL.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-138">Prior to [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)], all filters are ignored for all columns of DateTable, regardless of the [Date] column passed as an argument to ALL.</span></span><br /><br /> <span data-ttu-id="ac2ba-139">Поведение версии [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] и в PowerPivot в Excel 2013 заключается в том, что фильтры пропускаются только для указанного столбца, передаваемого в качестве аргумента функции ALL.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-139">In [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] and in PowerPivot in Excel 2013, the behavior will ignore filters only for the specified column passed as an argument to ALL.</span></span><br /><br /> <span data-ttu-id="ac2ba-140">Чтобы отказаться от нового поведения, по существу игнорируя применение всех столбцов в качестве фильтров для всей таблицы, можно исключить столбец [Date] из аргумента, например</span><span class="sxs-lookup"><span data-stu-id="ac2ba-140">To work around the new behavior, in effect ignore all columns as a filter for the entire table, you can exclude [Date] column from the argument, for example,</span></span><br /><br /> `=CALCULATE (<expression>, ALL(DateTable))`<br /><br /> <span data-ttu-id="ac2ba-141">Результат будет такой же, как при организации работы до выхода версии [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac2ba-141">This will yield the same result as the behavior prior to [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].</span></span>|  
  
##  <a name="behavior-changes-in-sssql11"></a><a name="bkmk_sql2012"></a><span data-ttu-id="ac2ba-142">Изменения в работе[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac2ba-142">Behavior Changes in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
 <span data-ttu-id="ac2ba-143">В этом разделе документированы изменения поведения в компонентах служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac2ba-143">This section documents the behavioral changes reported for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="ac2ba-144">Эти изменения также применяются к [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac2ba-144">These changes also apply to [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
### <a name="analysis-services-multidimensional-mode"></a><span data-ttu-id="ac2ba-145">Службы Analysis Services, многомерный режим</span><span class="sxs-lookup"><span data-stu-id="ac2ba-145">Analysis Services, Multidimensional Mode</span></span>  
  
#### <a name="nullprocessing-option-set-to-preserve-is-no-longer-supported-for-distinct-count-measures"></a><span data-ttu-id="ac2ba-146">Параметр NullProcessing со значением «Сохранять» больше не поддерживается для мер числа различных объектов.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-146">NullProcessing option set to Preserve is no longer supported for distinct count measures</span></span>  
 <span data-ttu-id="ac2ba-147">До [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , можно было установить [элемент NULLPROCESSING &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl) в `Preserve` для мер числа различных объектов.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-147">Prior to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], it was possible to set [NullProcessing Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl) to `Preserve` for distinct count measures.</span></span>  <span data-ttu-id="ac2ba-148">К сожалению, такой подход часто приводил к недопустимым результатам, а иногда — к сбою задания обработки.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-148">Unfortunately, this practice often produced invalid results and sometimes even crashed the processing job.</span></span> <span data-ttu-id="ac2ba-149">Поэтому данная конфигурация более недоступна в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac2ba-149">As a result, this configuration is no longer valid in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="ac2ba-150">При попытке использовать эту конфигурацию возникнет следующая ошибка проверки: «Ошибки в диспетчере метаданных.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-150">Attempting to use it will cause the following validation error to occur: "Errors in the metadata manager.</span></span> <span data-ttu-id="ac2ba-151">Параметр Preserve не является допустимым значением NullProcessing для \<measurename> меры числа различных объектов ".</span><span class="sxs-lookup"><span data-stu-id="ac2ba-151">Preserve is not a valid NullProcessing value for the \<measurename> distinct count measure."</span></span>  
  
#### <a name="cube-browser-in-management-studio-and-cube-designer-has-been-removed"></a><span data-ttu-id="ac2ba-152">Браузер кубов в среде Management Studio и конструктор кубов были удалены</span><span class="sxs-lookup"><span data-stu-id="ac2ba-152">Cube browser in Management Studio and Cube Designer has been removed</span></span>  
 <span data-ttu-id="ac2ba-153">Элемент управления браузера кубов, который позволяет перетаскивать поля в структуру сводной таблицы в среде Management Studio или в конструкторе кубов, был удален из продукта.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-153">The cube browser control that let you drag and drop fields onto a PivotTable structure in Management Studio or in Cube Designer has been removed from the product.</span></span> <span data-ttu-id="ac2ba-154">Элемент управления был веб-компонентом Office Web Control (OWC).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-154">The control was an Office Web Control (OWC) component.</span></span> <span data-ttu-id="ac2ba-155">Веб-компоненты Office работали с устаревшей версией Office, поэтому больше не доступны.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-155">OWC was deprecated by Office and is no longer available.</span></span>  
  
### <a name="powerpivot-for-sharepoint"></a><span data-ttu-id="ac2ba-156">PowerPivot для SharePoint</span><span class="sxs-lookup"><span data-stu-id="ac2ba-156">PowerPivot for SharePoint</span></span>  
  
#### <a name="higher-permission-requirements-for-using-a-powerpivot-workbook-as-an-external-data-source"></a><span data-ttu-id="ac2ba-157">Требование разрешений более высокого уровня для использования книги PowerPivot в качестве внешнего источника данных</span><span class="sxs-lookup"><span data-stu-id="ac2ba-157">Higher permission requirements for using a PowerPivot workbook as an external data source</span></span>  
 <span data-ttu-id="ac2ba-158">Книга Excel может отображать данные PowerPivot, внедренные в ту же или во внешнюю книгу.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-158">An Excel workbook can render PowerPivot data that is embedded within the same workbook or in an external workbook.</span></span> <span data-ttu-id="ac2ba-159">В предыдущем выпуске требования к разрешениям были одинаковыми независимо от того, были ли данные PowerPivot внедренными или внешними.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-159">In the previous release, permission requirements were the same regardless of whether the PowerPivot data was embedded or external.</span></span> <span data-ttu-id="ac2ba-160">Разрешение **Только просмотр** в книге PowerPivot давало полный доступ ко всем данным PowerPivot в книге как для внедренных, так и для внешних соединений.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-160">If you had **View Only** permissions on a PowerPivot workbook, you could get full access to all of the PowerPivot data in the workbook for both embedded and external connections.</span></span>  
  
 <span data-ttu-id="ac2ba-161">В этом выпуске требования к разрешениям были изменены для книг Excel, в которых отображаются данные PowerPivot из внешнего файла.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-161">In this release, permission requirements have changed for Excel workbooks that render PowerPivot data from an external file.</span></span> <span data-ttu-id="ac2ba-162">В этом выпуске для подключения к внешней книге PowerPivot из клиентского приложения необходимо иметь разрешения на **Чтение** (а точнее, разрешение **Открытие элементов** ).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-162">In this release, you must have **Read** permissions (or more specifically, the **Open Items** permission) to connect to an external PowerPivot workbook from a client application.</span></span> <span data-ttu-id="ac2ba-163">Дополнительные разрешения определяют, что пользователь имеет права на загрузку для просмотра исходных данных, внедренных в книгу.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-163">The additional permissions specify that a user has download rights to view the source data embedded in the workbook.</span></span> <span data-ttu-id="ac2ba-164">Дополнительные разрешения отражают тот факт, что данные о модели полностью доступны клиентскому приложению или книге, которые содержат ссылки на них, что в результате лучше выравнивает требования к разрешениям и фактическую работу подключения к данным.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-164">The additional permissions reflect the fact that model data is wholly available to the client application or workbook that links to it, resulting in a better alignment between permission requirements and the actual data connection behavior.</span></span>  
  
 <span data-ttu-id="ac2ba-165">Чтобы продолжить использование книги PowerPivot в качестве внешнего источника данных, необходимо повысить уровень разрешений SharePoint для пользователей, которые подключаются к внешним данным PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-165">To continue using a PowerPivot workbook as an external data source, you must increase SharePoint permissions for users who connect to external PowerPivot data.</span></span> <span data-ttu-id="ac2ba-166">Пока вы не измените разрешения, пользователи получат следующую ошибку при попытке доступа к книгам PowerPivot в соединении с источником данных: "веб-служба PowerPivot возвратила ошибку (доступ запрещен.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-166">Until you change the permissions, users will get the following error if they try to access PowerPivot workbooks in a data source connection: "PowerPivot Web service returned an error (Access denied.</span></span> <span data-ttu-id="ac2ba-167">Запрошенный документ не существует, или у вас нет разрешения на открытие файла.) "</span><span class="sxs-lookup"><span data-stu-id="ac2ba-167">The document you requested does not exist or you do not have permission to open the file.)"</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ac2ba-168">Далее описаны действия по прерыванию цепочки наследования разрешений на уровне библиотеки и повышению разрешений пользователя с уровня **Только просмотр** до уровня **Чтение** на определенные документы из этой библиотеки.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-168">The following steps instruct you to break permission inheritance at the library level and increase user permissions from **View Only** to **Read** for specific documents in this library.</span></span> <span data-ttu-id="ac2ba-169">Перед тем как продолжить, внимательно ознакомьтесь с существующими разрешениями и документами и убедитесь, что эти действия подходят для данного сайта.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-169">Before you proceed, carefully review existing permissions and documents and verify that these steps are appropriate for your site.</span></span>  
>   
>  <span data-ttu-id="ac2ba-170">В качестве альтернативы можно создать папку в библиотеке, переместить в нее все требуемые документы и задать уникальные разрешения на эту папку.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-170">Alternatively, you can create a folder in the library, move all affected documents to that folder, and set unique permissions on the folder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2ba-171">Если книги хранятся в галерее PowerPivot, разрыв цепочки наследования разрешений для книги приведет к невозможности формирования эскизов для этой книги, если для нее настроено обновление данных.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-171">If your workbooks are stored in PowerPivot Gallery, breaking permission inheritance on a workbook will disrupt thumbnail image generation for that workbook if it is configured for data refresh.</span></span> <span data-ttu-id="ac2ba-172">Чтобы одновременно разрешить доступ к книгам и к изображениям предварительного просмотра в галерее, рассмотрите возможность предоставления определенным пользователям разрешений на **Чтение** на уровне библиотеки для всех документов из этой библиотеки.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-172">To simultaneously allow access to both workbooks and preview images in the gallery, consider granting to specific users **Read** permissions at the library level, for all documents in the library.</span></span>  
  
 <span data-ttu-id="ac2ba-173">Изменять разрешения могут только владельцы сайтов.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-173">You must be a site owner to change permissions.</span></span>  
  
 <span data-ttu-id="ac2ba-174">**Как повысить разрешения до уровня «Чтение» для отдельных книг**</span><span class="sxs-lookup"><span data-stu-id="ac2ba-174">**How to increase permissions to Read permission level for individual workbooks**</span></span>  
  
1.  <span data-ttu-id="ac2ba-175">Щелкните стрелку вниз, чтобы открыть меню для отдельного документа.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-175">Click the down arrow to open the menu for an individual document.</span></span>  
  
2.  <span data-ttu-id="ac2ba-176">Нажмите **Управление разрешениями**.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-176">Click **Manage Permissions**.</span></span>  
  
3.  <span data-ttu-id="ac2ba-177">По умолчанию библиотека наследует разрешения.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-177">By default, a library inherits permissions.</span></span> <span data-ttu-id="ac2ba-178">Чтобы изменить разрешения для отдельных книг в этой библиотеке, нажмите кнопку **Прекратить наследование разрешений**.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-178">To change the permissions of individual workbooks in this library, click **Stop Inheriting Permissions**.</span></span>  
  
4.  <span data-ttu-id="ac2ba-179">Установите флажок около имени пользователя или группы, которым требуются дополнительные разрешения на книги PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-179">Select the checkbox by user or group names that require additional permissions on PowerPivot workbooks.</span></span> <span data-ttu-id="ac2ba-180">Дополнительные разрешения позволят этим пользователям получать доступ к внедренным данным PowerPivot и использовать эти данные в качестве внешнего источника данных в других документах.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-180">Additional permissions will allow these users to link to the embedded PowerPivot data and use that data as an external data source in other documents.</span></span>  
  
5.  <span data-ttu-id="ac2ba-181">Нажмите **Изменить разрешения пользователя**.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-181">Click **Edit User Permissions**.</span></span>  
  
6.  <span data-ttu-id="ac2ba-182">Выберите разрешения **Чтение** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-182">Choose **Read** permissions, and then click **OK**.</span></span>  
  
#### <a name="powerpivot-gallery-new-rules-for-snapshot-generation-for-some-powerpivot-workbooks"></a><span data-ttu-id="ac2ba-183">Коллекция PowerPivot. Новые правила для создания моментальных снимков для некоторых книг PowerPivot</span><span class="sxs-lookup"><span data-stu-id="ac2ba-183">PowerPivot Gallery: New rules for snapshot generation for some PowerPivot workbooks</span></span>  
 <span data-ttu-id="ac2ba-184">В этом выпуске появились новые требования для создания моментальных снимков в галерее PowerPivot, исключающие потенциальную возможность раскрытия сведений (а именно просмотр моментального снимка данных из источника данных, на просмотр которых у пользователя нет разрешений).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-184">This release introduces new requirements for generating snapshot images in PowerPivot Gallery, eliminating a potential source of information disclosure (namely, showing a snapshot of data from a data source that you do not have permission to view).</span></span> <span data-ttu-id="ac2ba-185">Эти требования относятся только к книгам PowerPivot, которые соединяются с внешними источниками данных при каждом просмотре книги.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-185">These requirements apply only to PowerPivot workbooks that connect to external data sources each time you view the workbook.</span></span> <span data-ttu-id="ac2ba-186">Если используются только книги, отображающие внедренные данные PowerPivot, никаких изменений в механизме формирования моментальных снимков в галерее PowerPivot заметно не будет.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-186">If you only use workbooks that visualize embedded PowerPivot data, you will see no change in how snapshots are generated in PowerPivot Gallery.</span></span>  
  
 <span data-ttu-id="ac2ba-187">Далее приведены новые требования к формированию моментальных снимков для книг, данные которых обновляются при каждом их открытии.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-187">For a workbook that refreshes its data each time it is opened, the new requirements for snapshot generation are as follows:</span></span>  
  
-   <span data-ttu-id="ac2ba-188">Книги PowerPivot, которые используются в качестве внешнего источника данных другими книгами или отчетами, должны находиться в той же библиотеке, что и книги, которые эти данные получают.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-188">PowerPivot workbooks that are used as external data sources by other workbooks or reports must be in the same library as the workbooks that consume the data.</span></span> <span data-ttu-id="ac2ba-189">Например, если данные из файла sales-data.xlsx передаются в файл sales-report.xlsx, обе эти книги должны находиться в одной галерее, чтобы моментальные снимки могли отображаться.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-189">For example, if you have sales-data.xlsx that provides data to sales-report.xlsx, both workbooks must be in the gallery in order for snapshot images to appear.</span></span>  
  
-   <span data-ttu-id="ac2ba-190">Книги, которые используются совместно, должны наследовать разрешения от общего родителя (другими словами, от галереи PowerPivot).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-190">Workbooks that are used together must inherit permissions from a common parent (that is, the PowerPivot Gallery).</span></span> <span data-ttu-id="ac2ba-191">В нашем примере файлы sales-data.xlsx и sales-report.xlsx должны наследовать разрешения от галереи PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-191">In our example, both sales-data.xlsx and sales-report.xlsx must inherit from PowerPivot Gallery.</span></span>  
  
 <span data-ttu-id="ac2ba-192">Если книга не удовлетворяет любому из этих критериев, вместо ожидаемого эскиза будет отображен следующий значок блокировки.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-192">If a workbook fails to meet any of the above criteria, the following locked icon will appear instead of the thumbnail image you expect:</span></span>  
  
 <span data-ttu-id="ac2ba-193">![GMNI_PowerPivotGalleryIcon_Locked](media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")</span><span class="sxs-lookup"><span data-stu-id="ac2ba-193">![GMNI_PowerPivotGalleryIcon_Locked](media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")</span></span>  
  
#### <a name="new-default-setting-for-load-balancing-requests-changed-from-round-robin-to-health-based"></a><span data-ttu-id="ac2ba-194">Новое значение по умолчанию параметра для запросов балансировки нагрузки изменилось с «Циклический перебор» на «По исправности»</span><span class="sxs-lookup"><span data-stu-id="ac2ba-194">New default setting for load balancing requests changed from Round-Robin to Health-Based</span></span>  
 <span data-ttu-id="ac2ba-195">Приложение службы PowerPivot имеет параметры по умолчанию, определяющие способ распределения запросов к данным PowerPivot между несколькими серверами PowerPivot для SharePoint в ферме.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-195">A PowerPivot service application has default settings that determine how requests for PowerPivot data are distributed across multiple PowerPivot for SharePoint servers in a farm.</span></span> <span data-ttu-id="ac2ba-196">В предыдущем выпуске значением по умолчанию было **Циклический перебор**, при котором запросы распределялись последовательно среди доступных серверов.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-196">In the previous release, the default setting was **Round Robin**, where requests were distributed sequentially among the available servers.</span></span> <span data-ttu-id="ac2ba-197">В этом выпуске значением по умолчанию является **По исправности**.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-197">In this release, the default is now **Health Based**.</span></span> <span data-ttu-id="ac2ba-198">Приложение службы PowerPivot использует статистику работоспособности сервера, такую как доступный объем памяти или ЦП, для определения того, какому экземпляру сервера направить запрос.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-198">The PowerPivot service application uses server health statistics, such as available memory or CPU, to determine which server instance gets the xt request.</span></span>  
  
 <span data-ttu-id="ac2ba-199">В случае обновления сервера в предыдущем выпуске приложение службы PowerPivot сохранит предыдущее значение по умолчанию (**Циклический перебор**).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-199">If you upgraded your server from the previous release, the PowerPivot service application retains the previous default setting (**Round Robin**).</span></span> <span data-ttu-id="ac2ba-200">Чтобы использовать способ распределения **По исправности** , необходимо изменить параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ac2ba-200">To use the **Health Based** allocation method setting, you must modify the configuration settings.</span></span> <span data-ttu-id="ac2ba-201">Дополнительные сведения см. в разделе [Create and Configure a PowerPivot Service Application in Central Administration](power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).</span><span class="sxs-lookup"><span data-stu-id="ac2ba-201">For more information, see [Create and Configure a PowerPivot Service Application in Central Administration](power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2ba-202">См. также:</span><span class="sxs-lookup"><span data-stu-id="ac2ba-202">See Also</span></span>  
 <span data-ttu-id="ac2ba-203">[Обратная совместимость](../../2014/getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ba-203">[Backward Compatibility](../../2014/getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="ac2ba-204">Критические изменения функций служб Analysis Services в SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="ac2ba-204">Breaking Changes to Analysis Services Features in SQL Server 2014</span></span>](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)  
  
  