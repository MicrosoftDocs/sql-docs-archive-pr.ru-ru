---
title: Средство запуска управляющей программы полнотекстовой фильтрации SQL (диспетчер конфигурации SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45194c893db048151cdb03d33f1419ef42246d69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654699"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>Средство запуска управляющей программы полнотекстовой фильтрации SQL (диспетчер конфигурации SQL Server)
  Начиная с версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], в полнотекстовом поиске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется средство запуска управляющей программы полнотекстовой фильтрации SQL (средство запуска FDHOST) для запуска хост-процесса управляющей программы полнотекстовой фильтрации, которая выполняет фильтрацию полнотекстового поиска и разбиение по словам. Для использования полнотекстового поиска эта служба должна быть запущена. Средство запуска FDHOST представляет собой привязанную к экземпляру службу, которая связана с конкретным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта служба передает сведения об учетной записи службы в каждый запущенный хост-процесс управляющей программы фильтрации. Сведения о хост-процессах управляющей программы фильтрации см. в разделе «Архитектура компонента Full-Text Search» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
