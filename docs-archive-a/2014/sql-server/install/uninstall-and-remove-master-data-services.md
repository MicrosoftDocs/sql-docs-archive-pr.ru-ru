---
title: Установка и удаление служб Master Data Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: efc2431c-588b-42e7-b23b-c875145a33f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 433de21538c4ece694118516d777c48ec7834cea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659152"
---
# <a name="uninstall-and-remove-master-data-services"></a><span data-ttu-id="6f537-102">Удаление служб Master Data Services</span><span class="sxs-lookup"><span data-stu-id="6f537-102">Uninstall and Remove Master Data Services</span></span>
  <span data-ttu-id="6f537-103">Чтобы удалить компонент [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните действия из раздела [Удаление существующего экземпляра SQL Server (программа установки)](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) и укажите [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в качестве компонента для удаления на странице **Выбор компонентов**.</span><span class="sxs-lookup"><span data-stu-id="6f537-103">To uninstall the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] feature from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], follow the steps in [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) and specify [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] as a feature to remove on the **Select Features** page.</span></span> <span data-ttu-id="6f537-104">В процессе удаления удаляются файлы и папки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , а также удаляется [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="6f537-104">The uninstall process removes [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] folders and files, and uninstalls [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] from the local computer.</span></span>  
  
 <span data-ttu-id="6f537-105">Чтобы избежать потери данных или нарушения работы других компьютеров в системе, некоторые компоненты при удалении не удаляются или не изменяются.</span><span class="sxs-lookup"><span data-stu-id="6f537-105">To prevent data loss and avoid affecting other computers in the system, some items are not removed or changed by the uninstall process.</span></span> <span data-ttu-id="6f537-106">Чтобы определить, следует ли оставить или удалить элементы, просмотрите следующую таблицу.</span><span class="sxs-lookup"><span data-stu-id="6f537-106">Review the following table to determine whether to leave or remove items.</span></span>  
  
|<span data-ttu-id="6f537-107">Элемент</span><span class="sxs-lookup"><span data-stu-id="6f537-107">Item</span></span>|<span data-ttu-id="6f537-108">Description</span><span class="sxs-lookup"><span data-stu-id="6f537-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6f537-109">Файлы и папки</span><span class="sxs-lookup"><span data-stu-id="6f537-109">Folders and files</span></span>|<span data-ttu-id="6f537-110">В процессе удаления удаляется большинство файлов и папок, расположенных в пути установки.</span><span class="sxs-lookup"><span data-stu-id="6f537-110">The uninstall process removes most folders and files from the installation path.</span></span><br /><br /> <span data-ttu-id="6f537-111">В процессе удаления в пути установки не удаляются папки Master Data Services и MDSTempDir.</span><span class="sxs-lookup"><span data-stu-id="6f537-111">The uninstall process does not remove the Master Data Services and MDSTempDir folders from the installation location.</span></span> <span data-ttu-id="6f537-112">После завершения процесса удаления эти папки можно удалить из файловой системы вручную.</span><span class="sxs-lookup"><span data-stu-id="6f537-112">After the uninstall process is complete, you can manually delete these folders from the file system.</span></span> <span data-ttu-id="6f537-113">Дополнительные сведения см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](../../master-data-services/folder-and-file-permissions-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6f537-113">For more information, see [Folder and File Permissions &#40;Master Data Services&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md).</span></span>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="6f537-114">сборки</span><span class="sxs-lookup"><span data-stu-id="6f537-114">assemblies</span></span>|<span data-ttu-id="6f537-115">Процесс удаления удаляет сборки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] из глобального кэша сборок (GAC).</span><span class="sxs-lookup"><span data-stu-id="6f537-115">The uninstall process removes [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] assemblies from the Global Assembly Cache (GAC).</span></span>|  
|<span data-ttu-id="6f537-116">База данных</span><span class="sxs-lookup"><span data-stu-id="6f537-116">Database</span></span>|<span data-ttu-id="6f537-117">Процесс удаления не затрагивает базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6f537-117">The uninstall process does not affect the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="6f537-118">База данных на экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] остается неизменной, поэтому все данные, включая основные данные, объекты моделей, разрешения пользователей и групп, бизнес-правила и т. п., сохраняются.</span><span class="sxs-lookup"><span data-stu-id="6f537-118">The database remains intact in the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] so that you do not lose any data, including master data, model objects, user and group permissions, business rules, and so on.</span></span><br /><br /> <span data-ttu-id="6f537-119">Если база данных больше не нужна и не предвидится ее соединение с другим веб-сайтом или приложением [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в будущем, можно удалить базу данных на экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором она размещена.</span><span class="sxs-lookup"><span data-stu-id="6f537-119">If you do not need the database, and do not anticipate connecting it to another [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web site or application in the future, you might want to delete the database from the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] that hosts it.</span></span> <span data-ttu-id="6f537-120">Дополнительные сведения см. в разделе [Удаление базы данных](../../relational-databases/databases/delete-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="6f537-120">For more information, see [Delete a Database](../../relational-databases/databases/delete-a-database.md).</span></span>|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="6f537-121">и Web.config</span><span class="sxs-lookup"><span data-stu-id="6f537-121">and Web.config</span></span>|<span data-ttu-id="6f537-122">В процессе удаления в файловой системе удаляется папка WebApplication.</span><span class="sxs-lookup"><span data-stu-id="6f537-122">The uninstall process removes the WebApplication folder from the file system.</span></span> <span data-ttu-id="6f537-123">Папка WebApplication содержит файлы веб-приложения и файл Web.config, используемые [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f537-123">The WebApplication folder contains the web application files and Web.config file for [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span><br /><br /> <span data-ttu-id="6f537-124">**\*\* Важно! \*\*** Перед удалением можно скопировать файл Web.config в другое расположение, чтобы сохранить любые пользовательские настройки или другие содержащиеся в файле сведения.</span><span class="sxs-lookup"><span data-stu-id="6f537-124">**\*\* Important \*\*** Before you uninstall, you might want to copy the Web.config file to another location to preserve any custom settings or other information in the file.</span></span> <span data-ttu-id="6f537-125">После завершения процесса удаления восстановить файл Web.config невозможно.</span><span class="sxs-lookup"><span data-stu-id="6f537-125">After the uninstall process completes, the Web.config file is not recoverable.</span></span>|  
|<span data-ttu-id="6f537-126">Элементы служб Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="6f537-126">Internet Information Services (IIS) items</span></span>|<span data-ttu-id="6f537-127">Процесс удаления не затрагивает пулы приложений, веб-сайты и веб-приложения в IIS на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="6f537-127">The uninstall process does not affect any application pools, web sites, or web applications in IIS on the local computer.</span></span> <span data-ttu-id="6f537-128">Так как процесс удаления удаляет папку WebApplication и файл Web.config для [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], любые веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , которым требуются эти файлы, прекратят работу.</span><span class="sxs-lookup"><span data-stu-id="6f537-128">Because the uninstall process removes the WebApplication folder and Web.config file for [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], any [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web applications that require those files will no longer serve content.</span></span> <span data-ttu-id="6f537-129">Если пользователь попытается обратиться к такому веб-приложению, он получит сообщение об ошибке HTTP 500.19 — внутренняя ошибка сервера: "Запрашиваемая страница не доступна из-за неверной конфигурации данных для этой страницы".</span><span class="sxs-lookup"><span data-stu-id="6f537-129">If users try to access the web application, they will receive HTTP Error 500.19-Internal Server Error: "The requested page cannot be accessed because the related configuration data for the page is invalid."</span></span><br /><br /> <span data-ttu-id="6f537-130">Если веб-сайт или приложение больше не нужны, а сайт или приложение предоставляются пулом приложений, для их удаления можно воспользоваться средствами IIS.</span><span class="sxs-lookup"><span data-stu-id="6f537-130">If you no longer require the web site or application, and the application pool serving your site or application, you can use an IIS tool to delete them.</span></span> <span data-ttu-id="6f537-131">Дополнительные сведения см. в [Руководстве по использованию IIS 7](https://go.microsoft.com/fwlink/?LinkId=184885) на сайте [!INCLUDE[msCoName](../../includes/msconame-md.md)] TechNet.</span><span class="sxs-lookup"><span data-stu-id="6f537-131">For more information, see [IIS 7 Operations Guide](https://go.microsoft.com/fwlink/?LinkId=184885) on [!INCLUDE[msCoName](../../includes/msconame-md.md)] TechNet.</span></span>|  
|<span data-ttu-id="6f537-132">Группа**MDS_ServiceAccounts**</span><span class="sxs-lookup"><span data-stu-id="6f537-132">**MDS_ServiceAccounts** group</span></span>|<span data-ttu-id="6f537-133">После завершения процесса удаления группа Windows **MDS_ServiceAccounts** и любые добавленные в нее учетные записи служб сохраняются.</span><span class="sxs-lookup"><span data-stu-id="6f537-133">After the uninstall process is complete, the **MDS_ServiceAccounts** Windows group and any service accounts added to the group remain.</span></span> <span data-ttu-id="6f537-134">Если эта группа и учетные записи больше не нужны, можно удалить их.</span><span class="sxs-lookup"><span data-stu-id="6f537-134">If you no longer need the group and accounts, you can remove them.</span></span>|  
|<span data-ttu-id="6f537-135">Реестр</span><span class="sxs-lookup"><span data-stu-id="6f537-135">Registry</span></span>|<span data-ttu-id="6f537-136">В процессе удаления из реестра Windows удаляются все разделы, связанные со службами [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6f537-136">The uninstall process removes all [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] registry keys from the Windows registry.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f537-137">См. также:</span><span class="sxs-lookup"><span data-stu-id="6f537-137">See Also</span></span>  
 [<span data-ttu-id="6f537-138">Установка служб Master Data Services</span><span class="sxs-lookup"><span data-stu-id="6f537-138">Install Master Data Services</span></span>](../../master-data-services/install-windows/install-master-data-services.md)  
  
  