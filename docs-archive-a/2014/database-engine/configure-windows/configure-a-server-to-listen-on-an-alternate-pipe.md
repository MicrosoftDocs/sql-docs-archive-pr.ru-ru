---
title: Настройка сервера для прослушивания альтернативного канала (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 57d70cf4cd1d7474b895aeb8cb144c885e8a0f99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655360"
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe-sql-server-configuration-manager"></a>Настройка сервера для прослушивания альтернативного канала (диспетчер конфигурации SQL Server)
  В этом разделе описан процесс настройки сервера на прослушивание другого канала в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. По умолчанию неименованный экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] прослушивает именованный канал \\\\.\pipe\sql\query. Именованные экземпляры компонентов [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и [!INCLUDE[ssEW](../../includes/ssew-md.md)] настроены на прослушивание других каналов.  
  
 Клиентское приложение можно подключить к конкретному именованному каналу тремя способами:  
  
-   запустив на сервере службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   создав псевдоним клиента с указанием именованного канала;  
  
-   Настройте клиент на использование пользовательской строки подключения.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a>Настройка именованного канала, используемого компонентом SQL Server Database Engine  
  
1.  В области консоли диспетчера конфигурации SQL Server разверните узел **Сетевая конфигурация SQL Server**, а затем **Протоколы для** *\<instance name>* .  
  
2.  В области сведений щелкните правой кнопкой мыши **Именованные каналы**и выберите пункт **Свойства**.  
  
3.  На вкладке **Протоколы** в поле **Имя канала** укажите канал, который должен прослушиваться компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] , и нажмите кнопку **ОК**.  
  
4.  В области консоли выберите **Службы SQL Server**.  
  
5.  В области сведений щелкните правой кнопкой мыши **SQL Server (** \<instance name> **)** и выберите команду **Перезапустить**, чтобы остановить и снова запустить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает альтернативный канал, то подключить клиентское приложение к конкретному именованному каналу можно тремя способами:  
  
-   запустив на сервере службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   создав псевдоним клиента с указанием именованного канала;  
  
-   Настройте клиент на использование пользовательской строки подключения.  
  
## <a name="see-also"></a>См. также:  
 [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](create-or-delete-a-server-alias-for-use-by-a-client.md)   
 [Сетевая конфигурация сервера](server-network-configuration.md)  
  
  
