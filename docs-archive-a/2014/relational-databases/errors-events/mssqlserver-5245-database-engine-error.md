---
title: MSSQLSERVER_ 5245 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f98c831642580587552bf60c604d84c38fffca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667102"
---
# <a name="mssqlserver_5245"></a>MSSQLSERVER_5245
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5245|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Текст сообщения|Объект с идентификатором O_ID (объект "имя_объекта"): команде DBCC не удалось заблокировать этот объект из-за превышения времени ожидания запроса на блокировку. Этот объект пропущен и останется необработанным.|  
  
## <a name="explanation"></a>Объяснение  
 Истекло время ожидания командой DBCC блокировки таблицы для заданного объекта.  
  
## <a name="user-action"></a>Действие пользователя  
 Повторно выполните команду DBCC.  
  
  
