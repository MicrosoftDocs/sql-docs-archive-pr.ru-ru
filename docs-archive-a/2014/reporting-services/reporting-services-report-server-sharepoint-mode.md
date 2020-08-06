---
title: Сервер отчетов служб Reporting Services (режим интеграции с SharePoint) | Документы Майкрософт
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 54fe41c3927d375163359e325b0fe116f8bffda2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666960"
---
# <a name="reporting-services-report-server-sharepoint-mode"></a>Сервер отчетов служб Reporting Services (режим SharePoint)

Сервер отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , настроенный на работу в **режиме интеграции с SharePoint** , может выполняться в развертывании продукта SharePoint. Сервер отчетов в режиме интеграции с SharePoint может использовать функции совместной работы и управления SharePoint для отчетов и других типов содержимого [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Для режима интеграции с SharePoint необходимо установить соответствующую версию надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint на компьютеры с клиентским веб-интерфейсом SharePoint.  
  
Дополнительные сведения об установке и настройке см. в следующем документе.  
  
- [Установка служб Reporting Services в режиме SharePoint для SharePoint 2013](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
- [Установите Reporting Services режиме интеграции с SharePoint для sharepoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
- [Добавьте дополнительный сервер отчетов в ферму &#40;горизонтальное масштабирование SSRS&#41;](install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).  
  
 Сведения о новых возможностях этого выпуска см. в разделе "SharePoint" статьи [новые &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md).  
  
 **В этом разделе:**  
  
-   [Сводка по функциям](#bkmk_featuresum)  
  
-   [Подключенный и локальный режимы](#bkmk_connectedandlocal)  
  
-   [Неподдерживаемые функции SharePoint](#bkmk_unsupportedsharepoint)  
  
-   [Поддерживаемые сочетания надстройки SharePoint и сервера отчетов](#bkmk_supportedcombinations)  
  
-   [Компоненты, обеспечивающие интеграцию](#bkmk_components)  
  
-   [Рекомендации по языку](#bkmk_language)  
  
-   [Связанные задачи](#bkmk_relatedtasks)  
  
##  <a name="feature-summary"></a><a name="bkmk_featuresum"></a>Сводка функций

 Настройка сервера отчетов для работы в режиме интеграции с SharePoint предоставляет следующие дополнительные возможности (доступные только при развертывании в этом режиме).  
  
-   Функции управления документами и совместной работы SharePoint, включая обработку предупреждений. Сайт SharePoint предоставляет единый портал для доступа ко всем документам и единую точку управления элементами отчета.  
  
-   Использование разрешений SharePoint и поставщиков служб проверки подлинности для управления доступом к отчетам, моделям и другим элементам.  
  
-   Топология развертывания SharePoint используется для распределения отчетов по Интернет-соединению за пределами брандмауэра. Сервер отчетов поддерживает службы обработки отчетов и данных в контексте более крупной конфигурации SharePoint, настроенной для доступа в Интернет.  
  
-   Управление отчетами, моделями, источниками данных, расписаниями и журналом отчетов с помощью пользовательских страниц приложений на сайте SharePoint. На сайте SharePoint можно задавать свойства, создавать расписания, оформлять подписки, а также создавать и вести журнал отчетов, используя те же методы, что и при работе с другими средствами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Публикация и передача отчетов, моделей отчетов, ресурсов и общих источников данных в библиотеку SharePoint, в том числе центр отчетов на сервере Office SharePoint.  
  
     Для создания отчетов и источников данных, которые будут публиковаться непосредственно в библиотеке SharePoint, используйте конструктор отчетов, конструктор моделей и построитель отчетов. Также можно использовать действие «Передача» на сайте SharePoint, чтобы добавить в библиотеку SharePoint любые определения отчетов и модели отчетов.  
  
     Сервер отчетов всегда обрабатывает определения отчетов одинаковым образом, независимо от используемого режима сервера, и режим сервера не влияет на данные отчета и его макет. Любой отчет, который может запускаться на сервере отчетов в собственном режиме, может запускаться и на сервере отчетов, настроенном для работы в режиме интеграции с SharePoint.  
  
-   Оформление подписки и доставка отчетов в библиотеку SharePoint с помощью нового модуля доставки SharePoint. Также можно доставлять отчеты по электронной почте или в общую папку. Для доставки отчетов применяются модули доставки сервера отчетов. Можно создать управляемые данными подписки для крупномасштабного распространения отчетов с использованием сведений о подписчике, запрошенных во время выполнения.  
  
-   Для просмотра отчета в веб-приложении SharePoint можно добавить веб-часть «Средство просмотра отчетов». В эту веб-часть входят средства перемещения по страницам, а также функции поиска, печати и экспорта.  
  
-   Программирование в контексте новой конечной точки SOAP для создания пользовательских приложений, интегрируемых с сайтом SharePoint. Также можно использовать обновленный поставщик инструментария управления Windows (WMI) для программной настройки экземпляра сервера отчетов, работающего в режиме интеграции с SharePoint.  
  
-   Отчеты Microsoft Access в подключенном режиме.  
  
-   AAM-зоны, развертывания, направленные в сторону Интернета, и токены пользователя SharePoint для списков SharePoint.  
  
##  <a name="connected-mode-and-local-mode"></a><a name="bkmk_connectedandlocal"></a>Подключенный и локальный режимы

 В выпуске SQL Server 2008 R2 введен новый *локальный режим* для просмотра отчетов с сервера SharePoint 2010 с установленной надстройкой служб Microsoft SQL Server 2008 R2 Reporting Services (или более поздней версии) для продуктов SharePoint 2010.  
  
-   *Локальный режим*. Локальный режим позволяет подготавливать отчеты локально из библиотеки документов SharePoint без интеграции с сервером отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Надстройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint является обязательной в отличие от сервера отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Надстройка может быть установлена несколькими различными способами, в том числе с помощью средства подготовки продуктов SharePoint 2010. Дополнительные сведения о локальном режиме см. [в разделе Отчеты о локальном и подключенном режимах в средстве просмотра отчетов &#40;Reporting Services в режиме интеграции с sharepoint&#41;](../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md) и [где найти надстройку Reporting Services для продуктов SharePoint](install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
-   *Подключенный режим*. Подключенный режим поддерживается путем интеграции сервера отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] с фермой SharePoint с помощью центра администрирования SharePoint. Интеграция с сервером отчетов обеспечивает комплексные возможности работы с отчетами, предоставляя функции совместной работы SharePoint 2010 и серверные функции сервера отчетов, в том числе подписку, моментальные снимки и серверную обработку.  
  
##  <a name="unsupported-sharepoint-features"></a><a name="bkmk_unsupportedsharepoint"></a>Неподдерживаемые функции SharePoint

 При работе в режиме интеграции доступны не все компоненты SharePoint. Далее приведен список функций SharePoint, с которыми службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не интегрируются напрямую.  
  
-   Служба Secure Store.  
  
-   Нельзя использовать интеграцию с календарем SharePoint Outlook и создавать расписания SharePoint для файлов служб отчетов в библиотеке документов.  
  
-   Каталог SharePoint Business Data.  
  
-   Возможность индивидуальной настройки SharePoint не поддерживается на страницах служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Интеграция с сервером отчетов невозможна, если веб-приложение SharePoint включено для анонимного доступа.  
  
-   Службы SQL Server Reporting Services **не** поддерживают управление версиями библиотеки документов SharePoint. Если сохранить элементы отчета в библиотеке документов, для которой включена функция "История версий документов", то функции службы Reporting Services будут работать неправильно и в журнале ULS будут формироваться ошибки. В следующем примере показана ошибка в журнале ULS:  
  
    -   "...отключен источник данных, связанный с отчетом".  
  
     История версий документов библиотеки настраивается на странице "Параметры версий" окна "Параметры библиотеки".  
  
##  <a name="supported-combinations-of-the-sharepoint-add-in-and-report-server"></a><a name="bkmk_supportedcombinations"></a>Поддерживаемые сочетания надстройки SharePoint и сервера отчетов

 Не все функции поддерживаются во всех сочетаниях сервера отчетов, надстройки служб Reporting Services для SharePoint и продуктов SharePoint. Дополнительные сведения см. в разделе [Поддерживаемые сочетания SharePoint и Reporting Services Server и надстройки &#40;SQL Server 2014&#41;](install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
> [!NOTE]  
>  Правильная версия надстройки служб Reporting Services должна использоваться с соответствующей версией продуктов SharePoint.  
  
##  <a name="components-that-provide-integration"></a><a name="bkmk_components"></a>Компоненты, обеспечивающие интеграцию

 Чтобы объединить серверы в одном развертывании, необходимо интегрировать установку [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] с экземпляром продуктов SharePoint.  
  
 Интеграция предоставляется [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и надстройкой служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint. Надстройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] является свободно распространяемым компонентом, который можно загрузить и установить на сервер с соответствующей версией SharePoint.  
  
> [!TIP]  
>  Не все функции поддерживаются во всех сочетаниях сервера отчетов, надстройки служб Reporting Services для SharePoint и продуктов SharePoint. Дополнительные сведения см. в разделе [Поддерживаемые сочетания SharePoint и Reporting Services Server и надстройки &#40;SQL Server 2014&#41;](install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   На сервере SharePoint надстройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] предоставляет конечную точку учетной записи-посредника для сервера отчетов, веб-часть средства просмотра отчетов и страницы приложений для просмотра, хранения и управления содержимым сервера отчетов на сайте SharePoint или ферме SharePoint.  
  
-   Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] предоставляют обновленные файлы программ, конечную точку SOAP и пользовательские модули безопасности и доставки. Сервер отчетов должен быть настроен для работы в режиме интеграции с SharePoint, специально выделенном для поддержки доступа к отчетам и их доставки через сайт SharePoint.  
  
 После установки надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] на SharePoint и настройки обоих серверов для интеграции можно передать или опубликовать тип содержимого сервера отчетов в библиотеке SharePoint, а затем просматривать эти документы и управлять ими с сайта SharePoint. Передача или публикация содержимого сервера отчетов является важным первым шагом. Веб-части и страницы становятся доступны при выборе определений отчетов RDL, моделей отчетов SMDL и источников общих данных RSDS на сайте SharePoint.  
  
##  <a name="language-considerations"></a><a name="bkmk_language"></a>Рекомендации по языку

 [!INCLUDE[SPF2010](../includes/spf2010-md.md)] и [!INCLUDE[SPS2010](../includes/sps2010-md.md)] поддерживают гораздо больше языков, чем [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 Если настроить сервер отчетов для работы с развертыванием продукта SharePoint, можно получить сочетание языков. Далее описано, какой язык будут иметь пользовательский интерфейс, документация и сообщения.  
  
-   Все страницы приложений, средства, сообщения об ошибках и предупреждения, создаваемые службами [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , будут выводиться на языке, используемом экземпляром служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (это один из языков [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).  
  
-   Страницы приложения, открываемые на сайте SharePoint, веб-часть средства просмотра отчетов и построитель отчетов отображаются на одном из языков, поддерживаемых для надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Список поддерживаемых языков см. в [загружаемых материалах по SQL Server](https://msdn.microsoft.com/sql/downloads/) и на странице загрузки надстройки для служб [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   Сайты и центр администрирования SharePoint, справка в Интернете и сообщения доступны на языках, поддерживаемых продуктами Office Server.  
  
 Если язык, используемый продуктом или технологией SharePoint, отличается от языка сервера отчетов, службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] будут использовать язык из той же языковой группы, который ближе всего к языку SharePoint. Если подходящий язык недоступен, сервер отчетов будет использовать английский язык.  
  
##  <a name="related-tasks"></a><a name="bkmk_relatedtasks"></a> Связанные задачи

 В следующей таблице перечислены задачи, связанные с сервером отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме SharePoint.  
  
|**Задача**|**Ссылка**|  
|--------------|--------------|  
|Подробные шаги по установке и настройке службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции SharePoint.|[Установите Reporting Services режим SharePoint для sharepoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) и [добавьте дополнительный сервер отчетов в ферму &#40;горизонтальное масштабирование SSRS&#41;](install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).|  
|Горизонтально масштабируемое развертывание [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint путем добавления дополнительных серверов отчетов.|[Добавьте дополнительный сервер отчетов в ферму &#40;масштабируемые&#41;](install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) и [топологии развертывания для функций бизнес-аналитики SQL Server в SharePoint](../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md) .|  
|Добавление дополнительных клиентских веб-интерфейсов SharePoint с установленными компонентами [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для просмотра и отображения элементов отчетов.|[Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферме](install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Настройка электронной почты для подписок и предупреждений об изменении данных в службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[Настройка электронной почты для приложения служб Reporting Services (SharePoint 2010 и SharePoint 2013)](install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|  
|Последние сведения об этом выпуске доступны на TechNet Wiki.|[SQL Server 2012 Reporting Services советы, приемы и устранение неполадок](https://go.microsoft.com/fwlink/?LinkId=221297).|  
  
## <a name="see-also"></a>См. также:  
 [Установка или удаление надстройки Reporting Services для sharepoint &#40;sharepoint 2010 и sharepoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) [требования к оборудованию и программному обеспечению для Reporting Services в](../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md) [веб-части «Средство просмотра отчетов](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) в режиме интеграции с SharePoint» на сайте SharePoint