---
title: MSSQLSERVER_-2 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d39b4a11387a60056bba3f87adffcb2653b60f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732689"
---
# <a name="mssqlserver_-2"></a>MSSQLSERVER_-2
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|-2|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Время ожидания истекло.  Время ожидания истекло до завершения операции, либо сервер не отвечает. (Microsoft SQL Server, ошибка: –2)|   
  
## <a name="explanation"></a>Объяснение  
 Клиенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается установить соединение с сервером. Эта ошибка возникает, если брандмауэр сервера отказывает в соединении. 
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что в брандмауэре на экземпляре сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешен прием соединений.  
  
## <a name="see-also"></a>См. также:  
 [Настройка брандмауэра Windows на разрешение доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)   
 [Настройка брандмауэра Windows для доступа к ядро СУБД](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Сетевые протоколы и сетевые библиотеки](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Конфигурация клиентской сети](../../database-engine/configure-windows/client-network-configuration.md)   
 [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
