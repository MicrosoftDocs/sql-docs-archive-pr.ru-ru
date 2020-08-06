---
title: Свойства агента SQL Server (страница "Дополнительно") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8ec0d9d7fbd51f9350bf692588f90c292e54f4e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667532"
---
# <a name="sql-server-agent-properties-advanced-page"></a>Свойства агента SQL Server (страница «Дополнительно»)
  Эта страница используется для просмотра и изменения дополнительных свойств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы агента.  
  
## <a name="options"></a>Варианты  
 **Пересылка событий SQL Server**  
 Параметры в данной категории активируют и настраивают пересылку событий.  
  
 **Переслать события на другой сервер**  
 Перенаправляет события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] другому серверу.  
  
 **Server**  
 Выберите имя сервера, которому нужно перенаправить события.  
  
 **Необработанные события**  
 Переправляет заданному серверу только необработанные события. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перенаправляет только события, на которые не реагирует ни одно предупреждение.  
  
 **Все события**  
 Переправляет все события. Если предупреждение локального экземпляра реагирует на событие, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перенаправит этот событие и обработает предупреждение.  
  
 **Если серьезность события равна или превышает**  
 Пересылает только события, уровень серьезности которых равен указанному или превышает его.  
  
 **Условие простоя ЦП**  
 Параметры в данной категории определяют условия, при которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускает задания, запланированные к выполнению в расписании простоя ЦП.  
  
 **Определить условие простоя ЦП**  
 Определяет условия, при которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] считает, что ЦП простаивает.  
  
 **Среднее время использования ЦП сократилось до**  
 Процент использования ЦП сократился до уровня, при котором считается, что ЦП простаивает.  
  
 **И остается ниже этого уровня в течение**  
 Отрезок времени, который средний ЦП должен простаивать, прежде чем агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запустит задания по расписанию простоя ЦП.  
  
## <a name="see-also"></a>См. также:  
 [Создание и присоединение расписаний к заданиям](create-and-attach-schedules-to-jobs.md)   
 [Управление событиями](manage-events.md)  
  
  
