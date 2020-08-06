---
title: Удаление соединений (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b037e317b629671f6ec5ea1fa90edfca6fafa627
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653989"
---
# <a name="remove-joins-visual-database-tools"></a>Удаление соединений (визуальные инструменты для баз данных)
  Если нежелательно, чтобы таблицы были соединены с помощью внутреннего или внешнего соединения, можно удалить это соединение между таблицами. Например, можно удалить соединение, автоматически созданное между двумя таблицами в [конструкторе запросов и представлений](visual-database-tools.md) .  
  
> [!NOTE]  
>  Удаление соединения из запроса не влияет на базовые связи, существующие в базе данных.  
  
 Если две соединяемые таблицы являются частью запроса и все условия соединения между ними удаляются, то результирующий запрос становится пересечением этих таблиц, то есть перекрестным соединением (CROSS JOIN).  
  
### <a name="to-remove-a-join"></a>Удаление соединения  
  
-   На [панели диаграммы](diagram-pane-visual-database-tools.md)выберите удаляемую линию соединения и нажмите клавишу DELETE. Можно одновременно выбрать и удалить несколько линий соединений.  
  
 Конструктор запросов и представлений удаляет линию соединения и изменяет инструкцию на [панели SQL](sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
 [Автоматическое соединение таблиц &#40;визуальных инструментов для баз данных&#41;](join-tables-automatically-visual-database-tools.md)   
 [Соединение таблиц вручную &#40;визуальных инструментов для баз данных&#41;](join-tables-manually-visual-database-tools.md)   
 [Запросы с соединениями (визуальные инструменты для баз данных)](query-with-joins-visual-database-tools.md)  
  
  
