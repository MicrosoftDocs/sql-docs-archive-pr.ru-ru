---
title: Средства настройки PowerPivot | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f934c51d-01fe-4e67-971d-cd87d7d7ee51
author: minewiskan
ms.author: owend
ms.openlocfilehash: de11cdaf304b3010dcf21725edd2d3cbfa84ae0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667419"
---
# <a name="powerpivot-configuration-tools"></a>PowerPivot Configuration Tools
  Настройка, восстановление или удаление с помощью [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] средства настройки PowerPivot.

 Мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] установит средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2010, а также средство настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2013. В этом разделе приводится описание принципов использования обоих средств и различий между ними.

 **[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 | SharePoint 2010

 **В этом разделе.**

-   [Требования к использованию средств настройки](#bkmk_requirements)

-   [2 версии средства настройки](#bkmk_twoversions)

-   [Общие сведения об использовании средства настройки PowerPivot](#bkmk_overview)

-   [Запустите одно из средств настройки PowerPivot.](#bmkm_start_tool)

##  <a name="requirements-for-using-the-configuration-tools"></a><a name="bkmk_requirements"></a>Требования к использованию Средства настройки

-   Необходимо быть администратором фермы.

-   Необходимо быть администратором сервера для экземпляра служб Analysis Services (только для SharePoint 2010).

-   Необходимо db_owner в базе данных конфигурации фермы.

-   При работе со средствами настройки порты TCP/IP не задействуются, поэтому не нужно выполнять какую-либо особую настройку брандмауэра. При работе со средством настройки подразумевается, что веб-приложения и общие службы входят в состав платформы SharePoint. Может потребоваться настройка брандмауэра для сервера служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в статье [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).

##  <a name="two-versions-of-the-configuration-tool"></a><a name="bkmk_twoversions"></a>Две версии средства настройки
 Мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] установит средства настройки PowerPivot для SharePoint 2010, а также средство настройки PowerPivot для SharePoint 2013.

 Средства можно использовать только с экземпляром [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] объекта [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Не следует использовать средства с установками [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .

|Имя|Поддерживаемая версия SharePoint|Подробные данные конфигурации|
|----------|-------------------------------------|----------------------------|
|Настройка PowerPivot для SharePoint 2013|SharePoint 2013|[Настройка или восстановление PowerPivot для SharePoint 2013 &#40;средства настройки PowerPivot&#41;](configure-or-repair-power-pivot-for-sharepoint-2013.md)|
|Средство настройки PowerPivot|SharePoint 2010 с @@@SharePoint 2010@@@|[Настройка или восстановление PowerPivot для SharePoint 2010 &#40;средства настройки PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md)|

###  <a name="how-the-two-configuration-tools-are-different"></a><a name="bkmk_sum_differences_betweentools"></a>Отличия двух Средства настройки
 Две версии средств настройки похожи, однако есть отличия в этапах настройки, которые применяются средствами. Отличия обусловлены изменениями между SharePoint 2010 и SharePoint 2013, а также отличиями в архитектуре между версией SQL Server 2012 с пакетом обновления 1 (SP1) PowerPivot для SharePoint и предыдущими версиями PowerPivot для SharePoint.

 В следующей таблице приводится описание новых и измененных функций в средстве **Настройка PowerPivot для SharePoint 2013** . Таблица также содержит описание возможностей в **средстве настройки PowerPivot** , не входящих в средство настройки PowerPivot для SharePont 2013. Строки в таблице располагаются в том же порядке, что и вкладки в средстве настройки.

|Настройка PowerPivot для SharePoint 2013|Средство настройки PowerPivot|
|--------------------------------------------------|-----------------------------------|
|На главной странице появился новый параметр для **PowerPivot Server для служб Excel**. Параметр поддерживает новую архитектуру с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , выполняемым за пределами фермы SharePoint. Необходимо настроить службы Excel для использования одного или нескольких серверов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , работающих в режиме интеграции с SharePoint.<br /><br /> ![Сервер PowerPivot в новом средстве настройки](../media/as-powerpivot-configtool-differences-new-mainpage.gif "Сервер PowerPivot в новом средстве настройки")||
||Средство 2010 содержит страницу **Регистрация служб SQL Server Analysis Services (PowerPivot) на локальном сервере** для настройки локального экземпляра [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Эта страница не является частью средства 2013, поскольку локальный экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]отсутствует.<br /><br /> ![Учетная запись службы AS в старом средстве настройки](../media/as-powerpivot-configtool-differences-old-register-as-localserver.gif "Учетная запись службы AS в старом средстве настройки")|
||Страница **Создание приложения службы PowerPivot** содержит дополнительный параметр **Обновить книги, чтобы получить возможность обновления данных**. Этот параметр недоступен в средстве 2013.<br /><br /> ![обновление книг в старом средстве настройки](../media/as-powerpivot-configtool-differences-old-uprgadeworkbooks.gif "обновление книг в старом средстве настройки")|
|В средстве 2013 появилась новая страница **Настройка серверов PowerPivot**. Эта страница поддерживает новую архитектуру экземпляра [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , выполняемого за пределами фермы SharePoint. По умолчанию имя сервера, которое было указано на главной странице в текстовом поле **Сервер PowerPivot для служб Excel**, также отображается на вкладке **Настройка серверов PowerPivot**.<br /><br /> ![Зарегистрировать новое средство настройки сервера PowerPivot](../media/as-powerpivot-configtool-differences-new-powerpivot-servers.gif "Зарегистрировать новое средство настройки сервера PowerPivot")||
|В средстве 2013 появилась новая страница **Регистрация надстройки PowerPivot в качестве модуля отслеживания служб Excel**. Службы Excel services SharePoint 2010 не отслеживают сведения об использовании PowerPivot.||
||Средство 2010 содержит страницу **Добавить MSOLAP.5 в качестве доверенного поставщика** для регистрации MSOLAP, чтобы службы Excel могли загружать в SharePoint 2010 модели PowerPivot. Эта страница не является частью средства 2013. SharePoint 2013 со службами Excel не использует поставщика MSOLAP для моделей загрузки.|

##  <a name="overview-of-using-a-powerpivot-configuration-tool"></a><a name="bkmk_overview"></a>Общие сведения об использовании средства настройки PowerPivot
 При запуске одного из средств настройки PowerPivot средство оценивает существующую установку для определения применимых операций. Для новой установки доступна только задача настройки. После настройки сервера появляется задача удаления. Если исходной установкой является экземпляр [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] , в списке доступных задач появится обновление.

 При отсутствии навыков работы с центром администрирования или Windows PowerShell это средство настройки можно использовать как альтернативу указанным инструментам для установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .

 Кроме того, средство умеет определять, настроена ли ферма, и не отсутствуют ли необходимые компоненты. Если программные файлы SharePoint установлены, но ферма не настроена, средство предоставляет действия для настройки фермы и установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .

 Ознакомьтесь с вкладкой **Скрипт** , чтобы изучить возможности настройки PowerPivot и SharePoint с помощью Windows PowerShell. Дополнительные сведения см. в следующих разделах:

-   [Настройка PowerPivot с помощью Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)

-   [Справочник по PowerShell для PowerPivot для SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)

> [!NOTE]
>  Средство не настраивает службы Reporting Services. При добавлении служб Reporting Services в среду SharePoint их следует устанавливать и настраивать отдельно. Дополнительные сведения см. в следующих разделах:
> 
>  -   [Установите Reporting Services режиме интеграции с SharePoint для sharepoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).
> -   [Установите Reporting Services режиме интеграции с SharePoint для sharepoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).

##  <a name="start-one-of-the-powerpivot-configuration-tools"></a><a name="bmkm_start_tool"></a>Запуск одной из Средства настройки PowerPivot

1.  На **начальном** экране введите`powerpivot`

     На **начальном** экране введите `powerpivot` или в меню **Пуск** последовательно выберите пункты **все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] , **средства настройки**и выберите один из следующих элементов:

    -   **Средство настройки PowerPivot**.

    -   **OR**

    -   **Настройка PowerPivot для SharePoint 2013**.

     ![два средства настройки powerpivot](../media/as-powerpivot-configtools-bothicons.gif "два средства настройки powerpivot")

     **Примечание.** Эти средства доступны, только если на локальном сервере установлен компонент [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .

2.  Во время запуска средство настройки проверяет состояние установки и предоставляет задачи, допустимые для нее.

3.  В зависимости от текущего состояния установки можно выполнить одну или несколько задач, указанных далее.

    1.  Нажмите кнопку **Настройка или восстановление PowerPivot для SharePoint** для выполнения задач после установки или для восстановления установки.

    2.  Нажмите кнопку **Удаление компонентов, служб, приложений и решений** для удаления компонентов и решений с фермы.

    3.  Нажмите кнопку **Обновление компонентов, служб, приложений и решений** для обновления компонентов и решений, установленных с помощью предыдущей версии [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].

     Например, изображение показывает страницу запуска средства настройки PowerPivot для SharePoint 2013.

     ![Средство настройки PowerPivot для SharePoint 2013](../media/ssas-powerpivot-configtool-4-sharepoint2013-choosemode.gif "Средство настройки PowerPivot для SharePoint 2013")

 Каждая задача состоит из индивидуальных действий, которые касаются определенных аспектов настройки сервера. Например, задача настройки включает действия по развертыванию решений, созданию приложения службы PowerPivot, активации компонентов и настройки обновления данных. Список действий зависит от текущего состояния установки. Если действие не требуется, средство исключает его из списка задач.

 При нажатии кнопки «Пуск» средство обработает все действия в пакетном режиме. Несмотря на то что каждое действие отображается как отдельный элемент в списке задач, все действия в составе задачи обрабатываются вместе. Обрабатываются только те действия, которые проходят проверку. Для прохождения проверки, возможно, потребуется добавить или изменить некоторые из входных значений.

## <a name="related-content"></a>См. также
 [Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) Рассматривает рабочий процесс, который обновляет установку, уже существующую в ферме.

 [Uninstall PowerPivot for SharePoint](../../sql-server/install/uninstall-power-pivot-for-sharepoint.md) Рассматривает рабочий процесс, который удаляет с фермы службы, решения и страницы приложений PowerPivot для SharePoint.

 [Настройка PowerPivot с помощью Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)

 [Настройка и администрирование сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md)


