---
title: Использование программы sqlcmd
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL statements, executing
- command prompt utilities [SQL Server], sqlcmd
- statements [SQL Server], executing
- sqlcmd utility, about sqlcmd utility
ms.assetid: 3ec89119-7314-43ef-9e91-12e72bb63d62
author: rothja
ms.author: jroth
ms.openlocfilehash: 922f9915272fb2d7fc63487ec135ce44ee91e88b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666480"
---
# <a name="use-the-sqlcmd-utility"></a><span data-ttu-id="ad73b-102">Использование программы sqlcmd</span><span class="sxs-lookup"><span data-stu-id="ad73b-102">Use the sqlcmd Utility</span></span>
  <span data-ttu-id="ad73b-103">Служебная программа `sqlcmd` представляет собой программу командной строки для нерегламентированного интерактивного выполнения инструкций и скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)], а также для автоматизации задач скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad73b-103">The `sqlcmd` utility is a command-line utility for ad hoc, interactive execution of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and scripts and for automating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripting tasks.</span></span> <span data-ttu-id="ad73b-104">Интерактивная работа с `sqlcmd` и создание файлов скриптов, исполняемых с помощью `sqlcmd`, требует от пользователя понимания языка [!INCLUDE[tsql](../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad73b-104">To use `sqlcmd` interactively, or to build script files to be run using `sqlcmd`, users must understand [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ad73b-105">Программа `sqlcmd` обычно применяется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ad73b-105">The `sqlcmd` utility is typically used in the following ways:</span></span>  
  
-   <span data-ttu-id="ad73b-106">Пользователь в интерактивном режиме вводит инструкции на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] так же, как и при работе в командной строке.</span><span class="sxs-lookup"><span data-stu-id="ad73b-106">Users interactively enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a manner similar to working at the command prompt.</span></span> <span data-ttu-id="ad73b-107">Результаты выводятся в окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="ad73b-107">The results are displayed at the command prompt.</span></span> <span data-ttu-id="ad73b-108">Чтобы открыть окно командной строки, в меню **Пуск**последовательно выберите команды **Все программы**, **Стандартные**и **Командная строка**.</span><span class="sxs-lookup"><span data-stu-id="ad73b-108">To open a Command Prompt window, click **Start**, click **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span> <span data-ttu-id="ad73b-109">В окне командной строки введите `sqlcmd` и необходимые параметры.</span><span class="sxs-lookup"><span data-stu-id="ad73b-109">At the command prompt, type `sqlcmd` followed by a list of options that you want.</span></span> <span data-ttu-id="ad73b-110">Полный список параметров, поддерживаемых `sqlcmd` , см. в разделе [программа sqlcmd](../../tools/sqlcmd-utility.md).</span><span class="sxs-lookup"><span data-stu-id="ad73b-110">For a complete list of the options that are supported by `sqlcmd`, see [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="ad73b-111">Пользователь отправляет задание `sqlcmd` на выполнение, указывая либо одиночную инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)], либо текстовый файл с выполняемыми инструкциями [!INCLUDE[tsql](../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad73b-111">Users submit a `sqlcmd` job either by specifying a single [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute, or by pointing the utility to a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to execute.</span></span> <span data-ttu-id="ad73b-112">Вывод обычно перенаправляется в текстовый файл, но может также быть отображен в окне командной строки.</span><span class="sxs-lookup"><span data-stu-id="ad73b-112">The output is usually directed to a text file, but it can also be displayed at the command prompt.</span></span>  
  
-   <span data-ttu-id="ad73b-113">Режим[SQLCMD](edit-sqlcmd-scripts-with-query-editor.md) в редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad73b-113">[SQLCMD mode](edit-sqlcmd-scripts-with-query-editor.md) in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="ad73b-114">Управляющие объекты SQL Server (SMO)</span><span class="sxs-lookup"><span data-stu-id="ad73b-114">SQL Server Management Objects (SMO)</span></span>  
  
-   <span data-ttu-id="ad73b-115">Задания CmdExec агента SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ad73b-115">SQL Server Agent CmdExec jobs.</span></span>  
  
## <a name="typically-used-sqlcmd-options"></a><span data-ttu-id="ad73b-116">Часто используемые параметры sqlcmd</span><span class="sxs-lookup"><span data-stu-id="ad73b-116">Typically Used sqlcmd Options</span></span>  
 <span data-ttu-id="ad73b-117">Чаще всего используются следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="ad73b-117">The following options are used most frequently:</span></span>  
  
-   <span data-ttu-id="ad73b-118">Параметр сервера (**-S**), определяющий экземпляр, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к которому `sqlcmd` подключается.</span><span class="sxs-lookup"><span data-stu-id="ad73b-118">The server option (**-S**) that identifies the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to which `sqlcmd` connects.</span></span>  
  
-   <span data-ttu-id="ad73b-119">Параметры проверки подлинности (**-E**, **-U**и **-P**), которые указывают учетные данные, `sqlcmd` используемые для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad73b-119">Authentication options (**-E**, **-U**, and **-P**) that specify the credentials that `sqlcmd` uses to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad73b-120">Параметр **-E** используется по умолчанию, и нет необходимости его указывать.</span><span class="sxs-lookup"><span data-stu-id="ad73b-120">The **-E** option is the default and does not have to be specified.</span></span>  
  
-   <span data-ttu-id="ad73b-121">Параметры ввода (**-q**, **-q**и **-i**), которые указывают расположение входных данных `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="ad73b-121">Input options (**-Q**, **-q**, and **-i**) that identify the location of the input to `sqlcmd`.</span></span>  
  
-   <span data-ttu-id="ad73b-122">Параметр Output (**-o**), указывающий файл, в котором `sqlcmd` следует разместить выходные данные.</span><span class="sxs-lookup"><span data-stu-id="ad73b-122">The output option (**-o**) that specifies the file in which `sqlcmd` is to put its output.</span></span>  
  
## <a name="connecting-to-the-sqlcmd-utility"></a><span data-ttu-id="ad73b-123">Соединение с программой sqlcmd</span><span class="sxs-lookup"><span data-stu-id="ad73b-123">Connecting to the sqlcmd Utility</span></span>  
 <span data-ttu-id="ad73b-124">Ниже перечислены наиболее частые способы использования служебной программы `sqlcmd`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-124">The following are common uses of the `sqlcmd` utility:</span></span>  
  
-   <span data-ttu-id="ad73b-125">Соединение с экземпляром по умолчанию с использованием проверки подлинности Windows для запуска инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] в интерактивном режиме:</span><span class="sxs-lookup"><span data-stu-id="ad73b-125">Connecting to a default instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad73b-126">В предыдущем примере параметр **-E** не указан, так как он используется по умолчанию и `sqlcmd` подключается к экземпляру по умолчанию с использованием проверки подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="ad73b-126">In the previous example, **-E** is not specified because it is the default and `sqlcmd` connects to the default instance by using Windows Authentication.</span></span>  
  
-   <span data-ttu-id="ad73b-127">Соединение с именованным экземпляром с использованием проверки подлинности Windows для запуска инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] в интерактивном режиме:</span><span class="sxs-lookup"><span data-stu-id="ad73b-127">Connecting to a named instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName>  
    ```  
  
     <span data-ttu-id="ad73b-128">,</span><span class="sxs-lookup"><span data-stu-id="ad73b-128">or</span></span>  
  
    ```  
    sqlcmd -S .\<InstanceName>  
    ```  
  
-   <span data-ttu-id="ad73b-129">Соединение с именованным экземпляром с использованием проверки подлинности Windows и указанием входного и выходного файла:</span><span class="sxs-lookup"><span data-stu-id="ad73b-129">Connecting to a named instance by using Windows Authentication and specifying input and output files:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName> -i <MyScript.sql> -o <MyOutput.rpt>  
    ```  
  
-   <span data-ttu-id="ad73b-130">Соединение с экземпляром по умолчанию на локальном компьютере с использованием проверки подлинности Windows, выполнение запроса и продолжение выполнения программы `sqlcmd` после завершения запроса:</span><span class="sxs-lookup"><span data-stu-id="ad73b-130">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, and having `sqlcmd` remain running after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -q "SELECT * FROM AdventureWorks2012.Person.Person"  
    ```  
  
-   <span data-ttu-id="ad73b-131">Соединение с экземпляром по умолчанию на локальном компьютере с использованием проверки подлинности Windows, выполнение запроса, запись в файл выходных данных и выход из программы `sqlcmd` после завершения запроса:</span><span class="sxs-lookup"><span data-stu-id="ad73b-131">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, directing the output to a file, and having `sqlcmd` exit after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -Q "SELECT * FROM AdventureWorks2012.Person.Person" -o MyOutput.txt  
    ```  
  
-   <span data-ttu-id="ad73b-132">Соединение с именованным экземпляром с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)] в интерактивном режиме; программа `sqlcmd` ожидает ввода пароля:</span><span class="sxs-lookup"><span data-stu-id="ad73b-132">Connecting to a named instance using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, with `sqlcmd` prompting for a password:</span></span>  
  
    ```  
    sqlcmd -U MyLogin -S <ComputerName>\<InstanceName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad73b-133">Для просмотра полного перечня параметров, поддерживаемых служебной программой `sqlcmd`, введите `sqlcmd -?`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-133">To see a list of the options that are supported by the `sqlcmd` utility run: `sqlcmd -?`.</span></span>  
  
## <a name="running-transact-sql-statements-interactively-by-using-sqlcmd"></a><span data-ttu-id="ad73b-134">Интерактивный запуск инструкций Transact-SQL с помощью программы sqlcmd</span><span class="sxs-lookup"><span data-stu-id="ad73b-134">Running Transact-SQL Statements Interactively by Using sqlcmd</span></span>  
 <span data-ttu-id="ad73b-135">С помощью программы `sqlcmd` можно интерактивно запускать инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] из окна командной строки.</span><span class="sxs-lookup"><span data-stu-id="ad73b-135">You can use the `sqlcmd` utility interactively to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a Command Prompt window.</span></span> <span data-ttu-id="ad73b-136">Для интерактивного выполнения [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций с помощью `sqlcmd` запустите программу, не используя параметры **-q**, **-q**, **-Z**или **-i** , чтобы указать входные файлы или запросы.</span><span class="sxs-lookup"><span data-stu-id="ad73b-136">To interactively execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using `sqlcmd`, run the utility without using the **-Q**, **-q**, **-Z**, or **-i** options to specify any input files or queries.</span></span> <span data-ttu-id="ad73b-137">Пример:</span><span class="sxs-lookup"><span data-stu-id="ad73b-137">For example:</span></span>  
  
 `sqlcmd -S <ComputerName>\<InstanceName>`  
  
 <span data-ttu-id="ad73b-138">Если команда выполняется без входных файлов или запросов, то программа `sqlcmd` подключается к заданному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выводит новую строку с символами `1>` и мигающим знаком подчеркивания, которая называется приглашением `sqlcmd`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-138">When the command is executed without input files or queries, `sqlcmd` connects to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then displays a new line with a `1>` followed by a blinking underscore that is named the `sqlcmd` prompt.</span></span> <span data-ttu-id="ad73b-139">Цифра `1` означает, что это первая строка инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], а приглашение `sqlcmd` является точкой, с которой начинается инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad73b-139">The `1` signifies that this is the first line of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, and the `sqlcmd` prompt is the point at which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will start when you type it in.</span></span>  
  
 <span data-ttu-id="ad73b-140">В приглашении `sqlcmd` можно вводить как инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], так и команды `sqlcmd`, например `GO` и `EXIT`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-140">At the `sqlcmd` prompt, you can type both [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands, such as `GO` and `EXIT`.</span></span> <span data-ttu-id="ad73b-141">Каждая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] помещается в буфер, называемый кэш инструкций.</span><span class="sxs-lookup"><span data-stu-id="ad73b-141">Each [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is put in a buffer called the statement cache.</span></span> <span data-ttu-id="ad73b-142">После ввода команды `GO` и нажатия клавиши ВВОД эти инструкции отправляются на сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad73b-142">These statements are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] after you type the `GO` command and press ENTER.</span></span> <span data-ttu-id="ad73b-143">Чтобы выйти `sqlcmd` , введите `EXIT` или `QUIT` в начале новой строки.</span><span class="sxs-lookup"><span data-stu-id="ad73b-143">To exit `sqlcmd`, type `EXIT` or `QUIT` at the start of a new line.</span></span>  
  
 <span data-ttu-id="ad73b-144">Чтобы очистить кэш инструкций, введите `:RESET`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-144">To clear the statement cache, type `:RESET`.</span></span> <span data-ttu-id="ad73b-145">Ввод `^C` причины `sqlcmd` выхода.</span><span class="sxs-lookup"><span data-stu-id="ad73b-145">Typing `^C` causes `sqlcmd` to exit.</span></span> <span data-ttu-id="ad73b-146">Кроме того, с помощью команды `^C` можно останавливать выполнение кэша инструкций после запуска команды `GO`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-146">`^C` can also be used to stop the execution of the statement cache after a `GO` command has been issued.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="ad73b-147">инструкции, вводимые во время интерактивного сеанса, можно изменить, введя команду **: ED** и `sqlcmd` запрос.</span><span class="sxs-lookup"><span data-stu-id="ad73b-147">statements that are entered in an interactive session can edited by entering the **:ED** command and the `sqlcmd` prompt.</span></span> <span data-ttu-id="ad73b-148">Откроется редактор, и после изменения инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и закрытия редактора измененная инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] появится в окне командной строки.</span><span class="sxs-lookup"><span data-stu-id="ad73b-148">The editor will open and, after editing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement and closing the editor, the revised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will appear in the command window.</span></span> <span data-ttu-id="ad73b-149">Введите `GO` , чтобы выполнить [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию измененной.</span><span class="sxs-lookup"><span data-stu-id="ad73b-149">Enter `GO` to run therevised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="quoted-strings"></a><span data-ttu-id="ad73b-150">Строки в кавычках</span><span class="sxs-lookup"><span data-stu-id="ad73b-150">Quoted Strings</span></span>  
 <span data-ttu-id="ad73b-151">Символы, заключенные в кавычки, используются без какой-либо дополнительной предварительной обработки, за исключением кавычек, которые вставляются в строку путем ввода двух последовательных кавычек.</span><span class="sxs-lookup"><span data-stu-id="ad73b-151">Characters that are enclosed in quotation marks are used without any additional preprocessing, except that quotations marks can be inserted into a string by entering two consecutive quotation marks.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ad73b-152">рассматривает такую последовательность символов как одни кавычки.</span><span class="sxs-lookup"><span data-stu-id="ad73b-152">treats this character sequence as one quotation mark.</span></span> <span data-ttu-id="ad73b-153">однако на сервере выполняется преобразование. Переменные скрипта при появлении в строке не раскрываются.</span><span class="sxs-lookup"><span data-stu-id="ad73b-153">(However, the translation occurs in the server.) Scripting variables will not be expanded when they appear within a string.</span></span>  
  
 <span data-ttu-id="ad73b-154">Пример:</span><span class="sxs-lookup"><span data-stu-id="ad73b-154">For example:</span></span>  
  
 `sqlcmd`  
  
 `PRINT "Length: 5"" 7'";`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Length: 5" 7'`  
  
## <a name="strings-that-span-multiple-lines"></a><span data-ttu-id="ad73b-155">Многострочные символьные строки</span><span class="sxs-lookup"><span data-stu-id="ad73b-155">Strings That Span Multiple Lines</span></span>  
 <span data-ttu-id="ad73b-156">Программа `sqlcmd` поддерживает скрипты, в которых одна символьная строка занимает несколько строк.</span><span class="sxs-lookup"><span data-stu-id="ad73b-156">`sqlcmd` supports scripts that have strings that span multiple lines.</span></span> <span data-ttu-id="ad73b-157">Например, следующая инструкция `SELECT` занимает несколько строк, но является одной символьной строкой, которая выполняется после ввода команды `GO`и нажатия клавиши ВВОД.</span><span class="sxs-lookup"><span data-stu-id="ad73b-157">For example, the following `SELECT` statement spans multiple lines but is a single string executed when you press the ENTER key after typing `GO`.</span></span>  
  
 `SELECT First line`  
  
 `FROM Second line`  
  
 `WHERE Third line;`  
  
 `GO`  
  
## <a name="interactive-sqlcmd-example"></a><span data-ttu-id="ad73b-158">Пример интерактивной команды sqlcmd</span><span class="sxs-lookup"><span data-stu-id="ad73b-158">Interactive sqlcmd Example</span></span>  
 <span data-ttu-id="ad73b-159">Ниже приведен пример интерактивного выполнения программы `sqlcmd`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-159">This is an example of what you see when you run `sqlcmd` interactively.</span></span>  
  
 <span data-ttu-id="ad73b-160">При открытии окна командной строки там отображается только одна строка:</span><span class="sxs-lookup"><span data-stu-id="ad73b-160">When you open a Command Prompt window, there is one line similar to:</span></span>  
  
 `C:\> _`  
  
 <span data-ttu-id="ad73b-161">Это означает, что текущей папкой является `C:\` , и если задать имя файла, то ОС Windows будет искать его в этой папке.</span><span class="sxs-lookup"><span data-stu-id="ad73b-161">This means the folder `C:\` is the current folder, and if you specify a file name, Windows will look for the file in that folder.</span></span>  
  
 <span data-ttu-id="ad73b-162">Для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию на локальном компьютере введите `sqlcmd`. Командная строка будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ad73b-162">Type `sqlcmd` to connect to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer, and the contents of the Command Prompt window will be:</span></span>  
  
 `C:\>sqlcmd`  
  
 `1> _`  
  
 <span data-ttu-id="ad73b-163">Это означает, что вы подключились к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и что программа `sqlcmd` готова обрабатывать инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и команды `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="ad73b-163">This means you have connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and `sqlcmd` is now ready to accept [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands.</span></span> <span data-ttu-id="ad73b-164">Мерцающий знак подчеркивания после `1>` является приглашением `sqlcmd` , отмечающим местоположение вводимых инструкций и команд.</span><span class="sxs-lookup"><span data-stu-id="ad73b-164">The flashing underscore after the `1>` is the `sqlcmd` prompt that marks the location at which the statements and commands you type will be displayed.</span></span> <span data-ttu-id="ad73b-165">Теперь введите `USE AdventureWorks2012` и нажмите клавишу ВВОД, а затем введите `GO` и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="ad73b-165">Now, type `USE AdventureWorks2012` and press ENTER, and then type `GO` and press ENTER.</span></span> <span data-ttu-id="ad73b-166">Содержимое окна командной строки будет выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ad73b-166">The contents of the Command Prompt window will be:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `1> _`  
  
 <span data-ttu-id="ad73b-167">После ввода команды `USE AdventureWorks2012` и нажатия клавиши ВВОД программа `sqlcmd` получила команду начать новую строку.</span><span class="sxs-lookup"><span data-stu-id="ad73b-167">Pressing ENTER after entering `USE AdventureWorks2012` signaled `sqlcmd` to start a new line.</span></span> <span data-ttu-id="ad73b-168">Нажатие клавиши ENTER после ввода `GO,` дает сигнал программе `sqlcmd` к отправке инструкции `USE AdventureWorks2012` экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad73b-168">Pressing ENTER, after you type `GO,` signaled `sqlcmd` to send the `USE AdventureWorks2012` statement to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ad73b-169">`sqlcmd` возвращает сообщение, указывающее, что инструкция `USE` успешно завершена, и отображает новое приглашение `1>` , которое служит сигналом готовности к вводу новой</span><span class="sxs-lookup"><span data-stu-id="ad73b-169">`sqlcmd` then returned a message to indicate that the `USE` statement completed successfully and displayed a new `1>` prompt as a signal to enter a new statement or command.</span></span>  
  
 <span data-ttu-id="ad73b-170">В следующем примере показано содержимое окна командной строки после ввода инструкции `SELECT` , команды `GO` для выполнения `SELECT`и команды `EXIT` для завершения программы `sqlcmd`:</span><span class="sxs-lookup"><span data-stu-id="ad73b-170">The following example shows what the Command Prompt window contains if you type a `SELECT` statement, a `GO` to execute the `SELECT`, and an `EXIT` to exit `sqlcmd`:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `BusinessEntityID   FirstName                 LastName`  
  
 `----------- -------------------------------- -----------`  
  
 `1           Syed                             Abbas`  
  
 `2           Catherine                        Abel`  
  
 `3           Kim                              Abercrombie`  
  
 `(3 rows affected)`  
  
 `1> EXIT`  
  
 `C:\>`  
  
 <span data-ttu-id="ad73b-171">Строки после `3> GO` — это выходные данные инструкции `SELECT` .</span><span class="sxs-lookup"><span data-stu-id="ad73b-171">The lines after line `3> GO` are the output of a `SELECT` statement.</span></span> <span data-ttu-id="ad73b-172">Когда выходные данные сформированы, программа `sqlcmd` сбрасывает приглашение `sqlcmd` и отображает `1>`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-172">After you generate output, `sqlcmd` resets the `sqlcmd` prompt and displays `1>`.</span></span> <span data-ttu-id="ad73b-173">После ввода команды `EXIT` в строке `1>`командная строка приобретает первоначальный вид.</span><span class="sxs-lookup"><span data-stu-id="ad73b-173">After entering `EXIT` at line `1>`, the Command Prompt window displays the same line it did when you first opened it.</span></span> <span data-ttu-id="ad73b-174">Это означает завершение сеанса `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="ad73b-174">This indicates that `sqlcmd` has exited its session.</span></span> <span data-ttu-id="ad73b-175">Теперь можно закрыть окно командной строки. Для этого введите еще одну команду `EXIT` .</span><span class="sxs-lookup"><span data-stu-id="ad73b-175">You can now close the Command Prompt window by typing another `EXIT` command.</span></span>  
  
## <a name="running-transact-sql-script-files-by-using-sqlcmd"></a><span data-ttu-id="ad73b-176">Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd</span><span class="sxs-lookup"><span data-stu-id="ad73b-176">Running Transact-SQL Script Files by Using sqlcmd</span></span>  
 <span data-ttu-id="ad73b-177">Можно использовать команду `sqlcmd` для выполнения файлов скриптов базы данных.</span><span class="sxs-lookup"><span data-stu-id="ad73b-177">You can use `sqlcmd` to execute database script files.</span></span> <span data-ttu-id="ad73b-178">Файлы скриптов — это текстовые файлы, содержащие сочетание [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций, `sqlcmd` команд и переменных скрипта.</span><span class="sxs-lookup"><span data-stu-id="ad73b-178">Script files are text files that contain a mix of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span> <span data-ttu-id="ad73b-179">Дополнительные сведения об использовании переменных скрипта см. в разделе [Использование программы sqlcmd с переменными скрипта](sqlcmd-use-with-scripting-variables.md).</span><span class="sxs-lookup"><span data-stu-id="ad73b-179">For more information about how to script variables, see [Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md).</span></span> <span data-ttu-id="ad73b-180">Программа  `sqlcmd` работает с инструкциями, командами и переменными скрипта, помещенными в файл скрипта, подобно тому как она работает с инструкциями и командами, вводимыми в интерактивном режиме.</span><span class="sxs-lookup"><span data-stu-id="ad73b-180">`sqlcmd` works with the statements, commands, and scripting variables in a script file in a manner similar to how it works with statements and commands that are entered interactively.</span></span> <span data-ttu-id="ad73b-181">Главное отличие заключается в том, что программа `sqlcmd` без остановок считывает входной файл, а не ждет, пока пользователь введет инструкции, команды или переменные скрипта.</span><span class="sxs-lookup"><span data-stu-id="ad73b-181">The main difference is that `sqlcmd` reads through the input file without pause instead of waiting for a user to enter the statements, commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="ad73b-182">Существуют различные способы создания файлов скрипта базы данных:</span><span class="sxs-lookup"><span data-stu-id="ad73b-182">There are different ways to create database script files:</span></span>  
  
-   <span data-ttu-id="ad73b-183">можно в интерактивном режиме создать и отладить набор инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и сохранить содержимое окна запроса в файл скрипта;</span><span class="sxs-lookup"><span data-stu-id="ad73b-183">You can interactively build and debug a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then save the contents of the Query window as a script file.</span></span>  
  
-   <span data-ttu-id="ad73b-184">можно создать текстовый файл инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , используя текстовый редактор, например «Блокнот».</span><span class="sxs-lookup"><span data-stu-id="ad73b-184">You can create a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using a text editor, such as Notepad.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ad73b-185">Примеры</span><span class="sxs-lookup"><span data-stu-id="ad73b-185">Examples</span></span>  
  
### <a name="a-running-a-script-by-using-sqlcmd"></a><span data-ttu-id="ad73b-186">A.</span><span class="sxs-lookup"><span data-stu-id="ad73b-186">A.</span></span> <span data-ttu-id="ad73b-187">Запуск скрипта с помощью программы sqlcmd</span><span class="sxs-lookup"><span data-stu-id="ad73b-187">Running a script by using sqlcmd</span></span>  
 <span data-ttu-id="ad73b-188">Откройте «Блокнот» и введите следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="ad73b-188">Start Notepad, and type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="ad73b-189">Создайте папку с именем `MyFolder` и сохраните скрипт в виде файла `MyScript.sql` в папке `C:\MyFolder`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-189">Create a folder named `MyFolder` and then save the script as the file `MyScript.sql` in the folder `C:\MyFolder`.</span></span> <span data-ttu-id="ad73b-190">Введите следующий текст в командной строке, чтобы запустить скрипт, и поместите выходные данные `MyOutput.txt` в папку `MyFolder`:</span><span class="sxs-lookup"><span data-stu-id="ad73b-190">Enter the following at the command prompt to run the script and put the output in `MyOutput.txt` in `MyFolder`:</span></span>  
  
 `sqlcmd -i C:\MyFolder\MyScript.sql -o C:\MyFolder\MyOutput.txt`  
  
 <span data-ttu-id="ad73b-191">Файл `MyOutput.txt` , просматриваемый в «Блокноте», содержит следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="ad73b-191">When you view the contents of `MyOutput.txt` in Notepad, you will see the following:</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `BusinessEntityID FirstName   LastName`  
  
 `---------------- ----------- -----------`  
  
 `1                Syed        Abbas`  
  
 `2                Catherine   Abel`  
  
 `3                Kim         Abercrombie`  
  
 `(3 rows affected)`  
  
### <a name="b-using-sqlcmd-with-a-dedicated-administrative-connection"></a><span data-ttu-id="ad73b-192">Б.</span><span class="sxs-lookup"><span data-stu-id="ad73b-192">B.</span></span> <span data-ttu-id="ad73b-193">Использование программы sqlcmd с выделенным административным соединением</span><span class="sxs-lookup"><span data-stu-id="ad73b-193">Using sqlcmd with a dedicated administrative connection</span></span>  
 <span data-ttu-id="ad73b-194">В следующем примере программа `sqlcmd` используется для подключения к серверу, на котором возникла проблема с блокировкой, с помощью выделенного административного соединения.</span><span class="sxs-lookup"><span data-stu-id="ad73b-194">In the following example, `sqlcmd` is used to connect to a server that has a blocking problem by using the dedicated administrator connection (DAC).</span></span>  
  
 `C:\>sqlcmd -S ServerName -A`  
  
 `1> SELECT blocked FROM sys.dm_exec_requests WHERE blocked <> 0;`  
  
 `2> GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `spid   blocked`  
  
 `------ -------`  
  
 `62       64`  
  
 `(1 rows affected)`  
  
 <span data-ttu-id="ad73b-195">С помощью `sqlcmd` завершите блокирующий процесс.</span><span class="sxs-lookup"><span data-stu-id="ad73b-195">Use `sqlcmd` to end the blocking process.</span></span>  
  
 `1> KILL 64;`  
  
 `2> GO`  
  
### <a name="c-using-sqlcmd-to-execute-a-stored-procedure"></a><span data-ttu-id="ad73b-196">В.</span><span class="sxs-lookup"><span data-stu-id="ad73b-196">C.</span></span> <span data-ttu-id="ad73b-197">Использование программы sqlcmd для выполнения хранимых процедур</span><span class="sxs-lookup"><span data-stu-id="ad73b-197">Using sqlcmd to execute a stored procedure</span></span>  
 <span data-ttu-id="ad73b-198">В следующем примере представлено действие, выполняющее хранимую процедуру с помощью `sqlcmd`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-198">The following example shows how to execute a stored procedure by using `sqlcmd`.</span></span> <span data-ttu-id="ad73b-199">Создайте следующую хранимую процедуру.</span><span class="sxs-lookup"><span data-stu-id="ad73b-199">Create the following stored procedure.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `IF OBJECT_ID ( ' dbo.ContactEmailAddress, 'P' ) IS NOT NULL`  
  
 `DROP PROCEDURE dbo.ContactEmailAddress;`  
  
 `GO`  
  
 `CREATE PROCEDURE dbo.ContactEmailAddress`  
  
 `(`  
  
 `@FirstName nvarchar(50)`  
  
 `,@LastName nvarchar(50)`  
  
 `)`  
  
 `AS`  
  
 `SET NOCOUNT ON`  
  
 `SELECT EmailAddress`  
  
 `FROM Person.Person`  
  
 `WHERE FirstName = @FirstName`  
  
 `AND LastName = @LastName;`  
  
 `SET NOCOUNT OFF`  
  
 <span data-ttu-id="ad73b-200">После приглашения `sqlcmd` введите следующее:</span><span class="sxs-lookup"><span data-stu-id="ad73b-200">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\sqlcmd`  
  
 `1> :Setvar FirstName Gustavo`  
  
 `1> :Setvar LastName Achong`  
  
 `1> EXEC dbo.ContactEmailAddress $(Gustavo),$(Achong)`  
  
 `2> GO`  
  
 `EmailAddress`  
  
 `-----------------------------`  
  
 `gustavo0@adventure-works.com`  
  
### <a name="d-using-sqlcmd-for-database-maintenance"></a><span data-ttu-id="ad73b-201">Г.</span><span class="sxs-lookup"><span data-stu-id="ad73b-201">D.</span></span> <span data-ttu-id="ad73b-202">Использование программы sqlcmd для обслуживания базы данных</span><span class="sxs-lookup"><span data-stu-id="ad73b-202">Using sqlcmd for database maintenance</span></span>  
 <span data-ttu-id="ad73b-203">В следующем примере кода показано, как использовать программу `sqlcmd` для задач обслуживания базы данных.</span><span class="sxs-lookup"><span data-stu-id="ad73b-203">The following example shows how to use `sqlcmd` for a database maintenance task.</span></span> <span data-ttu-id="ad73b-204">Создайте `C:\BackupTemplate.sql` со следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="ad73b-204">Create `C:\BackupTemplate.sql` with the following code.</span></span>  
  
 `USE master;`  
  
 `BACKUP DATABASE [$(db)] TO DISK='$(bakfile)';`  
  
 <span data-ttu-id="ad73b-205">После приглашения `sqlcmd` введите следующее:</span><span class="sxs-lookup"><span data-stu-id="ad73b-205">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\ >sqlcmd`  
  
 `1> :connect <server>`  
  
 `Sqlcmd: Successfully connected to server <server>.`  
  
 `1> :setvar db msdb`  
  
 `1> :setvar bakfile c:\msdb.bak`  
  
 `1> :r c:\BackupTemplate.sql`  
  
 `2> GO`  
  
 `Changed database context to 'master'.`  
  
 `Processed 688 pages for database 'msdb', file 'MSDBData' on file 2.`  
  
 `Processed 5 pages for database 'msdb', file 'MSDBLog' on file 2.`  
  
 `BACKUP DATABASE successfully processed 693 pages in 0.725 seconds (7.830 MB/sec)`  
  
### <a name="e-using-sqlcmd-to-execute-code-on-multiple-instances"></a><span data-ttu-id="ad73b-206">Д.</span><span class="sxs-lookup"><span data-stu-id="ad73b-206">E.</span></span> <span data-ttu-id="ad73b-207">Использование программы sqlcmd для выполнения кода на нескольких экземплярах</span><span class="sxs-lookup"><span data-stu-id="ad73b-207">Using sqlcmd to execute code on multiple instances</span></span>  
 <span data-ttu-id="ad73b-208">Следующий код представляет собой скрипт для соединения двух экземпляров.</span><span class="sxs-lookup"><span data-stu-id="ad73b-208">The following code in a file shows a script that connects to two instances.</span></span> <span data-ttu-id="ad73b-209">Обратите внимание на команду `GO` перед подключением ко второму экземпляру.</span><span class="sxs-lookup"><span data-stu-id="ad73b-209">Notice the `GO` before the connection to the second instance.</span></span>  
  
 `:CONNECT <server>\,<instance1>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
 `:CONNECT <server>\,<instance2>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
### <a name="e-returning-xml-output"></a><span data-ttu-id="ad73b-210">Д.</span><span class="sxs-lookup"><span data-stu-id="ad73b-210">E.</span></span> <span data-ttu-id="ad73b-211">Возврат выходных XML-данных</span><span class="sxs-lookup"><span data-stu-id="ad73b-211">Returning XML output</span></span>  
 <span data-ttu-id="ad73b-212">Следующий пример показывает, как выходные данные XML возвращаются неформатированными, в виде непрерывного потока.</span><span class="sxs-lookup"><span data-stu-id="ad73b-212">The following example shows how XML output is returned unformatted, in a continuous stream.</span></span>  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> :XML ON`  
  
 `1> SELECT TOP 3 FirstName + ' ' + LastName + ', '`  
  
 `2> FROM Person.Person`  
  
 `3> GO`  
  
 `Syed Abbas, Catherine Abel, Kim Abercrombie,`  
  
### <a name="f-using-sqlcmd-in-a-windows-script-file"></a><span data-ttu-id="ad73b-213">Е.</span><span class="sxs-lookup"><span data-stu-id="ad73b-213">F.</span></span> <span data-ttu-id="ad73b-214">Использование программы sqlcmd в файлах скриптов Windows</span><span class="sxs-lookup"><span data-stu-id="ad73b-214">Using sqlcmd in a Windows script file</span></span>  
 <span data-ttu-id="ad73b-215">`sqlcmd`Команда, например, `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` может быть выполнена в BAT-файле вместе с VBScript.</span><span class="sxs-lookup"><span data-stu-id="ad73b-215">A `sqlcmd`command such as `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` can be executed in a .bat file together with VBScript.</span></span> <span data-ttu-id="ad73b-216">В этом случае интерактивные параметры не используются.</span><span class="sxs-lookup"><span data-stu-id="ad73b-216">In this case, do not use interactive options.</span></span> <span data-ttu-id="ad73b-217">Программа `sqlcmd` должна быть установлена на компьютере, на котором выполняется файл BAT.</span><span class="sxs-lookup"><span data-stu-id="ad73b-217">`sqlcmd` must be installed on the computer that is executing the .bat file.</span></span>  
  
 <span data-ttu-id="ad73b-218">Сначала создайте следующие четыре файла.</span><span class="sxs-lookup"><span data-stu-id="ad73b-218">First, create the following four files:</span></span>  
  
-   <span data-ttu-id="ad73b-219">C:\badscript.sql</span><span class="sxs-lookup"><span data-stu-id="ad73b-219">C:\badscript.sql</span></span>  
  
    ```  
    SELECT batch_1_this_is_an_error  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="ad73b-220">C:\goodscript.sql</span><span class="sxs-lookup"><span data-stu-id="ad73b-220">C:\goodscript.sql</span></span>  
  
    ```  
    SELECT 'batch #1'  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="ad73b-221">C:\returnvalue.sql</span><span class="sxs-lookup"><span data-stu-id="ad73b-221">C:\returnvalue.sql</span></span>  
  
    ```  
    :exit(select 100)  
    @echo off  
    C:\windowsscript.bat  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
-   <span data-ttu-id="ad73b-222">C:\windowsscript.bat</span><span class="sxs-lookup"><span data-stu-id="ad73b-222">C:\windowsscript.bat</span></span>  
  
    ```  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
 <span data-ttu-id="ad73b-223">Затем из командной строки запустите `C:\windowsscript.bat`:</span><span class="sxs-lookup"><span data-stu-id="ad73b-223">Then, at the command prompt, run `C:\windowsscript.bat`:</span></span>  
  
 `C:\>windowsscript.bat`  
  
 `Running badscript.sql`  
  
 `== An error occurred`  
  
 `Running goodscript.sql`  
  
 `Running returnvalue.sql`  
  
 `SQLCMD returned 100 to the command shell`  
  
### <a name="g-using-sqlcmd-to-set-encryption-on-azure-sql-database"></a><span data-ttu-id="ad73b-224">Ж.</span><span class="sxs-lookup"><span data-stu-id="ad73b-224">G.</span></span> <span data-ttu-id="ad73b-225">Использование программы sqlcmd для включения шифрования в Базе данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="ad73b-225">Using sqlcmd to set encryption on Azure SQL Database</span></span>  
 <span data-ttu-id="ad73b-226">`sqlcmd`Можно выполнить для подключения к [!INCLUDE[ssSDS](../../includes/sssds-md.md)] данным в, чтобы указать шифрование и доверие сертификатов.</span><span class="sxs-lookup"><span data-stu-id="ad73b-226">A `sqlcmd`can be executed on a connection to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data on to specify encryption and certificate trust.</span></span> <span data-ttu-id="ad73b-227">Доступны два параметра "sqlcmd" ".</span><span class="sxs-lookup"><span data-stu-id="ad73b-227">Two \`sqlcmd\`\`\`options are available:</span></span>  
  
-   <span data-ttu-id="ad73b-228">Ключ -N используется клиентом для запроса зашифрованного соединения.</span><span class="sxs-lookup"><span data-stu-id="ad73b-228">The -N switch is used by the client to request an encrypted connection.</span></span> <span data-ttu-id="ad73b-229">Этот параметр аналогичен параметру ADO.net `ENCRYPT = true`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-229">This option is equivalent to the ADO.net option `ENCRYPT = true`.</span></span>  
  
-   <span data-ttu-id="ad73b-230">C помощью переключателя -C клиент настраивает неявное доверие к сертификату сервера без проверки.</span><span class="sxs-lookup"><span data-stu-id="ad73b-230">The -C switch is used by the client to configure it to implicitly the trust server certificate and not validate it.</span></span> <span data-ttu-id="ad73b-231">Этот параметр аналогичен параметру ADO.net `TRUSTSERVERCERTIFICATE = true`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-231">This option is equivalent to the ADO.net option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="ad73b-232">Служба [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не поддерживает все параметры `SET` , которые доступны в экземпляре SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ad73b-232">The [!INCLUDE[ssSDS](../../includes/sssds-md.md)] service does not support all the `SET` options available on a SQL Server instance.</span></span> <span data-ttu-id="ad73b-233">Следующие параметры вызывают ошибку, если соответствующий параметр `SET` имеет значение `ON` или `OFF`:</span><span class="sxs-lookup"><span data-stu-id="ad73b-233">The following options throw an error when the corresponding `SET` option is set to `ON` or `OFF`:</span></span>  
  
-   <span data-ttu-id="ad73b-234">SET ANSI_DEFAULTS</span><span class="sxs-lookup"><span data-stu-id="ad73b-234">SET ANSI_DEFAULTS</span></span>  
  
-   <span data-ttu-id="ad73b-235">SET ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="ad73b-235">SET ANSI_NULLS</span></span>  
  
-   <span data-ttu-id="ad73b-236">SET REMOTE_PROC_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="ad73b-236">SET REMOTE_PROC_TRANSACTIONS</span></span>  
  
-   <span data-ttu-id="ad73b-237">SET ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="ad73b-237">SET ANSI_NULL_DEFAULT</span></span>  
  
 <span data-ttu-id="ad73b-238">Следующие параметры SET не вызывают исключений, но использовать их нельзя.</span><span class="sxs-lookup"><span data-stu-id="ad73b-238">The following SET options do not throw exceptions but cannot be used.</span></span> <span data-ttu-id="ad73b-239">Они являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="ad73b-239">They are deprecated:</span></span>  
  
-   <span data-ttu-id="ad73b-240">SET CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="ad73b-240">SET CONCAT_NULL_YIELDS_NULL</span></span>  
  
-   <span data-ttu-id="ad73b-241">SET ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="ad73b-241">SET ANSI_PADDING</span></span>  
  
-   <span data-ttu-id="ad73b-242">SET QUERY_GOVERNOR_COST_LIMIT</span><span class="sxs-lookup"><span data-stu-id="ad73b-242">SET QUERY_GOVERNOR_COST_LIMIT</span></span>  
  
#### <a name="syntax"></a><span data-ttu-id="ad73b-243">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ad73b-243">Syntax</span></span>  
 <span data-ttu-id="ad73b-244">Следующий пример относится к случаям, когда поставщик для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет следующие параметры: `ForceProtocolEncryption = False`, `Trust Server Certificate = No`</span><span class="sxs-lookup"><span data-stu-id="ad73b-244">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = False`, `Trust Server Certificate = No`</span></span>  
  
 <span data-ttu-id="ad73b-245">Подключение с использованием учетных данных Windows и шифрование соединения:</span><span class="sxs-lookup"><span data-stu-id="ad73b-245">Connect using Windows credentials and encrypt communication:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="ad73b-246">Подключение с использованием учетных данных Windows и доверие сертификату сервера:</span><span class="sxs-lookup"><span data-stu-id="ad73b-246">Connect using Windows credentials and trust server certificate:</span></span>  
  
```  
SQLCMD -E -C  
  
```  
  
 <span data-ttu-id="ad73b-247">Подключение с использованием учетных данных Windows, шифрование соединения и доверие сертификату сервера:</span><span class="sxs-lookup"><span data-stu-id="ad73b-247">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="ad73b-248">Следующий пример относится к случаям, когда поставщик для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет следующие параметры: `ForceProtocolEncryption = True`, `TrustServerCertificate = Yes`.</span><span class="sxs-lookup"><span data-stu-id="ad73b-248">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = True`, `TrustServerCertificate = Yes`.</span></span>  
  
 <span data-ttu-id="ad73b-249">Подключение с использованием учетных данных Windows, шифрование соединения и доверие сертификату сервера:</span><span class="sxs-lookup"><span data-stu-id="ad73b-249">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E  
  
```  
  
 <span data-ttu-id="ad73b-250">Подключение с использованием учетных данных Windows, шифрование соединения и доверие сертификату сервера:</span><span class="sxs-lookup"><span data-stu-id="ad73b-250">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="ad73b-251">Подключение с использованием учетных данных Windows, шифрование соединения и доверие сертификату сервера:</span><span class="sxs-lookup"><span data-stu-id="ad73b-251">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -T  
  
```  
  
 <span data-ttu-id="ad73b-252">Подключение с использованием учетных данных Windows, шифрование соединения и доверие сертификату сервера:</span><span class="sxs-lookup"><span data-stu-id="ad73b-252">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="ad73b-253">Если поставщик установил значение `ForceProtocolEncryption = True` , шифрование включается даже в случае, если в строке соединения указано значение `Encrypt=No` .</span><span class="sxs-lookup"><span data-stu-id="ad73b-253">If the provider specifies `ForceProtocolEncryption = True` then encryption is enabled even if `Encrypt=No` in the connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad73b-254">См. также:</span><span class="sxs-lookup"><span data-stu-id="ad73b-254">See Also</span></span>  
 <span data-ttu-id="ad73b-255">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ad73b-255">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="ad73b-256">[Использование программы sqlcmd с переменными скрипта](sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="ad73b-256">[Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="ad73b-257">[Изменение скриптов SQLCMD при помощи редактора запросов](edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="ad73b-257">[Edit SQLCMD Scripts with Query Editor](edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="ad73b-258">[Управление шагами задания](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="ad73b-258">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="ad73b-259">Create a CmdExec Job Step</span><span class="sxs-lookup"><span data-stu-id="ad73b-259">Create a CmdExec Job Step</span></span>](../../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
