---
title: Справочник по программе командной строки (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server]
- command prompt utilities [SQL Server], about command prompt utilities
- command prompt [SQL Server]
- utilities [SQL Server], command prompt
- command prompt [SQL Server], utilities
ms.assetid: 48364bd9-6ea7-45e9-a332-acf3d81bbfae
author: stevestein
ms.author: sstein
ms.openlocfilehash: ffb5f15bb37bd4e15dd93404be3df47ce359586b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729005"
---
# <a name="command-prompt-utility-reference-database-engine"></a>Справка программы командной строки (компонент Database Engine)
  Программы командной строки позволяют вносить в скрипт операции [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . В следующей таблице содержится список программ командной строки, поставляемых вместе с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|**Служебная программа**|**Описание**|**Установлена в**|  
|-----------------|---------------------|----------------------|  
|[Программа bcp](bcp-utility.md)|Используется для копирования данных между экземпляром [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и файлом данных в указанном пользователем формате.|\<*drive*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta Utility](dta/dta-utility.md)|Используется для анализа рабочей нагрузки и дает рекомендации по структурам физического проектирования, чтобы оптимизировать производительность сервера с этой рабочей нагрузкой.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа dtexec](../integration-services/packages/dtexec-utility.md)|Используется для настройки и выполнения пакета служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Версия этой программы с пользовательским интерфейсом называется **DTExecUI**. Она вызывает служебную программу для запуска пакетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Программа dtutil](../integration-services/dtutil-utility.md)|Используется для управления пакетами служб SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Развертывание решений моделей с использованием программы развертывания](https://docs.microsoft.com/analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility)|Используется для развертывания проектов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на экземплярах служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[Программа osql](osql-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа Utility](profiler-utility.md)|Используется для запуска приложения среды [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] из командной строки.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Служебная программа RS.exe (SSRS)](../reporting-services/tools/rs-exe-utility-ssrs.md)|Используется для запуска скриптов, предназначенных для управления серверами отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа rsconfig (SSRS)](../reporting-services/tools/rsconfig-utility-ssrs.md)|Используется для настройки соединения сервера отчетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа rskeymgmt (SSRS)](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Используется для управления ключами шифрования на сервере отчетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlagent90](sqlagent90-application.md)|Используется для запуска агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из командной строки.|\<drive>:\Program Files\Microsoft SQL Server\\<*имя_экземпляра*>\MSSQL\Binn|  
|[Программа sqlcmd](sqlcmd-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|\<*drive*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Программа SQLdiag](sqldiag-utility.md)|Используется для сбора диагностических сведений для службы поддержки пользователей [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqllogship](sqllogship-application.md)|Используется приложениями для выполнения операций резервирования, копирования и восстановления, а также связанных с ними задач очистки в конфигурации доставки журналов без запуска соответствующих заданий.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа SqlLocalDB](sqllocaldb-utility.md)|Режим выполнения [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , рассчитанный на разработчиков программ.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа sqlmaint](sqlmaint-utility.md)|Служит для выполнения планов обслуживания баз данных, созданных в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<drive>: \Program Files\Microsoft SQL Server\MSSQL12. мссклсервер\мсскл\бинн|  
|[Программа sqlps](sqlps-utility.md)|Используется для выполнения команд и скриптов PowerShell. Загружает и регистрирует командлеты и поставщика PowerShell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlservr](sqlservr-application.md)|Служит для запуска и остановки экземпляра компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] из командной строки при устранении неполадок.|\<drive>: \Program Files\Microsoft SQL Server\MSSQL12. мссклсервер\мсскл\бинн|  
|[Программа SSMS](../ssms/ssms-utility.md)|Используется для запуска приложения среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[Программа tablediff](tablediff-utility.md)|Используется для сравнения данных в двух таблицах, чтобы обнаружить отсутствие конвергенции. Это полезно для устранения неполадок в топологии репликации.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  
  
 **Запуск диспетчера конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в [!INCLUDE[win8](../includes/win8-md.md)]**  
  
 Так как диспетчер конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] является оснасткой консоли управления [!INCLUDE[msCoName](../includes/msconame-md.md)] , а не отдельной программой, при работе в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] диспетчер конфигурации [!INCLUDE[win8](../includes/win8-md.md)]не отображается как приложение. Чтобы открыть [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager, на чудо-странице **поиска** в разделе **приложения**введите **SQLServerManager12. msc** (для [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] ) или **SQLServerManager11. msc** для ( [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ) и нажмите клавишу **Ввод**.  
  
## <a name="command-prompt-utilities-syntax-conventions"></a>Соглашения о синтаксисе программ командной строки  
  
|**Соглашение**|**Область использования**|  
|--------------------|------------------|  
|Прописные буквы|Инструкции и термины, используемые на уровне операционной системы.|  
|`monospace`|Образцы команд и программного кода.|  
|*курсив*|Параметры, указываемые пользователем.|  
|**полужирный**|Команды, параметры и другие элементы синтаксиса, которые должны в точности соответствовать примеру.|  
  
## <a name="see-also"></a>См. также:  
 [Replication Distribution Agent](../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replication Log Reader Agent](../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replication Merge Agent](../relational-databases/replication/agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
