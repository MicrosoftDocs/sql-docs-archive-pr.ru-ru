---
title: MSSQLSERVER_10538 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: edc6abf192a3341f9b84c99e99071343cc882c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731689"
---
# <a name="mssqlserver_10538"></a>MSSQLSERVER_10538
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10538|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_INVALID_PLANGUIDE_HANDLE|  
|Текст сообщения|Не удается найти структуру плана, поскольку указанный идентификатор структуры плана имеет значение NULL или является недопустимым, либо отсутствует разрешение на объект, упоминаемый в структуре плана. Убедитесь, что идентификатор структуры плана является допустимым, текущий сеанс настроен на правильный контекст базы данных и имеется разрешение ALTER DATABASE или разрешение ALTER на объект, упоминаемый в структуре плана.|  
  
## <a name="explanation"></a>Объяснение  
 Идентификатор указанной структуры плана имеет значение NULL или является недопустимым, либо отсутствует разрешение на объект, указанный в структуре плана.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что идентификатор структуры плана допустим, текущий сеанс настроен на правильный контекст базы данных и имеется разрешение ALTER DATABASE или разрешение ALTER на объект, упоминаемый в структуре плана.  
  
## <a name="see-also"></a>См. также:  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
