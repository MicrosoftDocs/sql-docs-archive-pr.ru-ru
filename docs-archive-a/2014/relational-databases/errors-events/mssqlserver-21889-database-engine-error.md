---
title: MSSQLSERVER_21889 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c152a542550d7b81af880545f526037baeb4644e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734097"
---
# <a name="mssqlserver_21889"></a>MSSQLSERVER_21889
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21889|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21889|  
|Текст сообщения|Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] «%s» не является издателем репликации. Запустите хранимую процедуру `sp_adddistributor` на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] «%s» с распространителем «%s», чтобы разрешить размещение на данном экземпляре базы данных публикации «%s». Убедитесь, что указаны те же имя входа и пароль, что и на исходном издателе.|  
  
## <a name="explanation"></a>Объяснение  
 Для размещения базы данных издателя экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть издателем репликации. `sp_validate_redirected_publisher` вызывает `sp_helpdistributor` на удаленном сервере, чтобы определить, является ли сервер издателем репликации. Эта ошибка возвращается, если при выполнении хранимой процедуры `sp_helpdistributor` целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не является издателем репликации.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните `sp_adddistributor` на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором расположена база данных издателя. При запуске `sp_adddistributor` правильно укажите распространителя. Используйте то же значение для *@password* параметра, которое использовалось при `sp_adddistributor` первоначальном запуске на распространителе.  
  
  
