---
title: MSSQLSERVER_9002 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40fe70db8849d09f9296a06cbeed65a9c71e5a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666068"
---
# <a name="mssqlserver_9002"></a>MSSQLSERVER_9002
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9002|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LOG_IS_FULL|  
|Текст сообщения|Журнал транзакций для базы данных «%.*ls» заполнен. Чтобы выяснить, почему пространство журнала не может быть использовано повторно, см. столбец log_reuse_wait_desc в представлении каталога sys.databases.|  
  
## <a name="explanation"></a>Объяснение  
 Недостаточно места в журнале базы данных. Столбец **log_reuse_wait_desc** в представлении каталога **sys.databases** показывает, почему пространство журнала не может использоваться повторно.  
  
## <a name="user-action"></a>Действие пользователя  
 Используя представление каталога **sys.databases**, определите, почему журнал полон, и исправьте неполадку. Дополнительные сведения см. в разделе «Устранение неполадок в полном журнале транзакций (ошибка 9002)» электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [Устранение неполадок при переполнении журнала транзакций (ошибка SQL Server 9002)](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)   
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
