---
title: Диспетчер соединений ODBC | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1069e31f3f8ffaf14dde091d913ff6d9f8fa7cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658345"
---
# <a name="odbc-connection-manager"></a>диспетчер соединений ODBC
  Диспетчер соединений ODBC позволяет пакету подключаться к разнообразным системам управления базами данных, используя открытый интерфейс взаимодействия с базами данных (ODBC).  
  
 При добавлении подключения ODBC к пакету и задании свойств диспетчера соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер соединений и добавляет его в `Connections` коллекцию пакета. Во время выполнения диспетчер соединений рассматривается как физическое соединение с ODBC.  
  
 Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `ODBC`.  
  
 Настроить диспетчер соединений ODBC можно следующими способами:  
  
-   Предоставить строку соединения, которая ссылается на пользовательское или системное имя источника данных.  
  
-   Указать сервер, к которому нужно подключиться.  
  
-   Указать, сохранять ли соединение во время выполнения.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Настройка диспетчера соединений ODBC  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [Справочник по пользовательскому интерфейсу диспетчера подключений ODBC](../odbc-connection-manager-ui-reference.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](integration-services-ssis-connections.md)  
  
  
