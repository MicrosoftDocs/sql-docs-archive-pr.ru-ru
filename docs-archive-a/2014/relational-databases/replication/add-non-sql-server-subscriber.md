---
title: Добавление подписчика, отличного от подписчика SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e36d048b11fcc71b27ab0ab2ee815b0284187c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664884"
---
# <a name="add-non-sql-server-subscriber"></a>Добавить подписчик, отличный от подписчика SQL Server
  Репликация поддерживает принудительные подписки на моментальные снимки и публикации транзакций для подписчиков Oracle и IBM DB2.  
  
## <a name="options"></a>Параметры  
 **Тип добавляемого подписчика:**  
 Выберите подписчик Oracle или подписчик IBM DB2. Дополнительные сведения о поддержке таких подписчиков см. в статье [Подписчики, отличные от подписчиков SQL Server](non-sql/non-sql-server-subscribers.md).  
  
 **Имя источника данных**  
 Данное имя позволяет найти базу данных в сети. Строка соединения с базой данных, формируемая репликацией, содержит имя источника данных, имя входа, пароль и параметры соединения, указанные на странице **Безопасность агента распространителя** данного мастера.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не проверяет имя источника данных и строку подключения, пока агент распространителя не попытается инициализировать подписку.  
  
## <a name="see-also"></a>См. также:  
 [Создание подписки для подписчика, отличного от подписчика SQL Server](create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [Подписка на публикации](subscribe-to-publications.md)  
  
  
