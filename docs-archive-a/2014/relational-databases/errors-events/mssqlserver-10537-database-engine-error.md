---
title: MSSQLSERVER_10537 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b1baccad5236bd8c1a71024b7dd542cc9d11cbd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734129"
---
# <a name="mssqlserver_10537"></a>MSSQLSERVER_10537
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10537|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_DUP_ENABLED|  
|Текст сообщения|Не удается включить структуру плана '%.*ls', поскольку включенная структура плана '%.\*ls' содержит ту же область и то же значение начального смещения для инструкции. Отключите существующую структуру плана перед включением указанной структуры.|  
  
## <a name="explanation"></a>Объяснение  
 Существующая структура плана содержит ту же область и то же значение начального смещения, что и инструкция в указанной структуре плана.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключите существующую структуру плана перед включением указанной структуры.  
  
## <a name="see-also"></a>См. также:  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
