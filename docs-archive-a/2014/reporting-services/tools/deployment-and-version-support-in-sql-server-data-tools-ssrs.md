---
title: Развертывание и поддержка версий в SQL Server Data Tools (службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 36f5686d-7e40-4f31-be81-bd197ca33a02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 512f762d828f56ceadc8458a8666bfe6269f5bb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658081"
---
# <a name="deployment-and-version-support-in-sql-server-data-tools-ssrs"></a><span data-ttu-id="03523-102">Развертывание и поддержка версий в SQL Server Data Tools (SSRS)</span><span class="sxs-lookup"><span data-stu-id="03523-102">Deployment and Version Support in SQL Server Data Tools (SSRS)</span></span>
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] <span data-ttu-id="03523-103">поддерживает следующие сценарии:</span><span class="sxs-lookup"><span data-stu-id="03523-103">supports the following scenarios:</span></span>  
  
-   <span data-ttu-id="03523-104">Открытые определения отчетов (\*RDL) и проекты сервера отчетов (\*RPTPROJ).</span><span class="sxs-lookup"><span data-stu-id="03523-104">Open report definitions (\*.rdl) and report server projects (\*.rptproj).</span></span>  
  
-   <span data-ttu-id="03523-105">Создайте определения отчетов.</span><span class="sxs-lookup"><span data-stu-id="03523-105">Build report definitions.</span></span>  
  
-   <span data-ttu-id="03523-106">Просмотрите отчеты в конструкторе отчетов.</span><span class="sxs-lookup"><span data-stu-id="03523-106">Preview reports in Report Designer.</span></span>  
  
-   <span data-ttu-id="03523-107">Разверните отчеты на серверах отчетов.</span><span class="sxs-lookup"><span data-stu-id="03523-107">Deploy reports to report servers.</span></span>  
  
