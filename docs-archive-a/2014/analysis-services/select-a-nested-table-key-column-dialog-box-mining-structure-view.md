---
title: Диалоговое окно "Выбор ключевого столбца вложенной таблицы" (представление структуры интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addnestedtable.f1
helpviewer_keywords:
- Select a Nested Table Key Column dialog box
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dc524f6913b7be15e87869355515397a3e0b65c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666786"
---
# <a name="select-a-nested-table-key-column-dialog-box-mining-structure-view"></a>Диалоговое окно «Выбор ключевого столбца вложенной таблицы» (представление структуры интеллектуального анализа данных)
  С помощью диалогового окна **Выбор ключевого столбца вложенной таблицы** можно назначить столбец, который будет ключевым для новой вложенной таблицы. При выходе из диалогового окна в структуру интеллектуального анализа данных, содержащую назначенный ключевой столбец, добавляется новая таблица. Во вложенную таблицу можно добавить дополнительные столбцы, щелкнув структуру правой кнопкой мыши и выбрав команду **Добавить столбец**. Диалоговое окно предлагает несколько параметров в зависимости от того, работаете ли вы с моделью интеллектуального анализа данных OLAP или реляционной моделью интеллектуального анализа данных.  
  
## <a name="options"></a>Варианты  
 **Исходная таблица**  
 Таблица, на которой основана модель интеллектуального анализа данных.  
  
 Это используется только для реляционных моделей интеллектуального анализа данных.  
  
 **Исходный столбец**  
 Список столбцов, доступных в исходной таблице, которые можно использовать в качестве ключевых для вложенной таблицы.  
  
 Это используется только для реляционных моделей интеллектуального анализа данных.  
  
 **Показать тип столбцов**  
 Список типов данных доступных столбцов. Выбрать или очистить типы данных для фильтрации столбцов в списке **Исходный столбец**. В списке **Исходный столбец** будут показаны только столбцы, удовлетворяющие отмеченным типам данных.  
  
 Это используется только для реляционных моделей интеллектуального анализа данных.  
  
 **Атрибуты**  
 Список атрибутов, которые можно использовать в качестве ключевых для вложенной таблицы.  
  
 Это используется только для моделей интеллектуального анализа данных OLAP.  
  
## <a name="see-also"></a>См. также:  
 [Представление структуры интеллектуального анализа &#40;конструктора моделей интеллектуального анализа данных&#41;](mining-structure-view-data-mining-model-designer.md)  
  
  
