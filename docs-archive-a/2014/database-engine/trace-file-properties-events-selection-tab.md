---
title: Свойства файла трассировки (вкладка «Выбор событий») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracefileproperties.eventsselection.f1
helpviewer_keywords:
- Trace File Properties dialog box
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abfadc2b1df4cda039d7e413e5ba0c7777e7c04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734401"
---
# <a name="trace-file-properties-events-selection-tab"></a><span data-ttu-id="bf53f-102">Свойства файла трассировки (вкладка «Выбор событий»)</span><span class="sxs-lookup"><span data-stu-id="bf53f-102">Trace File Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="bf53f-103">Вкладка **Выбор событий** диалогового окна **Свойства шаблона файла трассировки** позволяет просматривать столбец свойств трассировки и удалять из трассировки столбцы данных.</span><span class="sxs-lookup"><span data-stu-id="bf53f-103">Use the **Events Selection** tab of the **Trace File Template Properties** dialog box to view the column properties of the trace or remove data columns from the trace.</span></span>  
  
 <span data-ttu-id="bf53f-104">Для просмотра данного окна откройте файл трассировки.</span><span class="sxs-lookup"><span data-stu-id="bf53f-104">To view this window, open a trace file.</span></span> <span data-ttu-id="bf53f-105">Затем в меню **Файл** выберите пункт **Свойства**и выберите вкладку **Выбор событий** .</span><span class="sxs-lookup"><span data-stu-id="bf53f-105">Then, on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bf53f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bf53f-106">Options</span></span>  
 <span data-ttu-id="bf53f-107">Столбец**События**</span><span class="sxs-lookup"><span data-stu-id="bf53f-107">**Events** column</span></span>  
 <span data-ttu-id="bf53f-108">Просмотр событий трассировки, систематизированных по категориям событий.</span><span class="sxs-lookup"><span data-stu-id="bf53f-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="bf53f-109">Изначально выбираются все события в трассировке.</span><span class="sxs-lookup"><span data-stu-id="bf53f-109">Initially, all events in the trace are selected.</span></span> <span data-ttu-id="bf53f-110">Выбор событий может быть осуществлен путем установки флажка для поля или столбца события.</span><span class="sxs-lookup"><span data-stu-id="bf53f-110">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="bf53f-111">При установке флажка выбираются все столбцы данных, доступные для этого события.</span><span class="sxs-lookup"><span data-stu-id="bf53f-111">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="bf53f-112">Если флажок установлен для столбца данных, автоматически устанавливается флажок для события, а также для всех других необходимых столбцов данных.</span><span class="sxs-lookup"><span data-stu-id="bf53f-112">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="bf53f-113">При просмотре файла трассировки или таблицы снятие флажков событий и столбцов данных уменьшает количество видимых в окне трассировки данных, что облегчает их анализ.</span><span class="sxs-lookup"><span data-stu-id="bf53f-113">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="bf53f-114">Существует также возможность изменения фильтров столбцов, что позволяет уменьшить количество видимых в окне трассировки данных.</span><span class="sxs-lookup"><span data-stu-id="bf53f-114">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="bf53f-115">Дополнительные сведения о классах событий см. в разделе [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span><span class="sxs-lookup"><span data-stu-id="bf53f-115">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="bf53f-116">Столбцы данных</span><span class="sxs-lookup"><span data-stu-id="bf53f-116">Data Columns</span></span>  
 <span data-ttu-id="bf53f-117">Просмотр столбцов данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="bf53f-117">View traced data columns.</span></span> <span data-ttu-id="bf53f-118">По умолчанию для каждого события, включенного в трассировку, помечаются все относящиеся к нему столбцы данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="bf53f-118">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="bf53f-119">Для определения фильтра щелкните заголовок столбца данных и введите критерии фильтра.</span><span class="sxs-lookup"><span data-stu-id="bf53f-119">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="bf53f-120">Отфильтрованные столбцы данных отображаются значком фильтра слева от метки столбца в диалоговом окне **Изменение фильтра** .</span><span class="sxs-lookup"><span data-stu-id="bf53f-120">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="bf53f-121">**Показать все события**</span><span class="sxs-lookup"><span data-stu-id="bf53f-121">**Show all events**</span></span>  
 <span data-ttu-id="bf53f-122">Показать все доступные события.</span><span class="sxs-lookup"><span data-stu-id="bf53f-122">Show all available events.</span></span> <span data-ttu-id="bf53f-123">По умолчанию отображаются только те строки, которые отмечены в сетке **Выбор событий** .</span><span class="sxs-lookup"><span data-stu-id="bf53f-123">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="bf53f-124">Снимите этот флажок, чтобы скрыть все события, не выбранные в сетке **Выбор событий** .</span><span class="sxs-lookup"><span data-stu-id="bf53f-124">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="bf53f-125">Если установлен флажок **Показать все события** и идет просмотр файла или таблицы трассировки, то все события, фиксировавшиеся в ходе трассировки, отображаются в окне трассировки.</span><span class="sxs-lookup"><span data-stu-id="bf53f-125">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="bf53f-126">**Показать все столбцы**</span><span class="sxs-lookup"><span data-stu-id="bf53f-126">**Show all columns**</span></span>  
 <span data-ttu-id="bf53f-127">Показать все доступные столбцы данных.</span><span class="sxs-lookup"><span data-stu-id="bf53f-127">Show all available data columns.</span></span> <span data-ttu-id="bf53f-128">По умолчанию отображаются только выбранные столбцы данных.</span><span class="sxs-lookup"><span data-stu-id="bf53f-128">By default, only data columns that are selected display.</span></span> <span data-ttu-id="bf53f-129">Снимите этот флажок, чтобы скрыть все невыбранные столбцы данных в сетке **Выбор событий** .</span><span class="sxs-lookup"><span data-stu-id="bf53f-129">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="bf53f-130">**Фильтры столбцов**</span><span class="sxs-lookup"><span data-stu-id="bf53f-130">**Column Filters**</span></span>  
 <span data-ttu-id="bf53f-131">Открывает диалоговое окно **Изменить фильтр** , отображающее значок фильтра слева от метки фильтруемых столбцов данных.</span><span class="sxs-lookup"><span data-stu-id="bf53f-131">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label for filtered data columns.</span></span> <span data-ttu-id="bf53f-132">Используйте диалоговое окно **Изменение фильтра** для изменения фильтров столбцов.</span><span class="sxs-lookup"><span data-stu-id="bf53f-132">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="bf53f-133">**Систематизировать столбцы**</span><span class="sxs-lookup"><span data-stu-id="bf53f-133">**Organize Columns**</span></span>  
 <span data-ttu-id="bf53f-134">После выбора **событий** и столбцов данных для трассировки нажмите кнопку **Упорядочить столбцы**, чтобы принудительно переупорядочить столбцы в окне результатов трассировки.</span><span class="sxs-lookup"><span data-stu-id="bf53f-134">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf53f-135">См. также:</span><span class="sxs-lookup"><span data-stu-id="bf53f-135">See Also</span></span>  
 <span data-ttu-id="bf53f-136">[Укажите события и столбцы данных для файла трассировки &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bf53f-136">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="bf53f-137">[Фильтрация событий в SQL Server Profiler &#40;трассировки&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bf53f-137">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="bf53f-138">[Просмотр сведений о фильтре &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bf53f-138">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="bf53f-139">[Изменение &#40;фильтра SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bf53f-139">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="bf53f-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bf53f-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="bf53f-141">Шаблоны и разрешения приложения SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="bf53f-141">SQL Server Profiler Templates and Permissions</span></span>](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
  
  