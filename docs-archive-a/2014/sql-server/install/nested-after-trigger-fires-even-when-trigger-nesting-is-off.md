---
title: Вложенный триггер AFTER срабатывает, даже если вложенность триггера ОТКЛЮЧЕНа | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f91c04e8d69880b451c1479e2907cd1910e8f9c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751715"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a>Вложенный триггер AFTER срабатывает даже в том случае, если вложенные триггеры отключены
  Советник по переходу обнаружил триггер AFTER, вложенный в триггер INSTEAD OF, который определен для одной или нескольких таблиц. Вложенные триггеры AFTER могут срабатывать, даже если параметр конфигурации сервера `nested triggers` установлен в 0.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Первый триггер AFTER, вложенный в триггер INSTEAD OF, срабатывает, даже если параметру конфигурации сервера `nested triggers` присвоено значение 0. Однако при такой настройке последующие триггеры не срабатывают.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Проверьте приложения на наличие вложенных триггеров, чтобы определить, соответствуют ли приложения бизнес-правилам в случае, если параметру конфигурации сервера `nested triggers` присвоено значение 0, и проведите соответствующие изменения.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
