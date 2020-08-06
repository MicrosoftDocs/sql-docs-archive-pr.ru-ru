---
title: Публикация отчетов на сервере отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 644db7cc0d6647c160836596e6c87d524a94a4aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658094"
---
# <a name="publishing-reports-to-a-report-server"></a><span data-ttu-id="44900-102">Публикация отчетов на сервере отчетов</span><span class="sxs-lookup"><span data-stu-id="44900-102">Publishing Reports to a Report Server</span></span>
  <span data-ttu-id="44900-103">После создания и проверки отчета или набора отчетов можно воспользоваться встроенными функциями развертывания в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для публикации отчетов на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="44900-103">After you have designed and tested a report or set of reports, you can use the built-in deployment features in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to publish the reports to a report server.</span></span> <span data-ttu-id="44900-104">Можно опубликовать отдельные отчеты или проект «Сервер отчетов».</span><span class="sxs-lookup"><span data-stu-id="44900-104">You can publish individual reports or a Report Server project.</span></span> <span data-ttu-id="44900-105">Публикация проекта сервера отчетов — это самый простой способ публикации нескольких отчетов.</span><span class="sxs-lookup"><span data-stu-id="44900-105">Publishing a Report Server project is the easiest way to publish multiple reports.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="44900-106">использует термин *развертывание*, а не термин *опубликовать*.</span><span class="sxs-lookup"><span data-stu-id="44900-106">uses the term *deploy*, instead ofthe term *publish*.</span></span> <span data-ttu-id="44900-107">Два этих термина взаимозаменяемы.</span><span class="sxs-lookup"><span data-stu-id="44900-107">The two terms are interchangeable.</span></span>  
  
 <span data-ttu-id="44900-108">Прежде чем публиковать отчет, необходимо получить на это разрешение.</span><span class="sxs-lookup"><span data-stu-id="44900-108">Before you can publish a report, you must have permission to do so.</span></span> <span data-ttu-id="44900-109">Разрешение определяется параметрами безопасности на основе ролей, заданными администратором сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="44900-109">Permission is determined through role-based security that is defined by your report server administrator.</span></span> <span data-ttu-id="44900-110">Разрешения на операции публикации обычно предоставляются через роль «Издатель».</span><span class="sxs-lookup"><span data-stu-id="44900-110">Publishing operations are typically granted through the Publisher role.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="44900-111">предусматривает конфигурации проекта для управления публикацией отчета.</span><span class="sxs-lookup"><span data-stu-id="44900-111">provides project configurations for managing report publication.</span></span> <span data-ttu-id="44900-112">Конфигурация определяет местоположение сервера отчетов, версию служб SQL Server Reporting Services, установленных на сервере отчетов, перезапись источников данных, опубликованных на сервере отчетов, и т. д.</span><span class="sxs-lookup"><span data-stu-id="44900-112">The configuration specifies the location of the report server, the version of SQL Server Reporting Services installed on the report server, whether the data sources published to the report server are overwritten and so forth.</span></span> <span data-ttu-id="44900-113">Помимо использования конфигураций, имеющихся в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , можно создавать дополнительные конфигурации.</span><span class="sxs-lookup"><span data-stu-id="44900-113">In addition to using the configurations that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provides, you can create additional configurations.</span></span>  
  
## <a name="project-configurations"></a><span data-ttu-id="44900-114">Конфигурации проекта</span><span class="sxs-lookup"><span data-stu-id="44900-114">Project Configurations</span></span>  
 <span data-ttu-id="44900-115">Отчеты создаются до опубликования, что позволяет обеспечить публикацию на сервере отчетов только действительных определений отчета.</span><span class="sxs-lookup"><span data-stu-id="44900-115">Reports are built before they are published to ensure that only valid report definitions are published to the report server.</span></span> <span data-ttu-id="44900-116">Конфигурации проекта включают свойства для построения отчетов, например папку, в которой временно сохраняются отчеты о сборке и способах решения проблем сборки.</span><span class="sxs-lookup"><span data-stu-id="44900-116">Project configurations include properties for building reports, such as the folder in which to temporarily store the built reports, and how to handle build issues.</span></span> <span data-ttu-id="44900-117">Конфигурации также имеют свойства, используемые для обозначения местоположения и версии сервера отчетов, папок на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="44900-117">The configurations also have properties that you use to specify the location and version of the report server, the folders on the report server.</span></span>  
  
 <span data-ttu-id="44900-118">По умолчанию среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] предоставляет три конфигурации проекта: DebugLocal, Debug и Release.</span><span class="sxs-lookup"><span data-stu-id="44900-118">By default, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provides three project configurations: DebugLocal, Debug, and Release.</span></span> <span data-ttu-id="44900-119">Конфигурация по умолчанию — DebugLocal.</span><span class="sxs-lookup"><span data-stu-id="44900-119">The default configuration is DebugLocal.</span></span> <span data-ttu-id="44900-120">Как правило, конфигурация DebugLocal служит для просмотра отчетов в локальном окне просмотра, конфигурация Debug — для публикации отчетов на тестовом сервере, а конфигурация Release — для публикации отчетов на рабочем сервере.</span><span class="sxs-lookup"><span data-stu-id="44900-120">You typically use the DebugLocal configuration to view reports in a local preview window, the Debug configuration to publish reports to a test server, and the Release configuration to publish reports to a production server.</span></span> <span data-ttu-id="44900-121">Раскрывающийся список конфигураций решения на стандартной панели инструментов отображает активную конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="44900-121">The solution configurations drop-down list on the Standard toolbar shows the active configuration.</span></span> <span data-ttu-id="44900-122">Для использования другой конфигурации выберите ее из списка.</span><span class="sxs-lookup"><span data-stu-id="44900-122">To use a different configuration, select it from the list.</span></span>  
  
 <span data-ttu-id="44900-123">Среда создания отчетов может иметь несколько серверов отчетов и разные установленные версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="44900-123">Your reporting environment might have multiple report servers and different versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installed.</span></span> <span data-ttu-id="44900-124">Можно создать несколько конфигураций и использовать одну из них в зависимости от сценария развертывания.</span><span class="sxs-lookup"><span data-stu-id="44900-124">You can create multiple configurations and then use a different one depending the deployment scenario.</span></span> <span data-ttu-id="44900-125">Дополнительные сведения см. в статьях [Поддержка развертывания и версий в SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md) и [задание свойств развертывания &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md).</span><span class="sxs-lookup"><span data-stu-id="44900-125">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md) and [Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md).</span></span>  
  
