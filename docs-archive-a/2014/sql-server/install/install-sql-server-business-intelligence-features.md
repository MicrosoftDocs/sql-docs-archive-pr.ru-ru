---
title: Install SQL Server 2014 BI Features
ms.custom: ''
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.date: 10/24/2018
ms.technology: install
ms.openlocfilehash: 9770c8322e203231af6a964bcc9d7320a2ea22d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666390"
---
# <a name="install-sql-server-2014-bi-features"></a>Install SQL Server 2014 BI Features

  Компоненты SQL Server, которые являются частью платформы бизнес-аналитики Майкрософт, включают службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и несколько клиентских приложений, используемых для создания аналитических данных и работы с ними. В этом разделе документации по программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рассказывается, как установить эти функции.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно установить на автономных серверах, в конфигурациях с масштабным развертыванием или как приложения общей службы в ферме SharePoint. При установке служб в ферме включаются функции бизнес-аналитики, доступные только в Sharepoint, включая [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint и [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], конструктор нерегламентированных интерактивных отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который работает с табличными шаблонами баз данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Если пользователь уже знаком с шагами по установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]или PowerPivot для SharePoint, можно сразу перейти к контрольным спискам, в которых приведены указания, как реализовать определенные сценарии. Дополнительные сведения см. в разделе [Контрольные списки для установки функций бизнес-аналитики с помощью SharePoint](checklists-for-installing-bi-features-with-sharepoint.md).  
  
## <a name="contents"></a>Содержимое

В этом разделе рассматриваются следующие вопросы.
  
|Ссылка|Задача|  
|----------|----------|  
|[Контрольные списки для установки компонентов бизнес-аналитики в SharePoint](checklists-for-installing-bi-features-with-sharepoint.md)|Если параметры целевой системы уже известны и пользователь знаком с шагами по установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]или [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, можно сразу перейти к контрольным спискам, в которых приведены указания по порядку установки, требования к учетным записям и разрешениям, а также шаги по развертыванию расширенных топологий, включая развертывание нескольких серверов и нескольких компонентов.|  
|[Установка SQL Server компонентов бизнес-аналитики с помощью SharePoint &#40;PowerPivot и Reporting Services&#41;](install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)|В этом разделе описывается установка компонентов SQL Server в среде SharePoint. В нем указано, какие компоненты SQL Server можно установить при использовании той или иной версии и выпуска SharePoint. В нем также описаны процедуры установки PowerPivot для SharePoint и служб Reporting Services в режиме SharePoint.|  
|[Установка служб Analysis Services в многомерном режиме и режиме интеллектуального анализа данных](install-analysis-services-in-multidimensional-and-data-mining-mode.md)<br /><br /> [Установка служб Analysis Services в табличном режиме](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)<br /><br /> [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)<br /><br /> [Установка служб Integration Services](../../integration-services/install-windows/install-integration-services.md)<br /><br /> [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)<br /><br /> [Установка сервера отчетов служб Reporting Services в собственном режиме](../../reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)|В этом разделе приведены инструкции по установке служб Analysis Services, Integration Services, Master Data Services и Reporting Services, причем службы Analysis Services и Reporting Services устанавливаются без SharePoint. Иногда этот режим называется *собственным*, это наиболее часто используемый сценарий установки как служб Reporting Services, так и служб Analysis Services. В этом разделе рассказывается о параметрах установки, которые непосредственно определяют операционный контекст сервера. При установке служб Reporting Services это может быть предварительно настроенный сервер или же сервер, для подготовки к использованию которого потребуется выполнить несколько шагов по настройке. При установке служб Analysis Services выбранные параметры установки определят тип проекта, который можно будет развертывать на сервере.|  
|[Проверка или устранение неполадок при установке компонентов бизнес-аналитики SQL Server](../../../2014/sql-server/install/verify-or-troubleshoot-sql-server-bi-feature-installation-problems.md)|В этом разделе описаны шаги по проверке установки. В нем также приведены ссылки на сведения о решении проблем, размещенные в Интернете.|  
  
## <a name="related-content"></a>См. также  
  
|Ссылка|Задача|  
|----------|----------|  
|[Обновление до SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)<br /><br /> [Обновление служб Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)<br /><br /> [Обновление PowerPivot для SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)<br /><br /> [Обновление и перенос служб Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)|В этом разделе приведены указания по обновлению серверов и содержимого с предыдущей версии до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Удаление SQL Server 2014](uninstall-sql-server.md)<br /><br /> [Удаление PowerPivot для SharePoint](../../../2014/sql-server/install/uninstall-power-pivot-for-sharepoint.md)<br /><br /> [Удаление служб Reporting Services](../../../2014/sql-server/install/uninstall-reporting-services.md)|В указаниях в этом разделе описывается удаление компонентов BI.|  
  
## <a name="see-also"></a>См. также:

* [Новые возможности &#40;Reporting Services&#41;](../../../2014/reporting-services/what-s-new-reporting-services.md)

* [Новые возможности служб Analysis Services и бизнес-аналитики](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)

* [Установка SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)

* [Обновление до SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)
