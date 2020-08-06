---
title: MSSQLSERVER_833 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e20018c0fe1cd0748f4930e0022622adcbfad10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664205"
---
# <a name="mssqlserver_833"></a><span data-ttu-id="777ed-102">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="777ed-102">MSSQLSERVER_833</span></span>
    
## <a name="details"></a><span data-ttu-id="777ed-103">Сведения</span><span class="sxs-lookup"><span data-stu-id="777ed-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="777ed-104">Название продукта</span><span class="sxs-lookup"><span data-stu-id="777ed-104">Product Name</span></span>|<span data-ttu-id="777ed-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="777ed-105">SQL Server</span></span>|  
|<span data-ttu-id="777ed-106">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="777ed-106">Event ID</span></span>|<span data-ttu-id="777ed-107">833</span><span class="sxs-lookup"><span data-stu-id="777ed-107">833</span></span>|  
|<span data-ttu-id="777ed-108">Источник события</span><span class="sxs-lookup"><span data-stu-id="777ed-108">Event Source</span></span>|<span data-ttu-id="777ed-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="777ed-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="777ed-110">Компонент</span><span class="sxs-lookup"><span data-stu-id="777ed-110">Component</span></span>|<span data-ttu-id="777ed-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="777ed-111">SQLEngine</span></span>|  
|<span data-ttu-id="777ed-112">Символическое имя</span><span class="sxs-lookup"><span data-stu-id="777ed-112">Symbolic Name</span></span>|<span data-ttu-id="777ed-113">BUF_LONG_IO</span><span class="sxs-lookup"><span data-stu-id="777ed-113">BUF_LONG_IO</span></span>|  
|<span data-ttu-id="777ed-114">Текст сообщения</span><span class="sxs-lookup"><span data-stu-id="777ed-114">Message Text</span></span>|<span data-ttu-id="777ed-115">В SQL Server обнаружено% d запросов ввода-вывода, для выполнения которых в файле [% ls] в базе данных требуется больше% d секунд `[%ls] (%d)` .</span><span class="sxs-lookup"><span data-stu-id="777ed-115">SQL Server has encountered %d occurrence(s) of I/O requests taking longer than %d seconds to complete on file [%ls] in database`[%ls] (%d)`.</span></span>  <span data-ttu-id="777ed-116">Дескриптором файла ОС является 0x%p.</span><span class="sxs-lookup"><span data-stu-id="777ed-116">The OS file handle is 0x%p.</span></span>  <span data-ttu-id="777ed-117">Смещение последней длительной операции ввода-вывода: %#016I64x.</span><span class="sxs-lookup"><span data-stu-id="777ed-117">The offset of the latest long I/O is: %#016I64x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="777ed-118">Объяснение</span><span class="sxs-lookup"><span data-stu-id="777ed-118">Explanation</span></span>  
 <span data-ttu-id="777ed-119">Это сообщение указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издал запрос чтения или записи на диск, и выполнение запроса заняло более 15 секунд.</span><span class="sxs-lookup"><span data-stu-id="777ed-119">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="777ed-120">Данная ошибка возвращается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и говорит о проблеме с подсистемой ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="777ed-120">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the IO subsystem.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="777ed-121">Возможные причины</span><span class="sxs-lookup"><span data-stu-id="777ed-121">Possible Causes</span></span>  
 <span data-ttu-id="777ed-122">Причиной этой ошибки могут быть проблемы с производительностью системы, ошибки оборудования, ошибки встроенного ПО, проблемы с драйверами устройств или вмешательство фильтров в процессы ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="777ed-122">This problem can be caused system performance issues, hardware errors, firmware errors, device driver problems, or filter driver intervention in the IO process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="777ed-123">Действие пользователя</span><span class="sxs-lookup"><span data-stu-id="777ed-123">User Action</span></span>  
 <span data-ttu-id="777ed-124">Для устранения этой ошибки найдите в журнале системных событий сообщения об ошибках, связанных с оборудованием.</span><span class="sxs-lookup"><span data-stu-id="777ed-124">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="777ed-125">Также изучите журналы оборудования, если они доступны.</span><span class="sxs-lookup"><span data-stu-id="777ed-125">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="777ed-126">При помощи системного монитора проверьте следующие счетчики.</span><span class="sxs-lookup"><span data-stu-id="777ed-126">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="777ed-127">**Среднее время обращения к диску (сек)**</span><span class="sxs-lookup"><span data-stu-id="777ed-127">**Average Disk Sec/Transfer**</span></span>  
  
-   <span data-ttu-id="777ed-128">**Средняя длина очереди диска**</span><span class="sxs-lookup"><span data-stu-id="777ed-128">**Average Disk Queue Length**</span></span>  
  
-   <span data-ttu-id="777ed-129">**Текущая длина очереди диска**</span><span class="sxs-lookup"><span data-stu-id="777ed-129">**Current Disk Queue Length**</span></span>  
  
 <span data-ttu-id="777ed-130">Например, на компьютере, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], значение **среднего времени обращения к диску** обычно не превышает 15 миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="777ed-130">For example, the **Average Disk Sec/Transfer** time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="777ed-131">Если значение **среднего времени обращения к диску** увеличивается, значит подсистема ввода-вывода не справляется с числом запросов на операции ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="777ed-131">If the **Average Disk Sec/Transfer** value increases, this indicates that the I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="777ed-132">Доступ к диску может замедляться антивирусной программой.</span><span class="sxs-lookup"><span data-stu-id="777ed-132">Disk access can be slowed by an antivirus program.</span></span> <span data-ttu-id="777ed-133">Чтобы увеличить скорость доступа, исключите из активных заданий сканирования на вирусы файлы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указанные в сообщении об ошибке.</span><span class="sxs-lookup"><span data-stu-id="777ed-133">To increase access speed, exclude the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files that are specified in the error message from active virus scans.</span></span>  
  
 <span data-ttu-id="777ed-134">Дополнительные сведения об ошибках ввода-вывода см. в [главе 2 документации Microsoft SQL Server по основным операциям ввода-вывода](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) и в статье базы знаний по адресу [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284).</span><span class="sxs-lookup"><span data-stu-id="777ed-134">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) and the Knowledge Base article at [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284).</span></span>  
  
  
