---
title: Воспроизвести трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: c485317d1343958f9c430b73d858130097d44d75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737229"
---
# <a name="replay-traces"></a>Воспроизведение трассировок
  Воспроизведением называется возможность повторить действие, захваченное в трассировке. После создания или редактирования трассировки ее можно сохранить в файл и позже воспроизвести. Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] позволяет воспроизводить трассировку с одного компьютера. При высокой рабочей нагрузке используйте программу распределенного воспроизведения, которая позволяет воспроизводить данные трассировки с нескольких компьютеров.  
  
 В этом разделе описывается использование возможностей воспроизведения приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Дополнительные сведения о программе распределенного воспроизведения см. в разделе [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] содержит в себе многопоточный модуль воспроизведения, который имитирует соединения пользователей и проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Воспроизведение хорошо помогает при диагностике ошибок приложений и процессов. После изучения проблемы и внесения необходимых изменений можно снова запустить трассировку, которая обнаружила эту проблему, на исправленном приложении или процессе, а затем, после воспроизведения исходной трассировки, сравнить результаты.  
  
 Воспроизведение трассировки поддерживает отладку с использованием параметров **Точка останова** и **Выполнить до курсора** в меню **Воспроизведение** в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Эти команды особенно помогают при анализе длинных скриптов, позволяя разбить воспроизведение на короткие сегменты, которые могут быть последовательно проанализированы.  
  
 Сведения о том, какие разрешения необходимы для воспроизведения трассировки, см. в статье [Разрешения, необходимые для запуска приложения SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Требования к воспроизведению](replay-requirements.md)|Описывает события, которые могут быть включены в определение трассировки для последующего воспроизведения в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Параметры воспроизведения (приложение SQL Server Profiler)](replay-options-sql-server-profiler.md)|Описывает параметры, устанавливаемые в диалоговом окне **Конфигурация воспроизведения** приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Вопросы воспроизведения трассировки (приложение SQL Server Profiler)](considerations-for-replaying-traces-sql-server-profiler.md)|Описывает события трассировки, которые не могут быть воспроизведены в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , и влияние воспроизведения на производительность работы сервера.|  
  
## <a name="see-also"></a>См. также:  
 [Распределенное воспроизведение SQL Server](../distributed-replay/sql-server-distributed-replay.md)  
  
  
