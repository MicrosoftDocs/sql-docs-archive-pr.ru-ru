---
title: Установка обновлений из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3ced6cd72bfc972743d0f9d8c7c2a9ce57dfdd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655907"
---
# <a name="installing-updates-from-the-command-prompt"></a><span data-ttu-id="867dc-102">Установка обновлений из командной строки</span><span class="sxs-lookup"><span data-stu-id="867dc-102">Installing Updates from the Command Prompt</span></span>
  <span data-ttu-id="867dc-103">Проверьте скрипты установки и доработайте их в соответствии с задачами организации.</span><span class="sxs-lookup"><span data-stu-id="867dc-103">Test and modify installation scripts to meet the needs of your organization.</span></span>  
  
## <a name="sample-syntax-for-installation"></a><span data-ttu-id="867dc-104">Образец синтаксиса для программы установки</span><span class="sxs-lookup"><span data-stu-id="867dc-104">Sample Syntax for Installation</span></span>  
 <span data-ttu-id="867dc-105">Имя пакета может быть разным и включает обозначение языка, выпуска и архитектуры процессора.</span><span class="sxs-lookup"><span data-stu-id="867dc-105">The name of the update package can vary and may include a language, edition, and processor component.</span></span> <span data-ttu-id="867dc-106">Применение обновления из командной строки. Замените <имя_пакета> именем конкретного пакета обновления:</span><span class="sxs-lookup"><span data-stu-id="867dc-106">Apply an update at a command prompt, replacing <package_name> with the name of your update package:</span></span>  
  
