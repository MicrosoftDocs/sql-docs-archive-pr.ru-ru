---
title: Настройка сервера — учетные записи служб | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- service account configuration, SQL Server
ms.assetid: c283702d-ab20-4bfa-9272-f0c53c31cb9f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f82c1d50045f7dc60c131d81c6eb5750f2213c59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666347"
---
# <a name="server-configuration---service-accounts"></a>Настройка сервера — учетные записи служб
  На странице «Настройка сервера» мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно задать учетные записи входа для служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Службы, которые можно настраивать на этой странице, зависят от того, какие компоненты были выбраны во время установки.  
  
Стартовые учетные записи, используемые для запуска и запуска, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут представлять собой учетные записи пользователей домена, локальные учетные записи пользователей, управляемые учетные записи служб, виртуальные учетные записи или встроенные системные учетные записи.  
  
## <a name="options"></a>Варианты  
 Можно назначить одну учетную запись входа всем службам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или настроить учетные записи служб индивидуально. Можно также указать, будут службы запускаться автоматически или вручную либо будут отключены. В большинстве установок рекомендуется использовать учетную запись по умолчанию.  
  
 В Windows 7 и [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] R2 большинство учетных записей по умолчанию представлены виртуальной учетной записью.  
  
 При настройке служб с использованием учетных записей домена [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует настраивать учетные записи служб индивидуально, предоставляя каждой из служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] минимальные права доступа, необходимые для выполнения ее задач. Дополнительные сведения, в том числе описания типов учетных записей, см. в разделе [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
 **Настройка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетных записей служб по отдельности (рекомендуется)**  
 Для каждой из служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задайте в сетке имя и пароль пользователя для входа, а также тип запуска службы. Для служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно указать системные или локальные учетные записи, локальные группы, группы доменов или учетные записи пользователей доменов.  
  
 Выберите службу, настройки которой требуется изменить.  
  
|Служба|Настройки проверки подлинности|  
|-------------------------|----------------------------------------------|  
|Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Служба, которая запускает задания, мониторы и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также позволяет автоматизировать задачи администрирования.<br /><br /> Для этой службы нет учетной записи входа по умолчанию.<br /><br /> Тип запуска по умолчанию — «Вручную».|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|Тип запуска по умолчанию — «Авто».|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Тип запуска по умолчанию — «Авто».<br /><br /> Для режима интеграции с SharePoint следует указать учетную запись пользователя домена Windows. Указанная учетная запись используется для службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Учетная запись, указанная для текущего экземпляра, также должна использоваться для дополнительных экземпляров служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которые, возможно, будут добавлены к ферме в будущем.|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Учетные записи служб используются для настройки соединения с базой данных сервера отчетов. Если нужно использовать параметры проверки подлинности по умолчанию, выберите встроенную сетевую службу. Если указывается учетная запись пользователя домена, убедитесь, что для него зарегистрировано имя участника-службы, если на сервере отчетов используется проверка подлинности Windows. Дополнительные сведения см. в статье, посвященной [настройке проверки подлинности Windows на сервере отчетов](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md).<br /><br /> Тип запуска по умолчанию — «Авто».|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] представляют собой набор графических средств и программируемых объектов для перемещения, копирования и преобразования данных.<br /><br /> Тип запуска по умолчанию — «Авто».|  
|Клиент распределенного воспроизведения[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Учетная запись службы, используемая для службы клиента распределенного воспроизведения.<br /><br /> Укажите учетную запись, под которой будет запускаться служба клиента распределенного воспроизведения. Эта учетная запись должна отличаться от той, которая используется для службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Тип запуска по умолчанию — «Вручную».|  
|Контроллер распределенного воспроизведения[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Учетная запись, используемая для службы контроллера распределенного воспроизведения.<br /><br /> Укажите учетную запись, под которой будет запускаться служба контроллера распределенного воспроизведения. Эта учетная запись должна отличаться от той, которая используется для службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Тип запуска по умолчанию — «Вручную».|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство запуска управляющей программы полнотекстовой фильтрации|Служба, которая создает процессы fdhost.exe. Она необходима для размещения средств разбиений по словам и фильтров, которые обрабатывают текстовые данные для полнотекстового индексирования.<br /><br /> Если для запуска службы FDHOST Launcher указывается учетная запись домена, настоятельно рекомендуется использовать учетную запись с низкими правами доступа. Эта учетная запись должна отличаться от той, которая используется для службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|Браузер[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представляет службу разрешения имен, которая обеспечивает данные о соединении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с клиентскими компьютерами. Эта служба совместно используется множеством экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Учетная запись входа по умолчанию — NT Authority\Local Service, и она не может быть изменена в ходе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Учетную запись можно изменить после завершения установки. Если во время установки не указан тип запуска, он определяется следующим образом.<br /><br /> Служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроена на автоматический запуск и работает в описанных ниже сценариях установки.<br />-<br />                            Экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br />-<br />                            Именованный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если включен протокол TCP или NP.<br />-<br />                            Некластеризованный, именованный экземпляр сервера анализа данных.<br /><br /> Если ни один из указанных выше сценариев не применим и браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] уже установлен, будет поддерживаться текущее состояние браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Задается тип запуска «Отключено» и служба останавливается, если до установки не существовало экземпляра более старой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
## <a name="see-also"></a>См. также:  
 [Вопросы безопасности при установке SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
