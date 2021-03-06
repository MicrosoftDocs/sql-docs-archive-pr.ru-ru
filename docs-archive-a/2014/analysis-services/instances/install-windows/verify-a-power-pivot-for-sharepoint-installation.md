---
title: Проверка установки PowerPivot для SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f45e1aa1d48dd5a50b7ce38dc364089d438f215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666264"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a>Проверка установки PowerPivot для SharePoint
  Администрирование экземпляра PowerPivot для SharePoint, устанавливаемого в ферме SharePoint, осуществляется с помощью центра администрирования SharePoint. Как минимум, можно проверить страницы в центре администрирования и на сайтах SharePoint, чтобы убедиться в доступности компонентов и функций сервера PowerPivot. Однако, чтобы полностью проверить установку, необходимо иметь книгу PowerPivot, которую можно опубликовать в SharePoint и открывать из библиотеки. В целях тестирования можно опубликовать образец книги, в котором уже есть данные PowerPivot, и с его помощью удостовериться в правильности настройки интеграции с SharePoint.  
  
##  <a name="verify-central-administration-integration"></a><a name="verifyinstall"></a> Проверка интеграции центра администрирования  
 Чтобы проверить интеграцию PowerPivot с центром администрирования, выполните следующие действия.  
  
1.  В меню Пуск выберите пункт **все программы**, откройте Microsoft SharePoint 2010 Products и щелкните **центр администрирования SharePoint 2010**.  
  
2.  Введите имя пользователя и пароль, а затем нажмите кнопку **ОК**.  
  
     Также можно изменить параметры браузера, чтобы имя пользователя и пароль не нужно было вводить каждый раз при открытии центра администрирования. Чтобы добавить центр администрирования в список надежных сайтов, выполните следующие действия.  
  
    1.  В Internet Explorer в меню Сервис выберите **Свойства обозревателя**.  
  
    2.  На вкладке «Безопасность» в разделе **Выберите зону для настройки ее параметров безопасности** щелкните «Надежные узлы» и нажмите кнопку «Сайты».  
  
    3.  Снимите флажок **Для всех сайтов этой зоны требуется проверка серверов (https:)** .  
  
    4.  В поле **Добавить в зону следующий веб-сайт**введите URL-адрес сайта и нажмите кнопку **Добавить**.  
  
    5.  Щелкните **Закрыть**, а затем нажмите кнопку **ОК**.  
  
        > [!NOTE]  
        >  В документации по установке SharePoint имеются дополнительные инструкции по решению проблем с ошибками прокси-серверов, а также по отключению улучшенной конфигурации безопасности Internet Explorer, чтобы можно было загружать и устанавливать обновления. Дополнительные сведения см. в подразделе **Выполнение дополнительных задач** раздела [Развертывание одиночного сервера с SQL Server](https://go.microsoft.com/fwlink/?LinkId=177754) на веб-сайте Майкрософт.  
  
3.  В разделе «Системные параметры» центра администрирования выберите **Управление компонентами фермы**.  
  
4.  Параметр **Функция интеграции PowerPivot** должен иметь значение **Активна**.  
  
5.  В центре администрирования в окне «Системные параметры» выберите пункт **Управление службами на сервере**.  
  
6.  Убедитесь, что службы **SQL Server Analysis Services** и **Системная служба SQL Server PowerPivot** запущены.  
  
7.  В разделе «Управление приложениями» центра администрирования выберите пункт **Управление приложениями служб**.  
  
8.  Щелкните **приложение службы PowerPivot по умолчанию** , чтобы открыть панель управления PowerPivot для этого приложения. На первый запуск панели мониторинга требуется несколько минут.  
  
     Кроме того, щелкните пустое пространство рядом с **приложением службы PowerPivot по умолчанию** , чтобы выбрать строку, и щелкните **свойства** , чтобы просмотреть параметры конфигурации для этого приложения службы. Изменить конфигурацию сервера можно с помощью как параметров конфигурации, так и свойств приложения. Дополнительные сведения об этих параметрах см. [в разделе Создание и настройка приложения службы PowerPivot в центре администрирования](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).  
  
## <a name="verify-integration-at-the-site-level"></a>Проверка интеграции на уровне сайта  
 Чтобы проверить интеграцию PowerPivot с сайтом SharePoint, выполните следующие действия.  
  
1.  Откройте созданное веб-приложение в браузере. Если используются значения по умолчанию, можно указать http:// \<your computer name> в URL-адресе.  
  
2.  Удостоверьтесь в наличии в приложении доступа к данным PowerPivot и функциям обработки. Определить это можно по наличию предоставляемых PowerPivot шаблонов библиотек.  
  
    1.  В меню Действия сайта щелкните **Дополнительные параметры..**.  
  
    2.  В разделе библиотеки должны отобразиться **Библиотека веб-каналов данных** и **Галерея PowerPivot**. Эти шаблоны библиотек предоставляются компонентом PowerPivot и отображаются в списке библиотек только при правильной интеграции этого компонента.  
  
## <a name="verify-data-access-on-the-server"></a>Проверка доступа к данным на сервере  
 Чтобы выполнить проверку доступа к данным PowerPivot на сервере, выполните следующие действия.  
  
1.  [Загрузите](https://go.microsoft.com/fwlink/?LinkID=219108) образец данных Picnic, поставляемый вместе с учебником по службам Reporting Services. Книгу в этом образце можно использовать для проверки доступа к данным PowerPivot. Извлеките файлы.  
  
2.  Передайте книгу Excel (XLSX) в папку «Общие документы». Книга содержит внедренные данные PowerPivot.  
  
3.  Щелкните документ, чтобы открыть его из библиотеки.  
  
4.  Щелкните срез или фильтр в верхней части книги. В этой книге имеются следующие срезы: месяц, цвет и тип. При щелчке на срезе запускается запрос PowerPivot и проверяется работоспособность сервера. Сервер загрузит данные PowerPivot в фоновом режиме и вернет результаты.  
  
5.  Вернитесь в библиотеку. Щелкните стрелку вниз справа от книги и выберите **Запустить Power View**. На этом шаге подтверждается работоспособность функции [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] в службах Reporting Services. Если службы Reporting Services не устанавливались, пропустите этот шаг.  
  
     Далее нужно будет подключиться к серверу в среде Management Studio, чтобы удостовериться, что данные загружены и кэшированы.  
  
6.  Запустите среду SQL Server Management Studio из группы программ [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] в меню «Пуск». Если это средство не установлено на сервере, можно пропустить этот шаг и перейти к последнему шагу по подтверждению наличия кэшированных файлов.  
  
7.  В списке Тип сервера выберите **Analysis Services**.  
  
8.  В поле имя сервера введите ** \<server-name> \PowerPivot**, где **\<server-name>** — имя компьютера, на котором установлена PowerPivot для SharePoint установка.  
  
9. Нажмите кнопку **Подключиться**. Будет проверена доступность сервера служб Analysis Services.  
  
10. В обозревателе объектов можно щелкнуть **базы данных** , чтобы просмотреть список загруженных файлов данных PowerPivot.  
  
11. В файловой системе компьютера откройте следующую папку, чтобы определить, были ли файлы кэшированы на диск. Наличие кэшированных файлов служит еще одним подтверждением работоспособности развертывания. Чтобы просмотреть кэш файлов, перейдите к \<drive> папке: \Program FILES\MICROSOFT SQL Server\MSAS11. Папка приложения службы Поверпивот\олап\баккуп\сандбоксес\дефаулт PowerPivot. Каждая кэшируемая база данных хранится в собственной папке, схема именования которых основана на идентификаторах GUID и гарантирует уникальность имен.  
  
  
