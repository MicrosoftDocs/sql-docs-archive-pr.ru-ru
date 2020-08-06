---
title: Управление службами компонента Database Engine | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, accessing
- Database Engine [SQL Server], services
- managing services [SQL Server], about service management
- services [SQL Server]
- SQL Server Agent service, managing
- SQL Server services, about SQL Server service
- MSSQLServer
- server configuration [SQL Server]
- managing services [SQL Server]
- SQL Server Agent service
- services [SQL Server], managing
- administering SQL Server, services
- SQL Server services
ms.assetid: aa732e43-53ba-4eea-bb9b-089da0766fc1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c18338493777d14c5e6fe28cb38bd71aaffd5da3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728697"
---
# <a name="manage-the-database-engine-services"></a><span data-ttu-id="afbc3-102">Управление службами компонента Database Engine</span><span class="sxs-lookup"><span data-stu-id="afbc3-102">Manage the Database Engine Services</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="afbc3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается в операционной системе в качестве службы.</span><span class="sxs-lookup"><span data-stu-id="afbc3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on the operating systems as a service.</span></span> <span data-ttu-id="afbc3-104">Служба — это особый вид приложения, которое выполняется в системе в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="afbc3-104">A service is a type of application that runs in the system background.</span></span> <span data-ttu-id="afbc3-105">Службы обычно обеспечивают базовые функции операционной системы, например: ведение журнала событий, доступ к файлам или веб-страницам.</span><span class="sxs-lookup"><span data-stu-id="afbc3-105">Services usually provide core operating system features, such as Web serving, event logging, or file serving.</span></span> <span data-ttu-id="afbc3-106">Службы могут выполняться без отображения своего пользовательского интерфейса на рабочем столе компьютера.</span><span class="sxs-lookup"><span data-stu-id="afbc3-106">Services can run without showing a user interface on the computer desktop.</span></span> <span data-ttu-id="afbc3-107">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и некоторые другие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняются как службы</span><span class="sxs-lookup"><span data-stu-id="afbc3-107">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and several other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components run as services.</span></span> <span data-ttu-id="afbc3-108">и обычно запускаются при запуске операционной системы.</span><span class="sxs-lookup"><span data-stu-id="afbc3-108">These services typically are started when the operating system starts.</span></span> <span data-ttu-id="afbc3-109">Некоторые службы по умолчанию не запускаются, это зависит от указанных при установке параметров.</span><span class="sxs-lookup"><span data-stu-id="afbc3-109">This depends on what is specified during setup; some services are not started by default.</span></span> <span data-ttu-id="afbc3-110">В этом разделе описывается управление различными службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="afbc3-110">This section describes the management of the various [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span> <span data-ttu-id="afbc3-111">Прежде чем входить в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо уметь запускать, останавливать, приостанавливать и возобновлять, а также перезапускать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="afbc3-111">Before you log in to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you need to know how to start, stop, pause, resume, and restart an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="afbc3-112">После входа можно выполнять различные задачи: администрировать сервер или выполнять запросы к базе данных.</span><span class="sxs-lookup"><span data-stu-id="afbc3-112">After you are logged in, you can perform tasks such as administering the server or querying a database.</span></span>  
  
## <a name="using-the-sql-server-service"></a><span data-ttu-id="afbc3-113">Использование службы SQL Server</span><span class="sxs-lookup"><span data-stu-id="afbc3-113">Using the SQL Server Service</span></span>  
 <span data-ttu-id="afbc3-114">При запуске экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]запускается служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="afbc3-114">When you start an instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], you are starting the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="afbc3-115">После того как будет запущена служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пользователи смогут устанавливать новые соединения с сервером.</span><span class="sxs-lookup"><span data-stu-id="afbc3-115">After you start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service, users can establish new connections to the server.</span></span> <span data-ttu-id="afbc3-116">Служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может запускаться и останавливаться как любая служба, локально или удаленно.</span><span class="sxs-lookup"><span data-stu-id="afbc3-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service can be started and stopped as a service, either locally or remotely.</span></span> <span data-ttu-id="afbc3-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Служба называется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER), если это экземпляр по умолчанию, или MSSQL $, если это *\<instancename>* именованный экземпляр.</span><span class="sxs-lookup"><span data-stu-id="afbc3-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is referred to as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) if it is the default instance, or MSSQL$*\<instancename>* if it is a named instance.</span></span>  
  