## <a name="publishing-reports"></a><span data-ttu-id="44900-126">Публикация отчетов</span><span class="sxs-lookup"><span data-stu-id="44900-126">Publishing Reports</span></span>  
 <span data-ttu-id="44900-127">Можно опубликовать один отчет или проект «Сервер отчетов», содержащий несколько отчетов.</span><span class="sxs-lookup"><span data-stu-id="44900-127">You can publish a single report or a Report Server project that contains multiple reports.</span></span> <span data-ttu-id="44900-128">Инструкции по публикации отчетов см. в разделе [Публикация отчетов](../publish-reports.md).</span><span class="sxs-lookup"><span data-stu-id="44900-128">For instructions about publishing reports, see [Publish Reports](../publish-reports.md).</span></span>  
  
### <a name="publishing-a-single-report"></a><span data-ttu-id="44900-129">Публикация одного отчета</span><span class="sxs-lookup"><span data-stu-id="44900-129">Publishing a Single Report</span></span>  
 <span data-ttu-id="44900-130">Если не нужно публиковать все отчеты в проекте, то можно выбрать публикацию одного отчета.</span><span class="sxs-lookup"><span data-stu-id="44900-130">If you do not want to publish all reports in a project, you can chose to publish only a single report.</span></span> <span data-ttu-id="44900-131">Для этого выберите конфигурацию, в которой разворачивается отчет (например, конфигурацию Release), правой кнопкой мыши щелкните отчет и выберите пункт **Развернуть**.</span><span class="sxs-lookup"><span data-stu-id="44900-131">To do this, select a configuration that deploys the report (for example, the Release configuration), right-click the report, and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="44900-132">Если отчет использует общий источник данных, то необходимо также развернуть и его, иначе развернутый отчет не будет работать.</span><span class="sxs-lookup"><span data-stu-id="44900-132">If a report uses a shared data source, you need to also deploy the shared data source or the deployed report will not run.</span></span> <span data-ttu-id="44900-133">Щелкните правой кнопкой мыши общий источник данных и выберите пункт **Развернуть**.</span><span class="sxs-lookup"><span data-stu-id="44900-133">Right-click the shared data source and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="44900-134">Необходимо указать URL-адрес целевого сервера на сервере отчетов и, возможно, изменить папки по умолчанию, в которых буду разворачиваться отчеты и общие источники данных.</span><span class="sxs-lookup"><span data-stu-id="44900-134">The target server URL of the report server must be specified and you might want to change the default folders to which reports and shared data sources deploy.</span></span>  
  
### <a name="publishing-multiple-reports"></a><span data-ttu-id="44900-135">Публикация нескольких отчетов</span><span class="sxs-lookup"><span data-stu-id="44900-135">Publishing Multiple Reports</span></span>  
 <span data-ttu-id="44900-136">При публикации проекта «Сервер отчетов» публикуются все отчеты в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="44900-136">When you publish a Report Server project, you publish all reports in that project.</span></span> <span data-ttu-id="44900-137">Все отчеты разворачиваются с использованием одной конфигурации проекта: на одном сервере отчетов, в одной папке сервера и т. д.</span><span class="sxs-lookup"><span data-stu-id="44900-137">All reports are deployed using the same project configuration: to the same report server, the same folder on the server, and so on.</span></span> <span data-ttu-id="44900-138">Публикацию отчетов на разных серверах необходимо либо выполнять последовательно, либо включить в проект «Сервер отчетов» только необходимые отчеты.</span><span class="sxs-lookup"><span data-stu-id="44900-138">To publish reports to different servers, either publish them one by one or include only reports you want to in the Report Server project.</span></span> <span data-ttu-id="44900-139">Решение может включать несколько проектов сервера отчетов, а использование нескольких проектов поможет облегчить процесс управления развертыванием отчетов, так как дает возможность использовать разные конфигурации для развертывания разных проектов.</span><span class="sxs-lookup"><span data-stu-id="44900-139">A solution can include multiple Report Server projects, and using multiple project might make it easier to manage the deployment of reports because you can use a different configuration to deploy different projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44900-140">См. также:</span><span class="sxs-lookup"><span data-stu-id="44900-140">See Also</span></span>  
 <span data-ttu-id="44900-141">[Диалоговое окно "страницы свойств проекта"](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="44900-141">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="44900-142">[Управление содержимым сервера отчетов (службы Reporting Services в основном режиме)](../report-server/report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="44900-142">[Report Server Content Management &#40;SSRS Native Mode&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="44900-143">Обновление отчетов</span><span class="sxs-lookup"><span data-stu-id="44900-143">Upgrade Reports</span></span>](../install-windows/upgrade-reports.md)  
  
  