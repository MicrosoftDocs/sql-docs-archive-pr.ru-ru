---
title: Системные параметры (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- Master Data Services, system settings
- system settings [Master Data Services]
ms.assetid: 83075cdf-f059-4646-8ba2-19be8202f130
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 667c154998a0e3f43018b63472619bcb37d9795a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664968"
---
# <a name="system-settings-master-data-services"></a>Системные параметры (службы Master Data Services)
  Для всех веб-приложений и веб-служб, связанных с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , можно задавать системные настройки.  
  
 Многие из этих параметров можно изменить в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] на странице **База данных** . Другие параметры можно настроить в таблице системных параметров (mdm.tblSystemSetting) в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Параметры можно разделить на следующие категории:  
  
-   [Общие параметры](#General)  
  
-   [Параметры управления версиями](#Versions)  
  
-   [Параметры промежуточного хранения](#Staging)  
  
-   [Параметры обозревателя](#Explorer)  
  
-   [Надстройка для параметров Excel](#xls)  
  
-   [Параметры бизнес-правил](#BusinessRules)  
  
-   [Параметры уведомлений](#Notifications)  
  
-   [Параметры безопасности](#Security)  
  
-   [Не используется](#NotUsed)  
  
##  <a name="general-settings"></a><a name="General"></a>Общие параметры  
  
|Параметр диспетчера конфигурации|Системный параметр|Описание|  
|-----------------------------------|--------------------|-----------------|  
|**Время ожидания подключения к базе данных**|**DatabaseConnectionTimeOut**|Число секунд, которое база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] отводит на установление соединения. Если в течение этого времени соединение не установлено, оно отменяется и возвращается ошибка. Значение по умолчанию — **60** секунд (1 минута).|  
|**Время ожидания выполнения команды в базе данных**|**DatabaseCommandTimeOut**|Число секунд, которое база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] отводит на выполнение команды. Если команда не завершается в течение указанного времени, то она отменяется и возвращается ошибка. Значение по умолчанию — **3600** секунд (60 минут).|  
|**Время ожидания веб-службы**|**ServerTimeOut**|Число секунд, которое ASP.NET отводит на выполнение запроса страницы [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Если запрос не выполняется в течение указанного периода времени, выполнение запроса отменяется и возвращается ошибка. Значение по умолчанию — **120000** секунд (2000 минут).|  
|**Время ожидания клиента**|**ClientTimeOut**|Период неактивности в секундах, по истечении которого [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] возвращается на домашнюю страницу. Значение по умолчанию — **300** секунд (5 минут).|  
|**Количество строк в пакете**|**ровспербатч**|Число записей для извлечения в каждом пакете, возвращаемом веб-службой. Значение по умолчанию — **50**.|  
||**ApplicationName**|Текст, отображаемый в журналах событий. Значение по умолчанию — **MDM**.|  
||**SiteTitle**|Текст, отображаемый в заголовке окна веб-браузера [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Значение по умолчанию — **Диспетчер основных данных**.|  
  
##  <a name="version-management-settings"></a><a name="Versions"></a> Параметры управления версиями  
  
|Параметр диспетчера конфигурации|Системный параметр|Описание|  
|-----------------------------------|--------------------|-----------------|  
|**Копирование только подтвержденных версий**|**CopyOnlyCommittedVersion**|В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]определяет, могут ли пользователи копировать версии модели с состоянием **Зафиксирована**либо версии с произвольным состоянием. Значение по умолчанию — **Да** или **1**. Оно указывает, что пользователи могут копировать только версии в состоянии **Зафиксировано** . Чтобы разрешить пользователям копировать все версии, измените это значение на **Нет** или **2**.|  
  
 Дополнительные сведения см. в разделе [Версии (службы Master Data Services)](versions-master-data-services.md).  
  
##  <a name="staging-settings"></a><a name="Staging"></a> Промежуточные параметры  
  
|Параметр диспетчера конфигурации|Системный параметр|Описание|  
|-----------------------------------|--------------------|-----------------|  
|**Регистрация всех промежуточных транзакций в журнале**|**StagingTransactionLogging**|Применимо только к SQL Server 2008 R2. Определяет, будет ли вестись запись в журнал транзакций при загрузке промежуточных данных в базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Значение по умолчанию — **Выключено** или **2**. Измените значение на **Включено** или **1** , чтобы включить ведение журнала.|  
|**Интервал промежуточного хранения пакетов**|**StagingBatchInterval**|В функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Integration Management** functional area, the number of seconds after you select **Start Batches** that your batch is processed. Значение по умолчанию — **60** секунд (1 минута).|  
  
 Дополнительные сведения см. в разделе [Импорт данных (службы Master Data Services)](overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="explorer-settings"></a><a name="Explorer"></a> Параметры обозревателя  
  
|Параметр диспетчера конфигурации|Системный параметр|Описание|  
|-----------------------------------|--------------------|-----------------|  
|**Количество элементов в иерархии, задаваемое по умолчанию**|**HierarchyChildNodeLimit**|В функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Обозреватель** отображается максимальное количество элементов, которые отображаются в каждом узле иерархии до появления ссылки **…еще…**. Ссылку **…еще…** можно щелкнуть для отображения следующей группы элементов. Значение по умолчанию — **50**.|  
|**Отображать имена в иерархии по умолчанию**|**ShowNamesInHierarchy**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, determines the default setting that is selected when you view hierarchies.<br /><br /> Значение по умолчанию — **Да** или **1**, что задает отображение имени и кода каждого элемента. Измените значение на **Нет** или **2** , чтобы отображать только код.|  
|**Количество атрибутов на основе домена в списке**|**DBAListRowLimit**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the number of attributes that are displayed in a list when you double-click a domain-based attribute value in the grid. Значение по умолчанию — **50**. Если имеется более 50 элементов, вместо этого отображается диалоговое окно с возможностью поиска.|  
||**GridFilterDefaultFuzzySimilarityLevel**|Определяет функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the level of similarity used when using the **Matches** filter criteria. Значение по умолчанию — **0,3**. При выборе значения ближе к **1** возвращаются элементы, более соответствующие указанным критериям. Задайте значение **1** для точного сопоставления.|  
  
##  <a name="add-in-for-excel-settings"></a><a name="xls"></a>Надстройка для параметров Excel  
  
|Параметр диспетчера конфигурации|Системный параметр|Описание|  
|-----------------------------------|--------------------|-----------------|  
|Отображать текст надстройки для Excel на домашней странице веб-сайта|ShowAddInText|Отображать ссылку на домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , чтобы пользователь мог скачать [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|  
|Путь установки надстройки для Excel на домашней странице веб-сайта|AddInURL|Если на домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] отображается ссылка на [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] , то это будет место, куда будут переходить пользователи при нажатии на эту ссылку.|  
  
##  <a name="business-rule-settings"></a><a name="BusinessRules"></a> Параметры бизнес-правил  
  
|Параметр диспетчера конфигурации|Системный параметр|Описание|  
|-----------------------------------|--------------------|-----------------|  
|**Шаг приращения для новых бизнес-правил**|**BusinessRuleDefaultPriorityIncrement**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **System Administration** functional area, the number the priority of each new business rule is incremented by. Значение по умолчанию: **10**.|  
|**Количество элементов, к которым применяются бизнес-правила**|**BusinessRuleRealtimeMemberCount**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the maximum number of members in the grid to apply business rules to. В [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]— максимальное число элементов на активном листе, к которым применяется бизнес-правило. Значение по умолчанию — **10000**.|  
  
 Дополнительные сведения см. в статье [Бизнес-правила (службы Master Data Services)](../../2014/master-data-services/business-rules-master-data-services.md).  
  
##  <a name="notification-settings"></a><a name="Notifications"></a>Параметры уведомлений  
  
|Параметр диспетчера конфигурации|Системный параметр|Описание|  
|-----------------------------------|--------------------|-----------------|  
|**URL-адрес диспетчера основных данных для уведомлений**|**MDMRootURL**|URL-адрес для веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], используемый в ссылке в уведомлениях, передаваемых по электронной почте, например http://constoso/mds.|  
|**Интервал передачи уведомлений по электронной почте**|**NotificationInterval**|Частота отправки уведомлений по электронной почте в секундах. Значение по умолчанию — **120** секунд (2 минуты).|  
|**Число уведомлений в одном сообщении электронной почты**|**NotificationsPerEmail**|Максимальное число ошибок проверки, которые могут быть перечислены в одном уведомлении по электронной почте. Остальные ошибки, если они есть, не будут включены в сообщение электронной почты, но с ними можно ознакомиться в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].|  
|**Формат сообщений электронной почты по умолчанию**|**EmailFormat**|Формат для всех уведомлений по электронной почте. Значение по умолчанию — **HTML** или **1**. Значение **2** этого параметра базы данных означает **Текст**.<br /><br /> Примечание. Этот формат можно переопределить для отдельного пользователя в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], изменив и сохранив **Формат электронной почты** на вкладке **Общие** пользователя.|  
|**Регулярное выражение для адреса электронной почты**|**EmailRegExPattern**|В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] функциональной области **разрешения пользователей и групп** регулярное выражение, используемое для проверки адреса электронной почты, указанного на вкладке **Общие** пользователя. Дополнительные сведения о регулярных выражениях см. в разделе [элементы языка регулярных выражений](https://go.microsoft.com/fwlink/?LinkId=164401) в библиотеке MSDN.|  
|**Учетная запись Database Mail**|**EmailProfilePrincipalAccount**|Отображает учетную запись компонента Database Mail, которая используется при отправке уведомлений по электронной почте. Профиль по умолчанию — **mds_email_user**.|  
|**Профиль Database Mail**|**DatabaseMailProfile**|Профиль компонента Database Mail, который используется при отправке уведомлений по электронной почте. Значение по умолчанию — пусто.|  
||**ValidationIssueHTML**|В формате HTML — текст сообщения электронной почты, которое получают пользователи при сбое проверки бизнес-правила.|  
||**ValidationIssueText**|В текстовом формате — текст сообщения электронной почты, которое получают пользователи при сбое проверки бизнес-правила.|  
||**VersionStatusChangeText**|В текстовом формате — текст сообщения электронной почты, которое получают пользователи при изменении состояния версии. Это сообщение электронной почты получают только пользователи, имеющие разрешение **Обновление** для всей модели.|  
||**VersionStatusChangeHTML**|В формате HTML — текст электронного сообщения, которые получают пользователи при изменении состояния версии. Это сообщение электронной почты получают только пользователи, имеющие разрешение **Обновление** для всей модели.|  
  
 Дополнительные сведения см. в разделе [Уведомления (службы Master Data Services)](../../2014/master-data-services/notifications-master-data-services.md).  
  
##  <a name="security-settings"></a><a name="Security"></a>Параметры безопасности  
  
|Параметр диспетчера конфигурации|Системный параметр|Описание|  
|-----------------------------------|--------------------|-----------------|  
||**SecurityMemberProcessInterval**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **User and Group Permissions** functional area, the frequency, in seconds, that user and group permissions set on the **Hierarchy Members** tab are applied. Значение по умолчанию — **3600** секунд (60 минут).|  
  
 Дополнительные сведения см. в разделе [Срочное применение разрешений для элемента (службы Master Data Services)](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="not-used"></a><a name="NotUsed"></a>Не используется  
 Следующие параметры в таблице системных параметров не используются:  
  
-   **SecurityMode**  
  
-   **MDSHubName**  
  
-   **ApplicationLogging**  
  
-   **ReportServer**  
  
-   **ReportDirectory**  
  
-   **BusinessRuleEngineIterationLimit**  
  
-   **BusinessRuleExtensibility**  
  
-   **AttributeExplorerMarkAllActionMemberCount**  
  
## <a name="see-also"></a>См. также:  
 [Защита объектов базы данных (службы Master Data Services)](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  
