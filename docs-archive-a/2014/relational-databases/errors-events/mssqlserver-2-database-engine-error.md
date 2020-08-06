---
title: MSSQLSERVER_2 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 87d19a24219fda79de2cad4c06af4f1936b37b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667145"
---
# <a name="mssqlserver_2"></a>MSSQLSERVER_2
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|При соединении с сервером произошла ошибка.  Эта ошибка при соединении с SQL Server может быть вызвана тем, что в параметрах SQL Server по умолчанию запрещены удаленные соединения. (поставщик: поставщик именованных каналов, ошибка: 40: не удалось открыть соединение с SQL Server (поставщик данных .Net SqlClient)|  
  
## <a name="explanation"></a>Объяснение  
 Вероятно, от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поступил ответ на запрос клиента, потому что этот сервер не был запущен.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что сервер запущен.  
  
## <a name="see-also"></a>См. также:  
 [Управление службами компонента Database Engine](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Сетевые протоколы и сетевые библиотеки](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Конфигурация клиентской сети](../../database-engine/configure-windows/client-network-configuration.md)   
 [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
