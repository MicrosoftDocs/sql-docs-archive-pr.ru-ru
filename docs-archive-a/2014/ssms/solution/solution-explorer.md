---
title: Обозреватель решений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- solutions [SQL Server Management Studio], about solutions
- SQL Server Management Studio [SQL Server], items
- items [SQL Server]
ms.assetid: 0df09843-0d4f-4925-bc6c-99265035a0c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa312f5e097fa1c59b9ba545709dc964a184c3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658022"
---
# <a name="solution-explorer"></a>Обозреватель решений
  Панель обозревателя решений в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит контейнеры (проекты) для управления такими элементами, как скрипты базы данных, запросы, подключения к данным и файлы. Один или несколько связанных между собой проектов могут быть объединены в контейнер, который называется решением.  
  
 Решение содержит один или несколько проектов, а также файлы и метаданные, которые позволяют определить решение как единое целое. Проект — это набор файлов и относящихся к ним метаданных, например сведений о соединении. Решения и проекты содержат элементы, которые представляют собой скрипты, запросы, сведения о соединениях и файлы, необходимые для создания решения базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="benefits-of-using-solutions"></a>Преимущества использования решений  
 Эти контейнеры позволяют:  
  
-   реализовать систему управление версиями для запросов и скриптов;  
  
-   управлять параметрами как решения в целом, так и конкретных проектов;  
  
-   облегчить работу с файлами и позволить сосредоточиться на работе с элементами, которые составляют решение базы данных;  
  
-   добавлять элементы одновременно к нескольким проектам решения либо ко всему решению, не указывая элемент в каждом из проектов;  
  
-   работать с различными файлами, формат которых не зависит от решений и проектов.  
  
 Элементы, содержащиеся в проектах, зависят от типа проекта и от того, используется ли среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="related-tasks"></a>Связанные задачи  
 Используйте следующие разделы для начала работы с решениями SQL Server.  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает, как добавить один или несколько проектов в решение.|[Решения (среда SQL Server Management Studio)](solutions-sql-server-management-studio.md)|  
|Описывает, как создать проект и добавить элементы, например скрипты и соединения.|[Проекты (SQL Server Management Studio)](projects-sql-server-management-studio.md)|  
|Описывает, как интегрировать решения или отдельные проекты в систему управления исходными кодами.|[Обозреватель решений для системы управления версиями](../../database-engine/solution-explorer-source-control.md)|  
|Сведения о файлах, используемых средой [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для управления решениями и файлами.|[Файлы для управления решениями и проектами](files-that-manage-solutions-and-projects.md)|  
  
  
