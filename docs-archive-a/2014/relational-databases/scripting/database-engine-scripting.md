---
title: Работа со сценариями компонента Database Engine
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
author: rothja
ms.author: jroth
ms.openlocfilehash: 79dca27e2aa5f2c0bc473534e0a8b204345b3993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654138"
---
# <a name="database-engine-scripting"></a><span data-ttu-id="85e7c-102">Работа со сценариями компонента Database Engine</span><span class="sxs-lookup"><span data-stu-id="85e7c-102">Database Engine Scripting</span></span>
  <span data-ttu-id="85e7c-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] поддерживает среду скриптов [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell для управления экземплярами компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и объектами в экземплярах.</span><span class="sxs-lookup"><span data-stu-id="85e7c-103">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] supports the [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell scripting environment to manage instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the objects in the instances.</span></span> <span data-ttu-id="85e7c-104">Можно также строить и запускать запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , содержащие [!INCLUDE[tsql](../../includes/tsql-md.md)] и XQuery, в средах, подобных средам сценариев.</span><span class="sxs-lookup"><span data-stu-id="85e7c-104">You can also build and run [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries that contain [!INCLUDE[tsql](../../includes/tsql-md.md)] and XQuery in environments very similar to scripting environments.</span></span>  
  
## <a name="sql-server-powershell"></a><span data-ttu-id="85e7c-105">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="85e7c-105">SQL Server PowerShell</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="85e7c-106">включает две оснастки PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые реализуют следующее:</span><span class="sxs-lookup"><span data-stu-id="85e7c-106">includes two [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins that implement:</span></span>  
  
-   <span data-ttu-id="85e7c-107">Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, отображающий иерархии моделей управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде путей PowerShell, подобных путям файловой системы.</span><span class="sxs-lookup"><span data-stu-id="85e7c-107">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider that exposes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management object model hierarchies as PowerShell paths that are similar to file system paths.</span></span> <span data-ttu-id="85e7c-108">С помощью классов модели управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно управлять объектами, представленными на каждом узле пути.</span><span class="sxs-lookup"><span data-stu-id="85e7c-108">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management object model classes to manage the objects represented at each node of the path.</span></span>  
  
-   <span data-ttu-id="85e7c-109">Набор командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , реализующих команды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7c-109">A set of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cmdlets that implement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commands.</span></span> <span data-ttu-id="85e7c-110">Одним из командлетов является **Invoke-Sqlcmd**.</span><span class="sxs-lookup"><span data-stu-id="85e7c-110">One of the cmdlets is **Invoke-Sqlcmd**.</span></span> <span data-ttu-id="85e7c-111">Используется для запуска [!INCLUDE[ssDE](../../includes/ssde-md.md)] скриптов запросов, запускаемых с помощью `sqlcmd` программы.</span><span class="sxs-lookup"><span data-stu-id="85e7c-111">This is used to run [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query scripts to be run with the `sqlcmd` utility.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="85e7c-112">поддерживает эти возможности для запуска PowerShell.</span><span class="sxs-lookup"><span data-stu-id="85e7c-112">provides these features for running PowerShell:</span></span>  
  
-   <span data-ttu-id="85e7c-113">Модуль PowerShell **sqlps** , который может быть импортирован в сеанс PowerShell, после чего модуль загружает оснастки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Можно запускать нерегламентированные команды PowerShell в интерактивном режиме.</span><span class="sxs-lookup"><span data-stu-id="85e7c-113">The **sqlps** PowerShell module that can be imported to a PowerShell session, the module then loads the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] snap-ins. You can interactively run ad hoc PowerShell commands.</span></span> <span data-ttu-id="85e7c-114">Файлы скриптов можно запускать с помощью команды вида «.\MyFolder\MyScript.ps1».</span><span class="sxs-lookup"><span data-stu-id="85e7c-114">You can run script files using a command such as .\MyFolder\MyScript.ps1.</span></span>  
  
-   <span data-ttu-id="85e7c-115">Файлы скриптов PowerShell можно использовать в качестве ввода для шагов заданий PowerShell агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые запускают скрипты через назначенные интервалы времени или в ответ на системные события.</span><span class="sxs-lookup"><span data-stu-id="85e7c-115">PowerShell script files can be used as input to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell job steps that run the scripts either at scheduled intervals or in response to system events.</span></span>  
  
