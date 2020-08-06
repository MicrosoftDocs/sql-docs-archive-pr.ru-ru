---
title: Занятие 3. Синхронизация подписки на публикацию слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
author: rothja
ms.author: jroth
ms.openlocfilehash: bf0256c69d69d1236869fa83285bf4dbf5c462da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739698"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Занятие 3. Синхронизация подписки на публикацию слиянием
  На этом занятии будет запущен агент слияния для инициализации подписки с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Эта процедура также используется для синхронизации с издателем. Приступать к этому занятию нужно только по завершении предыдущего: [Занятие 2. Создание подписки на публикацию слиянием](lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Запуск синхронизации и инициализация подписки  
  
1.  Подключитесь к подписчику в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], раскройте узел сервера, а затем папку **Репликация** .  
  
2.  В папке **Локальные подписки** щелкните правой кнопкой мыши подписку в базе данных **SalesOrdersReplica** и выберите пункт **Просмотр состояния синхронизации**.  
  
3.  Нажмите кнопку **Пуск** , чтобы инициализировать подписку.  
  
## <a name="next-steps"></a>Next Steps  
 Был запущен агент слияния для синхронизации и инициализации подписки. Можно вставить, обновить или удалить данные из таблицы **SalesOrderHeader** или **SalesOrderDetail** на стороне издателя или подписчика, повторить эту процедуру, когда доступно соединение сети, для синхронизации данных между издателем и подписчиком, после чего выполнить запросы к таблице **SalesOrderHeader** или **SalesOrderDetail** на другом сервере, чтобы просмотреть реплицированные изменения.  
  
 На этом раздел «Репликация данных с мобильными клиентами» завершается. Похожий учебник, использующий репликацию транзакций, см. в разделе [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>См. также:  
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)   
 [Синхронизация данных](synchronize-data.md)   
 [Синхронизация подписки по запросу](synchronize-a-pull-subscription.md)  
  
  
