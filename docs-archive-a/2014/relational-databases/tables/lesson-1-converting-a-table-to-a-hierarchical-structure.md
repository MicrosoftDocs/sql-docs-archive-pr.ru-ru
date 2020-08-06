---
title: Занятие 1. Преобразование таблицы в иерархическую структуру | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 196a546093786f9be4b88536763b3150ae750f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749692"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Урок 1. преобразование таблицы в иерархическую структуру
  Если у клиентов имеются таблицы, в которых для выражения иерархических связей используются самосоединения, то эти таблицы можно преобразовать в иерархическую структуру, руководствуясь указаниями из данного занятия. Миграция от старого метода представления к методу представления, использующему тип данных `hierarchyid`, проходит относительно легко. После миграции пользователи получат компактное и легкое для понимания иерархическое представление, которое может быть проиндексировано несколькими способами для обеспечения эффективного поиска.  
  
 В этом занятии происходит изучение существующей таблицы, создание новой таблицы, содержащей столбец `hierarchyid`, заполнение этой таблицы данными из таблицы источника, а также проводится демонстрация трех стратегий индексирования. Это занятие содержит следующие разделы:  
  
-   [Изучение текущей структуры таблицы сотрудников](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Заполнение таблицы существующими иерархическими данными](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Оптимизация таблицы NewOrg](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Сводка. Преобразование таблицы в иерархическую структуру](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для этого занятия требуется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Изучение текущей структуры таблицы сотрудников](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 2. Создание данных и управление ими в иерархической таблице](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
