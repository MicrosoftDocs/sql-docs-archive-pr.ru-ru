---
title: Запуск монитора зеркального отображения баз данных (среда SQL Server Management Studio) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- Database Mirroring Monitor [SQL Server], starting
- database mirroring [SQL Server], monitoring
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67c7b393b28d4d400535281c18c637146a5d8da7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654494"
---
# <a name="start-database-mirroring-monitor-sql-server-management-studio"></a>Запуск монитора зеркального отображения баз данных (среда SQL Server Management Studio)
  Монитор зеркального отображения баз данных является частью монитора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запускаемого в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  Монитор зеркального отображения баз данных доступен не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
### <a name="to-launch-the-database-mirroring-monitor"></a>Запуск монитора зеркального отображения баз данных  
  
1.  После подключения к экземпляру основного сервера в обозревателе объектов щелкните имя сервера, чтобы развернуть дерево сервера.  
  
2.  Разверните узел **Базы данных**и выберите базу данных для мониторинга.  
  
3.  Щелкните правой кнопкой мыши базу данных, выберите пункт **Задачи**, а затем щелкните **Запустить монитор зеркального отображения баз данных**.  
  
4.  В диалоговом окне **Монитор зеркального отображения баз данных** нажмите кнопку **Зарегистрировать зеркальную базу данных** , чтобы зарегистрировать одну или более зеркальных баз данных.  
  
    > [!NOTE]  
    >  После регистрации базы данных на одном партнере база данных автоматически регистрируется на других партнерах. Если монитор уже имеет учетные данные соединения для экземпляра другого участника, они используются для подключения. В противном случае, монитор попытается подключиться с помощью проверки подлинности Windows. Если необходимо изменить учетные данные для подключения к экземпляру сервера, установите флажок **Показать диалоговое окно «Управление соединениями сервера» после нажатия кнопки «ОК»**.  
  
 Дополнительные сведения о мониторе зеркального отображения баз данных см. в разделе [Обзор монитора зеркального отображения баз данных](database-mirroring-monitor-overview.md).  
  
## <a name="see-also"></a>См. также:  
 [Зеркальное отображение базы данных (SQL Server)](database-mirroring-sql-server.md)   
 [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
  
