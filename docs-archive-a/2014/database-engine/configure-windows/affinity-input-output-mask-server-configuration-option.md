---
title: Параметр конфигурации сервера "affinity Input-Output mask" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- affinity I/O mask option
- processor affinity [SQL Server]
- binding processors [SQL Server]
- CPU affinity mask option
ms.assetid: 9950a8c9-9fe0-4003-95df-6f0d1becb0e7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d0606e2a3f5480b27e27a4a585562f4b289b640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654496"
---
# <a name="affinity-input-output-mask-server-configuration-option"></a>Параметр конфигурации сервера "affinity Input-Output mask"
  Для одновременного выполнения множества задач операционные системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 и Windows Server 2003 иногда распределяют потоки обработки задач по различным процессорам. Хотя с точки зрения операционной системы эти действия эффективны, они могут снизить производительность [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при больших системных нагрузках, так как данные кэша каждого процессора будут постоянно обновляться. В этих условиях назначение определенного потока задач процессору может улучшить производительность, поскольку количество перезагрузок процессора будет снижено; такая связь между определенным потоком задач и процессором называется соответствием процессоров.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает схожесть процессоров с помощью двух параметров: **affinity mask** (также известен как **CPU affinity mask**) и **affinity I/O mask**. Дополнительные сведения о параметре **affinity mask** см. в разделе [Параметр конфигурации сервера "affinity mask"](affinity-mask-server-configuration-option.md). Поддержка соответствия процессоров и ввода-вывода для серверов с числом ЦП от 33 до 64 требует также использования параметров [Параметр конфигурации сервера "affinity64 mask"](affinity64-mask-server-configuration-option.md) и [Параметр конфигурации сервера "affinity64 I/O mask"](affinity64-input-output-mask-server-configuration-option.md) соответственно.  
  
> [!NOTE]  
>  Поддержка соответствия процессоров для серверов с числом процессоров от 33 до 64 доступна только в 64-разрядных версиях операционных систем.  
  
 Параметр **affinity I/O mask** привязывает операцию дискового ввода-вывода [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к определенному подмножеству ЦП. В средах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] высокоскоростной обработки транзакций (OLTP) данное расширение может улучшать производительность потоков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выдающих вводы-выводы. Это улучшение не поддерживает привязку оборудования для отдельных дисков или контроллеров дисков.  
  
 Значение параметра **affinity I/O mask** указывает, какие ЦП в многопроцессорном компьютере подходят для обработки операций ввода-вывода на диске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Маска — это битовая карта, в которой самый правый бит обозначает ЦП самого низкого уровня (0), второй бит справа обозначает ЦП второго снизу уровня (1) и т. д. Чтобы настроить более 32 процессоров, нужно задать и параметр **affinity I/O mask** , и параметр **affinity64 I/O mask**.  
  
 Ниже приведены возможные значения параметра **affinity I/O mask** .  
  
-   Однобайтовое значение **affinity I/O mask** обеспечивает управление компьютерами, содержащими до 8 ЦП.  
  
-   Двухбайтовое значение **affinity I/O mask** обеспечивает управление компьютерами, содержащими до 16 ЦП.  
  
-   Трехбайтовое значение **affinity I/O mask** обеспечивает управление компьютерами, содержащими до 24 ЦП.  
  
-   Четырехбайтовое значение **affinity I/O mask** обеспечивает управление компьютерами, содержащими до 32 ЦП.  
  
-   Для работы более чем с 32 ЦП настройте четырехбайтовое значение **affinity I/O mask** для первых 32 ЦП и включающее до 4 байт значение **affinity64 I/O mask** для оставшихся ЦП.  
  
 1 бит в шаблоне привязки ввода-вывода показывает, что соответствующий ЦП может выполнять операции ввода-вывода с диском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; 0 бит указывает, что для соответствующего ЦП не следует планировать никаких операций ввода-вывода с диском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Когда все биты установлены на ноль или параметр **affinity I/O mask** не указан, ввод-вывод диска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] планируется для любого ЦП, способного обрабатывать потоки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Поскольку настройка параметра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **affinity I/O mask** является специализированной операцией, она должна использоваться только при необходимости. В большинстве случаев привязка по умолчанию в системах Windows 2000 или Windows Server 2003 обеспечивает самую высокую производительность.  
  
 При задании параметра **affinity I/O mask** его следует использовать вместе с параметром конфигурации **affinity mask** . Не следует включать один и тот же процессор и в переключателе **affinity I/O mask** , и в параметре **affinity mask** . Биты, относящиеся к каждому процессору, могут находиться в одном из трех состояний:  
  
-   0 в параметре **affinity I/O mask** и в параметре **affinity mask** ;  
  
-   1 в параметре **affinity I/O mask** и 0 в параметре **affinity mask** ;  
  
-   0 в параметре **affinity I/O mask** и 1 в параметре **affinity mask** .  
  
 Параметр **affinity I/O mask** является дополнительным параметром. Если `sp_configure` для изменения параметра используется системная хранимая процедура, **маску сопоставления ввода-вывода** можно изменить только в том случае, если параметру **Показывать дополнительные параметры** присвоено значение 1. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]для изменения параметра **affinity I/O mask** требуется перезапуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!CAUTION]  
>  Не используйте маску привязки процессоров в операционной системе Windows и маску привязки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]одновременно. Эти настройки предназначены для достижения одного результата, и если их значения будут несогласованными, результат может быть непредсказуем. Привязка ЦП [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] лучше всего настраивается с использованием параметра `sp_configure` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
