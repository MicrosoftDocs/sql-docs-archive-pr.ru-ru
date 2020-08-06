---
title: Мониторинг использования памяти | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tuning databases [SQL Server], memory
- monitoring server performance [SQL Server], memory usage
- isolating memory [SQL Server]
- paging rate [SQL Server]
- memory [SQL Server], monitoring usage
- monitoring [SQL Server], memory usage
- low-memory conditions
- database monitoring [SQL Server], memory usage
- available memory [SQL Server]
- page faults [SQL Server]
- monitoring performance [SQL Server], memory usage
- server performance [SQL Server], memory
ms.assetid: 1aee3933-a11c-4b87-91b7-32f5ea38c87f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1986d9576f9b067cad18f27d4febbf097ed52703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739740"
---
# <a name="monitor-memory-usage"></a>Наблюдение за использованием памяти
  Проводите периодический мониторинг экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для подтверждения того, что память используется в допустимых пределах.  
  
 Для контроля условий нехватки памяти используйте следующие счетчики объектов.  
  
-   **Память: доступно байтов**  
  
-   **Память: страниц/с**  
  
 Счетчик **Доступно байтов** указывает на то, сколько байт памяти доступно на данный момент для использования процессами. Счетчик **Страниц/с** показывает число страниц, которые были или получены с диска из-за ошибок страниц физической памяти, или записаны на диск для освобождения пространства в рабочем множестве из-за ошибок страниц.  
  
 Малые значения счетчика **Доступно байтов** могут указывать на то, что существует общая нехватка памяти на компьютере или что приложение не освобождает память. Большое значение счетчика **Страниц/с** может означать излишнюю подкачку. Наблюдение за счетчиком **Память: ошибок страниц/с** позволяет убедиться в том, что активность диска не вызвана трансляцией страниц.  
  
 Низкий уровень подкачки (и редкие ошибки страниц) является нормальным, даже если у компьютера достаточно большое количество доступной памяти. Диспетчер виртуальной памяти (VMM) Microsoft Windows берет страницы из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и других процессов по мере того, как он урезает размеры рабочих множеств этих процессов. Деятельность VMM может привести к ошибкам страниц. Чтобы определить, является ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или другой процесс причиной излишней подкачки, наблюдайте за счетчиком **Процесс: ошибок страниц/с** для экземпляра процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Дополнительные сведения об устранении проблемы излишней подкачки см. в документации по операционной системе Windows.  
  
## <a name="isolating-memory-used-by-sql-server"></a>Изоляция памяти, используемой SQL Server  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] изменяет свои требования к памяти динамически, исходя из доступных ресурсов системы. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нужно больше памяти, он производит запрос к операционной системе, чтобы определить, доступна ли свободная физическая память, и использует ее. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не нуждается в памяти, выделенной для него, он освобождает ее для операционной системы. Однако можно отказаться от динамического использования памяти, задав значения параметрам конфигурации сервера **minservermemory**и **maxservermemory** . Дополнительные сведения см. в разделе [Параметры памяти сервера](../../database-engine/configure-windows/server-memory-server-configuration-options.md).  
  
 Для мониторинга объема памяти, используемого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , наблюдайте за следующими счетчиками производительности.  
  
-   **Процесс: рабочий набор**  
  
-   **SQL Server: Buffer Manager: коэффициент попаданий в буферный кэш**  
  
-   **SQL Server: Buffer Manager: страниц базы данных**  
  
-   **SQL Server: Memory Manager: общая память сервера (КБ)**  
  
 Счетчик **WorkingSet** отображает объем памяти, занятый процессом. Если это число постоянно меньше объема памяти, установленного параметрами сервера **min server memory** и **max server memory** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для использования слишком большого объема памяти.  
  
 Значения счетчика **Коэффициент попаданий в кэш буфера** зависят от конкретного приложения. Однако желательно значение коэффициента, равное 90 процентам или выше. Добавляйте память, пока значение не будет постоянно больше 90 процентов. Значение выше 90 процентов указывает на то, что более 90 процентов всех запрошенных данных были получены из кэша данных.  
  
 Если счетчик **TotalServerMemory (KB)** постоянно показывает высокие значения по сравнению с объемом физической памяти компьютера, это может означать, что требуется установить в компьютер больше памяти.  
  
## <a name="determining-current-memory-allocation"></a>Определение Текущего Распределения Памяти  
 Следующий запрос возвращает информацию о текущем распределении памяти.  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
  
