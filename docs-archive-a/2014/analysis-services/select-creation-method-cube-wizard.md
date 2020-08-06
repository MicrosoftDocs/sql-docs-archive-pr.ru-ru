---
title: Выбор метода создания (мастер кубов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
author: minewiskan
ms.author: owend
ms.openlocfilehash: c8c4d611e00a2b3f5d115ea5749b1e494a44bf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667411"
---
# <a name="select-creation-method-cube-wizard"></a>Выберите метод построения (мастер кубов)
  Страница **Выбор метода создания** позволяет задать метод создания куба.  
  
## <a name="options"></a>Варианты  
 **Использовать существующие таблицы**  
 Выберите этот параметр, чтобы создать куб с использованием таблиц, существующих в источнике данных. При построении нового куба мастер предоставит вам последовательные рекомендации по процессу выбора и определения групп мер и измерений, основанных на существующих таблицах.  
  
 **Создать пустой куб**  
 Позволяет создать пустой куб. Этот параметр используется при необходимости создания вручную либо когда все группы мер куба являются связанными группами мер.  
  
> [!NOTE]  
>  Этот параметр доступен только при работе с проектом служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и отсутствии прямого подключения к базе данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Создать таблицы в источнике данных**  
 Позволяет сначала создать куб, а затем на основе его определения создать в источнике данных новые таблицы.  
  
> [!NOTE]  
>  Чтобы использовать этот параметр, необходимо иметь разрешение на создание объектов в базовом источнике данных.  
  
 При выборе этого параметра становится доступным параметр **Шаблон** .  
  
 **Шаблон**  
 Выберите шаблон, используемый для создания куба. Шаблоны предоставляют набор определений, ориентированных на конкретную бизнес-задачу.  
  
> [!NOTE]  
>  Этот параметр доступен, только если выбран параметр **Создать таблицы в источнике данных** .  
  
## <a name="see-also"></a>См. также:  
 [Объекты куба &#40;Analysis Services многомерных данных&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [Кубы в многомерных моделях](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Измерения в многомерных моделях](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
