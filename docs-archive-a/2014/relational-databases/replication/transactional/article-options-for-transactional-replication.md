---
title: Параметры статьи для репликации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1cc13a3d11e35ed47eac4ff401fb8b7cb607b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664856"
---
# <a name="article-options-for-transactional-replication"></a>Параметры статьи для репликации транзакций
  Для статей в публикациях транзакций существует несколько параметров. Репликация транзакций позволяет выполнять следующее:  
  
-   Задавать способ передачи изменений от издателя подписчикам. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](transactional-articles-specify-how-changes-are-propagated.md).  
  
-   Указывать, что необходима репликация выполнения хранимой процедуры. Это полезно при репликации результатов хранимых процедур, связанных с обслуживанием и работающих с большими объемами данных. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Укажите параметры схемы, например копируются ли ограничения и триггеры на подписчик. Дополнительные сведения см. в разделе [Указание параметров схемы](../publish/specify-schema-options.md).  
  
-   Использовать фильтры строк и фильтры столбцов. Фильтрация статей таблиц позволяет создавать секции публикуемых данных. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](../publish/filter-published-data.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../publish/publish-data-and-database-objects.md)  
  
  
