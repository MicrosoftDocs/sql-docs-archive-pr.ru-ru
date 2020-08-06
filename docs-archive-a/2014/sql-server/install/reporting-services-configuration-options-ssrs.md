---
title: Параметры конфигурации Reporting Services (службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.ins.instwizard.reportserverinstoptions.f1
helpviewer_keywords:
- Report Server Installation Options page [SQL Server Installation Wizard]
- report servers [Reporting Services], installing
- SQL Server Installation Wizard, Report Server Installation Options page
ms.assetid: e4561f6c-bc7f-467e-821a-cde8e5cd7391
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8d76701cab2c8cd8141241651d3e771ba4114504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659173"
---
# <a name="reporting-services-configuration-options-ssrs"></a>параметры конфигурации служб Reporting Services (SSRS)
  Для задания параметров, определяющих способ установки и настройки сервера отчетов, служит страница **Настройка служб Reporting Services** мастера установки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Доступность того или иного параметра установки зависит от того, какие параметры были выбраны на странице **Выбор компонентов** , а также от того, устанавливается ли одновременно с сервером отчетов также и локальный экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] .  
  
 В некоторых случаях, если сертификат протокола SSL установлен на компьютер и привязан к строгому шаблону, программа установки создает URL-адреса служб Reporting Services с префиксом HTTPS. Дополнительные сведения о сопоставлении сертификатов с URL-адресами Reporting Services см. в статье [Настройка сервера отчетов для подключений SSL (SSL)](https://go.microsoft.com/fwlink/?LinkId=199089) ( https://go.microsoft.com/fwlink/?LinkId=199089) в Электронная документация на SQL Server.  
  
 Самые последние сведения о [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и установке и настройке этого выпуска см. в разделе [Дополнительные сведения об установке](https://go.microsoft.com/fwlink/?LinkId=207425) ( https://go.microsoft.com/fwlink/?LinkId=207425) .  
  
## <a name="options"></a>Варианты  
  
### <a name="reporting-services-native-mode"></a>Службы Reporting Services в собственном режиме  
 Если программа установки не может выполнить настройку сервера отчетов по умолчанию из-за того, что не выполняется одно или несколько требований, то мастер установки позволяет выполнить минимальную установку, скопировав все необходимые файлы, однако после завершения установки нужно будет выполнить сервер отчетов в собственном режиме с помощью диспетчера конфигурации служб Reporting Services.  
  
> [!NOTE]  
>  Существующий файл базы данных сервера отчетов может вызвать ошибку, если выбран один из параметров установки по умолчанию. В этом случае программа установки пытается создать базу данных сервера отчетов с именем по умолчанию. Если база данных с таким именем уже существует, установка завершится ошибкой и придется производить откат установки. Во избежание этой проблемы можно переименовать существующую базу данных перед запуском программы установки либо выбрать параметр **Установить только** , что позволяет указать пользовательские параметры базы данных после завершения установки.  
  
#### <a name="install-and-configure"></a>Установка и настройка.  
 Устанавливает экземпляр сервера отчетов в собственном режиме с использованием значений по умолчанию для базы данных сервера отчетов, учетной записи службы и резервирований URL-адресов. При выборе этого параметра после завершения установки экземпляр сервера отчетов готов к использованию. Программа установки создает базу данных сервера отчетов, использующую локальный экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , и настраивает сервер отчетов для работы со значениями по умолчанию.  
  
 Этот параметр доступен, только если значения по умолчанию, использованные при установке сервера отчетов, допустимы для системы. Этот вариант мы рекомендуем разработчикам, которые хотят установить все компоненты локально, и пользователям, оценивающим программное обеспечение.  
  
 Чтобы просмотреть сведения об используемых программой установки настройках по умолчанию или выяснить, почему невозможно установить конфигурацию по умолчанию, нажмите кнопку **Подробности**. Дополнительные сведения о конфигурации по умолчанию для сервера отчетов в собственном режиме см. в разделе [Конфигурация по умолчанию для установки в собственном режиме (Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199091) ( https://go.microsoft.com/fwlink/?LinkId=199091) .  
  
#### <a name="install-only"></a>Установить только  
 Устанавливает программные файлы сервера отчетов, создает учетную запись службы сервера отчетов и регистрирует поставщик данных инструментария управления Windows (WMI) сервера отчетов. Этот параметр установки называется «Только файлы». Выберите этот параметр, если использование конфигурации по умолчанию нежелательно. Это единственный доступный параметр, если невозможно установить конфигурацию по умолчанию или устанавливается кластер отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включающий службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения об установке только файлов см. в разделе [Установка только файлов (Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199093) ( https://go.microsoft.com/fwlink/?LinkId=199093) .  
  
 После завершения программы установки, прежде чем сервер отчетов можно будет использовать, следует создать базу данных сервера отчетов и настроить сервер отчетов. Чтобы настроить сервер отчетов и создать базу данных, воспользуйтесь диспетчером конфигурации служб Reporting Services. Дополнительные сведения см. [в разделе как создать базу данных сервера отчетов (Reporting Services конфигурацию)](https://go.microsoft.com/fwlink/?LinkId=199094) ( https://go.microsoft.com/fwlink/?LinkId=199094) и [настроить подключение к базе данных сервера отчетов](https://go.microsoft.com/fwlink/?LinkId=199095) () https://go.microsoft.com/fwlink/?LinkId=199095) .  
  
### <a name="reporting-services-sharepoint-mode"></a>Службы Reporting Services в режиме SharePoint  
  
#### <a name="install-only"></a>Установить только  
 Устанавливает программные файлы сервера отчетов и командлеты PowerShell. После завершения установки необходимо запустить службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint и создать приложение служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в следующих разделах:  
  
-   [Установка Reporting Services сервера отчетов в режиме интеграции с SharePoint для Power View и предупреждений об изменении данных](https://go.microsoft.com/fwlink/?LinkId=207543) ( https://go.microsoft.com/fwlink/?LinkId=207543) .  
  
-   [Установите Reporting Services режиме SharePoint в качестве фермы одиночных серверов](https://go.microsoft.com/fwlink/?LinkId=207544) ( https://go.microsoft.com/fwlink/?LinkId=207544) .  
  
-   [Сервер отчетов Reporting Services (службы SSRS)](https://go.microsoft.com/fwlink/?LinkID=207244) ( https://go.microsoft.com/fwlink/?LinkID=207244) .  
  
## <a name="installing-the-reporting-services-add-in-for-sharepoint-technologies"></a>Установка надстройки служб Reporting Services для технологий SharePoint  
 Начиная с версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , надстройку можно установить в составе установки SQL Server на странице выбора компонентов мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Однако можно установить надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint 2010 одним из следующих способов.  
  
-   Запустите средство подготовки продуктов SharePoint 2010 **PreRequisiteInstaller.exe**.  
  
-   Установите с установочного носителя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После завершения работы программы установки **запустите файл** rsSharePoint.msi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из папки «Setup», расположенной на установочном носителе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Загрузите и установите надстройку. Дополнительные сведения см. в разделе [где найти надстройку Reporting Services для продуктов SharePoint](https://go.microsoft.com/fwlink/?LinkID=208634) ( https://go.microsoft.com/fwlink/?LinkID=208634) .  
  
## <a name="see-also"></a>См. также:  
 [Запуск диспетчер конфигурации служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=199096)   
 [Создание базы данных сервера отчетов (конфигурация Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199094)   
 [Обновление и перенос служб Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)   
 [Установка режима интеграции с SharePoint и собственного режима для служб Reporting Services из командной строки](https://go.microsoft.com/fwlink/?LinkId=217620)  
  
  
