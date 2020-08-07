---
title: Веб-часть "средство просмотра отчетов" на сайте SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: b6341a73-172f-4632-a9e9-cc79fed3f36b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d867df9fca54a74b846c6100f4f6734cd2e28a05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734994"
---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a><span data-ttu-id="aecf1-102">Веб-часть средства просмотра отчетов на сайте SharePoint</span><span class="sxs-lookup"><span data-stu-id="aecf1-102">Report Viewer Web Part on a SharePoint Site</span></span>
  <span data-ttu-id="aecf1-103">Средство просмотра отчетов — это специальная веб-часть, устанавливаемая в составе надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для технологий SharePoint.</span><span class="sxs-lookup"><span data-stu-id="aecf1-103">The Report Viewer Web Part is a custom Web Part that is installed by the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in for SharePoint Products.</span></span> <span data-ttu-id="aecf1-104">Она позволяет просматривать, печатать и экспортировать отчеты с сервера отчетов, настроенного для работы в режиме интеграции с SharePoint.</span><span class="sxs-lookup"><span data-stu-id="aecf1-104">You can use the Web Part to view, navigate, print, and export reports on a report server that is configured to run in SharePoint integrated mode.</span></span> <span data-ttu-id="aecf1-105">Веб-часть «средство просмотра отчетов» связана с файлами определения отчета (RDL), которые обрабатываются [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сервером отчетов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-105">The Report Viewer Web Part is associated with report definition (.rdl) files that are processed by a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="aecf1-106">Ее нельзя использовать с отчетами, созданными с помощью других программных продуктов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-106">You cannot use it with other report documents that you create in other software products.</span></span>  
  
 <span data-ttu-id="aecf1-107">Чтобы установить веб-часть, запустите программу установки надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="aecf1-107">To install the Web Part, you must run Setup for the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="aecf1-108">Нельзя установить или удалить веб-часть отдельно.</span><span class="sxs-lookup"><span data-stu-id="aecf1-108">You should not install or uninstall the Web Part independently.</span></span> <span data-ttu-id="aecf1-109">Она является составной частью надстройки и может быть установлена только с помощью пакета установки надстройки.</span><span class="sxs-lookup"><span data-stu-id="aecf1-109">It is part of the add-in and can only be installed through the add-in setup package.</span></span> <span data-ttu-id="aecf1-110">Имя файла веб-части «Средство просмотра отчетов» — ReportViewer.dwp.</span><span class="sxs-lookup"><span data-stu-id="aecf1-110">The Report Viewer Web Part file name is ReportViewer.dwp.</span></span> <span data-ttu-id="aecf1-111">Он находится в папке «Program Files\Common Files\Microsoft Shared\web server extensions\12\template\features\reportserver» и не может быть перемещен в другое место.</span><span class="sxs-lookup"><span data-stu-id="aecf1-111">It is located in the Program Files\Common Files\Microsoft Shared\web server extensions\12\template\features\reportserver folder and should not be moved to other folders.</span></span>  
  
 <span data-ttu-id="aecf1-112">Чтобы использовать эту веб-часть, необходимо установить и настроить надстройку служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , а также настроить сервер отчетов для интеграции с SharePoint.</span><span class="sxs-lookup"><span data-stu-id="aecf1-112">To use the Web Part, you must have installed and configured the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in and configured the report server for SharePoint integration.</span></span> <span data-ttu-id="aecf1-113">Кроме того, необходимо иметь отчеты для отображения в программе просмотра.</span><span class="sxs-lookup"><span data-stu-id="aecf1-113">You must also have reports to display in the viewer.</span></span> <span data-ttu-id="aecf1-114">Открыть можно лишь отчеты, размещенные в библиотеке, в папках библиотеки, в журнале отчетов, либо отчеты, связывающие веб-часть «Библиотека» с веб-частью «Средство просмотра отчетов».</span><span class="sxs-lookup"><span data-stu-id="aecf1-114">You can only open reports that are in a library, a library folder, report history, or a link from a Library Web Part to a Report Viewer Web Part.</span></span> <span data-ttu-id="aecf1-115">Нельзя открыть отчеты, сохраненные в виде вложений в объекты пользовательских списков.</span><span class="sxs-lookup"><span data-stu-id="aecf1-115">You cannot open reports that are saved as an attachment to an item in a custom list.</span></span>  
  
 <span data-ttu-id="aecf1-116">Изменяя свойства веб-части «Средство просмотра отчетов», можно управлять внешним видом панели инструментов и областей просмотра, а также связывать веб-часть с конкретным отчетом.</span><span class="sxs-lookup"><span data-stu-id="aecf1-116">You can set properties on the Report Viewer Web Part to control the appearance of the toolbar and view areas, and to link the Web Part to a specific report.</span></span> <span data-ttu-id="aecf1-117">Средство просмотра отчетов отображает либо явно связанный с ним отчет, либо открытый RDL-файл.</span><span class="sxs-lookup"><span data-stu-id="aecf1-117">The Report Viewer either shows a report that you explicitly link to it, or it shows any .rdl file that you open.</span></span>  
  
 <span data-ttu-id="aecf1-118">С одним экземпляром средства просмотра отчетов нельзя связать более одного отчета, однако, если необходимо сгруппировать отчеты, можно создать панель или страницу «Веб-часть», в которую внедрены несколько экземпляров веб-части «Средство просмотра отчетов».</span><span class="sxs-lookup"><span data-stu-id="aecf1-118">You cannot link multiple reports to a single Report Viewer instance, but if you want to group reports together, you can create a dashboard or a Web Part page that embeds multiple Report Viewer Web Part instances on a single page.</span></span>  
  
 <span data-ttu-id="aecf1-119">Веб-часть включает в себя область просмотра, панель инструментов, свертывающуюся область для ввода учетных данных и параметров, а также свойства.</span><span class="sxs-lookup"><span data-stu-id="aecf1-119">The Web Part includes a view area, a toolbar, a collapsible area for setting credentials and parameters, and properties.</span></span> <span data-ttu-id="aecf1-120">На следующем рисунке изображена веб-часть с образцом отчета Company Sales и параметры экспорта, которые могут быть выбраны на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-120">The following image shows the Web Part with the sample Company Sales report and the export options that you can select from the toolbar.</span></span>  
  
 <span data-ttu-id="aecf1-121">![Веб-часть средства просмотра отчетов](media/rs-sharepointrvwebpart.gif "Веб-часть средства просмотра отчетов")</span><span class="sxs-lookup"><span data-stu-id="aecf1-121">![Report Viewer Web Part](media/rs-sharepointrvwebpart.gif "Report Viewer Web Part")</span></span>  
  
## <a name="web-part-components"></a><span data-ttu-id="aecf1-122">Компоненты веб-части</span><span class="sxs-lookup"><span data-stu-id="aecf1-122">Web Part components</span></span>  
 <span data-ttu-id="aecf1-123">В области просмотра отображается отчет в формате HTML.</span><span class="sxs-lookup"><span data-stu-id="aecf1-123">The view area displays a report in HTML.</span></span> <span data-ttu-id="aecf1-124">В зависимости от настройки веб-части область просмотра может быть развернута, чтобы отображать отчет в полностраничном режиме, или будет делить доступное пространство с соседними областями и панелью инструментов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-124">Depending on how the Web Part is configured, the view area might be maximized to show the report in full-page mode, or it might share the available space with adjacent panes and a toolbar.</span></span>  
  
 <span data-ttu-id="aecf1-125">Панель инструментов предоставляет функции перемещения по страницам, поиска, изменения масштаба и функцию экспорта, позволяющую просматривать отчеты в форматах других приложений.</span><span class="sxs-lookup"><span data-stu-id="aecf1-125">The toolbar provides page navigation, search, zoom, and export features so that you can view a report in another application format.</span></span> <span data-ttu-id="aecf1-126">Кроме того, она позволяет печатать документы, предоставляя возможность разбивки HTML-отчетов на страницы, возможности изменения параметров страницы и настройки полей.</span><span class="sxs-lookup"><span data-stu-id="aecf1-126">It also provides optional print functionality, offering paginated print output for HTML reports and the ability to change page layout and margin settings.</span></span> <span data-ttu-id="aecf1-127">В меню**Действия**, **Открыть в построителе отчетов, Подписка**, **Экспорт** и **Печать** .</span><span class="sxs-lookup"><span data-stu-id="aecf1-127">**Open with Report Builder, Subscribe**, **Export**, and **Print** are provided in the **Actions** menu on the toolbar.</span></span> <span data-ttu-id="aecf1-128">Элементы управления перемещением по страницам и изменением масштаба расположены непосредственно на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-128">Page navigation and zoom controls are directly on the toolbar.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aecf1-129">Настройка панели инструментов не предусмотрена, однако можно задать свойства, позволяющие скрыть некоторые или все элементы управления.</span><span class="sxs-lookup"><span data-stu-id="aecf1-129">You cannot customize the toolbar unless you write code to do so, but you can set properties to hide all or some of its controls.</span></span>  
  
### <a name="export-action-on-the-report-toolbar"></a><span data-ttu-id="aecf1-130">Действие «Экспорт» на панели инструментов отчета</span><span class="sxs-lookup"><span data-stu-id="aecf1-130">Export Action on the Report Toolbar</span></span>  
 <span data-ttu-id="aecf1-131">Команда**Экспорт** в меню **Действия** отображает форматы приложений, которые связаны с модулями подготовки отчетов, развернутыми на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-131">**Export** on the **Actions** menu shows application formats that are associated with rendering extensions deployed on a report server.</span></span> <span data-ttu-id="aecf1-132">Чтобы определить доступность некоторого формата, можно добавить или удалить модуль подготовки отчетов на сервере отчетов либо изменить настройки конфигурации для удаления из списка того или иного формата экспорта.</span><span class="sxs-lookup"><span data-stu-id="aecf1-132">To determine the availability of a specific format, you can add or remove a rendering extension on the report server, or you can modify configuration settings to remove a particular export format from the list.</span></span> <span data-ttu-id="aecf1-133">Кроме того, управлять доступностью форматов можно с помощью настроек конфигурации на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-133">You can also specify configuration settings on the report server to control which formats are available.</span></span> <span data-ttu-id="aecf1-134">Можно изменить поведение по умолчанию того или иного формата за счет добавления и изменения настроек конфигурации для соответствующего модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-134">You can modify the default behavior of a specific format by adding and modifying configuration settings for that rendering extension.</span></span>  
  
### <a name="print-action-on-the-report-toolbar"></a><span data-ttu-id="aecf1-135">Действие «Печать» на панели инструментов отчета</span><span class="sxs-lookup"><span data-stu-id="aecf1-135">Print Action on the Report Toolbar</span></span>  
 <span data-ttu-id="aecf1-136">Команда**Печать** в меню **Действия** обеспечивает специальные функции печати, предоставляемые службами [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aecf1-136">**Print** on the **Actions** menu is custom print functionality that is provided through [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="aecf1-137">При нажатии кнопки **Печать**на компьютер клиента загружается элемент управления печатью ActiveX.</span><span class="sxs-lookup"><span data-stu-id="aecf1-137">When you click **Print**, an ActiveX client-side print control is downloaded to the client computer.</span></span> <span data-ttu-id="aecf1-138">В большинстве случаев пользователь, нажимающий кнопку **Печать** , должен иметь разрешения администратора локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="aecf1-138">In most cases, the user who clicks **Print** must have Administrator permissions on the local computer.</span></span> <span data-ttu-id="aecf1-139">Как правило, правом загружать элементы управления ActiveX наделяются лишь пользователи, обладающие разрешениями администратора.</span><span class="sxs-lookup"><span data-stu-id="aecf1-139">It is common practice to restrict ActiveX control downloads to only those users who have Administrator permissions.</span></span> <span data-ttu-id="aecf1-140">Центр администрирования SharePoint можно использовать для включения или отключения скачивания клиентского элемента управления печатью.</span><span class="sxs-lookup"><span data-stu-id="aecf1-140">You can use SharePoint Central Administration to enable or disable the download of the client-side print control.</span></span>  
  
### <a name="find-action-on-the-report-toolbar"></a><span data-ttu-id="aecf1-141">Действие «Поиск» на панели инструментов отчета</span><span class="sxs-lookup"><span data-stu-id="aecf1-141">Find Action on the Report Toolbar</span></span>  
 <span data-ttu-id="aecf1-142">Команда**Найти** в меню **Действия** предоставляет возможность перемещения к нужному месту в отчете.</span><span class="sxs-lookup"><span data-stu-id="aecf1-142">**Find** on the **Actions** menu provides a way to move to a target location in the report.</span></span> <span data-ttu-id="aecf1-143">Можно искать содержимое в отчете, вводя искомое слово или фразу.</span><span class="sxs-lookup"><span data-stu-id="aecf1-143">You can search for content in a report by typing a word or phrase that you want to find.</span></span> <span data-ttu-id="aecf1-144">Длина строки поиска не должна превышать 256 символов.</span><span class="sxs-lookup"><span data-stu-id="aecf1-144">The maximum value of a search term is 256 characters.</span></span> <span data-ttu-id="aecf1-145">Когда искомое значение найдено в отчете, фокус перемещается к содержащему его фрагменту отчета.</span><span class="sxs-lookup"><span data-stu-id="aecf1-145">When your search finds a matching value in the report, focus is moved to the part of the report that contains that value.</span></span>  
  
 <span data-ttu-id="aecf1-146">При вводе значения для поиска, его следует указывать так, как оно должно выглядеть в отчете.</span><span class="sxs-lookup"><span data-stu-id="aecf1-146">When you enter a value to search on, type the value as you expect it to appear in the report.</span></span> <span data-ttu-id="aecf1-147">Не следует вводить вопросы (например, «какова средняя прибыль за текущий месяц»), если только каждое слово этого предложения не содержится в отчете.</span><span class="sxs-lookup"><span data-stu-id="aecf1-147">Do not pose a question, such as "what is the average profit for this month" unless you expect every word in the sentence to be in the report.</span></span>  
  
 <span data-ttu-id="aecf1-148">За один раз может быть выполнен поиск только одного термина или значения.</span><span class="sxs-lookup"><span data-stu-id="aecf1-148">You can only search for one term or value at a time.</span></span> <span data-ttu-id="aecf1-149">Нельзя использовать операторы поиска (`AND`, `OR` и т. п.), символы и шаблоны.</span><span class="sxs-lookup"><span data-stu-id="aecf1-149">You cannot use search operators (such as `AND` or `OR`), or symbols and wildcards.</span></span> <span data-ttu-id="aecf1-150">Нельзя также выполнить поиск для разреза данных (например, найти чистую выручку от продаж по конкретному продукту за определенный месяц).</span><span class="sxs-lookup"><span data-stu-id="aecf1-150">You cannot perform a search on a cross-section of the data (for example, searching for net sales for specific month for a particular product).</span></span> <span data-ttu-id="aecf1-151">Для выполнения анализа такого рода применяется построитель отчетов, который позволяет создавать отчеты с дополнительной информацией.</span><span class="sxs-lookup"><span data-stu-id="aecf1-151">For that kind of analysis, use Report Builder to create clickthrough reports.</span></span>  
  
 <span data-ttu-id="aecf1-152">На операции поиска влияют настройки безопасности базы данных и модели, ограничивающие доступ к данным отчета.</span><span class="sxs-lookup"><span data-stu-id="aecf1-152">Database and model security settings that restrict access to report data apply to search operations.</span></span> <span data-ttu-id="aecf1-153">Если выполняется поиск значения в отчете с дополнительной информацией, который использует модель в качестве источника данных, и при этом к части модели доступ отсутствует, то недоступные данные будут исключены из поиска.</span><span class="sxs-lookup"><span data-stu-id="aecf1-153">If you are searching for a value in a clickthrough report that uses a model as a data source, and you do not have access to part of the model, data that is represented by that part of the model will be excluded from the search.</span></span>  
  
### <a name="panes-for-specifying-credentials-and-parameters"></a><span data-ttu-id="aecf1-154">Панели для указания параметров и учетных данных</span><span class="sxs-lookup"><span data-stu-id="aecf1-154">Panes for Specifying Credentials and Parameters</span></span>  
 <span data-ttu-id="aecf1-155">**Учетные данные** и **Параметры** — это панели, отображаемые рядом с областью просмотра.</span><span class="sxs-lookup"><span data-stu-id="aecf1-155">**Credentials** and **Parameters** are panes that appear next to the view area.</span></span> <span data-ttu-id="aecf1-156">Область**Учетные данные** отображается в том случае, если подключение к источнику данных отчета настроено для запроса у пользователя учетной записи и пароля, имеющих права на доступ к источнику данных.</span><span class="sxs-lookup"><span data-stu-id="aecf1-156">**Credentials** appears when the data source connection for the report is configured to prompt the user for an account and password that has rights to access the data source.</span></span> <span data-ttu-id="aecf1-157">Область**Параметры** отображается в том случае, если отчет требует ввода пользователем параметров, определенных в нем.</span><span class="sxs-lookup"><span data-stu-id="aecf1-157">**Parameters** appears when the report accepts user input for parameters defined in the report.</span></span>  
  
### <a name="setting-properties-on-the-report-viewer-web-part"></a><span data-ttu-id="aecf1-158">Задание свойств веб-части «Средство просмотра отчетов»</span><span class="sxs-lookup"><span data-stu-id="aecf1-158">Setting Properties on the Report Viewer Web Part</span></span>  
 <span data-ttu-id="aecf1-159">Свойства веб-части включают в себя пользовательские свойства — как относящиеся к средству просмотра отчетов, так и общие свойства, которые можно настроить для любой веб-части.</span><span class="sxs-lookup"><span data-stu-id="aecf1-159">Properties on the Web Part include custom properties that are specific to Report Viewer and general properties that you can set for any Web Part.</span></span> <span data-ttu-id="aecf1-160">Дополнительные сведения см. в разделе [Настройка веб-части "Средство просмотра отчетов"](../../2014/reporting-services/customize-the-report-viewer-web-part.md).</span><span class="sxs-lookup"><span data-stu-id="aecf1-160">For more information, see [Customize the Report Viewer Web Part](../../2014/reporting-services/customize-the-report-viewer-web-part.md).</span></span>  
  
 <span data-ttu-id="aecf1-161">По умолчанию отчеты открываются в полностраничном режиме.</span><span class="sxs-lookup"><span data-stu-id="aecf1-161">Reports open in full-page mode by default.</span></span> <span data-ttu-id="aecf1-162">В этом режиме отображается панель инструментов, содержащая средства перемещения по страницам, поиска и другие функции.</span><span class="sxs-lookup"><span data-stu-id="aecf1-162">Full-page mode shows the toolbar that provides page navigation, search, and other functionality.</span></span> <span data-ttu-id="aecf1-163">Можно настроить внешний вид веб-части и поведение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aecf1-163">You can customize the Web Part to change appearance or default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aecf1-164">См. также:</span><span class="sxs-lookup"><span data-stu-id="aecf1-164">See Also</span></span>  
 <span data-ttu-id="aecf1-165">[Установка или удаление надстройки Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="aecf1-165">[Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="aecf1-166">Добавление веб-части средства просмотра отчетов на веб-страницу (службы Reporting Services в режиме интеграции с SharePoint)</span><span class="sxs-lookup"><span data-stu-id="aecf1-166">Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
  