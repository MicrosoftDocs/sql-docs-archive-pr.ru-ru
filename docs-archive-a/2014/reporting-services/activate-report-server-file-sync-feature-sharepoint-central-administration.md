---
title: Активация компонента Синхронизация файлов сервера отчетов в центре администрирования SharePoint | Документация Майкрософт
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: 55feac69da85c7287ea56f4b8245350dd7e69565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665883"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint

Функция синхронизации файлов сервера отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] использует обработчики событий SharePoint для синхронизации каталога сервера отчетов с элементами в библиотеках документов. Эта функция может оказаться полезной в том случае, если пользователи часто передают элементы опубликованных отчетов напрямую в библиотеки документов SharePoint. Если функция синхронизации файлов не активирована, содержимое будет по-прежнему синхронизировано, но не так часто.  
  
Функция синхронизации файлов активируется в центре администрирования сайта SharePoint после установки надстройки служб [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] для продуктов SharePoint.  
  
Эту функцию можно активировать и деактивировать вручную не на уровне семейства веб-сайтов, а раздельно для каждого сайта.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Надстройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для SharePoint должна быть установлена. Если надстройка не установлена, функция синхронизации файлов не будет отображаться в списке возможностей сайта.  
  
 Чтобы проверить установку, просмотрите список установленных приложений на [!INCLUDE[msCoName](../includes/msconame-md.md)]**панели управления** Windows. Если надстройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] установлена, следуйте инструкциям в этом разделе для активации функции синхронизации файлов сервера отчетов.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>Активация и деактивация функции синхронизации файлов служб Reporting Services на сайте  
  
1.  На главной странице сайта щелкните меню **действия сайта** и выберите пункт **Параметры сайта**.  
  
2.  В области **действия сайта**щелкните **Управление компонентами сайта**.  
  
3.  Найдите в списке **Синхронизация файлов сервера отчетов** .  
  
4.  Щелкните **Активировать**.  
  
> [!NOTE]  
>  Деактивировать функцию синхронизации файлов сервера отчетов можно с помощью той же процедуры, но выбрав пункт **Деактивировать**.  
  
## <a name="see-also"></a>См. также:  
 [Устранение неполадок элементов отчетов &#40;построитель отчетов и SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Активация функций интеграции сервера отчетов и Power View в SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Установка или удаление надстройки Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Установка или удаление надстройки Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
