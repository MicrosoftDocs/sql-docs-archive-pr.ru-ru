---
title: База данных доступности приостановлена | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07a547f217367f13df739348325461c862d831f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655391"
---
# <a name="availability-database-is-suspended"></a>База данных доступности приостановлена
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние приостановки базы данных доступности|  
|**Проблема**|База данных доступности приостановлена.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|База данных доступности|  
  
## <a name="description"></a>Описание  
 Эта политика проверяет состояние перемещения данных базы данных-получателя (которая также называется «реплика базы данных-получателя»). Эта политика находится в нерабочем состоянии, если перемещение данных приостановлено. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>   Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях доступны в разделе [База данных доступности приостановлена](https://go.microsoft.com/fwlink/p/?LinkId=220860) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Возможны следующие причины приостановки синхронизации данных в этой базе данных доступности:  
  
-   Из-за ошибки система могла приостановить синхронизацию данных.  
  
-   Администратор базы данных мог приостановить синхронизацию данных для выполнения задач технического обслуживания.  
  
## <a name="possible-solution"></a>Возможное решение  
 Восстановите синхронизацию данных. При повторном возникновении проблемы проверьте группу доступности в журнале событий, а затем с помощью диагностики определите причину приостановки перемещения данных системой.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
