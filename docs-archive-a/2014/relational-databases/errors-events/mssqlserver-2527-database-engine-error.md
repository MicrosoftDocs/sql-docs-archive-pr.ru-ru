---
title: MSSQLSERVER_2527 | | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 900707634a016ecfd29f9f676e68b4d2f557ccea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657799"
---
# <a name="mssqlserver_2527"></a>MSSQLSERVER_2527
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2527|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_INDEX_FILEGROUP_IS_OFFLINE|  
|Текст сообщения|Невозможно обработать индекс I_NAME таблицы O_NAME, так как файловая группа F_NAME находится в режиме «вне сети».|  
  
## <a name="explanation"></a>Объяснение  
 Это информационное сообщение указывает, что индекс невозможно проверить, поскольку одна из файловых групп, в которой хранятся данные индекса, находится в режиме «вне сети». Состояние файлов в файловой группе определяет доступность всей файловой группы. Чтобы файловая группа была доступна, необходимо, чтобы все файлы в файловой группе находились в режиме в сети. Если других проблем нет, будут проверяться все остальные индексы того же объекта.  
  
## <a name="user-action"></a>Действие пользователя  
 Чтобы просмотреть текущее состояние файлов указанной файловой группы, выполните запрос к представлению каталога **sys.database_files** или**sys.master_files**.  
  
 Восстановите автономный файл из резервной копии.  
  
## <a name="see-also"></a>См. также:  
 [sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)   
 [sys. master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
