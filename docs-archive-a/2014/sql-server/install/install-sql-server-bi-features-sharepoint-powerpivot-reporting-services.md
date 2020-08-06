---
title: Установка SQL Server компонентов бизнес-аналитики с помощью SharePoint (PowerPivot и Reporting Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3166107c-30c2-468e-bb1b-bb42b79b37c3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0a01c4bb8830483eec5f8299e8bd81de897d7ddb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666388"
---
# <a name="install-sql-server-bi-features-with-sharepoint-powerpivot-and-reporting-services"></a>Установка компонентов бизнес-аналитики SQL Server с SharePoint (PowerPivot и службы Reporting Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] могут интегрироваться с фермой Microsoft SharePoint для поддержки функций бизнес-аналитики (BI) в SharePoint. Эти компоненты включают [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]используется для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] доступа к данным в ферме SharePoint. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] — это подсистема обработки данных для книг, созданных в [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel, доступ к которым осуществляется из библиотеки SharePoint. После сохранения книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в библиотеке SharePoint ее можно использовать в качестве источника данных для отчетов [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] .

 Некоторые действия по установке и настройке, необходимые для SharePoint 2010, отличаются от действий, необходимых для SharePoint 2013. Некоторые подразделы в этом разделе применимы к обеим версиям SharePoint.

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|

 ![Примечание](../../../2014/reporting-services/media/rs-fyinote.png "Примечание.") . Заметки о текущем выпуске см. в разделе [заметки о выпуске SQL server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).

##  <a name="in-this-topic"></a><a name="bkmk_top"></a> Содержание раздела

-   [Сценарии бизнес-аналитики SQL Server и SharePoint 2013](#bkmk_bi_scenarios)

-   [Общие сведения об установке](#bkmk_install_sharepoint2013_overview)

## <a name="in-this-section"></a>в этом разделе
 В дополнение к сведениям в этом разделе см. следующие темы также в этом разделе содержимого.

 [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)

 [Указания по использованию функций бизнес-аналитики SQL Server в ферме SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)

 [Контрольные списки для установки компонентов бизнес-аналитики в SharePoint](../../../2014/sql-server/install/checklists-for-installing-bi-features-with-sharepoint.md)

 [Reporting Services установки в режиме интеграции с SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)

 [Установка PowerPivot для SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)

 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)

##  <a name="sql-server-bi-scenarios-and-sharepoint-2013"></a><a name="bkmk_bi_scenarios"></a>SQL Server сценариев бизнес-аналитики и SharePoint 2013
 В этом разделе представлены различные уровни бизнес-аналитики, которые можно установить и настроить.

 Службы Excel в SharePoint 2013 включают функции модели данных для обеспечения взаимодействия с книгой [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в браузере. Для базовых функций модели данных нет необходимости развертывать в ферму надстройку [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013. Достаточно установить сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint и зарегистрировать сервер в параметрах **Модель данных** служб Excel.

 Развертывание надстройки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 позволяет задействовать дополнительные функции и компоненты в ферме SharePoint. Дополнительные возможности включают коллекцию [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , обновления данных расписания и панели управления PowerPivot. Дополнительные сведения см. в таблице.

||Level|Компоненты|Установка и настройка|
|-|-----------|--------------|--------------------------|
|1|Только SharePoint|Собственные функции служб Excel|Службы Excel и другие службы, поставляемые с SharePoint Server 2013.|
|**2**|SharePoint со службами Analysis Services в режиме интеграции с SharePoint|Интерактивные книги PowerPivot в браузере|Установите [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint.<br /><br /> Зарегистрируйте сервер служб Analysis Services в службах Excel.|
|**3**|SharePoint со службами Reporting Services в режиме интеграции с SharePoint|Power View|Установите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.<br /><br /> Установите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройку **(rsSharePoint.msi)** для SharePoint. Дополнительные сведения см. [в разделе Установка или удаление надстройки Reporting Services для sharepoint &#40;sharepoint 2010 и sharepoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)|
|**4**|Все функции PowerPivot|Доступ к книгам для использования их в качестве источника данных из-за пределов фермы.<br /><br /> Расписание обновления данных.<br /><br /> Коллекция PowerPivot.<br /><br /> Панель мониторинга управления.<br /><br /> Тип содержимого файла связи BISM.|Развертывание надстройки PowerPivot для SharePoint 2013 **(spPowerPivot.msi)**. Дополнительные сведения см. в следующих разделах:<br /><br /> [Установка и удаление надстройки PowerPivot для SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)<br /><br /> Дополнительные сведения о том, как загрузить **spPowerPivot.msi**, см. в разделе [Загрузка SQL Server 2014 PowerPivot для SharePoint](https://go.microsoft.com/fwlink/?LinkID=296473).|

 Дополнительные сведения о включении [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] функций см. [в статье о SQL Server бизнес-аналитики для SharePoint 2013](https://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) ( https://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) .

##  <a name="overview-of-installation"></a><a name="bkmk_install_sharepoint2013_overview"></a>Общие сведения об установке
 Если вы желаете использовать и службу [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], запустите мастер установки SQL Server дважды. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] являются отдельными вариантами на странице **роль установки** мастера установки SQL Server.

 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] поддерживает SharePoint 2010 и SharePoint 2013, но в зависимости от версии SharePoint используются различные архитектуры и процесс установки.

 Ниже приводится сводка шагов установки для развертывания компонентов бизнес-аналитики [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на одиночном сервере.

 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013**

 Для **SharePoint 2013**установку [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] можно запустить на сервере без установленного продукта SharePoint. Архитектура [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , используемая для SharePoint 2013, выполняется **за пределами** фермы SharePoint и может быть установлена как на сервере, который содержит установку SharePoint, так и на сервере, на котором не содержится установка SharePoint.

1.  Установите SharePoint Server 2013 и включите службы Excel.

2.  Установите службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции фермы SharePoint и предоставьте учетным записям службы и ферме права администратора в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].

     Для обеих версий SharePoint установка [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] начинается с выбора установки роли **SQL Server PowerPivot для SharePoint** в мастере установки SQL Server или с использованием установки посредством командной строки SQL Server.

     ![Роль установки](../../../2014/sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Роль установки")

3.  Для SharePoint 2013 можно расширить функции и возможности работы в [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Загрузите и запустите **spPowerPivot.msi** , чтобы добавить возможности обработки обновления данных на сервере, совместной работы и поддержки управления для книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Дополнительные сведения см. в разделе [Microsoft SQL Server 2014 PowerPivot для Microsoft® SharePoint](https://go.microsoft.com/fwlink/?LinkID=324854).

     Запустите пакет установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 **spPowerPivot.msi** для каждого сервера в ферме SharePoint, чтобы убедиться, что установлена правильная версия поставщиков данных.

4.  Чтобы настроить [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2013, используйте средство **настройки PowerPivot для SharePoint 2013** .

     Мастер установки SQL Server устанавливает два средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Одно из средств настройки поддерживает SharePoint 2013, а другое — SharePoint 2010.

     ![два средства настройки powerpivot](../../analysis-services/media/as-powerpivot-configtools-bothicons.gif "два средства настройки powerpivot")

5.  Настройте службы Excel в SharePoint Server 2013 для использования экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в подразделе «Настройка базовой Analysis Services интеграции с SharePoint» раздела [установка PowerPivot для SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)и [Управление параметрами модели данных служб Excel (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx) ( https://technet.microsoft.com/library/jj219780.aspx) .

6.  Дополнительные сведения см. в разделе [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).

 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010**

 Для SharePoint 2010 необходимо выполнять установку [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint на сервере, на котором уже установлен или будет установлен SharePoint 2010. Архитектура [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2010 выполняется **внутри** фермы, поэтому на сервере, где установлены [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, должен быть установлен и сам SharePoint.

1.  Установите службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции фермы SharePoint и предоставьте учетным записям службы и ферме права администратора в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].

     Развертывание SharePoint 2010 не поддерживает файл spPowerPivot.msi, и MSI-файл **не требуется** для SharePoint 2010.

     Для обеих версий SharePoint установка [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] начинается с выбора установки роли **SQL Server PowerPivot для SharePoint** в мастере установки SQL Server или с использованием установки посредством командной строки SQL Server.

2.  Мастер установки SQL Server устанавливает два средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Одно из средств настройки поддерживает SharePoint 2013, а другое — SharePoint 2010.

     Для настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2010 используйте **Средство настройки PowerPivot** .

3.  Дополнительные сведения см. в разделе [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md).

 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** для SharePoint 2010 и 2013

1.  Процесс установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint не изменился по сравнению с предыдущей версией.

     Действия по установке [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint 2010 и SharePoint 2013 очень схожи. Важные замечания о версиях SharePoint:

    -   См. поддерживаемые сочетания из следующих:

        -   Версия служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

        -   Надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint.

        -   Версия продукта SharePoint.

         [Поддерживаемые сочетания SharePoint и Reporting Services Server и надстроек &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)

    -   Для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в SharePoint 2010 требуется SharePoint 2010 с пакетом обновления 2 (SP2).

    1.  Установите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. [Reporting Services установки в режиме интеграции с sharepoint &#40;sharepoint 2010 и sharepoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md) и [установите Reporting Services режим sharepoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).

    2.  Установите надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint (rsSharePoint.msi). См. статью [Установка или удаление надстройки Reporting Services для sharepoint &#40;sharepoint 2010 и sharepoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Текущую версию [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройки для SharePoint см. в разделе [где найти надстройку Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).

    3.  Настройте службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint и по крайней мере одно приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в подразделе «Создание приложения службы Reporting Services» раздела [Install Reporting Services SharePoint в режиме интеграции с sharepoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).

##  <a name="overview-of-database-attach-upgrade-and-sharepoint-2013"></a><a name="bkm_database_attach"></a>Обзор обновления присоединения базы данных и SharePoint 2013
 SharePoint 2013 не поддерживает обновление на месте. Однако **обновление присоединением базы данных поддерживается**.

 Если имеется экземпляр PowerPivot, интегрированный с SharePoint 2010, невозможно выполнить обновление на месте сервера SharePoint.  Однако можно выполнить следующие действия в процессе обновления присоединением базы данных SharePoint.

1.  Установка новой фермы SharePoint Server 2013

2.  Выполните обновление присоединением базы данных SharePoint и перенесите связанные с PowerPivot базы данных содержимого в ферму SharePoint 2013.

3.  Установите экземпляр службы Analysis Services SQL Server в режиме интеграции SharePoint и предоставьте учетным записям фермы и служб SharePoint права администратора сервера в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].

4.  Установите пакет установки PowerPivot для SharePoint 2013 **spPowerPivot.msi** на каждом сервере в ферме SharePoint.

5.  В центре администрирования SharePoint 2013 настройте службы Excel для использования сервера служб Analysis Services в режиме интеграции с SharePoint, созданном на шаге 3.

     Для переноса расписаний обновления настройте приложение службы PowerPivot.

> [!NOTE]
>  Дополнительные сведения об обновлении присоединением базы данных PowerPivot и SharePoint см. в следующих разделах:

-   [Перенос PowerPivot на SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013)

-   [Общие сведения о процессе обновления до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688).

-   [Подготовка с очисткой перед обновлением до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689).

-   [Обновление баз данных с SharePoint 2010 до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690).

## <a name="see-also"></a>См. также:
 [Где найти надстройку Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md) [, поддерживаемые сочетаниями SharePoint и Reporting Services Server и надстройки &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md) [установить или удалить надстройку Reporting Services для SharePoint &#40;sharepoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)


