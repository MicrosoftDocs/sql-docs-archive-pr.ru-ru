---
title: MSSQL_ENG014144 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d93f06a585bcc01c52438ff7b99bbd635532402
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654182"
---
# <a name="mssql_eng014144"></a>MSSQL_ENG014144
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14144|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Невозможно удалить подписчик '%s'. В базе данных публикации '%s' для него есть подписки.|  
  
## <a name="explanation"></a>Объяснение  
 Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , настроенный в качестве подписчика, не может быть удален из роли подписчика до тех пор, пока есть активные подписки, настроенные для данного экземпляра.  
  
## <a name="user-action"></a>Действие пользователя  
 Удалите все связанные подписки, прежде чем пытаться изменить состояние подписчика для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
1.  Выполните [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) в базе данных публикации в издателе, чтобы найти подписки.  
  
2.  Выполните [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) в базе данных публикации в издателе, чтобы удалить подписки.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)   
 [Подписка на публикации](subscribe-to-publications.md)  
  
  
