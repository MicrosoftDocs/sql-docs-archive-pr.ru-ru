---
title: Установка Reporting Services режима SharePoint для SharePoint 2010 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 47efa72e-1735-4387-8485-f8994fb08c8c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8be76ab37ce66f4ef93d29093202768aa85c4fb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666389"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2010"></a>Установка служб Reporting Services в режиме SharePoint для SharePoint 2010
  Процедуры, описанные в данном разделе, позволят установить сервер отчетов служб Reporting Services на одиночный сервер в режиме SharePoint. Эти шаги включают запуск мастера установки SQL Server, а также дополнительные задачи по настройке с использованием центра администрирования SharePoint 2010. В этом разделе также можно ознакомиться с отдельными процедурами для существующей установки, например созданием приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Сведения о добавлении дополнительных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] серверов в существующую ферму см. в разделе [Добавление дополнительного сервера отчетов в ферму &#40;масштабирование SSRS&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) и [Добавление дополнительного Reporting Services клиентского веб-интерфейса в ферму](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010|  
  
 Установка на одиночный сервер полезна в сценариях разработки и тестирования, но не рекомендуется для рабочих сред.  
  
> [!NOTE]  
>  Сведения об обновлении и существующей [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] установке в режиме интеграции с SharePoint в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] см. в разделе [обновление и миграция Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  

  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Предварительные требования  
  
-   > [!IMPORTANT]  
    >  Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] больше не требуется и может использоваться для настройки и администрирования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Для настройки сервера отчетов в режиме Sharepoint используйте центр администрирования SharePoint. Дополнительные сведения см. [в разделе Управление приложением службы Reporting Services SharePoint](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
-   В следующих разделах содержится описание применимых требований, в том числе к продуктам SharePoint 2010:  
  
    -   [Заметки о выпуске в Интернете](https://msdn.microsoft.com/library/dn169381.aspx)
  
    -   [Указания по использованию функций бизнес-аналитики SQL Server в ферме SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
-   Этот раздел не охватывает установку продуктов SharePoint 2010. Дополнительные сведения см. [в руководстве по использованию SQL Server функций бизнес-аналитики в ферме SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).  
  
-   Эти процедуры предназначены для настройки сервера отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и не работают для предыдущих версий сервера отчетов. Предыдущие версии сервера отчетов не использовали архитектуру общей службы SharePoint. Примерами могут служить серверы отчетов служб SQL Server 2008 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и SQL Server 2008 R2 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   Убедитесь, что служба **администрирования SharePoint 2010** запущена в Диспетчер сервера Windows.  
  
 ![Компоненты служб SSRS на 1 установке сервера](../../../2014/sql-server/install/media/rs-deployment-1-server.gif "Компоненты служб SSRS на 1 установке сервера")  
  
### <a name="database-considerations-for-a-single-server-configuration"></a>Сведения о базах данных для конфигурации с одиночным сервером  
  
-   Как службы Reporting Services, так и продукты и технологии SharePoint используют реляционные базы данных SQL Server для хранения данных приложений.  
  
-   Службы [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] требуют наличия совместимого экземпляра ознакомительного выпуска компонента SQL Engine сервера SQL Server.  
  
-   Продукты SharePoint могут использовать существующий экземпляр базы данных. Если экземпляр компонента ядра СУБД не установлен, программа установки продуктов SharePoint устанавливает для баз данных приложений SharePoint экспресс-выпуск SQL Server.  
  
-   Экземпляр сервера отчетов не может использовать для своей базы данных выпуск SQL Server Express Edition. Однако экземпляр экспресс-выпуска SQL Server, установленный продуктом SharePoint, может существовать параллельно с другими выпусками компонента ядра СУБД.  
  

  
##  <a name="install-reporting-services-report-server-in-sharepoint-mode"></a><a name="bkmk_install_SSRS"></a>Установка Reporting Services сервера отчетов в режиме интеграции с SharePoint  
  
1.  Запустите мастер установки SQL Server.  
  
2.  Нажмите кнопку **Установка** в левой части мастера, затем выберите пункт **Новая изолированная установка SQL Server или добавление функций в существующую установку**.  
  
3.  Нажмите кнопку **ОК** на странице **Правила поддержки установки** в предположении, что все правила выполнены.  
  
4.  Нажмите кнопку **Установить** на странице **Файлы поддержки установки** .  
  
5.  Нажмите кнопку **Далее** после завершения установки файлов поддержки, после чего правила поддержки отобразят состояние **пройдено**. Просмотрите все предупреждения и определите критические препятствия.  
  
6.  На странице **ключ продукта** введите свой ключ или примите значение по умолчанию для выпуска Enterprise Evaluation.  
  
     Щелкните **Далее**.  
  
7.  Просмотрите и примите условия лицензионного соглашения. Корпорация Майкрософт будет признательна вам за согласие отправлять данные об использовании компонентов, которые помогут улучшить функции и поддержку продукта.  
  
     Щелкните **Далее**.  
  
8.  Выберите **SQL Server Установка компонентов** на странице **роль установки** .  
  
     Нажмите кнопку **Далее**  
  
     ![Установка компонентов SQL Server для роли установки](../../../2014/sql-server/install/media/rs-setuprole.gif "Установка компонентов SQL Server для роли установки")  
  
9. Выберите следующие компоненты на странице **Выбор компонентов** :  
  
    -   **Reporting Services — SharePoint**  
  
    -   **Reporting Services надстройки для продуктов SharePoint 2010**. ![Примечание](../../../2014/reporting-services/media/rs-fyinote.png "Примечание.") . Параметр мастера установки для установки надстройки является новым в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] выпуске.  
  
    -   Если экземпляр компонента SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]еще не установлен, для завершения установки можно также выбрать **Службы ядра СУБД** и **Полный набор средств управления** .  
  
     Щелкните **Далее**.  
  
     ![Выбор компонентов служб SSRS для режима интеграции с SharePoint](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "Выбор компонентов служб SSRS для режима интеграции с SharePoint")  
  
10. На странице **правила установки** нажмите кнопку **Далее** . Просмотрите все предупреждения и определите критические препятствия.  
  
11. Если выбрана установка служб Database Engine, примите экземпляр **MSSQLSERVER** по умолчанию на странице **Настройка экземпляра** и нажмите кнопку **Далее**. Архитектура общей службы Reporting Services не основывается на «экземпляре» SQL Server, как в прежних версиях архитектуры служб Reporting Services.  
  
12. Просмотрите страницу **Требования к месту на диске** и нажмите **Далее**.  
  
13. На странице **Конфигурация сервера** введите соответствующие учетные данные. Если необходимо использовать функции предупреждения об изменении данных или подписки на данные служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , необходимо изменить **Тип запуска** для агента SQL Server на **Автоматический**.  
  
     Щелкните **Далее**.  
  
14. Если выбрана установка служб ядра СУБД, откроется страница **Настройка компонента Database Engine** , на которой следует добавить соответствующие учетные записи в список администраторов SQL и нажать кнопку **Далее**.  
  
15. На странице **Настройка служб Reporting Services** будет выбран вариант **Только установка** . При выборе этого варианта устанавливаются файлы сервера отчетов, но среда SharePoint для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не настраивается. По завершении установки SQL Server нужно будет настроить среду SharePoint, как описано в других подразделах этого раздела. В том числе надо будет установить общую службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и создать приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
     ![rs_SQL11_SETUP_SSRS_configpage_withcircles](../../../2014/sql-server/install/media/rs-kj-setup-ssrs-configpage-withcircles.gif "rs_SQL11_SETUP_SSRS_configpage_withcircles")  
  
16. Помогите компании Майкрософт улучшить работу функций и служб SQL Server, установив флажок в знак согласия отправлять отчеты об ошибках на странице **Отчеты об ошибках** .  
  
     Щелкните **Далее**.  
  
17. Просмотрите возможные предупреждения и нажмите кнопку **Далее** на странице **Правила настройки установки** .  
  
18. На странице **Все готово для установки** просмотрите сводку по установке и нажмите кнопку **Далее**. В сводку будет включен узел **Reporting Services** , который будет включать в себя значение режима установки **SharePointFilesOnlyMode** , а также сведения об учетной записи.  
  

  
##  <a name="install-and-start-the-reporting-services-sharepoint-service"></a><a name="bkmk_install_SSRS_sharedservice"></a>Установка и запуск службы Reporting Services SharePoint  
 ![Содержимое, связанное с PowerShell](../../../2014/reporting-services/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
> [!NOTE]  
>  Если вы устанавливаете в существующую ферму SharePoint, **вам не нужно** выполнять действия, описанные в этом разделе. Служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint была установлена и запущена в результате выполнения мастера установки SQL Server, описанного в предыдущем разделе.  
  
 Необходимые файлы были установлены в процессе работы мастера установки SQL Server, но службы необходимо зарегистрировать в ферме SharePoint. В выпуске [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] появилась поддержка PowerShell для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint. Следующие шаги позволяют открыть консоль управления SharePoint и запустить командлеты.  
  
1.  Нажмите кнопку **Пуск** .  
  
2.  Щелкните группу **продуктов Microsoft SharePoint 2010** .  
  
3.  Щелкните правой кнопкой мыши **SharePoint 2010 Management Shell** и выберите команду **Запуск от имени администратора**.  
  
4.  Выполните следующую команду PowerShell, чтобы установить службу SharePoint. При успешном завершении команды отобразится новая строка в консоли управления. При успешном завершении работы команды в консоль управления не возвращаются какие-либо сообщения:  
  
    ```powershell
    Install-SPRSService  
    ```  
  
5.  Выполните следующую команду PowerShell, чтобы установить прокси-сервер службы:  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  Выполните следующую команду PowerShell, чтобы запустить службу, или просмотрите нижеперечисленные замечания для получения указаний по запуску службы из центра администрирования SharePoint.  
  
    ```powershell
    Get-SPServiceInstance -All | Where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 Можно также запустить службу из центра администрирования SharePoint, а не с помощью третьей команды PowerShell. С помощью следующих шагов можно также проверить, выполняется ли служба.  
  
1.  В центре администрирования SharePoint выберите пункт **Управление службами на сервере** в группе **Параметры системы** .  
  
2.  Найдите **Службу SQL Server Reporting Services** и нажмите кнопку **Запуск** в столбце «Действие».  
  
3.  Состояние службы Reporting Services изменится с **Остановлена** на **Запущена**. Если служба Reporting Services отсутствует в списке, используйте PowerShell для установки службы.  
  
    > [!NOTE]  
    >  Если служба Reporting Services остается в состоянии **запуска** и не меняется на " **запущена**", проверьте, запущена ли служба администрирования SharePoint 2010 в Windows Диспетчер сервера.  

##  <a name="create-a-reporting-services-service-application"></a><a name="bkmk_create_serrviceapplication"></a>Создание приложения службы Reporting Services  
 В этом разделе описаны шаги по созданию приложения службы и описания его свойств (в случае просмотра существующего приложения службы).  
  
1.  В центре администрирования SharePoint в группе **Управление** приложениями щелкните **Управление приложениями служб**.  
  
2.  На ленте SharePoint нажмите кнопку **Создать** .  
  
3.  В меню кнопки «Создать» выберите пункт **Приложение службы SQL Server Reporting Services**.  
  
    > [!WARNING]  
    >  Если [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] параметр не отображается в списке, это **означает, что [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Общая служба не установлена**. Просмотрите предыдущий раздел, в котором описана установка службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с помощью командлетов PowerShell.  
  
4.  На странице **Создание приложения службы SQL Server Reporting Services** введите имя приложения. При создании нескольких приложений службы Reporting Services описательное имя или контекст именования поможет лучше организовать администрирование и управление.  
  
5.  В разделе **Пул приложений** создайте для данного приложения новый пул приложений (рекомендуется). Если использовать для нового пула приложений то же имя, что и для приложения службы, дальнейшее администрирование станет проще.  
  
     Выберите или создайте управляемую учетную запись для пула приложений. Обязательно укажите учетную запись домена. Учетная запись пользователя домена позволяет использовать функцию управляемой учетной записи SharePoint, с помощью которой пароли и данные учетной записи можно изменять в одном месте. Учетные записи домена также требуются, если планируется расширение развернутой системы и включение дополнительных экземпляров службы, которые работают от лица одного идентификатора.  
  
6.  В поле **Сервер баз данных**можно указать текущий сервер или выбрать другой SQL Server.  
  
7.  В поле **Имя базы данных** будет содержаться значение по умолчанию `ReportingService_<guid>`, представляющее собой уникальное имя базы данных. При вводе нового значения оно должно быть уникальным.  
  
8.  В списке **Проверка подлинности базы данных**по умолчанию выбрано значение «Проверка подлинности Windows». Если выбран параметр **Проверка подлинности SQL**, то рекомендации по использованию этого типа проверки подлинности в развернутой системе SharePoint см. в руководстве администратора SharePoint.  
  
9. В подразделе **Связь с веб-приложением** выберите веб-приложение, которое должно быть подготовлено для доступа со стороны текущего приложения службы Reporting Services. Одно приложение службы Reporting Services можно связать с одним веб-приложением. Если все имеющиеся веб-приложения уже связаны с приложением службы Reporting Services, отображается предупреждение.  
  
10. Нажмите кнопку **ОК**.  
  
11. Создание приложения службы может занять несколько минут. По завершении этого процесса отобразятся подтверждение и ссылка на страницу **Подготовка подписок и предупреждений** . Выполните этот шаг подготовки, если нужно использовать функции подписки и предупреждения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения см. в разделе [Подготовка подписок и предупреждений для приложений служб SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  
 ![Содержимое, связанное с PowerShell](../../../2014/reporting-services/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") Сведения об использовании PowerShell для создания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] приложения службы см. в статье [Создание приложения службы Reporting Services с помощью PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).  
  

  
##  <a name="activate-the-power-view-site-collection-feature"></a><a name="bkmk_powerview"></a>Активируйте компонент семейства веб-сайтов Power View.  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], компонент [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройки для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] выпуска Enterprise Edition — это функция семейства веб-сайтов. Этот компонент активируется автоматически для корневых семейств веб-сайтов, созданных после установки надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Если вы планируете использовать [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], необходимо удостовериться в том, что этот компонент активирован.  
  
 При установке надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint 2010 после установки продукта SharePoint 2010 функция интеграции с сервером отчетов и функция интеграции с Power View будут активированы только для корневых семейств веб-сайтов. Для других семейств веб-сайтов необходимо активировать эти компоненты вручную.  
  
#### <a name="to-activate-the-power-view-feature"></a>Активация компонента Power View  
  
1.  Откройте в браузере требуемый сайт SharePoint.  
  
2.  Щелкните **Действия сайта**.  
  
3.  Щелкните элемент **Настройки сайта**.  
  
4.  Щелкните **Функции семейства веб-сайтов** в группе администраторов семейства веб-сайтов.  
  
5.  Найдите в списке **Компонент интеграции Power View** .  
  
6.  Щелкните **Активировать**.  
  
 Эта процедура выполняется для каждого семейства веб-сайтов. Дополнительные сведения см. [в разделе Активация сервера отчетов и функций интеграции Power View в SharePoint](../../reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) .  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional_config"></a>Дополнительная настройка  
 В этом разделе описываются дополнительные действия по настройке, которые важны для большинства развертываний SharePoint.  
  
###  <a name="provision-subscriptions-and-alerts"></a><a name="bkmk_provision_agent"></a>Подготавливайте подписки и оповещения  
 Для функций подписок и предупреждений об изменении данных в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] может потребоваться настройка разрешений для агента SQL Server. Если отображается сообщение об ошибке, указывающее, что необходим агент SQL Server, хотя агент SQL Server уже запущен, обновите разрешения. Щелкните ссылку **Подготовка подписок и предупреждений** на странице с сообщением об успешном создании приложения службы, чтобы перейти на страницу провизионирования агента SQL Server. Шаг подготовки необходим, если система развернута более чем на одном компьютере, например если экземпляр базы данных SQL Server находится на другом компьютере. Дополнительные сведения см. в статье о [подготовке подписок и предупреждений для приложений служб SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md) .  
  

  
### <a name="configure-e-mail-for-a-service-application"></a>Настройка электронной почты для приложения службы  
 Функция предупреждения об изменении данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отправляет предупреждения в сообщениях электронной почты. Для отправки электронной почты могут потребоваться настройка приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и изменение модуля доставки электронной почты приложением службы. Параметры электронной почты необходимо настроить и в случае, если планируется использование модуля доставки электронной почты функцией подписки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в статье [Настройка электронной почты для приложения служб Reporting Services (SharePoint 2010 и SharePoint 2013)](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  

  
### <a name="add-reporting-services-content-types"></a>Добавление типов содержимого служб Reporting Services  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] обеспечивают стандартные типы содержимого, предназначенные для управления файлами общих источников данных (RSDS), моделей отчетов (SMDL) и определений отчетов (RDL) построителя отчетов. После добавления в библиотеку типов содержимого **Отчет построителя отчетов**, **Модель отчета**и **Источник данных отчета** становится доступной команда **Создать** , позволяющая создавать новые документы этих типов. Дополнительные сведения см. в разделе [Добавление типов содержимого сервера отчетов в библиотеку &#40;Reporting Services в режиме интеграции с SharePoint&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  

  
### <a name="activate-the-file-sync-feature"></a>Активация функции синхронизации файлов  
 Если пользователи часто передают элементы опубликованных отчетов непосредственно в библиотеки документов SharePoint, может оказаться полезной функция синхронизации файлов сервера отчетов. Функция синхронизации файлов позволяет синхронизировать каталог сервера отчетов с элементами библиотек документов на более регулярной основе. Дополнительные сведения см. [в разделе Активация компонента синхронизация файлов сервера отчетов в центре администрирования SharePoint](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).  
  
## <a name="see-also"></a>См. также:  
 [Командлеты PowerShell для Reporting Services режиме SharePoint](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)   
 [Функции, поддерживаемые различными выпусками SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473)   
 [Служба SharePoint и Служебные приложения службы Reporting Services](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)  
