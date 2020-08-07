---
title: Использование веб-каналов данных (PowerPivot для SharePoint) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 50140fdf-6fd1-41a1-9c14-8ecfb97ba2e1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 19e3c5b448005314696f8167156a2326dc5009e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732082"
---
# <a name="use-data-feeds-powerpivot-for-sharepoint"></a><span data-ttu-id="5e33f-102">использовать веб-каналы данных (PowerPivot для SharePoint)</span><span class="sxs-lookup"><span data-stu-id="5e33f-102">Use Data Feeds (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="5e33f-103">Канал данных — это один или несколько потоков данных, формируемых из источника данных в сети и направляемых в целевой документ или приложение.</span><span class="sxs-lookup"><span data-stu-id="5e33f-103">Data feeds are one or more data streams that are generated from an online data source and streamed to a destination document or application.</span></span> <span data-ttu-id="5e33f-104">Если используется PowerPivot для Excel, веб-каналы данных позволяют получать существующие корпоративные данные или бизнес-данные из произвольных источников данных в окно PowerPivot в книге Excel 2010.</span><span class="sxs-lookup"><span data-stu-id="5e33f-104">If you are using PowerPivot for Excel, data feeds can help you get existing corporate or business data from arbitrary data sources into the PowerPivot window in your Excel 2010 workbook.</span></span> <span data-ttu-id="5e33f-105">После импорта веб-канала данных в книгу на него можно ссылаться в любых операциях обновления данных, планируемых на сервере SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5e33f-105">After you import a data feed to a workbook, you can reference it later in any data refresh operations that you schedule on a SharePoint server.</span></span>  
  
 <span data-ttu-id="5e33f-106">Использование веб-канала данных зависит от того, используются встроенные функции экспорта в приложениях, поддерживающих веб-каналы данных Atom, или настраиваемые службы данных.</span><span class="sxs-lookup"><span data-stu-id="5e33f-106">How you use a data feed depends on whether you are using built-in export features in applications that support Atom data feeds, or creating and using custom data services.</span></span> <span data-ttu-id="5e33f-107">Приложения, которые могут публиковать и считывать XML-данные Atom, позволяют передавать данные таким образом, чтобы пользователю не нужно было работать с каналами данных и службами.</span><span class="sxs-lookup"><span data-stu-id="5e33f-107">Applications that are able to publish and read Atom XML data provide seamless data transfer that hides the mechanics of data feeds and data services from users.</span></span> <span data-ttu-id="5e33f-108">С точки зрения пользователя данные просто перемещаются между приложениями.</span><span class="sxs-lookup"><span data-stu-id="5e33f-108">To a user, he or she is simply moving data from one application to another.</span></span>  
  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="5e33f-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и Microsoft SharePoint 2010 предоставляют веб-каналы данных, которые можно использовать в книгах PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="5e33f-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and Microsoft SharePoint 2010 provide data feeds that can be used in PowerPivot workbooks.</span></span> <span data-ttu-id="5e33f-110">Сведения в данном разделе можно использовать для изучения доступа к веб-каналам данных из уже имеющихся отчетов и списков.</span><span class="sxs-lookup"><span data-stu-id="5e33f-110">You can use the information in this topic to learn how to access data feeds from reports and lists that you already have.</span></span>  
  
 <span data-ttu-id="5e33f-111">Этот раздел состоит из следующих подразделов.</span><span class="sxs-lookup"><span data-stu-id="5e33f-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="5e33f-112">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="5e33f-112">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="5e33f-113">Создание веб-канала данных из списка SharePoint</span><span class="sxs-lookup"><span data-stu-id="5e33f-113">Create a Data Feed from a SharePoint List</span></span>](#sharepointlist)  
  
 [<span data-ttu-id="5e33f-114">Создание веб-канала данных из Reporting Services отчета</span><span class="sxs-lookup"><span data-stu-id="5e33f-114">Create a Data Feed from a Reporting Services Report</span></span>](#rsreport)  
  
 [<span data-ttu-id="5e33f-115">Создание веб-канала данных из сервисного документа данных</span><span class="sxs-lookup"><span data-stu-id="5e33f-115">Create a Data Feed from a Data Service Document</span></span>](#dsdoc)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="5e33f-116">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="5e33f-116">Prerequisites</span></span>  
 <span data-ttu-id="5e33f-117">Для импорта веб-канала данных в Excel 2010 требуется PowerPivot для Excel.</span><span class="sxs-lookup"><span data-stu-id="5e33f-117">You must have the PowerPivot for Excel to import a data feed into Excel 2010.</span></span>  
  
 <span data-ttu-id="5e33f-118">Необходима веб-служба или служба данных, которые поставляют данные в формате Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="5e33f-118">You must have a Web service or a data service that provides data in the Atom 1.0 format.</span></span> <span data-ttu-id="5e33f-119">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] И SharePoint 2010 могут предоставлять данные в этом формате.</span><span class="sxs-lookup"><span data-stu-id="5e33f-119">Both [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and SharePoint 2010 can provide data in this format.</span></span>  
  
 <span data-ttu-id="5e33f-120">Перед экспортом списка SharePoint в качестве веб-канала данных необходимо установить на сервере SharePoint службы ADO.NET Data Services.</span><span class="sxs-lookup"><span data-stu-id="5e33f-120">Before you can export a SharePoint list as a data feed, you must install ADO.NET Data Services on the SharePoint server.</span></span> <span data-ttu-id="5e33f-121">Дополнительные сведения см. в разделе [Установка служб ADO.NET Data Services для поддержки экспорта списков SharePoint в виде веб-каналов данных](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).</span><span class="sxs-lookup"><span data-stu-id="5e33f-121">For more information, see [Install ADO.NET Data Services to support data feed exports of SharePoint lists](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).</span></span>  
  
##  <a name="create-a-data-feed-from-a-sharepoint-list"></a><a name="sharepointlist"></a><span data-ttu-id="5e33f-122">Создание веб-канала данных из списка SharePoint</span><span class="sxs-lookup"><span data-stu-id="5e33f-122">Create a Data Feed from a SharePoint List</span></span>  
 <span data-ttu-id="5e33f-123">На ферме SharePoint 2010 список SharePoint имеет кнопку «Экспортировать как веб-канал данных» на ленте списка.</span><span class="sxs-lookup"><span data-stu-id="5e33f-123">In a SharePoint 2010 farm, a SharePoint list has an Export as Data Feed button on the List ribbon.</span></span> <span data-ttu-id="5e33f-124">Нажав ее, можно экспортировать лист в качестве канала.</span><span class="sxs-lookup"><span data-stu-id="5e33f-124">You can click this button to export the list as a feed.</span></span> <span data-ttu-id="5e33f-125">Для получения наилучших результатов на рабочей станции должно быть установлено приложение Excel 2010 с клиентским приложением PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="5e33f-125">For best results, you should have Excel 2010 with the PowerPivot client application on your workstation.</span></span> <span data-ttu-id="5e33f-126">В ответ на экспорт веб-канала данных запускается клиентское приложение PowerPivot и создается новая таблица PowerPivot, содержащая список.</span><span class="sxs-lookup"><span data-stu-id="5e33f-126">The PowerPivot client application will launch in response to the data feed export, creating a new PowerPivot table that contains the list.</span></span>  
  
1.  <span data-ttu-id="5e33f-127">Откройте список на сайте SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5e33f-127">Open the list on your SharePoint site.</span></span>  
  
2.  <span data-ttu-id="5e33f-128">В окне «Средства списков» нажмите кнопку **Список**.</span><span class="sxs-lookup"><span data-stu-id="5e33f-128">In List Tools, click **List**.</span></span>  
  
3.  <span data-ttu-id="5e33f-129">В окне «Подключение и Экспорт» нажмите кнопку **Экспортировать как веб-канал данных**.</span><span class="sxs-lookup"><span data-stu-id="5e33f-129">In Connect and Export, click **Export as Data Feed**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e33f-130">Кнопка **экспортировать как веб-канал данных** добавляется в SharePoint с помощью PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="5e33f-130">The **Export as Data Feed** button is added to SharePoint by way of PowerPivot.</span></span> <span data-ttu-id="5e33f-131">Если компонент PowerPivot для SharePoint не установлен или не активирован, эта кнопка будет недоступна.</span><span class="sxs-lookup"><span data-stu-id="5e33f-131">If you do not have PowerPivot for SharePoint installed or you did not activate the PowerPivot feature, this button will not be available.</span></span>  
  
4.  <span data-ttu-id="5e33f-132">Щелкните **Открыть** , если PowerPivot для Excel установлен локально, или нажмите кнопку **сохранить** , чтобы сохранить ATOMSVC документ на жестком диске для выполнения операций импорта позже.</span><span class="sxs-lookup"><span data-stu-id="5e33f-132">Click **Open** if PowerPivot for Excel is installed locally, or click **Save** to save the .atomsvc document to your hard drive for import operations at a later time.</span></span>  
  
5.  <span data-ttu-id="5e33f-133">Если выбрано **открытие документа**, используйте мастер импорта таблиц для импорта веб-канала данных на лист.</span><span class="sxs-lookup"><span data-stu-id="5e33f-133">If you chose **Open**, use the Table Import Wizard to import the data feed to a worksheet.</span></span> <span data-ttu-id="5e33f-134">Веб-канал данных будет добавлен в окно PowerPivot в виде новой таблицы.</span><span class="sxs-lookup"><span data-stu-id="5e33f-134">The data feed will be added as a new table in the PowerPivot window.</span></span>  
  
 <span data-ttu-id="5e33f-135">Если службы ADO.NET Data Services 3.5.1 не установлены на сервере SharePoint, возникнет ошибка.</span><span class="sxs-lookup"><span data-stu-id="5e33f-135">An error will occur if ADO.NET Data Services 3.5.1 is not installed on the SharePoint server.</span></span> <span data-ttu-id="5e33f-136">Дополнительные сведения об ошибках и способах их устранения см. в статье [Установка служб ADO.NET Data Services для поддержки экспорта списков SharePoint в виде веб-каналов данных](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).</span><span class="sxs-lookup"><span data-stu-id="5e33f-136">For more information about the error and how to resolve it, see [Install ADO.NET Data Services to support data feed exports of SharePoint lists](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).</span></span>  
  
##  <a name="create-a-data-feed-from-a-reporting-services-report"></a><a name="rsreport"></a> <span data-ttu-id="5e33f-137">Создание веб-канала данных на основе отчета служб Reporting Services</span><span class="sxs-lookup"><span data-stu-id="5e33f-137">Create a Data Feed from a Reporting Services Report</span></span>  
 <span data-ttu-id="5e33f-138">Если на компьютере развернуты службы SQL Server 2008 R2 Reporting Services, можно использовать новый модуль подготовки отчетов Atom для создания веб-канала данных из существующего отчета.</span><span class="sxs-lookup"><span data-stu-id="5e33f-138">If you have a deployment of SQL Server 2008 R2 Reporting Services, you can use the new Atom rendering extension to generate a data feed from an existing report.</span></span> <span data-ttu-id="5e33f-139">Для получения наилучших результатов на рабочей станции должно быть установлено приложение Excel 2010 с надстройкой PowerPivot для Excel.</span><span class="sxs-lookup"><span data-stu-id="5e33f-139">For best results, you should have Excel 2010 with the PowerPivot for Excel on your workstation.</span></span> <span data-ttu-id="5e33f-140">При выполнении экспорта веб-канала данных запускается клиентское приложение Gemini PowerPivot, которое автоматически добавляет и связывает таблицы и столбцы по мере их поступления в поток.</span><span class="sxs-lookup"><span data-stu-id="5e33f-140">The PowerPivot client application will launch in response to the data feed export, automatically adding and relating the tables and columns as they are streamed in.</span></span>  
  
 <span data-ttu-id="5e33f-141">Инструкции по экспорту потока данных из отчета см. в разделе [Формирование веб-каналов данных из отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md)[справки по построителю отчетов](https://go.microsoft.com/fwlink/?LinkId=154494).</span><span class="sxs-lookup"><span data-stu-id="5e33f-141">For instructions on how to export a data feed from a report, see [Generate Data Feeds from a Report &#40;Report Builder and SSRS&#41;](../../reporting-services/report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md) in the [Report Builder help file](https://go.microsoft.com/fwlink/?LinkId=154494).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e33f-142">Чтобы настроить обновление данных по расписанию, при котором выполняется повторный импорт данных отчетов в книгу PowerPivot, опубликованную в библиотеке SharePoint, сервер отчетов должен быть настроен в режиме интеграции с SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5e33f-142">To set up a recurring data refresh schedule that re-imports report data into a PowerPivot workbook that is published to a SharePoint library, the report server must be configured for SharePoint integration.</span></span> <span data-ttu-id="5e33f-143">Дополнительные сведения об использовании PowerPivot для SharePoint и Reporting Services совместно см. [в разделе Настройка и администрирование сервера отчетов &#40;Reporting Services режиме интеграции с SharePoint&#41;](../../reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md).</span><span class="sxs-lookup"><span data-stu-id="5e33f-143">For more information about using PowerPivot for SharePoint and Reporting Services together, see [Configuration and Administration of a Report Server &#40;Reporting Services SharePoint Mode&#41;](../../reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md).</span></span>  
  
##  <a name="create-a-data-feed-from-a-data-service-document"></a><a name="dsdoc"></a> <span data-ttu-id="5e33f-144">Создание веб-канала данных на основе сервисного документа данных</span><span class="sxs-lookup"><span data-stu-id="5e33f-144">Create a Data Feed from a Data Service Document</span></span>  
 <span data-ttu-id="5e33f-145">Если имеется пользовательская служба данных, которая формирует веб-каналы Atom, то можно настроить сервисный документ данных, чтобы сделать данные доступными для пользователей и приложений.</span><span class="sxs-lookup"><span data-stu-id="5e33f-145">If you have a custom data service that generates Atom feeds, you can set up a data service document as a way to make the data available to users and applications.</span></span> <span data-ttu-id="5e33f-146">В файле *сервисного документа данных* (ATOMSVC) указывается одно или несколько соединений с источниками в сети, которые публикуют данные в формате подключения Atom.</span><span class="sxs-lookup"><span data-stu-id="5e33f-146">A *data service document* (.atomsvc) file specifies one or more connections to online sources that publish data in the Atom wire format.</span></span> <span data-ttu-id="5e33f-147">Сервисные документы данных можно создать в *библиотеке каналов данных*, которая является специальной библиотекой, обеспечивающей точку общего доступа для поиска сервисных документов данных, опубликованных на сервере SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5e33f-147">Data service documents can be created in a *data feed library*, which is a special-purpose library that provides a common access point for browsing data service documents that have been published to a SharePoint server.</span></span> <span data-ttu-id="5e33f-148">Информационные работники, имеющие разрешение на доступ к сервисным документам данных в библиотеке веб-каналов данных, могут использовать URL-адрес документа на SharePoint для импорта веб-каналов данных в свои книги и приложения.</span><span class="sxs-lookup"><span data-stu-id="5e33f-148">Information workers who have permission to access data service documents in the data feed library can reference the document's SharePoint URL to import the data feeds to their workbooks and applications.</span></span>  
  
1.  <span data-ttu-id="5e33f-149">Откройте библиотеку веб-каналов данных, которая создана администратором сайта.</span><span class="sxs-lookup"><span data-stu-id="5e33f-149">Open a data feed library that was created by your site administrator.</span></span> <span data-ttu-id="5e33f-150">Дополнительные сведения см. [в разделе Создание или Настройка библиотеки веб-каналов данных &#40;PowerPivot для SharePoint&#41;](create-or-customize-a-data-feed-library-power-pivot-for-sharepoint.md).</span><span class="sxs-lookup"><span data-stu-id="5e33f-150">For more information, see [Create or Customize a Data Feed Library &#40;PowerPivot for SharePoint&#41;](create-or-customize-a-data-feed-library-power-pivot-for-sharepoint.md).</span></span>  
  
2.  <span data-ttu-id="5e33f-151">В инструментах библиотеки выберите **Документы**.</span><span class="sxs-lookup"><span data-stu-id="5e33f-151">In Library Tools, click **Documents**.</span></span>  
  
3.  <span data-ttu-id="5e33f-152">Нажмите кнопку **Создать документ**.</span><span class="sxs-lookup"><span data-stu-id="5e33f-152">Click **New Document**.</span></span>  
  
4.  <span data-ttu-id="5e33f-153">Введите имя файла и описание.</span><span class="sxs-lookup"><span data-stu-id="5e33f-153">Provide a file name and description.</span></span>  
  
5.  <span data-ttu-id="5e33f-154">Укажите один или несколько URL-адресов, по которым передается канал.</span><span class="sxs-lookup"><span data-stu-id="5e33f-154">Specify one or more URLs that provide the feed:</span></span>  
  
    1.  <span data-ttu-id="5e33f-155">**Базовый URL-адрес** является необязательным.</span><span class="sxs-lookup"><span data-stu-id="5e33f-155">**Base URL** is optional.</span></span> <span data-ttu-id="5e33f-156">Его следует указывать, если сервисный документ данных содержит несколько каналов.</span><span class="sxs-lookup"><span data-stu-id="5e33f-156">You should specify it if a data service document provides multiple feeds.</span></span> <span data-ttu-id="5e33f-157">В базовом URL-адресе должна указываться часть URL-адреса, общая для всех каналов (например, имя сервера и сайт).</span><span class="sxs-lookup"><span data-stu-id="5e33f-157">Base URL should specify the portion of the URL that is common to all the feeds (for example, the server name and site).</span></span> <span data-ttu-id="5e33f-158">Если создается сервисный документ данных для отчета служб Reporting Services, то базовым URL-адресом будет URL-адрес сервера отчетов и отчет.</span><span class="sxs-lookup"><span data-stu-id="5e33f-158">If you are creating a data service document to a Reporting Services report, the base URL would be the report server URL and report.</span></span>  
  
    2.  <span data-ttu-id="5e33f-159">**URL-адрес веб-службы** является обязательным.</span><span class="sxs-lookup"><span data-stu-id="5e33f-159">**Web Service URL** is required.</span></span> <span data-ttu-id="5e33f-160">В отсутствие базового URL-адреса это значение должно содержать http:// или https://.</span><span class="sxs-lookup"><span data-stu-id="5e33f-160">Without the Base URL, this value must include http:// or https:// in the address.</span></span> <span data-ttu-id="5e33f-161">Если указан базовый URL-адрес, то URL-адрес веб-службы представляет часть URL-адреса, следующую за базовым адресом.</span><span class="sxs-lookup"><span data-stu-id="5e33f-161">If you specified a Base URL, the Web service URL is the portion that follows the Base URL.</span></span> <span data-ttu-id="5e33f-162">Например, если полный URL-адрес имеет значение, http://adventure-works/inventory/today.aspx то базовый URL-адрес будет иметь значение http://adventure-works/inventory , а URL веб службы будет/Тодай.аспкс..</span><span class="sxs-lookup"><span data-stu-id="5e33f-162">For example, if the full URL is http://adventure-works/inventory/today.aspx, the Base URL would be http://adventure-works/inventory, and the Web service URL would be /today.aspx.</span></span>  
  
         <span data-ttu-id="5e33f-163">В URL-адрес веб-службы могут входить параметры, выполняющие фильтрацию или выбирающие подмножество данных.</span><span class="sxs-lookup"><span data-stu-id="5e33f-163">The Web service URL can include parameters that filter or select a subset of data.</span></span> <span data-ttu-id="5e33f-164">Приложение или служба, предоставляющие канал, должны поддерживать параметры, указываемые в URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="5e33f-164">The application or service that provides the feed must support the parameters that you specify in the URL.</span></span>  
  
6.  <span data-ttu-id="5e33f-165">Введите в поле **Имя таблицы**по одной таблице на каждый канал.</span><span class="sxs-lookup"><span data-stu-id="5e33f-165">Enter a **Table Name**, one table for each feed.</span></span> <span data-ttu-id="5e33f-166">Это значение обязательно.</span><span class="sxs-lookup"><span data-stu-id="5e33f-166">This value is required.</span></span> <span data-ttu-id="5e33f-167">Имя таблицы используется клиентским приложением, получающим веб-канал данных.</span><span class="sxs-lookup"><span data-stu-id="5e33f-167">The table name is used by a client application that consumes the data feed.</span></span> <span data-ttu-id="5e33f-168">В PowerPivot для Excel имя таблицы используется для таблиц в окне PowerPivot. которые будут содержать импортируемые данные.</span><span class="sxs-lookup"><span data-stu-id="5e33f-168">In PowerPivot for Excel, the table name is used to name tables in the PowerPivot window that will contain the imported data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e33f-169">См. также:</span><span class="sxs-lookup"><span data-stu-id="5e33f-169">See Also</span></span>  
 <span data-ttu-id="5e33f-170">[Активация интеграции функций PowerPivot для семейств веб-сайтов в центре администрирования](activate-power-pivot-integration-for-site-collections-in-ca.md) </span><span class="sxs-lookup"><span data-stu-id="5e33f-170">[Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md) </span></span>  
 [<span data-ttu-id="5e33f-171">Совместное использование веб-каналов данных с помощью библиотеки каналов данных &#40;PowerPivot для SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="5e33f-171">Share Data Feeds Using a Data Feed Library &#40;PowerPivot for SharePoint&#41;</span></span>](share-data-feeds-using-a-data-feed-library-power-pivot-for-sharepoint.md)  
  
  