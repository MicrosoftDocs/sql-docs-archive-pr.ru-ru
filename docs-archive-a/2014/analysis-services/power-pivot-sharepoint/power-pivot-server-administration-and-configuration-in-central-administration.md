---
title: Администрирование и настройка сервера PowerPivot в центре администрирования | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2cdbfdc5-45a9-4000-a03d-318cc7ac8fe9
author: minewiskan
ms.author: owend
ms.openlocfilehash: ce5c06eda86fb8e8ac03803513c8767988a728eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664542"
---
# <a name="powerpivot-server-administration-and-configuration-in-central-administration"></a>Настройка и администрирование сервера PowerPivot в центре администрирования
  Администрирование и настройка сервера PowerPivot осуществляется администраторами приложения службы SharePoint с помощью центра администрирования SharePoint.  
  
 Перед использованием сервера PowerPivot для SharePoint его необходимо настроить. После установки PowerPivot для SharePoint из программы установки SQL Server его необходимо настроить с помощью  
  
-   Средство настройки PowerPivot или средство настройки PowerPivot для SharePoint 2013  
  
-   Центр администрирования SharePoint  
  
-   Командлеты PowerShell  
  
 Все три подхода позволяют создать полностью настроенный сервер.  
  
 В этом разделе описано, как настроить ПО в центре администрирования. Необходимо выполнить все три обязательные задачи по настройке из нижеприведенного списка.  
  
> [!IMPORTANT]  
>  При работе с фермой SharePoint 2010 необходимо установить SharePoint 2010 с пакетом обновления 1 (SP1), чтобы иметь возможность настроить PowerPivot для SharePoint или ферму SharePoint, в которой используется сервер базы данных [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Если пакет обновления еще не установлен, установите его перед тем, как начать настройку сервера.  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-central-administration"></a>Преимущества настройки PowerPivot для работы с SharePoint в центре администрирования.  
 Центр администрирования SharePoint — это приложение для администрирования фермы SharePoint. Если вы являетесь администратором фермы, то, возможно, предпочтете воспользоваться для добавления PowerPivot для экземпляра SharePoint в ферму знакомым приложением.  
  
 В отличие от средств настройки PowerPivot или командлетов PowerShell, на страницах центра администрирования представлен полный набор параметров, которые можно задать при настройке приложения или сервера. При использовании других подходов либо процесс настройки выполняется за меньшее количество шагов, либо требуется предварительное знание методов настройки сервера SharePoint с помощью PowerShell.  
  
## <a name="related-content"></a>См. также  
 [Настройка PowerPivot с помощью Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [PowerPivot Configuration Tools](power-pivot-configuration-tools.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Ссылка|Type|Описание задачи|  
|----------|----------|----------------------|  
|[Развертывание решений PowerPivot в SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)|Обязательный|В этом шаге выполняется установка файлов решения, при котором файлы программы и страницы приложения добавляются в ферму и в семейство веб-сайтов.|  
|[Создание и настройка приложения службы PowerPivot в центре администрирования](create-and-configure-power-pivot-service-application-in-ca.md)|Обязательный|На этом шаге выполняется выделение системной службы PowerPivot.|  
|[Активация интеграции функций PowerPivot для семейств веб-сайтов в центре администрирования](activate-power-pivot-integration-for-site-collections-in-ca.md)|Обязательный|На этом шаге выполняется включение функций PowerPivot на уровне семейств веб-сайтов.|  
|[Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services](add-msolap-5-as-a-trusted-data-provider-in-excel-services.md)|Обязательный|На этом шаге поставщик OLE DB служб Analysis Services добавляется как надежный поставщик в службах Excel.|  
|[Обновление данных PowerPivot с SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)|Рекомендуемая|Использование обновления данных необязательно, но рекомендуется. Это позволяет задать расписание автоматических обновлений данных PowerPivot в опубликованных книгах Excel.|  
|[Настройте учетную запись автоматического обновления данных PowerPivot &#40;PowerPivot для SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)|Рекомендуемая|На этом шаге заводится специальная учетная запись, которая может быть использована для запуска заданий обновления данных на сервере.|  
|[Настройка сбора данных об использовании для &#40;PowerPivot для SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)|Необязательно|Сбор данных об использовании настраивается по умолчанию. Эти шаги можно использовать для изменения настроек по умолчанию.|  
|[Настройка выделенного обновления данных или &#40;обработки только запросов PowerPivot для SharePoint&#41;](../configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md)|Необязательно|Можно выделить экземпляр PowerPivot только для заданий и запросов обновления данных. Кроме того, можно изменить настройки по умолчанию для параллельных заданий обновления данных.|  
|[Указание учетных записей служб PowerPivot](configure-power-pivot-service-accounts.md)|Необязательно|Пояснение для обновления паролей или для изменения учетных записей, используемых службами.|  
|[Подключение приложения службы PowerPivot к веб-приложению SharePoint в центре администрирования](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)|Необязательно|В этом разделе приведено описание изменения служебных параметров.|  
|[Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)|Необязательно|В этой статье описано, как добавить галерею PowerPivot в качестве доверенного местоположения.|  
|[Настройка и просмотр файлов журнала SharePoint и журнала диагностики &#40;PowerPivot для SharePoint&#41;](configure-and-view-sharepoint-and-diagnostic-logging.md)|Необязательно|Запись событий в журнал настраивается по умолчанию. Эти шаги можно использовать для изменения настроек по умолчанию.|  
|[Правила определения исправности PowerPivot — настройка](configure-power-pivot-health-rules.md)|Необязательно|Правила для определения исправности сервера настраиваются по умолчанию. Эти шаги помогут изменить некоторые настройки по умолчанию.|  
|[создать и настроить галерею PowerPivot](create-and-customize-power-pivot-gallery.md)|Необязательно|Для установки, настраиваемой вручную, эта процедура описывает способ создания библиотеки галереи PowerPivot, в которой отображаются миниатюрные эскизы содержащихся книг PowerPivot.|  
|[Добавление типа содержимого соединения семантической модели бизнес-аналитики в библиотеку &#40;PowerPivot для SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md)|Необязательно|Описывает, как следует расширить библиотеку документов так, чтобы она поддерживала создание файлов связи семантической модели.|  
  
## <a name="see-also"></a>См. также:  
 [Установка PowerPivot для SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Ссылка на параметр конфигурации &#40;PowerPivot для SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Аварийное восстановление в PowerPivot для SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
