---
title: Просмотр журнала приложений Windows (Windows) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1255e95833d9fc56abd1700f5acb0d2f49ebf77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731549"
---
# <a name="view-the-windows-application-log-windows"></a>Просмотр журнала приложений Windows (Windows)
  Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен на использование журнала приложений Windows, каждый сеанс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает новые события в этот журнал. В отличие от журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , новый журнал приложений не создается заново каждый раз при запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="to-view-the-windows-application-log"></a>Просмотр журнала приложений Windows  
  
1.  В меню **Пуск** укажите пункт **Все программы**, затем **Администрирование**и выберите пункт **Просмотр событий**.  
  
2.  В окне «Просмотр событий» щелкните элемент **Приложение**.  
  
3.  События [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентифицируются записью **MSSQLSERVER** в столбце **Источник** (именованные экземпляры обозначаются как **MSSQL$** _<имя_экземпляра>_ ). События агента SQL Server идентифицируются записью SQLSERVERAGENT (для именованных экземпляров сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентифицируются при помощи **SQLAgent$** \<*instance_name*>). События службы Microsoft Search идентифицируются записью **Microsoft Search**.  
  
4.  Чтобы просмотреть журнал другого компьютера, щелкните правой кнопкой мыши в окне **Просмотр событий**, выберите пункт **Подключение к другому компьютеру** и заполните диалоговое окно **Выбор компьютера**.  
  
5.  Дополнительно для отображения только событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в меню **Просмотр** выберите пункт **Фильтрация**и в списке **Источник событий** выберите **MSSQLSERVER**. Чтобы просмотреть только события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в списке **Источник события** вместо этого выберите **SQLSERVERAGENT** .  
  
6.  Чтобы просмотреть дополнительные сведения о событии, дважды щелкните событие.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)](../../ssms/sql-server-management-studio-ssms.md)  
  
  
