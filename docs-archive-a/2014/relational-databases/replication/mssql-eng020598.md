---
title: MSSQL_ENG020598 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cef26001c353dea94ec9b658dfb38285231bc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730510"
---
# <a name="mssql_eng020598"></a>MSSQL_ENG020598
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20598|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|При применении реплицированной команды строка на подписчике не была найдена.|  
  
## <a name="explanation"></a>Объяснение  
 Данная ошибка возникает в репликации транзакций, если строка, которую агент распространителя пытается обновить на подписчике, была удалена или ее первичный ключ был изменен. По умолчанию для подписчиков все подписки на публикацию транзакций доступны только для чтения, так как все изменения нельзя применить на издателе. В случае с репликацией транзакций пользователь должен вносить изменения на подписчике только при использовании обновляемых подписок или одноранговой репликации. Сведения об этих параметрах см. в разделе [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) и [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).  
  
## <a name="user-action"></a>Действие пользователя  
 **Чтобы разрешить эту проблему:**  
  
1.  Если в ходе репликации был обнаружен источник ошибки, но репликация при этом должна быть продолжена, укажите параметр **-SkipErrors 20598** для агента распространителя. Это позволит агенту пропустить изменения, приведшие к ошибке 20598, но разрешит при этом репликацию других изменений.  
  
2.  Определите на подписчике строки, которые были удалены или имеют первичный ключ, отличный от первичного ключа соответствующих строк на издателе. При помощи [tablediff Utility](../../tools/tablediff-utility.md) можно определить, какие строки в базах данных публикации и подписки отличаются. Сведения об использовании этой программы с реплицированными базами данных см. в статье [Сравнение реплицируемых таблиц на предмет различий (программирование репликации)](administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
3.  Используя программу **tablediff** или другой способ, внесите необходимые исправления в строки подписчика.  
  
4.  Удалите параметр **-SkipErrors** (необязательно).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
