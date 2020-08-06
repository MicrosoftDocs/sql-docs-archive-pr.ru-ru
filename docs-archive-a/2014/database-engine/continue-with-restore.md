---
title: Продолжить восстановление | Документация Майкрософт
description: В SQL Server используйте диалоговое окно продолжение восстановления, чтобы указать, нужно ли восстанавливать следующий резервный набор данных.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.continuerestore.f1
ms.assetid: 987ac05f-57c0-49a9-9903-9889717aae4f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c7a438ac7b8696d2f57bdf93ff86030cf607e682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740313"
---
# <a name="continue-with-restore"></a>Продолжить восстановление
  Диалоговое окно **Продолжение восстановления** используется для указания, нужно ли восстанавливать следующий резервный набор данных в последовательности восстановления. Чтобы приостановить операцию восстановления, например при смене ленты, завершите подготовительные операции и нажмите кнопку **ОК**.  
  
 Нажатие на кнопку **Нет** останавливает последовательность восстановления, оставляя базу данных в состоянии восстановления из копии. Чтобы продолжить восстановление позже, используйте задачи **Восстановить базу данных** или **Восстановить журнал транзакций** в зависимости от ситуации.  
  
## <a name="options"></a>Варианты  
 **Набор носителей**  
 Отображает имя следующего набора носителей (если доступно).  
  
 **Резервный набор данных**  
 Отображает имя резервного набора данных.  
  
 **Описание резервного набора данных**  
 Отображает описание резервного набора данных.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр содержимого ленты или файла резервной копии (SQL Server)](../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)   
 [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)   
 [Восстановление резервной копии базы данных &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [Восстановление резервной копии журнала транзакций (SQL Server)](../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
  