## <a name="using-sql-server-configuration-manager"></a><span data-ttu-id="afbc3-118">Использование диспетчера конфигурации SQL Server</span><span class="sxs-lookup"><span data-stu-id="afbc3-118">Using SQL Server Configuration Manager</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="afbc3-119">позволяет останавливать, запускать и приостанавливать различные службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="afbc3-119">Configuration Manager allows you to stop, start, or pause various [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="afbc3-120">Диспетчер конфигурации не может управлять службами [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="afbc3-120">Configuration Manager cannot manage [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] services.</span></span>  
  
 <span data-ttu-id="afbc3-121">Диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать для просмотра свойств выбранной службы.</span><span class="sxs-lookup"><span data-stu-id="afbc3-121">You can also use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to view the properties of the selected service.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="afbc3-122">Диспетчер конфигурации является оснасткой консоли управления [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MMC).</span><span class="sxs-lookup"><span data-stu-id="afbc3-122">Configuration Manager is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC) snap-in.</span></span> <span data-ttu-id="afbc3-123">Дополнительные сведения о консоли MMC и работе оснастки см. в справке по Windows.</span><span class="sxs-lookup"><span data-stu-id="afbc3-123">For more information about MMC and how a snap-in works, see Windows Help.</span></span>  
  
 <span data-ttu-id="afbc3-124">**Запуск диспетчера конфигурации SQL Server**</span><span class="sxs-lookup"><span data-stu-id="afbc3-124">**To access SQL Server Configuration Manager**</span></span>  
  
-   <span data-ttu-id="afbc3-125">В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="afbc3-125">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
 <span data-ttu-id="afbc3-126">**Доступ к диспетчеру конфигурации SQL Server с помощью Windows 8**</span><span class="sxs-lookup"><span data-stu-id="afbc3-126">**To access SQL Server Configuration Manager Using Windows 8**</span></span>  
  
 <span data-ttu-id="afbc3-127">Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления [!INCLUDE[msCoName](../../includes/msconame-md.md)] , а не изолированной программой, при работе в Windows 8.0 диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.</span><span class="sxs-lookup"><span data-stu-id="afbc3-127">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager not does not appear as an application when running Windows 8.0.</span></span> <span data-ttu-id="afbc3-128">Чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите в чудо-кнопке **Поиск** в области **Приложения**значение **SQLServerManager12.msc** (для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]), **SQLServerManager11.msc** (для [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) или **SQLServerManager10.msc** (для[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) и нажмите клавишу **ВВОД**.</span><span class="sxs-lookup"><span data-stu-id="afbc3-128">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager12.msc** (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]), **SQLServerManager11.msc** (for [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), or **SQLServerManager10.msc** for ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]), and then press **Enter**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afbc3-129">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="afbc3-129">In this Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="afbc3-130">Требования безопасности к службам управления</span><span class="sxs-lookup"><span data-stu-id="afbc3-130">Security Requirements for Managing Services</span></span>](security-requirements-for-managing-services.md)|[<span data-ttu-id="afbc3-131">Отключение автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)</span><span class="sxs-lookup"><span data-stu-id="afbc3-131">Prevent Automatic Startup of an Instance of SQL Server &#40;SQL Server Configuration Manager&#41;</span></span>](scm-services-prevent-automatic-startup-of-an-instance.md)|  