-   <span data-ttu-id="867dc-107">Обновление одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов, таких как [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: Можно указать экземпляр с помощью параметра InstanceName или параметра InstanceID.</span><span class="sxs-lookup"><span data-stu-id="867dc-107">Update a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and all shared components, like [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and Management Tools: You can specify the instance either by using the InstanceName parameter or the InstanceID parameter.</span></span> <span data-ttu-id="867dc-108">Чтобы обновить подготовленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо указать параметр InstanceID<PACKAGE_NAME # C1.exe/QS/IAcceptSQLServerLicenseTerms/Action = Patch/instanceName = myInstance или <PACKAGE_NAME # C3.exe/QS/IAcceptSQLServerLicenseTerms/Action = Patch/InstanceId = \<Instance ID> .</span><span class="sxs-lookup"><span data-stu-id="867dc-108">To update a prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must specify the InstanceID parameter<package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance  or <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceID=\<Instance ID>.</span></span>  
  
-   <span data-ttu-id="867dc-109">Программа установки может интегрировать последние обновления продукта в основную установку продукта, чтобы он и применимые обновления устанавливались одновременно.</span><span class="sxs-lookup"><span data-stu-id="867dc-109">Setup can integrate the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span> <span data-ttu-id="867dc-110">Вы можете подготовить установку экземпляра ядра СУБД для включения обновления продукта: setup.exe/q/IAcceptSQLServerLicenseTerms/ACTION = PrepareImage/UpdateEnabled = true/UpdateEnabled = true/UpdateSource = \<path where the update is downloaded> /InstanceId = \<Instance ID> /Features = SQLEngine.</span><span class="sxs-lookup"><span data-stu-id="867dc-110">You can prepare an installation of database engine instance to include product update: setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=PrepareImage /UpdateEnabled=True /UpdateEnabled=True /UpdateSource=\<path where the update is downloaded> /INSTANCEID=\<Instance ID> /FEATURES=SQLEngine.</span></span>  
  
-   <span data-ttu-id="867dc-111">Обновление только общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], таких как [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: <имя_пакета>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch</span><span class="sxs-lookup"><span data-stu-id="867dc-111">Update [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared components only, like [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and Management Tools: <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch</span></span>  
  
-   <span data-ttu-id="867dc-112">Обновление всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере и всех общих компонентов, таких как [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: <имя_пакета>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances.</span><span class="sxs-lookup"><span data-stu-id="867dc-112">Update all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer and all shared components, like [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and Management Tools: <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances.</span></span>  
  
 <span data-ttu-id="867dc-113">Удаление обновления из командной строки. Замените <имя_пакета> именем конкретного пакета обновления.</span><span class="sxs-lookup"><span data-stu-id="867dc-113">Remove an update from the command prompt replacing <package_name> with the name of your update package:</span></span>  
  
-   <span data-ttu-id="867dc-114">Удаление обновления из одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов, таких как [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: <имя_пакета>.exe /qs /Action=RemovePatch /InstanceName=MyInstance.</span><span class="sxs-lookup"><span data-stu-id="867dc-114">Remove an update from a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and all shared components, like [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and Management Tools: <package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance.</span></span>  
  
-   <span data-ttu-id="867dc-115">Удаление обновления только из общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], таких как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: <имя_пакета>.exe /qs /Action=RemovePatch</span><span class="sxs-lookup"><span data-stu-id="867dc-115">Remove an update from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared components only, like [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and Management Tools: <package_name>.exe /qs /Action=RemovePatch</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="867dc-116">Установщик обновлений поддерживает версию общих компонентов такой же или более поздней, чем версия экземпляра, на самом высоком уровне.</span><span class="sxs-lookup"><span data-stu-id="867dc-116">The update installer ensures that the shared components are always at or above the version of the instance at the highest level.</span></span>  
  
## <a name="supported-command-prompt-parameters"></a><span data-ttu-id="867dc-117">Поддерживаемые параметры командной строки</span><span class="sxs-lookup"><span data-stu-id="867dc-117">Supported Command Prompt Parameters</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="867dc-118">При возможности указывайте учетные данные безопасности в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="867dc-118">When possible, supply security credentials at run time.</span></span> <span data-ttu-id="867dc-119">Если нужно хранить учетные данные в файле скрипта, для этого файла необходимо обеспечить защиту, чтобы исключить несанкционированный доступ.</span><span class="sxs-lookup"><span data-stu-id="867dc-119">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
|<span data-ttu-id="867dc-120">Параметр</span><span class="sxs-lookup"><span data-stu-id="867dc-120">Switch</span></span>|<span data-ttu-id="867dc-121">Описание</span><span class="sxs-lookup"><span data-stu-id="867dc-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="867dc-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="867dc-122">**/?**</span></span>|<span data-ttu-id="867dc-123">Отображает справку командной строки для автоматической установки</span><span class="sxs-lookup"><span data-stu-id="867dc-123">Displays unattended installation command prompt help</span></span>|  
|<span data-ttu-id="867dc-124">**/action=Patch или /action=RemovePatch**</span><span class="sxs-lookup"><span data-stu-id="867dc-124">**/action=Patch or /action=RemovePatch**</span></span>|<span data-ttu-id="867dc-125">Задает действие установки: Patch или RemovePatch.</span><span class="sxs-lookup"><span data-stu-id="867dc-125">Specifies the installation action: Patch or RemovePatch.</span></span>|  
|<span data-ttu-id="867dc-126">**/allinstances**</span><span class="sxs-lookup"><span data-stu-id="867dc-126">**/allinstances**</span></span>|<span data-ttu-id="867dc-127">Устанавливает обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.</span><span class="sxs-lookup"><span data-stu-id="867dc-127">Applies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] update to all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and to all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared, instance-unaware components.</span></span>|  
|<span data-ttu-id="867dc-128">**/instanceName = instanceName** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="867dc-128">**/instancename=InstanceName** <sup>1</sup></span></span>|<span data-ttu-id="867dc-129">Устанавливает обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем InstanceName и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.</span><span class="sxs-lookup"><span data-stu-id="867dc-129">Applies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] update to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named InstanceName, and to all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared, instance-unaware components.</span></span>|  
|<span data-ttu-id="867dc-130">**/InstanceID=Inst1**</span><span class="sxs-lookup"><span data-stu-id="867dc-130">**/InstanceID=Inst1**</span></span>|<span data-ttu-id="867dc-131">Применяет обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем «Inst1» и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.</span><span class="sxs-lookup"><span data-stu-id="867dc-131">Applies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] update to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Inst1, and to all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared, instance-unaware components.</span></span>|  
|<span data-ttu-id="867dc-132">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="867dc-132">**/quiet**</span></span>|<span data-ttu-id="867dc-133">Запускает программу установки обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в автоматическом режиме.</span><span class="sxs-lookup"><span data-stu-id="867dc-133">Runs the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] update Setup in unattended mode.</span></span>|  
|<span data-ttu-id="867dc-134">**/qs**</span><span class="sxs-lookup"><span data-stu-id="867dc-134">**/qs**</span></span>|<span data-ttu-id="867dc-135">Отображается только диалоговое окно выполнения.</span><span class="sxs-lookup"><span data-stu-id="867dc-135">Displays only the progress UI dialog.</span></span>|  
|<span data-ttu-id="867dc-136">**/UpdateEnabled**</span><span class="sxs-lookup"><span data-stu-id="867dc-136">**/UpdateEnabled**</span></span>|<span data-ttu-id="867dc-137">Задает, должна ли программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаруживать и включать обновления продукта.</span><span class="sxs-lookup"><span data-stu-id="867dc-137">Specifies whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup should discover and include product updates.</span></span> <span data-ttu-id="867dc-138">Допустимые значения — True и False либо 1 и 0.</span><span class="sxs-lookup"><span data-stu-id="867dc-138">The valid values are True and False or 1 and 0.</span></span> <span data-ttu-id="867dc-139">По умолчанию программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет включать найденные обновления.</span><span class="sxs-lookup"><span data-stu-id="867dc-139">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup will include updates that are found.</span></span>|  
|<span data-ttu-id="867dc-140">**/IAcceptSQLServerLicenseTerms**</span><span class="sxs-lookup"><span data-stu-id="867dc-140">**/IAcceptSQLServerLicenseTerms**</span></span>|<span data-ttu-id="867dc-141">Требуется только в том случае, если для автоматической установки указан параметр /Q или /QS.</span><span class="sxs-lookup"><span data-stu-id="867dc-141">Required only when the /Q or /QS parameter is specified for unattended installations.</span></span>|  
  
 <span data-ttu-id="867dc-142"><sup>1</sup> этот параметр нельзя указать, чтобы применить обновление к подготовленному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="867dc-142"><sup>1</sup> You cannot specify this parameter to apply an update to a prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="867dc-143">Вместо этого необходимо указать параметр /instanceID.</span><span class="sxs-lookup"><span data-stu-id="867dc-143">You must specify the /instanceID parameter instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="867dc-144">См. также:</span><span class="sxs-lookup"><span data-stu-id="867dc-144">See Also</span></span>  
 [<span data-ttu-id="867dc-145">Общие сведения об обслуживании установки SQL Server</span><span class="sxs-lookup"><span data-stu-id="867dc-145">Overview of SQL Server Servicing Installation</span></span>](../../sql-server/install/overview-of-sql-server-servicing-installation.md)  
  
  