##  <a name="configuration-and-deployment-properties"></a><a name="bkmk_ConfigurationandDeploymentProperties"></a> <span data-ttu-id="03523-108">Свойства настройки и развертывания</span><span class="sxs-lookup"><span data-stu-id="03523-108">Configuration and Deployment Properties</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="03523-109">поддерживает конфигурации проекта.</span><span class="sxs-lookup"><span data-stu-id="03523-109">supports project configurations.</span></span> <span data-ttu-id="03523-110">Конфигурация проекта состоит из набора свойств, определяющего местоположения и поведения в том случае, когда проект создан в качестве шага просмотра или развертывания отчетов.</span><span class="sxs-lookup"><span data-stu-id="03523-110">A project configuration consists of a set of properties that specify locations and behaviors when a project is built either as a step in previewing or deploying reports.</span></span> <span data-ttu-id="03523-111">Дополнительные сведения о конфигурациях проекта см. в документации по Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03523-111">To learn more about project configurations, see the Visual Studio documentation.</span></span>  
  
 <span data-ttu-id="03523-112">Используйте конфигурации проектов, чтобы управлять обновлением определений отчетов до версий схем, совместимых с целевыми серверами отчетов.</span><span class="sxs-lookup"><span data-stu-id="03523-112">Use project configurations to control the upgrade of report definitions to schema versions compatible with target report servers.</span></span> <span data-ttu-id="03523-113">Конфигурация проекта включает такие свойства, как целевой сервер отчетов, папка, где процесс построения временно сохраняет определения отчетов для предварительного просмотра и развертывания, и уровни ошибок.</span><span class="sxs-lookup"><span data-stu-id="03523-113">The properties controlled by project configurations include the target report server, the folder where the build process temporarily stores report definitions for preview and deployment, and error levels.</span></span>  
  
 <span data-ttu-id="03523-114">Построение отчетов производится перед подготовкой к просмотру в конструкторе отчетов или развертыванием на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="03523-114">Reports are built before they are rendered as previews in Report Designer or deployed to the report server.</span></span>  
  
 <span data-ttu-id="03523-115">Задать свойства конфигурации можно в диалоговом окне [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Свойства проекта**среды**.</span><span class="sxs-lookup"><span data-stu-id="03523-115">You set the configuration properties in the [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] **Project Property** dialog box.</span></span>  
  
 <span data-ttu-id="03523-116">Свойства построения и развертывания включают:</span><span class="sxs-lookup"><span data-stu-id="03523-116">The build and deployment properties include:</span></span>  
  
-   <span data-ttu-id="03523-117">OutputPath — свойство сборки, показывающее путь к папке для хранения определения отчета, используемого при проверке сборки, развертывании и просмотре отчетов.</span><span class="sxs-lookup"><span data-stu-id="03523-117">OutputPath is a build property that identifies the path of folders to store the report definition used in build verification, deployment, and preview of reports.</span></span>  
  
-   <span data-ttu-id="03523-118">ErrorLevel — свойство сборки, отображающее серьезность проблем сборки, помечаемых как ошибки.</span><span class="sxs-lookup"><span data-stu-id="03523-118">ErrorLevel is a build property that identifies the severity of the build issues that are reported as errors.</span></span> <span data-ttu-id="03523-119">Проблемы, степень серьезности которых меньше значения ErrorLevel или равна ему, выводятся как ошибки. В противном случае они помечаются как предупреждения.</span><span class="sxs-lookup"><span data-stu-id="03523-119">Issues with severity levels less than or equal to the value of ErrorLevel are reported as errors; otherwise, the issues are reported as warnings.</span></span> <span data-ttu-id="03523-120">Дополнительные сведения см. в подразделе "Проверка отчета и уровни ошибок" раздела [Разработка отчетов с использованием конструктора отчетов (SSRS)](design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="03523-120">For more information, see The "Report Validation and Error Levels" section in [Design Reports with Report Designer &#40;SSRS&#41;](design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
-   <span data-ttu-id="03523-121">TargetServerVersion — это свойство развертывания, задающее ожидаемую версию служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], которая установлена на целевом сервере отчетов, указанном в свойстве TargetServerURL.</span><span class="sxs-lookup"><span data-stu-id="03523-121">TargetServerVersion is a deployment property that identifies the expected version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that is installed on the target report server specified in the TargetServerURL property.</span></span>  
  
 <span data-ttu-id="03523-122">Если указывается более ранняя версия служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в диалоговом окне **Свойства проекта**, отчеты не преобразуются автоматически в предыдущую версию.</span><span class="sxs-lookup"><span data-stu-id="03523-122">When you specify the earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in the **Project Property** dialog box, the reports are not reverted automatically to the earlier version.</span></span> <span data-ttu-id="03523-123">По сути дела, проект сервера отчетов может содержать отчеты из двух разных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03523-123">As such, a Report Server project can contain reports from the two different versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="03523-124">Когда развертывается проект сервера отчетов, все отчеты в проекте преобразуются в версию, указанную в TargetServerVersion.</span><span class="sxs-lookup"><span data-stu-id="03523-124">When the Report Server project is deployed, all reports in the project are converted to the version specified in TargetServerVersion.</span></span>  
  
 <span data-ttu-id="03523-125">К проекту может быть добавлено более одной конфигурации проекта. Разные конфигурации используются для разных сценариев, например для развертывания в разных версиях серверов отчетов.</span><span class="sxs-lookup"><span data-stu-id="03523-125">You can add more than one project configuration to a project; each one is used for a different scenario, such as deploying to different versions of report servers.</span></span> <span data-ttu-id="03523-126">Дополнительные сведения см. в разделах [Задание свойства развертывания (службы Reporting Services)](set-deployment-properties-reporting-services.md) и [Диалоговое окно страниц свойств проекта](project-property-pages-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="03523-126">For more information, see [Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) and [Project Property Pages Dialog Box](project-property-pages-dialog-box.md).</span></span>  
  
##  <a name="supported-versions"></a><a name="bkmk_SupportedVersions"></a> <span data-ttu-id="03523-127">Поддерживаемые версии</span><span class="sxs-lookup"><span data-stu-id="03523-127">Supported Versions</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="03523-128">, которая является 32-разрядной версией среды разработки проектов сервера отчетов, не предназначена для работы на компьютерах архитектуры [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]и не устанавливается на серверах с архитектурой [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03523-128">, the 32-bit development environment for Report Server projects, is not designed to run on [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-based computers and is not installed on [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-based servers.</span></span> <span data-ttu-id="03523-129">Однако имеется поддержка среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] для компьютеров с архитектурой x64.</span><span class="sxs-lookup"><span data-stu-id="03523-129">However, support for [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] is available for x64-based computers.</span></span>  
  
 <span data-ttu-id="03523-130">В приведенной ниже таблице описаны поддерживаемые версии для создания и публикации отчетов в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03523-130">The following table describes the supported versions for authoring and publishing reports in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03523-131">Схема не изменялась после [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03523-131">The schema has not changed since [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
|<span data-ttu-id="03523-132">Тип проекта или файла</span><span class="sxs-lookup"><span data-stu-id="03523-132">Project or File type</span></span>|<span data-ttu-id="03523-133">Версия</span><span class="sxs-lookup"><span data-stu-id="03523-133">Version</span></span>|<span data-ttu-id="03523-134">Разработка отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-134">Author Reports</span></span>|<span data-ttu-id="03523-135">Публикация отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-135">Publish Reports</span></span>|<span data-ttu-id="03523-136">Примечания</span><span class="sxs-lookup"><span data-stu-id="03523-136">Notes</span></span>|  
|--------------------------|-------------|--------------------|---------------------|-----------|  
|<span data-ttu-id="03523-137">Проект сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-137">Report Server Project</span></span><br /><br /> <span data-ttu-id="03523-138">или диспетчер конфигурации служб</span><span class="sxs-lookup"><span data-stu-id="03523-138">or</span></span><br /><br /> <span data-ttu-id="03523-139">Проект мастера сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-139">Report Server Wizard Project</span></span>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|<span data-ttu-id="03523-140">Схема языка определения отчетов версии 2014</span><span class="sxs-lookup"><span data-stu-id="03523-140">2014 RDL schema</span></span>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="03523-141">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03523-141">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]</span></span>||  
|<span data-ttu-id="03523-142">Проект сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-142">Report Server Project</span></span><br /><br /> <span data-ttu-id="03523-143">,</span><span class="sxs-lookup"><span data-stu-id="03523-143">or</span></span><br /><br /> <span data-ttu-id="03523-144">Проект мастера сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-144">Report Server Wizard Project</span></span>|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|<span data-ttu-id="03523-145">Схема языка определения отчетов версии 2012</span><span class="sxs-lookup"><span data-stu-id="03523-145">2012 RDL schema</span></span>|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="03523-146">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03523-146">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]</span></span>||  
|<span data-ttu-id="03523-147">Проект сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-147">Report Server Project</span></span><br /><br /> <span data-ttu-id="03523-148">,</span><span class="sxs-lookup"><span data-stu-id="03523-148">or</span></span><br /><br /> <span data-ttu-id="03523-149">Проект мастера сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-149">Report Server Wizard Project</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|<span data-ttu-id="03523-150">Схема языка определения отчетов версии 2008 R2</span><span class="sxs-lookup"><span data-stu-id="03523-150">2008 R2 RDL schema</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="03523-151">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03523-151">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]</span></span>||  
|<span data-ttu-id="03523-152">Проект сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-152">Report Server Project</span></span><br /><br /> <span data-ttu-id="03523-153">,</span><span class="sxs-lookup"><span data-stu-id="03523-153">or</span></span><br /><br /> <span data-ttu-id="03523-154">Проект мастера сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-154">Report Server Wizard Project</span></span>|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="03523-155">Схема языка определения отчетов версии 2008</span><span class="sxs-lookup"><span data-stu-id="03523-155">2008 RDL schema</span></span>|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="03523-156">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]только сервер отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-156">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server only</span></span>|<span data-ttu-id="03523-157">Производит локальное обновление схем языка определения отчетов с версий 2003 и 2005 до версии 2008.</span><span class="sxs-lookup"><span data-stu-id="03523-157">Upgrades 2003 RDL and 2005 RDL to the 2008 RDL schema locally.</span></span>|  
|<span data-ttu-id="03523-158">Проект сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-158">Report Server Project</span></span><br /><br /> <span data-ttu-id="03523-159">,</span><span class="sxs-lookup"><span data-stu-id="03523-159">or</span></span><br /><br /> <span data-ttu-id="03523-160">Проект мастера сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-160">Report Server Wizard Project</span></span>|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="03523-161">Схема языка определения отчетов версии 2005</span><span class="sxs-lookup"><span data-stu-id="03523-161">2005 RDL schema</span></span>|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="03523-162">или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сервер отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-162">or [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server</span></span>||  
|<span data-ttu-id="03523-163">Проект сервера отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-163">Report Server Project</span></span>|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|<span data-ttu-id="03523-164">Схема языка определения отчетов версии 2003</span><span class="sxs-lookup"><span data-stu-id="03523-164">2003 RDL schema</span></span>|<span data-ttu-id="03523-165">Не поддерживается</span><span class="sxs-lookup"><span data-stu-id="03523-165">Not supported</span></span>||  
|<span data-ttu-id="03523-166">Конструктор отчетов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] RDLC</span><span class="sxs-lookup"><span data-stu-id="03523-166">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] RDLC Report Designer</span></span>|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <span data-ttu-id="03523-167">2005</span><span class="sxs-lookup"><span data-stu-id="03523-167">2005</span></span><br /><br /> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <span data-ttu-id="03523-168">2008</span><span class="sxs-lookup"><span data-stu-id="03523-168">2008</span></span>|<span data-ttu-id="03523-169">Схема языка определения отчетов версии 2005</span><span class="sxs-lookup"><span data-stu-id="03523-169">2005 RDL schema</span></span>|<span data-ttu-id="03523-170">Не поддерживается</span><span class="sxs-lookup"><span data-stu-id="03523-170">Not supported</span></span>|<span data-ttu-id="03523-171">Схема языка определения отчетов версии 2008 не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="03523-171">Does not support 2008 RDL schema.</span></span>|  
|<span data-ttu-id="03523-172">Элементы управления [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Viewer</span><span class="sxs-lookup"><span data-stu-id="03523-172">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Viewer controls</span></span>|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <span data-ttu-id="03523-173">2005</span><span class="sxs-lookup"><span data-stu-id="03523-173">2005</span></span><br /><br /> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <span data-ttu-id="03523-174">2008</span><span class="sxs-lookup"><span data-stu-id="03523-174">2008</span></span>|<span data-ttu-id="03523-175">Язык определения отчетов версии 2008 не поддерживается в локальном режиме</span><span class="sxs-lookup"><span data-stu-id="03523-175">2008 RDL not supported in local mode</span></span>|<span data-ttu-id="03523-176">Недоступно</span><span class="sxs-lookup"><span data-stu-id="03523-176">N/A</span></span>|<span data-ttu-id="03523-177">Может просматривать отчеты на языке определения отчетов 2008 на [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сервере отчетов в режиме сервера.</span><span class="sxs-lookup"><span data-stu-id="03523-177">Can view 2008 RDL reports on [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server in server mode.</span></span>|  
  
 <span data-ttu-id="03523-178">Дополнительные сведения об открытии отчетов в предыдущей версии схемы определения отчета см. в разделе [Обновление отчетов](../install-windows/upgrade-reports.md).</span><span class="sxs-lookup"><span data-stu-id="03523-178">For more information about opening reports in a previous version of the report definition schema, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span> <span data-ttu-id="03523-179">Дополнительные сведения о конкретных схемах определений отчетов см. в разделе [Спецификация по языку определения отчетов](https://go.microsoft.com/fwlink/?linkid=116865).</span><span class="sxs-lookup"><span data-stu-id="03523-179">For more information about specific report definition schemas, see [Report Definition Language Specification](https://go.microsoft.com/fwlink/?linkid=116865).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03523-180">См. также:</span><span class="sxs-lookup"><span data-stu-id="03523-180">See Also</span></span>  
 [<span data-ttu-id="03523-181">Публикация источников данных и отчетов</span><span class="sxs-lookup"><span data-stu-id="03523-181">Publishing Data Sources and Reports</span></span>](../reports/publishing-data-sources-and-reports.md)  
  
  