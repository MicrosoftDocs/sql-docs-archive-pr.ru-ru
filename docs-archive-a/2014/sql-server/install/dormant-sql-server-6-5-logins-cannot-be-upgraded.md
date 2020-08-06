---
title: Не удается обновить неактивные SQL Server 6,5 для входа | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f78bca9bf2b99b2ab6f530613b64bc0e46c4001c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659193"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>Невозможно обновить неактивные имена входа SQL Server 6.5
  Советник по переходу обнаружил имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], пароль которого нельзя напрямую обновить до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Чтобы активировать имя входа, необходимо сбросить его пароль. Можно изменить пароль с помощью инструкции ALTER LOGIN.  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 Новый пароль будет проверен на соответствие политике сложности паролей системы, если проверка политики не отключена. Рекомендуется использовать сложные пароли и не отключать политику проверки. Параметр MUST_CHANGE принуждает пользователя выбрать новый пароль. Это не обязательно, но рекомендуется.  
  
 Можно определить неактивные имена входа с помощью следующего запроса:  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
