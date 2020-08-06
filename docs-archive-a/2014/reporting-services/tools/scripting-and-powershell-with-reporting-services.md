---
title: Работа с отчетами и PowerShell в Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7a8dc805351897c11202467ed8bcb0373ef77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665235"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Сценарии и PowerShell со службами Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] поддерживает целый ряд сценариев разработки и управления посредством скриптов, включая служебную программу командной строки rs.exe, командлеты PowerShell для серверов отчетов в режиме SharePoint и использование объектной модели [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] из PowerShell для режима SharePoint и собственного режима.

-   Администратор может написать скрипт на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], чтобы автоматизировать развертывание установки сервера отчетов и управление ей. Администраторы также могут создавать и запускать скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] для создания, настройки и обновления базы данных сервера отчетов. Администраторы также могут использовать возможности записи и воспроизведения компонентов скрипта в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], чтобы автоматизировать стандартные задачи обслуживания.

-   Разработчики могут создавать пользовательские приложения, включающие скрипты. Можно запустить скрипт, который выполнит вызовы к веб-службе сервера отчетов. Практически любая операция доступная в управляемом коде, может быть написана и в скрипте.

-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] поддерживает скрипт .NET [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] как язык скриптов, который можно обработать с помощью программы RS.exe (сервер скриптов, который выполняется на сервере отчетов).

## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Образцы и командлеты PowerShell в режиме SharePoint для служб Reporting Services
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включает [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] командлеты для администрирования сервера отчетов.

-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) содержит следующие примеры.

    -   Создайте приложение службы и прокси-сервер

    -   Проверьте и обновите модуль доставки

    -   Получение и задание свойств базы данных приложения служб Reporting Services, например времени ожидания базы данных

    -   Расширения данных списка

## <a name="reporting-services-object-model-and-powershell-samples"></a>Объектная модель служб Reporting Services и примеры отчетов Powershell
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")

 Вызов PowerShell основной объектной модели, в большинстве случаев допустимый для режима SharePoint и собственного режима, например при работе с миграцией и подписками, а также дополнительные сопутствующие примеры по работе с подписками в SQL15.

-   [Использование PowerShell для смены и перечисления владельцев подписок служб Reporting Services и запуска подписки](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).

-   [Использование PowerShell для создания виртуальной машины Windows Azure с помощью сервера отчетов, работающего в собственном режиме](https://msdn.microsoft.com/library/azure/dn449661.aspx).

-   См. раздел "Доступ к классам WMI с помощью PowerShell" в статье [Доступ к поставщику WMI для служб Reporting Services](access-the-reporting-services-wmi-provider.md).

-   [Администрирование служб SSRS с помощью PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin

## <a name="rsexe-scripting-samples"></a>Образцы скриптов RS.exe

-   [Пример Reporting Services rs.exe сценария для переноса содержимого между серверами отчетов](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).

-   Дополнительные примеры скриптов, приложений и расширений см. в разделе [Примеры продуктов SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).

## <a name="see-also"></a>См. также:
 [RS.exe служебной программы &#40;службы SSRS&#41;](rs-exe-utility-ssrs.md) скрипт [развертывания и администрирования сценариев](script-deployment-and-administrative-tasks.md) [с помощью служебной программы rs.exe и веб-службы](script-with-the-rs-exe-utility-and-the-web-service.md)


