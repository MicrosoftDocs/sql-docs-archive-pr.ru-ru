---
title: Параметр конфигурации сервера "disallow results from triggers" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f162a6e06706561d861bfc54a1ae4027f2c3466e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727346"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a>Параметр конфигурации сервера «disallow results from triggers»
  Параметр **disallow results from triggers** предназначен, чтобы определить, разрешается ли триггерам возвращать результирующие наборы. Триггеры, возвращающие результирующие наборы, могут привести к непредвиденному поведению приложений, не предназначенных для работы с ними.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Рекомендуется установить это значение равным 1.  
  
 При установке в значение 1 параметр **disallow results from triggers** включается (ON). Значение по умолчанию для этого параметра равно 0 (OFF). Если этот параметр равен 1 (ON), любая попытка триггера вернуть результирующий набор завершается неудачей и пользователь получает следующее сообщение об ошибке:  
  
 "Сообщение 524, уровень 16, состояние 1, процедура \<Procedure Name>, строка \<Line#>  
  
 «Триггер возвратил результирующий набор при параметре сервера "disallow results from triggers", равном True».  
  
 Параметр **disallow results from triggers** применяется на уровне экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то есть определяет работу всех триггеров, существующих в данном экземпляре.  
  
 Параметр **disallow results from triggers** является дополнительным. Изменить значение этого параметра при помощи системной хранимой процедуры **sp_configure** можно только при условии, если параметр **show advanced options** имеет значение 1. Параметр вступает в силу сразу без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