-   <span data-ttu-id="85e7c-116">Программа **sqlps** , которая запускает PowerShell и импортирует модуль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7c-116">The **sqlps** utility that starts PowerShell and imports the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] module.</span></span> <span data-ttu-id="85e7c-117">Затем можно выполнять все действия, поддерживаемые в модуле.</span><span class="sxs-lookup"><span data-stu-id="85e7c-117">You can then perform all actions supported by the module.</span></span> <span data-ttu-id="85e7c-118">Программу **sqlps** можно запустить либо из командной строки, либо щелкнув правой кнопкой мыши узлы дерева обозревателя объектов среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio и выбрав команду **Запустить PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="85e7c-118">You can start the **sqlps** utility either in a command prompt or by right-clicking on the nodes in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio Object Explorer tree and selecting **Start PowerShell**.</span></span>  
  
## <a name="database-engine-queries"></a><span data-ttu-id="85e7c-119">Запросы к компоненту Database Engine</span><span class="sxs-lookup"><span data-stu-id="85e7c-119">Database Engine Queries</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="85e7c-120">содержат три типа элементов.</span><span class="sxs-lookup"><span data-stu-id="85e7c-120">query scripts contain three types of elements:</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="85e7c-121">.</span><span class="sxs-lookup"><span data-stu-id="85e7c-121">language statements.</span></span>  
  
-   <span data-ttu-id="85e7c-122">Инструкции языка XQuery.</span><span class="sxs-lookup"><span data-stu-id="85e7c-122">XQuery language statements</span></span>  
  
-   <span data-ttu-id="85e7c-123">Команды и переменные из `sqlcmd` программы.</span><span class="sxs-lookup"><span data-stu-id="85e7c-123">Commands and variables from the `sqlcmd` utility.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="85e7c-124">поддерживает три среды для построения и запуска запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7c-124">provides three environments for building and running [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries:</span></span>  
  
-   <span data-ttu-id="85e7c-125">Запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно запускать в интерактивном режиме и отлаживать в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85e7c-125">You can interactively run and debug [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="85e7c-126">В одном сеансе можно закодировать и отладить несколько инструкций, а затем сохранить их все в одном файле скрипта.</span><span class="sxs-lookup"><span data-stu-id="85e7c-126">You can code and debug several statements in one session, then save all of the statements in a single script file.</span></span>  
  
