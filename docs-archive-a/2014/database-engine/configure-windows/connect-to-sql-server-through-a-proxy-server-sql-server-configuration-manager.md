---
title: Подключение к SQL Server через прокси-сервер (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: de22ad6043c509f08471a6bea40c0efa18d76842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665545"
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a>Подключение к SQL Server через прокси-сервер (диспетчер конфигурации SQL Server)
  В этом разделе описано, как в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] установить соединение с SQL Server через прокси-сервер с помощью диспетчера конфигурации SQL Server. Для удаленного прослушивания прокси-сервером Remote WinSock (RWS) определите таблицу локальных адресов (LAT) для прокси-сервера таким образом, чтобы адрес прослушивающего узла находился вне диапазона записей LAT.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a>Обеспечение соединений с SQL Server с помощью прокси-сервера Microsoft  
  
1.  Следуйте указаниям в разделе [Настройка сервера для прослушивания указанного TCP-порта (SQL Server Configuration Manager)](configure-a-server-to-listen-on-a-specific-tcp-port.md), чтобы определить, какие TCP/IP-порты используются [!INCLUDE[ssDE](../../includes/ssde-md.md)], или настроить [!INCLUDE[ssDE](../../includes/ssde-md.md)] для использования нужного порта.  
  
2.  В прокси-сервере определите таблицу локальных адресов (LAT) для прокси-сервера таким образом, чтобы адрес прослушивающего узла находился вне диапазона записей LAT. Дополнительные сведения см. в документации по прокси-серверу.  
  
  
