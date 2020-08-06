---
title: Обновление и перенос служб Reporting Services | Документы Майкрософт
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSRS, upgrading
- Reporting Services, upgrades
- SQL Server Reporting Services, upgrading
- upgrading Reporting Services
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 75385074b445c2741c548e488fb123b12be036d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654905"
---
# <a name="upgrade-and-migrate-reporting-services"></a>Upgrade and Migrate Reporting Services

Этот раздел содержит общие сведения о вариантах обновления и миграции для служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Существуют два принципиальных подхода к обновлению развертывания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

-   **Обновление.** Обновляются компоненты [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на тех серверах и экземплярах, где они установлены в данный момент. Обычно это называется обновлением на месте. Обновление на месте с одного режима сервера [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на другой режим не поддерживается. Например, невозможно обновить сервер отчетов в собственном режиме до сервера отчетов в режиме интеграции с SharePoint. Элементы отчета можно переносить из одного режима в другой. Дополнительные сведения см. в подразделе "Встроенная миграция в SharePoint" Далее в этом документе, а также в соответствующем разделе [образец Reporting Services rs.exe сценария для переноса содержимого между серверами отчетов](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).

-   **Миграция.** Устанавливается и настраивается новая среда SharePoint, в нее копируются элементы отчетов и ресурсы, а затем выполняется настройка новой среды для использования существующего содержимого. Более низкая форма миграции — копирование баз данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , файлов конфигурации и при использовании режима интеграции с SharePoint баз данных содержимого SharePoint.

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint.|

##  <a name="in-this-topic"></a><a name="bkmk_top"></a> В этом разделе:

-   [Известные проблемы и рекомендации по обновлению](#bkmk_known_issues)

-   [Параллельные установки](#bkmk_side_by_side)

-   [Обновление на месте](#bkmk_inplace_upgrade)

-   [Контрольный список перед обновлением](#bkmk_upgrade_checklist)

-   [Сценарии обновления и миграции в собственном режиме](#bkmk_native_scenarios)

-   [Обновление Reporting Services масштабного развертывания в собственном режиме](#bkmk_native_scaleout)

-   [Сценарии обновления и миграции в режиме интеграции с SharePoint](#bkmk_sharePoint_scenarios)

-   [Рекомендации по миграции](#bkmk_migration_considerations)

-   [Дополнительные ресурсы](#bkmk_additional_resources)

##  <a name="known-upgrade-issues-and-best-practices"></a><a name="bkmk_known_issues"></a> Известные проблемы и рекомендации, связанные с обновлением
 Подробный список поддерживаемых версий и выпусков, которые можно обновить, см. в разделе [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).

> [!TIP]
>  Последние сведения о проблемах, связанных с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], см. в следующих разделах:
> 
>  -   [Заметки о Выпуске SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).
> -   [Рекомендации, советы и сведения по устранению неполадок служб SQL Server 2014 Reporting Services](https://go.microsoft.com/fwlink/?LinkID=391254).
> -   Используйте советник по переходу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статьях [Reporting Services обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md) и [инструкции по установке помощника по обновлению](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md).

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

##  <a name="side-by-side-installations"></a><a name="bkmk_side_by_side"></a> Параллельная установка
 Собственный режим[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] может быть установлен параллельно с развертыванием служб [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] в собственном режиме.

 Отсутствует поддержка параллельных развертываний служб [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] в режиме интеграции с SharePoint и всех предыдущих версий компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

##  <a name="in-place-upgrade"></a><a name="bkmk_inplace_upgrade"></a>Обновление на месте
 Обновление завершается программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать для обновления любого компонента или всех компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включая службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Программа установки обнаружит существующие экземпляры и предложит выполнить обновление. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки позволяет использовать параметры обновления, которые можно указывать в качестве параметров командной строки или в мастере установки.

 После запуска программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно либо обновить одну из следующих версий, либо установить новый экземпляр служб [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] , который будет выполняться параллельно с существующими установками.

-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]

-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]

-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]

-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]

 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в следующих разделах:

||
|-|
|[Обновление до SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)|
|[Обновление до SQL Server 2014 с помощью мастера установки &#40;установки&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)|
|[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)|

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

##  <a name="pre-upgrade-checklist"></a><a name="bkmk_upgrade_checklist"></a> Контрольный список действий перед обновлением
 Перед обновлением до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]просмотрите следующие источники:

-   Ознакомьтесь с требованиями, чтобы определить, поддерживает ли оборудование и программное обеспечение службы [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]. Дополнительные сведения см. в разделе [Hardware and Software Requirements for Installing SQL Server 2014](../../../2014/sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).

-   Средство проверки конфигурации системы (SCC) используется для просмотра на компьютере сервера отчетов условий, которые могут препятствовать успешной установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md).

-   Просмотрите рекомендации и руководство по безопасности для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Security Considerations for a SQL Server Installation](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).

-   Чтобы определить проблемы, которые могу препятствовать успешному обновлению, запустите советник по переходу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере сервера отчетов. Дополнительные сведения см. в разделе [Use Upgrade Advisor to Prepare for Upgrades](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).

-   Создайте резервную копию симметричного ключа. Дополнительные сведения см. в разделе [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).

-   Создайте резервные копии баз данных сервера отчетов и файлов конфигурации. Дополнительные сведения см. в разделе [Backup and Restore Operations for Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md).

-   Создайте резервные копии всех настроек виртуальных каталогов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , существующих в IIS.

-   Удалите недопустимые SSL-сертификаты.  К ним относятся сертификаты с истекшим сроком действия, которые не планируется обновлять до обновления служб Reporting Services.  Наличие недопустимых сертификатов приведет к неудаче обновления, а в файл журнала служб Reporting Services будет записано сообщение об ошибке, аналогичное следующему: **Microsoft.ReportingServices.WmiProvider.WMIProviderException: A Secure Sockets Layer (SSL) certificate is not configured on the Web site.** (На веб-сайте не настроен SSL-сертификат).

 Перед обновлением рабочей среды всегда запускайте проверку обновления в предварительной рабочей среде, имеющей аналогичную конфигурацию.

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

## <a name="overview-of-migration-scenarios"></a>Общие сведения о сценариях миграции
 При обновлении поддерживаемой версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в общем случае у вас будет возможность запустить мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обновить программные файлы, базу данных и все данные программы сервера отчетов.

 Но при этом требуется **миграция** установки сервера отчетов вручную, если обнаруживаются любые из следующих условий.

-   Советник по переходу обнаружил одну или несколько ошибок обновления. Дополнительные сведения см. в разделе [Use Upgrade Advisor to Prepare for Upgrades](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).

-   Вы хотите изменить тип сервера отчетов, используемого в вашем развертывании. Например, невозможно обновить или преобразовать сервер отчетов в собственном режиме в сервер, работающий в режиме интеграции с SharePoint. Дополнительные сведения см. в статье [Миграция из собственного режима в режим интеграции с SharePoint (службы SSRS)](../../reporting-services/install-windows/native-to-sharepoint-migration-ssrs.md).

-   Нужно уменьшить время, на которое сервер отчетов переводится в режим «вне сети» во время процесса обновления. Текущая установка остается в режиме «в сети» при копировании данных содержимого на новый экземпляр сервера отчетов и проверки установки без изменения состояния существующей установки сервера отчетов.

-   Необходимо выполнить миграцию развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 2010 на SharePoint 2013. SharePoint 2013 не поддерживает обновление на месте из SharePoint 2010. Дополнительные сведения см. в статье [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

##  <a name="native-mode-upgrade-and-migration-scenarios"></a><a name="bkmk_native_scenarios"></a> Обновление в собственном режиме и сценарии миграции
 **Обновление.** Обновление на месте в собственном режиме выполняется одинаково для каждой из поддерживаемых версий, перечисленных ранее в этом разделе. Запустите мастер установки SQL Server или процесс установки из командной строки. После установки база данных сервера отчетов автоматически обновляется до новой схемы базы данных сервера отчетов. Дополнительные сведения см. в разделе [обновление на месте](#bkmk_inplace_upgrade) этой статьи.

 Процесс обновления начинается с выбора существующего экземпляра сервера отчетов, подлежащего обновлению.

1.  Если база данных сервера отчетов размещается на удаленном компьютере и у вас нет разрешения на обновление этой базы данных, программа установки предложит вам представить учетные данные для обновления базы данных удаленного сервера отчетов. Обязательно представьте учетные данные, имеющие разрешение `sysadmin` или разрешение на обновление базы данных.

2.  Программа установки выявляет обстоятельства или настройки, не позволяющие осуществлять обновление, и считывает параметры конфигурации. Ниже представлены примеры, включающие пользовательские модули, развернутые на сервере отчетов. Если обновление заблокировано, необходимо либо изменить установку, чтобы разблокировать обновление, либо выполнить миграцию на новый экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Дополнительные сведения см. в документации помощника по обновлению.

3.  Если процесс обновления может быть продолжен, программа установки предлагает продолжить его выполнение.

4.  Программа установки создает новые папки для программных файлов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . К папкам программы для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] установки относятся MSRS12. \<*instance name*>

5.  Программа установки добавляет программные файлы сервера отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , средства настройки, а также программы командной строки, которые входят в состав компонента сервера отчетов.

    1.  Программные файлы предшествующих версий удаляются.

    2.  К средствам настройки сервера отчетов и программам, обновляемым до уровня новой версии, относятся средство настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме, утилиты командной строки, такие как RS.exe, а также построитель отчетов.

    3.  Другие клиентские средства, такие как среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и электронная документация, не обновляются. Получить новые версии этих средств можно путем их добавления при выполнении программы установки. Более ранние версии будут существовать наряду с версиями [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . В случае установки образцов более ранние версии сохраняются. Программа установки не поддерживает обновление образцов SQL Server.

    4.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] загружается отдельно. Дополнительные сведения см. в разделе [Средства Microsoft SQL Server Data Tools 2014 — бизнес-аналитика для Microsoft Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843).

6.  Программа установки повторно использует запись службы в диспетчере управления службами для службы сервера отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Эта запись службы включает учетную запись службы Windows сервера отчетов.

7.  Программа установки резервирует новые URL-адреса в соответствии с существующими настройками виртуального каталога в службах IIS. Программа установки может не удалить виртуальные каталоги в IIS, поэтому не забывайте удалять их вручную по завершении процесса обновления.

8.  Программа установки обновляет базы данных сервера отчетов до уровня новой схемы и модифицирует роль `RSExecRole` посредством добавления к ней разрешений владельца базы данных. Этот шаг выполняется только при обновлении с до с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] пакетом обновления 1 (SP1).

9. Программа установки осуществляет слияние параметров в файлах конфигурации. При использовании в качестве основы файлов конфигурации из текущей установки добавляются новые записи. Устаревшие записи не удаляются, но по завершении процесса обновления они не считываются сервером отчетов. Старые файлы регистрации, устаревший файл RSWebApplication.config и установки виртуального каталога в IIS при обновлении не удаляются. Конструктор отчетов SQL Server 2005, среда Management Studio и другие клиентские средства при обновлении не удаляются. Если они больше не нужны, позаботьтесь об удалении этих файлов и средств по завершении обновления.

 **Миграция.** Миграция предыдущей версии установки в собственном режиме в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] представляет собой одну последовательность шагов для всех поддерживаемых версий, перечисленных ранее в этом разделе. Дополнительные сведения см. в статье [Перенос установки служб Reporting Services (собственный режим)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

##  <a name="upgrade-a-reporting-services-native-mode-scale-out-deployment"></a><a name="bkmk_native_scaleout"></a> Обновление масштабного развертывания служб Reporting Services, работающих в собственном режиме
 Ниже приводится сводка действий по обновлению развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме, которое масштабировано на использование более одного сервера отчетов. Этот процесс требует остановки развертывания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :

1.  Создайте резервные копии ключей шифрования и баз данных сервера отчетов. Дополнительные сведения см. в статьях [Операции резервного копирования и восстановления для служб Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md) и [Добавление и удаление ключей шифрования для масштабного развертывания (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md).

2.  Используйте диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и удалите все серверы отчетов из масштабированного развертывания. Дополнительные сведения см. в разделе [Настройка масштабного развертывания сервера отчетов в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).

3.  Обновите один из серверов отчетов до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

4.  Используйте диспетчер конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для добавления серверов отчетов обратно в развертывание. Дополнительные сведения см. в разделе [Настройка масштабного развертывания сервера отчетов в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).

     Для каждого сервера повторите шаги по обновлению и масштабированию.

##  <a name="sharepoint-mode-upgrade-and-migration-scenarios"></a><a name="bkmk_sharePoint_scenarios"></a> Обновление в режиме интеграции с SharePoint и сценарии миграции
 В следующих разделах описаны проблемы и основные шаги, необходимые для обновления или перехода с указанных версий [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режима интеграции с SharePoint на режим интеграции с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint.

 Есть два компонента установки для обновления развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Shared Service.

    > [!TIP]
    >  Используйте командлет [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint `Get-SPRSServiceApplicationServers` , чтобы определить серверы в ферме SharePoint, на которых в данный момент выполняется общая служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint и которые потому подлежат обновлению.

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Надстройка для продуктов SharePoint. Дополнительные сведения см. [в разделе Установка или удаление надстройки Reporting Services для sharepoint &#40;sharepoint 2010 и sharepoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).

 Подробные инструкции по переносу установки в режиме SharePoint см. в статье [Перенос установки служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).

> [!IMPORTANT]
>  При выполнении некоторых из следующих сценариев для среды SharePoint неизбежно время простоя. Это вызвано необходимостью обновления различных технологий. Если простой неприемлем, необходимо вместо обновления на месте выполнить миграцию.

### <a name="sssql11-to-sssql14"></a>[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] — [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]
 **Начальная среда:** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint 2010.

 **Конечная среда:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SharePoint 2010 или SharePoint 2013.

-   **SharePoint 2010.** Поддерживается обновление [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на месте, но скрипт обновления требует остановки среды SharePoint.

     Если также требуется, чтобы результирующая среда выполнения выполняла SharePoint 2013, необходимо завершить обновление присоединения базы данных SharePoint 2010 к SharePoint 2013.

-   **SharePoint 2013.** SharePoint 2013 не поддерживает обновление на месте из SharePoint 2010. Однако процедура **обновления присоединением базы данных поддерживается**  . Это поведение отличается от обновления до версии SharePoint 2010, при котором клиент может выбрать между двумя базовыми подходами к обновлению: обновление на месте и обновление присоединением базы данных.

     Если имеется установленная версия [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , интегрированная с SharePoint 2010, нельзя обновить сервер SharePoint на месте. Однако можно выполнить миграцию баз данных содержимого и баз данных приложения службы из фермы SharePoint 2010 в ферму SharePoint 2013.

### <a name="sskilimanjaro-to-sssql14"></a>[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] — [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]
 **Начальная среда:** SQL Server 2008 R2, SharePoint 2010.

 **Конечная среда:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SharePoint 2010.

-   Поддерживается обновление на месте, и отсутствует простой для среды SharePoint.

-   Установите версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint на все клиентские веб-интерфейсы в ферме. Установить надстройку можно с помощью мастера установки служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или с помощью загрузки надстройки.

-   Запустите [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] установку, чтобы обновить режим интеграции с SharePoint для каждого сервера отчетов. Мастер установки SQL Server установит [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] службу и создаст новое приложение службы.

     Если также требуется, чтобы результирующая среда выполнения выполняла SharePoint 2013, необходимо завершить обновление присоединения базы данных SharePoint 2010 к SharePoint 2013.

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

### <a name="sskatmai-sp2-to-sssql14"></a>[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2) до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]
 **Начальная среда:** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2, SharePoint 2007.

 **Конечная среда:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SharePoint 2010.

-   При выполнении этого сценария обновления для среды SharePoint неизбежно время простоя. Это вызвано необходимостью обновления технологий SharePoint и SQL Server. Можно рассмотреть возможность выполнения миграции, а не обновление на месте.

-   Сначала обновите [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до версии с пакетом обновления 2 (SP2), если этого еще не было сделано.

-   Обновите SharePoint до версии 2010. При запуске установщика необходимых компонентов SharePoint 2010 выполняется обновление надстройки служб Reporting Services для продуктов SharePoint 2010.

-   Установите версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint на все клиентские веб-интерфейсы в ферме. Установщик необходимых компонентов SharePoint устанавливает версию надстройки SQL Server 2008 R2, но для работы с сервером отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] требуется версия служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .

-   > [!WARNING]
    >  После обновления SharePoint среду служб Reporting Services можно будет использовать только после обновления SQL Server.

-   Обновите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. После запуска мастера установки SQL Server открывается диалоговое окно**Проверка подлинности служб SQL Server Reporting Services в режиме интеграции с SharePoint**. Устанавливается служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а для создания нового пула приложений SharePoint используются учетные данные, указанные на странице проверки подлинности.

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

### <a name="sql-server-2005-sp2-to-sssql14"></a>Пакет обновления 2 (SP2) для SQL Server 2005 в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]
 **Начальная среда:** SQL Server 2005 с пакетом обновления 2 (SP2), SharePoint 2007.

 **Конечная среда:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SharePoint 2010.

-   При выполнении этого сценария обновления для среды SharePoint неизбежно время простоя. Это вызвано необходимостью обновления технологий SharePoint и SQL Server. Можно рассмотреть возможность выполнения миграции, а не обновление на месте.

-   Сначала обновите SQL Server 2005 до версии с пакетом обновления 2 (SP2), если этого еще не было сделано.

-   Обновите SharePoint до SharePoint 2010. При запуске установщика необходимых компонентов SharePoint 2010 выполняется обновление надстройки служб Reporting Services для продуктов SharePoint 2010.

-   > [!WARNING]
    >  После обновления SharePoint среду служб Reporting Services можно будет использовать только после обновления SQL Server.

-   Установите версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint на все клиентские веб-интерфейсы в ферме. Установщик необходимых компонентов SharePoint устанавливает версию надстройки SQL Server 2008 R2, но для работы с сервером отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] требуется версия служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .

-   Обновите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. После запуска мастера установки SQL Server открывается диалоговое окно «Проверка подлинности служб SQL Server Reporting Services в режиме интеграции с SharePoint». Устанавливается служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а для создания нового пула приложений SharePoint используются учетные данные, указанные на странице проверки подлинности.

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

##  <a name="considerations-for-a-migration"></a><a name="bkmk_migration_considerations"></a> Вопросы миграции
 При перемещении данных приложения необходимо помнить о следующих проблемах и ограничениях.

-   Для защиты ключа шифрования применяется хэш, содержащий идентификатор компьютера.

-   Имена баз данных сервера отчетов фиксированы и не могут быть изменены на новом компьютере.

### <a name="encryption-key-considerations"></a>Дополнительные сведения о ключе шифрования
 Всегда создавайте резервные копии ключей шифрования перед перемещением базы данных сервера отчетов на новый компьютер.

 При перемещении установки сервера отчетов на другой компьютер становится недействительным хэш, который защищает ключи шифрования, используемые для защиты конфиденциальных данных в базе данных сервера отчетов. Каждый экземпляр сервера отчетов, который использует базу данных, имеет собственную копию ключа шифрования, которая шифруется с удостоверением учетной записи службы, как она определена на текущем компьютере. Если сменить компьютеры, служба не будет иметь доступа к своему ключу, даже если использовать такое же имя учетной записи на новом компьютере.

 Чтобы восстановить обратимое шифрование на новом компьютере сервера отчетов, необходимо восстановить ключ, резервная копия которого была сделана ранее. Полный набор ключей, хранимых в базе данных сервера отчетов, состоит из значения симметричного ключа и идентификатора службы, используемых для ограничения доступа к ключу, чтобы он мог использоваться только экземпляром сервера отчетов, на котором был сохранен. В процессе восстановления ключа сервер отчетов заменяет существующие копии ключа новыми версиями. Новая версия содержит значения идентификаторов компьютера и службы, как они определены на текущем компьютере. Дополнительные сведения см. в следующих разделах:

-   Режим интеграции с SharePoint: см. раздел "Управление ключами" статьи [Управление служебным приложением SharePoint службы Reporting Services](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).

-   Собственный режим: см. статью [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

### <a name="fixed-database-name"></a>Фиксированное имя базы данных
 Нельзя переименовать базу данных сервера отчетов. Идентификатор базы данных записывается в хранимых процедурах сервера отчетов при создании базы данных. Переименование первичной или временной баз данных сервера отчетов приведет к ошибкам при запуске процедур, что нарушит функционирование установки сервера отчетов.

 Если имя базы данных из существующей установки непригодно для новой установки, то необходимо рассмотреть возможность создания новой базы данных с предпочтительным именем, а затем загрузить существующие данные приложения с использованием методов из следующего списка.

-   Запишите [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] скрипт, который вызывает методы SOAP веб-службы сервера отчетов, чтобы копировать данные между базами данных. Можно использовать служебную программу RS.exe для выполнения скрипта. Дополнительные сведения об этом подходе см. в статье [Сценарии и PowerShell со службами Reporting Services](../tools/scripting-and-powershell-with-reporting-services.md).

-   Запишите код, который вызывает поставщика инструментария WMI, чтобы копировать данные между базами данных. Дополнительные сведения об этом подходе см. в статье [Доступ к поставщику WMI для служб Reporting Services](../tools/access-the-reporting-services-wmi-provider.md).

-   Если число элементов невелико, можно переиздать отчеты, модели отчетов и общие источники данных из конструктора отчетов, конструктора моделей и построителя отчетов на новом сервере отчетов. Необходимо создать повторно назначения ролей, подписки, общие расписания, расписания моментальных снимков отчета, пользовательские свойства, установленные для отчетов или других элементов, безопасность элементов модели и свойства, назначенные на сервере отчетов. Будут потеряны журнал отчетов и данные журнала выполнения отчета.

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

##  <a name="additional-resources"></a><a name="bkmk_additional_resources"></a> Дополнительные ресурсы

> [!NOTE]
>  Дополнительные сведения об обновлении присоединением базы данных SharePoint см. в разделах:

-   [Общие сведения о процессе обновления до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688) ( https://go.microsoft.com/fwlink/p/?LinkId=256688) .

-   [Выполните предварительную подготовку перед обновлением до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689) ( https://go.microsoft.com/fwlink/p/?LinkId=256689) .

-   [Обновите базы данных с sharepoint 2010 на sharepoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) ( https://go.microsoft.com/fwlink/p/?LinkId=256690) .

 ![Значок стрелки, используемый в ссылке "назад на начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый со ссылкой В начало") [" в этом разделе:](#bkmk_top)

## <a name="see-also"></a>См. также:
 Обновление [отчетов](../../reporting-services/install-windows/upgrade-reports.md) [обновление до SQL Server 2014 с помощью мастера установки &#40;установки&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)


