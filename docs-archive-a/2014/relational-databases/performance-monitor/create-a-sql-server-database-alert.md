---
title: Создание предупреждения для базы данных SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fd0cc926412d64f7686744ee60840a32473d2386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739755"
---
# <a name="create-a-sql-server-database-alert"></a>Создание предупреждения для базы данных SQL Server
  Можно использовать системный монитор для создания предупреждения, которое будет выводиться, когда счетчик компонента System Monitor достигает порогового значения. В ответ на предупреждение системный монитор запускает приложение, такое как пользовательское приложение, созданное для обработки условий предупреждения. Например можно создать предупреждение, которое будет выводиться, когда число взаимоблокировок превысит заданное значение.  
  
 Предупреждения также могут задаваться при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Оповещения](../../ssms/agent/alerts.md).  
  
 Дополнительные сведения об использовании системного монитора для настройки предупреждения базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Настройка оповещения базы данных SQL Server (Windows)](../performance/set-up-a-sql-server-database-alert-windows.md).  
  
## <a name="see-also"></a>См. также:  
 [sp_add_alert (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)   
 [sys.sysperfinfo (Transact-SQL)](/sql/relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql)  
  
  
