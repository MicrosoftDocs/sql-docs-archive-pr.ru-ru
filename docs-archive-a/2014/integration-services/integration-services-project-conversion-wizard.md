---
title: Мастер преобразования Integration Services проектов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.migrationwizard.f1
ms.assetid: a192b094-4d0f-4c21-b911-460ec844a49f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c47dc8ed1d0485a62128be732cc34de1dca35740
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664391"
---
# <a name="integration-services-project-conversion-wizard"></a>Мастером преобразования проекта служб Integration Services
  **Мастер преобразования проекта служб Integration Services** преобразует проект в модель развертывания проекта.  
  
> [!NOTE]  
>  Если проект содержит один или более источников данных, то они будут удалены после завершения преобразования проекта. Для создания соединения с источником данных, который может совместно использоваться пакетами в проекте, добавьте диспетчер соединений на уровне проекта. Дополнительные сведения см. в статье [Добавление, удаление или совместное использование диспетчера соединений в пакете](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).  
  
 **Выбор действия**  
  
-   [Открытие мастера преобразования проекта служб Integration Services](#open_dialog)  
  
-   [Задание параметров на странице «Поиск пакетов»](#locate)  
  
-   [Задание параметров на странице «Выбор пакетов»](#selectPackages)  
  
-   [Задание параметров на странице «Выбор назначения»](#destination)  
  
-   [Задание параметров на странице «Задание свойств проекта»](#projectProperties)  
  
-   [Задание параметров на странице «Обновление задачи выполнения пакета»](#executePackage)  
  
-   [Задание параметров на странице «Выбор конфигурации»](#configurations)  
  
-   [Задание параметров на странице «Создание параметров»](#createParameters)  
  
-   [Задание параметров на странице «Настройка параметров»](#configureParameters)  
  
-   [Задание параметров на странице «Просмотр»](#review)  
  
-   [Задание параметров на странице «Выполнение преобразования»](#conversion)  
  
##  <a name="open-the-integration-services-project-conversion-wizard"></a><a name="open_dialog"></a>Открытие мастера преобразования Integration Services проектов  
 Выполните одно из следующих действий, чтобы открыть мастер **преобразования проекта служб Integration Services** .  
  
-   Откройте проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], а затем в обозревателе решений щелкните его правой кнопкой мыши и выберите команду **Преобразовать в модель развертывания проекта**.  
  
-   В среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]в обозревателе объектов щелкните правой кнопкой мыши узел **Проекты** и выберите команду **Импорт пакетов**.  
  
 В зависимости от того, запускается ли **Мастер преобразования проекта служб Integration Services** из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] или из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], он выполняет разные задачи по преобразованию. Дополнительные сведения см. в разделе [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
##  <a name="set-options-on-the-locate-packages-page"></a><a name="locate"></a>Задание параметров на странице «Размещение пакетов»  
  
> [!NOTE]  
>  Страница **Поиск пакетов** доступна только при запуске мастера из среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 При выборе пункта **Файловая система** в раскрывающемся списке **Источник** на странице отображается следующий параметр. Выберите этот параметр, если пакет размещен в файловой системе.  
  
 **Папка**  
 Введите путь к пакету или перейдите к пакету, нажав кнопку **Обзор**.  
  
 При выборе пункта **Хранилище пакетов служб SSIS** в раскрывающемся списке **Источник** на странице отображаются следующие параметры. Дополнительные сведения о хранилище пакетов см. в разделе [Управление пакетами (службы SSIS)](service/package-management-ssis-service.md).  
  
 **Server**  
 Введите имя сервера или выберите сервер.  
  
 **Папка**  
 Введите путь к пакету или перейдите к пакету, нажав кнопку **Обзор**.  
  
 При выборе пункта **Microsoft SQL Server** в раскрывающемся списке **Источник** на странице отображаются следующие параметры. Выберите этот параметр, если пакет находится в Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **Server**  
 Введите имя сервера или выберите сервер.  
  
 **Использовать проверку подлинности Windows**  
 Режим проверки подлинности Microsoft Windows позволяет подключаться с учетной записью пользователя Windows. При использовании проверки подлинности Windows не требуется ввод имени пользователя или пароля.  
  
 **Использовать проверку подлинности SQL Server**  
 При соединении пользователя с указанным именем и паролем из ненадежных соединений [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] выполняет проверку подлинности подключения посредством проверки настройки учетной записи входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и проверки совпадения указанного пароля с ранее сохраненным. Если в службе [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не задана учетная запись входа, проверка подлинности завершается ошибкой, о которой пользователь получит сообщение.  
  
 **User name**  
 При использовании проверки подлинности SQL Server укажите имя пользователя.  
  
 **Пароль**  
 Укажите пароль, если используется проверка подлинности SQL Server.  
  
 **Папка**  
 Введите путь к пакету или перейдите к пакету, нажав кнопку **Обзор**.  
  
##  <a name="set-options-on-the-select-packages-page"></a><a name="selectPackages"></a>Задание параметров на странице «Выбор пакетов»  
 **Имя пакета**  
 Выводит список файлов пакета.  
  
 **Состояние**  
 Указывает, готов ли пакет к преобразованию в модель развертывания проекта.  
  
 **Message**  
 Отображает сообщение, связанное с пакетом.  
  
 **Пароль**  
 Отображает пароль, связанный с пакетом. Текст пароля скрыт.  
  
 **Применить к выбранным объектам**  
 Нажмите эту кнопку для установки пароля в текстовом поле **Пароль** для выбранного пакета или пакетов.  
  
 **Обновить**  
 Обновляет список пакетов.  
  
##  <a name="set-options-on-the-select-destination-page"></a><a name="destination"></a>Задание параметров на странице «Выбор назначения»  
 На этой странице укажите имя и путь к новому файлу развертывания проекта (ISPAC) или выберите существующий файл.  
  
> [!NOTE]  
>  Страница **Выбор назначения** доступна только при запуске мастера из среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 **Путь для создаваемых файлов**  
 Введите путь к файлу развертывания или перейдите к файлу, нажав кнопку **Обзор**.  
  
 **Имя проекта**  
 Введите имя проекта.  
  
 **Уровень защиты**  
 Выберите уровень защиты. Дополнительные сведения см. в разделе [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).  
  
 **Описание проекта**  
 Введите необязательное описание для проекта.  
  
##  <a name="set-options-on-the-specify-project-properties-page"></a><a name="projectProperties"></a>Задание параметров на странице «Задание свойств проекта»  
  
> [!NOTE]  
>  Страница **Задание свойств проекта** доступна только при запуске мастера из среды [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 **Имя проекта**  
 Выводит список имен проекта.  
  
 **Уровень защиты**  
 Выбор уровня защиты для пакетов, содержащихся в проекте. Дополнительные сведения об уровнях защиты см. в разделе [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).  
  
 **Описание проекта**  
 Введите необязательное описание проекта.  
  
##  <a name="set-options-on-the-update-execute-package-task-page"></a><a name="executePackage"></a>Задание параметров на странице «Обновление задачи выполнения пакета»  
 Обновление задачи «Выполнение пакета» содержится в пакетах для использования ссылки на основе проектов. Дополнительные сведения см. в разделе [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md).  
  
 **Родительский пакет**  
 Выводит список имен пакета, который выполняет дочерний пакет с помощью задачи «Выполнение пакета».  
  
 **Имя задачи**  
 Выводит список имен задачи «Выполнение пакета».  
  
 **Исходная ссылка**  
 Отображает текущий путь к дочернему пакету.  
  
 **Назначение ссылки**  
 Выбор дочернего пакета, хранящегося в этом проекте.  
  
##  <a name="set-options-on-the-select-configurations-page"></a><a name="configurations"></a>Задание параметров на странице «Выбор конфигураций»  
 Выберите конфигурации пакетов, которые требуется заменить параметрами.  
  
 **Пакет**  
 Выводит список файлов пакета.  
  
 **Тип**  
 Выводит список типов конфигурации, например XML-файл конфигурации.  
  
 **Строка конфигурации**  
 Отображает путь к файлу конфигурации.  
  
 **Состояние**  
 Отображает сообщение о состоянии конфигурации. Щелкните это сообщение для просмотра его содержимого.  
  
 **Добавление конфигураций**  
 Добавление конфигурации пакета, содержащейся в других проектах, в список доступных конфигураций, которые необходимо заменить параметрами. Вы можете выбрать конфигурации, которые хранятся в файловой системе или в SQL Server.  
  
 **Обновить**  
 Нажмите эту кнопку для обновления списка конфигураций.  
  
 **Удаление конфигураций из всех пакетов после преобразования**  
 Рекомендуется удалить все конфигурации из проекта, выбрав этот параметр.  
  
 Если не выбрать этот параметр, будут удалены только те конфигурации, которые требуется заменить параметрами.  
  
##  <a name="set-options-on-the-create-parameters-page"></a><a name="createParameters"></a>Задание параметров на странице «Создание параметров»  
 Выбор имени параметра и области каждого свойства конфигурации.  
  
 **Пакет**  
 Выводит список файлов пакета.  
  
 **Имя параметра**  
 Выводит список имен параметра.  
  
 **Область**  
 Выбор области параметра, пакета или проекта.  
  
##  <a name="set-options-on-the-configure-parameters-page"></a><a name="configureParameters"></a>Задание параметров на странице «Настройка параметров»  
 **имя**;  
 Выводит список имен параметра.  
  
 **Область**  
 Отображает область действия параметров.  
  
 **Значение**  
 Выводит список значений параметра.  
  
 Для настройки свойства параметра нажмите кнопку с многоточием рядом с полем значения.  
  
 В диалоговом окне **Задание сведений о параметре** вы можете изменить значение параметра. Вы можете также указать, необходимо ли при запуске пакета указывать значение параметра.  
  
 Изменить значение вы можете на странице **Параметры** диалогового окна **Настройка** в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], нажав кнопку обзора рядом с параметром. Отобразится диалоговое окно **Задание значения параметра** .  
  
 В диалоговом окне **Задание сведений о параметре** перечислены также типы данных значения параметра и его начальное значение.  
  
##  <a name="set-the-options-on-the-review-page"></a><a name="review"></a>Задание параметров на странице «Проверка»  
 Подтвердить параметры, которые выбраны для преобразования проекта, можно на странице **Обзор**.  
  
 **Назад**  
 Нажмите эту кнопку для изменения параметра.  
  
 **Преобразовать**  
 Нажмите эту кнопу для преобразования проекта в модель развертывания проекта.  
  
##  <a name="set-the-options-on-the-perform-conversion"></a><a name="conversion"></a>Задание параметров для выполнения преобразования  
 На странице «Выполнение преобразования» отображается состояние преобразования проекта.  
  
 **Действие**  
 Выводит список заданных шагов преобразования.  
  
 **Результат**  
 Отображает состояние каждого шага преобразования. Щелкните сообщение о состоянии для получения дополнительных сведений.  
  
 Преобразование проекта не сохраняется до тех пор, пока проект сохранен в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 **Сохранить отчет**  
 Нажмите эту кнопку, чтобы сохранить сводку по преобразованию проекта в XML-файл.  
  
## <a name="see-also"></a>См. также:  
 [Развертывание проектов на сервере служб Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md)  
  
  