|[<span data-ttu-id="afbc3-132">Настройка учетных записей службы Windows и разрешений</span><span class="sxs-lookup"><span data-stu-id="afbc3-132">Configure Windows Service Accounts and Permissions</span></span>](configure-windows-service-accounts-and-permissions.md)|[<span data-ttu-id="afbc3-133">Изменение стартовой учетной записи службы для SQL Server (диспетчер конфигурации SQL Server)</span><span class="sxs-lookup"><span data-stu-id="afbc3-133">Change the Service Startup Account for SQL Server &#40;SQL Server Configuration Manager&#41;</span></span>](scm-services-change-the-service-startup-account.md)|  
|[<span data-ttu-id="afbc3-134">Запуск SQL Server при наличии и отсутствии сети</span><span class="sxs-lookup"><span data-stu-id="afbc3-134">Run SQL Server With or Without a Network</span></span>](run-sql-server-with-or-without-a-network.md)|[<span data-ttu-id="afbc3-135">Настройка параметров запуска сервера (диспетчер конфигурации SQL Server)</span><span class="sxs-lookup"><span data-stu-id="afbc3-135">Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;</span></span>](scm-services-configure-server-startup-options.md)|  
|[<span data-ttu-id="afbc3-136">Служба обозревателя SQL Server (компонент Database Engine и SSAS)</span><span class="sxs-lookup"><span data-stu-id="afbc3-136">SQL Server Browser Service &#40;Database Engine and SSAS&#41;</span></span>](sql-server-browser-service-database-engine-and-ssas.md)|[<span data-ttu-id="afbc3-137">Изменение пароля учетных записей, используемых SQL Server (диспетчер конфигурации SQL Server)</span><span class="sxs-lookup"><span data-stu-id="afbc3-137">Change the Password of the Accounts Used by SQL Server &#40;SQL Server Configuration Manager&#41;</span></span>](scm-services-change-the-password-of-the-accounts-used.md)|  
|[<span data-ttu-id="afbc3-138">Параметры запуска службы Database Engine</span><span class="sxs-lookup"><span data-stu-id="afbc3-138">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)|[<span data-ttu-id="afbc3-139">Настройка журналов ошибок SQL Server</span><span class="sxs-lookup"><span data-stu-id="afbc3-139">Configure SQL Server Error Logs</span></span>](scm-services-configure-sql-server-error-logs.md)|  
|[<span data-ttu-id="afbc3-140">Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server</span><span class="sxs-lookup"><span data-stu-id="afbc3-140">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)|[<span data-ttu-id="afbc3-141">Изменение режима проверки подлинности сервера</span><span class="sxs-lookup"><span data-stu-id="afbc3-141">Change Server Authentication Mode</span></span>](change-server-authentication-mode.md)|  
|[<span data-ttu-id="afbc3-142">Запуск SQL Server в однопользовательском режиме</span><span class="sxs-lookup"><span data-stu-id="afbc3-142">Start SQL Server in Single-User Mode</span></span>](start-sql-server-in-single-user-mode.md)|[<span data-ttu-id="afbc3-143">cлужба «Модуль записи SQL»</span><span class="sxs-lookup"><span data-stu-id="afbc3-143">SQL Writer Service</span></span>](sql-writer-service.md)|  
|[<span data-ttu-id="afbc3-144">Запустите SQL Server с минимальной конфигурацией</span><span class="sxs-lookup"><span data-stu-id="afbc3-144">Start SQL Server with Minimal Configuration</span></span>](start-sql-server-with-minimal-configuration.md)|[<span data-ttu-id="afbc3-145">Рассылка сообщения о завершении работы (командная строка)</span><span class="sxs-lookup"><span data-stu-id="afbc3-145">Broadcast a Shutdown Message &#40;Command Prompt&#41;</span></span>](broadcast-a-shutdown-message-command-prompt.md)|  
|[<span data-ttu-id="afbc3-146">Подключение к другому компьютеру (диспетчер конфигурации SQL Server)</span><span class="sxs-lookup"><span data-stu-id="afbc3-146">Connect to Another Computer &#40;SQL Server Configuration Manager&#41;</span></span>](scm-services-connect-to-another-computer.md)|[<span data-ttu-id="afbc3-147">Вход в экземпляр SQL Server (командная строка)</span><span class="sxs-lookup"><span data-stu-id="afbc3-147">Log In to an Instance of SQL Server &#40;Command Prompt&#41;</span></span>](log-in-to-an-instance-of-sql-server-command-prompt.md)|  
|[<span data-ttu-id="afbc3-148">Настройка автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)</span><span class="sxs-lookup"><span data-stu-id="afbc3-148">Set an Instance of SQL Server to Start Automatically &#40;SQL Server Configuration Manager&#41;</span></span>](scm-services-set-an-instance-to-start-automatically.md)|[<span data-ttu-id="afbc3-149">Настройка разрешений файловой системы для доступа к компоненту ядра СУБД</span><span class="sxs-lookup"><span data-stu-id="afbc3-149">Configure File System Permissions for Database Engine Access</span></span>](configure-file-system-permissions-for-database-engine-access.md)|  
  
## <a name="related-content"></a><span data-ttu-id="afbc3-150">См. также</span><span class="sxs-lookup"><span data-stu-id="afbc3-150">Related Content</span></span>  
 [<span data-ttu-id="afbc3-151">Настройка агента SQL Server</span><span class="sxs-lookup"><span data-stu-id="afbc3-151">Configure SQL Server Agent</span></span>](../../ssms/agent/sql-server-agent.md)  
  
 [<span data-ttu-id="afbc3-152">Вход в систему SQL Server</span><span class="sxs-lookup"><span data-stu-id="afbc3-152">Logging In to SQL Server</span></span>](logging-in-to-sql-server.md)  
  
  