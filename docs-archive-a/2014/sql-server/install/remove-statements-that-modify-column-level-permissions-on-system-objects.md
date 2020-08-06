---
title: Удалите инструкции, изменяющие разрешения уровня столбца на системные объекты | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e55af3dca0c55c2babd09bc6cfc48ed0ddf3ad7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666369"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>Удаление инструкций, которые изменяют разрешения уровня столбца в системных объектах
  Помощник по обновлению обнаружил нестандартные разрешения уровня столбцов на системные объекты. Эти изменения разрешений не поддерживаются при обновлении. Кроме того, разрешения уровня столбцов на системные объекты больше не поддерживаются. Удалите из своих приложений инструкции, задающие разрешения уровня столбца в системных объектах.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите из своих приложений инструкции, которые предоставляют, запрещают или отменяют разрешения уровня столбца для системных объектов.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
