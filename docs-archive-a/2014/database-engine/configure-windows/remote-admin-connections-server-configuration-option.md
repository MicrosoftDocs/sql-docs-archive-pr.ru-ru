---
title: Параметр конфигурации сервера "remote admin connections" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c17cf278d18444c5b93d4f4b7e0a3da8dbfb671e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667393"
---
# <a name="remote-admin-connections-server-configuration-option"></a>Параметр конфигурации сервера «remote admin connections»
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет выделенное административное соединение (DAC). Такое подключение позволяет администратору получать доступ к серверу для выполнения диагностических функций или инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или решения проблем на сервере, даже когда сервер заблокирован или работает в аварийном состоянии и не отвечает на соединение компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . По умолчанию выделенные административные соединения доступны только с клиента на сервер. Чтобы разрешить клиентским приложениям на удаленных компьютерах подключение DAC, используйте параметр remote admin connections хранимой процедуры sp_configure.  
  
 По умолчанию DAC ожидает соединения только на IP-адресе обратной связи (127.0.0.1), порт 1434. Если TCP-порт 1434 недоступен, то TCP-порт динамически назначается при запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Если на компьютере установлено более одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо проверить номер TCP-порта в журнале ошибок.  
  
 В следующей таблице приведены возможные значения параметра remote admin connections.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Означает, что разрешены только локальные соединения через DAC.|  
|1|Означает, что разрешены удаленные соединения через DAC.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано подключение через DAC с удаленного компьютера.  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Диагностическое соединение для администраторов баз данных](diagnostic-connection-for-database-administrators.md)  
  
  