-   <span data-ttu-id="85e7c-127">`sqlcmd`Программа командной строки позволяет выполнять запросы в интерактивном режиме [!INCLUDE[ssDE](../../includes/ssde-md.md)] , а также запускать существующие [!INCLUDE[ssDE](../../includes/ssde-md.md)] файлы сценариев запросов.</span><span class="sxs-lookup"><span data-stu-id="85e7c-127">The `sqlcmd` command prompt utility lets you interactively run [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries, and also run existing [!INCLUDE[ssDE](../../includes/ssde-md.md)] query script files.</span></span>  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="85e7c-128">обычно кодируются в интерактивном режиме в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с помощью редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7c-128">query script files are typically coded interactively in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="85e7c-129">В дальнейшем файл можно открыть в одной из следующих сред.</span><span class="sxs-lookup"><span data-stu-id="85e7c-129">The file can later be opened in one of these environments:</span></span>  
  
-   <span data-ttu-id="85e7c-130">Чтобы открыть файл в новом окне редактора запросов [!INCLUDE[ssDE](../../includes/ssde-md.md)], воспользуйтесь меню **Файл**/**Открыть** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85e7c-130">Use the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **File**/**Open** menu to open the file in a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span>  
  
-   <span data-ttu-id="85e7c-131">Используйте параметр **-i**_input_file_ для запуска файла с помощью `sqlcmd` программы.</span><span class="sxs-lookup"><span data-stu-id="85e7c-131">Use the **-i**_input_file_ parameter to run the file with the `sqlcmd` utility.</span></span>  
  
-   <span data-ttu-id="85e7c-132">Чтобы запустить файл с помощью командлета **Invoke-Sqlcmd** в скриптах **PowerShell, укажите параметр** -QueryFromFile [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7c-132">Use the **-QueryFromFile** parameter to run the file with the **Invoke-Sqlcmd** cmdlet in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell scripts.</span></span>  
  
-   <span data-ttu-id="85e7c-133">Для запуска скриптов через назначенные интервалы времени или в ответ на системные события используются шаги заданий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7c-133">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps to run the scripts either at scheduled intervals or in response to system events.</span></span>  
  
 <span data-ttu-id="85e7c-134">Кроме того, для формирования скриптов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать мастер формирования скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7c-134">In addition, you can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Generate Script Wizard to generate [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="85e7c-135">Можно щелкнуть объекты правой кнопкой мыши в обозревателе объектов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , а затем выбрать пункт меню **Создать скрипт** .</span><span class="sxs-lookup"><span data-stu-id="85e7c-135">You can right-click objects in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, then select the **Generate Script** menu item.</span></span> <span data-ttu-id="85e7c-136">Команда**Создать скрипт** запускает мастер, который облегчает процесс создания скрипт.</span><span class="sxs-lookup"><span data-stu-id="85e7c-136">**Generate Script** launches the wizard, which guides you through the process of creating a script.</span></span>  
  
## <a name="database-engine-scripting-tasks"></a><span data-ttu-id="85e7c-137">Работа со скриптами компонента Database Engine</span><span class="sxs-lookup"><span data-stu-id="85e7c-137">Database Engine Scripting Tasks</span></span>  
  
|<span data-ttu-id="85e7c-138">Описание задачи</span><span class="sxs-lookup"><span data-stu-id="85e7c-138">Task Description</span></span>|<span data-ttu-id="85e7c-139">Раздел</span><span class="sxs-lookup"><span data-stu-id="85e7c-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="85e7c-140">Описывает порядок использования редактора кода и текстового редактора в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для интерактивной разработки, отладки и выполнения скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7c-140">Describes how to use the code and text editors in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to interactively develop, debug, and run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts</span></span>|[<span data-ttu-id="85e7c-141">Редакторы запросов и текста (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="85e7c-141">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|<span data-ttu-id="85e7c-142">Описывает порядок использования программы `sqlcmd` для выполнения скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] из командной строки, включая возможность интерактивной разработки скриптов.</span><span class="sxs-lookup"><span data-stu-id="85e7c-142">Describes how to use the `sqlcmd` utility to run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts from the command prompt, including the ability to interactively develop scripts.</span></span>|[<span data-ttu-id="85e7c-143">Связанные инструкции по sqlcmd</span><span class="sxs-lookup"><span data-stu-id="85e7c-143">sqlcmd How-to Topics</span></span>](../../database-engine/sqlcmd-how-to-topics.md)|  
|<span data-ttu-id="85e7c-144">Описывает порядок интеграции компонентов SQL Server в среду Windows PowerShell 2.0 с последующим построением скриптов PowerShell для управления экземплярами и объектами SQL Server.</span><span class="sxs-lookup"><span data-stu-id="85e7c-144">Describes how to integrate the SQL Server components into a Windows PowerShell 2.0 environment and then build PowerShell scripts for managing SQL Server instances and objects.</span></span>|[<span data-ttu-id="85e7c-145">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="85e7c-145">SQL Server PowerShell</span></span>](../../powershell/sql-server-powershell.md)|  
|<span data-ttu-id="85e7c-146">Описывает порядок использования мастера **формирования и публикации скриптов** для создания скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые повторно создают один или несколько объектов из базы данных.</span><span class="sxs-lookup"><span data-stu-id="85e7c-146">Describes how to use the **Generate and Publish Scripts** wizard to create [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that recreate one or more of the objects from a database.</span></span>|[<span data-ttu-id="85e7c-147">Формирование скриптов (среда SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="85e7c-147">Generate Scripts &#40;SQL Server Management Studio&#41;</span></span>](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a><span data-ttu-id="85e7c-148">См. также:</span><span class="sxs-lookup"><span data-stu-id="85e7c-148">See Also</span></span>  
 <span data-ttu-id="85e7c-149">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="85e7c-149">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="85e7c-150">Руководство. Составление инструкций Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="85e7c-150">Tutorial: Writing Transact-SQL Statements</span></span>](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  