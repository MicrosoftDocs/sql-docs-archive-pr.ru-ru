---
title: Фильтрация событий по времени окончания (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d25d8e1adbd95f48d88fd1516c48dcc0f8374a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750388"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a>фильтровать события на основе времени окончания события (приложение SQL Server Profiler)
  В этом подразделе описывается, как при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]отфильтровать события трассировки на основе времени окончания события.  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a>Фильтрование событий на основе времени окончания события  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В диалоговом окне **Свойства трассировки** выберите вкладку **Общие** и введите имя в текстовое поле **Имя трассировки** .  
  
3.  В списке **Использовать шаблон**выберите шаблон трассировки.  
  
4.  Можно также задать целевой файл или таблицу, в которых будут сохраняться результаты трассировки.  
  
5.  На вкладке **Выбор событий**щелкните столбец данных **EndTime** , чтобы открыть диалоговое окно **Изменение фильтра** . Можно также щелкнуть правой кнопкой мыши заголовок столбца и выбрать пункт **Изменить фильтр столбца**.  
  
6.  Разверните узел **больше** или **меньше**, а затем введите `datetime` значение в поле, которое отображается под оператором сравнения.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](sql-server-profiler.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
