---
title: Реплика доступности не присоединена | Документы Майкрософт
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7c4f76e98d373e50124f5ca2b135a9fad8f34226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733153"
---
# <a name="availability-replica-is-not-joined"></a>Реплика доступности не присоединена
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние присоединения реплики доступности|  
|**Проблема**|Реплика доступности не присоединена.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|Реплика доступности|  
  
## <a name="description"></a>Описание  
 Эта политика проверяет состояние присоединения реплики доступности. Политика находится в состоянии неисправности, когда реплика доступности добавлена в группу доступности, но она не присоединена с соблюдением всех требований. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях приведены в разделе [Реплика доступности не присоединена](https://go.microsoft.com/fwlink/p/?LinkId=220859) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Вторичная реплика не присоединена к группе доступности. Реплика доступности успешно присоединена к группе доступности, когда она имеет состояние присоединения «Присоединенный автономный экземпляр» (1) или «Присоединенный отказоустойчивый кластер» (2).  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте Transact-SQL, PowerShell или среду SQL Server Management Studio для присоединения вторичной реплики к группе доступности. Дополнительные сведения о присоединении вторичных реплик к группам доступности приведены в разделе [Присоединение вторичной реплики к группе доступности (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
