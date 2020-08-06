---
title: Запуск помощника по обновлению (пользовательский интерфейс) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a5e47ef2b8183823dff884e114adc420e371adf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668605"
---
# <a name="running-upgrade-advisor-user-interface"></a>Запуск помощника по обновлению (пользовательский интерфейс)
  Советник по переходу может быть запущен для анализа локальных или удаленных компонентов в процессе планирования обновления. Для каждого проанализированного компонента и экземпляра помощник по обновлению создает отчет.  
  
> [!IMPORTANT]  
>  Помощник по обновлению не анализирует удаленные экземпляры служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Чтобы выполнить анализ экземпляра служб [!INCLUDE[ssRS](../../includes/ssrs.md)], необходимо установить помощник по обновлению на компьютере, где установлены службы [!INCLUDE[ssRS](../../includes/ssrs.md)].  
>   
>  Для анализа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services на одном компьютере должны быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлены и [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] установлены.  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a>Мастер анализа помощника по обновлению  
 Работа мастера анализа помощника по обновлению включает шесть этапов.  
  
1.  Запустите мастер с начальной страницы помощника по обновлению.  
  
2.  Определите анализируемый сервер и компоненты.  
  
3.  Соберите сведения для проверки подлинности.  
  
4.  Определите дополнительные параметры в зависимости от типа компонентов.  
  
5.  Выполните анализ выбранных компонентов.  
  
6.  Создайте отчет о выявленных проблемах обновления.  
  
 Дополнительные сведения о мастере анализа помощника по обновлению см. в разделе [инструкции. Запуск мастера анализа помощника по обновлению](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).  
  
 Конкретные сведения, необходимые для каждого шага, см. в разделе [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a>Средство просмотра отчетов помощника по обновлению  
 Средство просмотра отчетов помощника по обновлению используется для просмотра отчетов, созданных мастером анализа помощника по обновлению. После загрузки отчета его компоненты можно отфильтровать по следующим параметрам:  
  
-   все проблемы;  
  
-   все проблемы, связанные с обновлением;  
  
-   проблемы, связанные с подготовкой к обновлению;  
  
-   все проблемы, связанные с миграцией;  
  
-   устраненные проблемы.  
  
-   Неустраненные проблемы  
  
 Пошаговые инструкции по использованию средства просмотра отчетов см. в следующих разделах.  
  
-   [Просмотр отчета помощника по обновлению](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [Фильтрация отчетов](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [Экспорт отчетов](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a>См. также:  
 [Как запустить мастер анализа помощника по обновлению](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Устранение проблем с обновлением](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
