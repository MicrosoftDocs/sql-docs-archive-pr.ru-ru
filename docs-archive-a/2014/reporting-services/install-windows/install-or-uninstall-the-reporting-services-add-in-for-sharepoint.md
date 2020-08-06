---
title: Установка или удаление надстройки Reporting Services для SharePoint (SharePoint 2010 и SharePoint 2013) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e30014ec823e89172b36f35d7f313568432a26f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665856"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a>Установка и удаление надстройки служб Reporting Services для SharePoint (SharePoint 2010 и SharePoint 2013)
  Запустите [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройку пакета установки служб для продуктов SharePoint (rsSharePoint.msi) на серверах SharePoint, чтобы включить [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] функции в развертывании SharePoint. К этим компонентам относится Power View, веб-часть средства просмотра отчетов, конечная точка прокси для URL-адреса, типы содержимого и страницы приложений, которые позволяют создавать и просматривать отчеты, модели отчетов, источники данных и другое содержимое сервера отчетов на сайте SharePoint, а также управлять всем этим. Для сервера отчетов, работающего в режиме интеграции с SharePoint, надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint является обязательным компонентом. Надстройку можно установить с помощью мастера установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или загрузить файл rsSharePoint.msi из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Список версий надстройки и страницы загрузки приведены в разделе [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|

 **В этом разделе:**

-   [Предварительные требования](#bkmk_prereq)

-   [Что устанавливает эта надстройка?](#bkmk_whatinstalled)

-   [Общие сведения о методах установки](#bkmk_3ways_to_install)

-   [Установите надстройку с помощью файла установки rsSharePoint.msi](#bkmk_install_rssharepoint)

    -   [Установка только файлов](#bkmk_files_only_installation)

-   [Удаление надстройки служб Reporting Services](#bkmk_remove_addin)

-   [Восстановление rssharepoint.msi из командной строки](#bkmk_repair)

-   [Файлы журналов установки](#bkmk_logfiles)

-   [Обновление](#bkmk_upgrade)

-   [rsCustomAction.exe](#bkmk_rscustomaction)

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Предварительные требования
 Установка надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] является одним из обязательных шагов интеграции сервера отчетов с экземпляром продукта SharePoint. Дополнительные сведения о полном наборе предварительных требований для использования режима интеграции с SharePoint см. в разделе [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md). Дополнительные сведения об установке и настройке см [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . в [статье Установка Reporting Services SharePoint в режиме интеграции с SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).

-   При интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с фермой SharePoint, содержащей несколько приложений клиентского веб-интерфейса, установите надстройку на каждый компьютер фермы с сервером клиентского веб-интерфейса. Это необходимо сделать только для веб-серверов, обслуживающих клиентские запросы, которые будут производить доступ к содержимому сервера отчетов.

-   Чтобы установить надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , необходимо быть администратором компьютера. Например, чтобы запустить файл rsSharePoint.msi из командной строки, следует открыть командную строку с правами администратора с помощью команды **Запуск от имени администратора** .

-   Чтобы установить надстройку [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , требуется членство в группе администраторов фермы SharePoint.

-   Чтобы активировать функции интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , необходимо быть администратором семейства веб-сайтов.

-   Схемы примеров развертывания с надстройкой см. в разделе [топологии развертывания для SQL Server функций бизнес-аналитики в SharePoint](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).

##  <a name="what-does-the-add-in-install"></a><a name="bkmk_whatinstalled"></a>Что устанавливает надстройка?
 Процесс установки надстройки состоит из двух фаз, при этом обе они выполняются автоматически при стандартной установке.

-   Сначала файлы устанавливаются в нужные папки. Это стандартные папки для развертываний SharePoint. Один из устанавливаемых файлов называется rsCustomAction.exe.

-   На втором этапе установки выполняется набор пользовательских действий для регистрации файлов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в SharePoint. Пользовательские действия выполняются с помощью файла rsCustomAction.exe. По окончании двух этапов установки этот EXE-файл удаляется. Можно выполнить установку **только файлов** , при которой файл rsCustomAction.exe по окончании установки не запускается и остается на диске.

## <a name="the-reporting-services-installation-order"></a>Порядок установки служб Reporting Services
 Надстройку можно установить перед установкой SharePoint либо после установки SharePoint. Надстройка соответствует стандартам развертывания до установки SharePoint и устанавливает файлы в расположения, которые используются при установке SharePoint.

> [!NOTE]
>  Преимущество установки надстройки до развертывания продукта SharePoint заключается в том, что по мере добавления новых серверов в ферму надстройка служб Reporting Services будет настраиваться и активироваться фермой SharePoint.

 **SharePoint 2010**

-   Средство подготовки продуктов SharePoint 2010 устанавливает версию [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] надстройки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] содержит новую версию надстроек, необходимых для функций [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

     При использовании средства подготовки продуктов SharePoint все равно необходимо установить надстройку служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

-   Если сначала была установлена надстройка служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], то при запуске средства подготовки продуктов SharePoint появится следующее диалоговое окно, в котором сообщается, что средство подготовки не установило предыдущую версию надстройки и была обнаружена более поздняя версия. Такое поведение является стандартным.

     ![Надстройка SSRS уже установлена.](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "Надстройка SSRS уже установлена.")

 **SharePoint 2013**

 Средство подготовки продуктов SharePoint 20103 **не** устанавливает [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройку для продуктов SharePoint.

##  <a name="overview-of-the-installation-methods"></a><a name="bkmk_3ways_to_install"></a> Общие сведения о методах установки
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Надстройку служб для продуктов SharePoint можно установить с помощью одного из следующих двух методов:

-   **Мастер установки.** ![Примечание](../../../2014/reporting-services/media/rs-fyinote.png "Примечание."). новые [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] возможности. надстройка может быть установлена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастером установки. Выберите **надстройку служб Reporting Services для продуктов SharePoint** на странице мастера **Выбор компонентов** .

-   **rsSharepoint.msi** . Надстройку можно установить напрямую с установочного носителя или скачать и установить. Файл rsSharepoint.msi поддерживает как графический пользовательский интерфейс, так и установку из командной строки. Файл MSI необходимо запустить с правами администратора, сначала открыв окно командной строки с повышенными разрешениями, затем запустить файл rsSharepoint.msi из командной строки. Дополнительные сведения о скачивании надстройки см. в разделе [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).

    > [!NOTE]
    >  При использовании параметра **/q** для автоматической установки из командной строки условия лицензионного соглашения не отображаются. Независимо от метода установки, использование программного обеспечения регулируется лицензионным соглашением и пользователь несет ответственность за его соблюдение.

##  <a name="install-the-add-in-using-the-installation-file-rssharepointmsi"></a><a name="bkmk_install_rssharepoint"></a> Установка надстройки с помощью файла rsSharePoint.msi
 В этом разделе рассматривается установка напрямую с помощью файла rssharepoint.msi, либо с помощью мастера установки, либо из командной строки. Если надстройка была установлена с помощью мастера установки SQL Server, выполнять эти действия не нужно.

 С помощью следующей команды можно вывести полный список параметров командной строки:

```
Rssharepoint.msi /?
```

1.  Скачайте программу установки ( `rsSharepoint.msi` ) для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройки. Дополнительные сведения о скачивании надстройки см. в разделе [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).

2.  От имени администратора запустите файл `rsSharepoint.msi`, чтобы открыть мастер установки. Мастер отобразит страницу приветствия, условия лицензионного соглашения на использование программного обеспечения и регистрационные сведения. Программа установки создаст папки по следующему пути и скопирует туда файлы:

     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`

     ,

     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`

3.  Настройте параметры сервера отчетов и включите нужные компоненты в центре администрирования SharePoint. . Дополнительные сведения об установке и настройке [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint см. в статье [Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).

###  <a name="files-only-installation"></a><a name="bkmk_files_only_installation"></a>Установка только файлов
 Чтобы установить файлы и пропустить этап пользовательских действий, запустите файл rssharepoint.msi из командной строки с параметром SKIPCA.

1.  Откройте командную строку **с разрешениями администратора**.

2.  Выполните следующую команду:

    ```cmd
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1
    ```

 Откроется пользовательский интерфейс, и установка пройдет в обычном режиме, файл `rsCustomAction.exe` будет установлен. Но EXE-файл не будет запущен в конце установки и `rsCustomAction.exe` останется на компьютере по завершении установки.

### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a>Установка в два шага для устранения проблем с установкой или установки типов содержимого
 Если во время установки вы получаете ошибки или типы содержимого [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не отображаются в параметрах библиотеки документов, можно запустить установку в виде двухэтапного процесса из командной строки.

1.  Откройте командную строку **с разрешениями администратора** и запустите установку в режиме «только файлы», как описано в предыдущем разделе.

2.  Запустите исполняемый файл пользовательских действий.

    1.  Перейдите к папке с файлом `rsCustomAction.exe`. Этот файл копируется на компьютер программой установки надстройки, которая устанавливает только файлы. `rsCustomAction.exe`находится в каталоге **% TEMP%** . Для перехода к файлу введите в командной строке следующую команду:

         **CD %temp%**.

         Файл должен быть расположен в папке: **\Users\\<ваше имя\>\AppData\Local\Temp**.

    2.  Введите указанную ниже команду. Выполнение этого шага настройки требует нескольких минут. В течение этого времени будет перезапущена служба W3SVC. Пока программа копирует файлы, регистрирует компоненты и запускает мастер настройки продуктов SharePoint, на экране будут появляться различные сообщения о состоянии.

        ```cmd
        rsCustomAction.exe /i
        ```

    3.  Время, необходимое для применения изменений, варьируется и зависит от используемой среды сервера. Можно также запустить **iisreset** , чтобы принудительно выполнить более быстрое обновление.

### <a name="quiet-installation-for-scripting"></a>Автоматическая установка
 Можно использовать параметры **/q** или **/quiet** для автоматической установки без отображения диалоговых окон и предупреждений. Автоматическая установка удобна, если установку надстройки нужно выполнить из скрипта.

> [!NOTE]
>  При использовании параметра **/q** для автоматической установки из командной строки условия лицензионного соглашения не отображаются. Независимо от метода установки, использование программного обеспечения регулируется лицензионным соглашением и пользователь несет ответственность за его соблюдение.

 Выполнение автоматической установки

1.  Откройте командную строку **с разрешениями администратора**.

2.  Выполните следующую команду:

    ```cmd
    Msiexec.exe /i rsSharePoint.msi /q
    ```

##  <a name="how-to-remove-the-reporting-services-add-in"></a><a name="bkmk_remove_addin"></a>Удаление надстройки Reporting Services
 Удалить надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint можно с помощью панели управления [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows или из командной строки.

1.  При использовании панели управления выполняется полное удаление файлов с данного компьютера **И** удаление объекта и компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] из фермы SharePoint. Когда объект и компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] будут удалены, вы больше не сможете просматривать и обновлять отчеты.

2.  Метод удаления надстройки с помощью командной строки позволяет с помощью параметра LocalOnly удалять только файлы надстройки с локального компьютера, при этом объект и компоненты [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в ферме остаются без изменений.

 При удалении надстройки будут удалены функции интеграции сервера, используемые для обработки отчетов на сервере отчетов. Также будут удалены страницы служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] из центра администрирования SharePoint и другие пользовательские страницы служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . При необходимости также удалите все отчеты и другие элементы сервера отчетов, которые больше не используются на затронутых сайтах SharePoint. Их запуск будет невозможен после удаления надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

 Чтобы удалить надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], необходим работающий экземпляр [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]. Если SharePoint 2010 была удалена ранее, чтобы удалить надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], SharePoint придется установить повторно.

 Удаление надстройки выполняется одинаково для изолированных серверов и для ферм серверов. С помощью программы установки удаляются программные файлы и настройки конфигурации, добавленные во время установки.

 При удалении надстройки следующие элементы не удаляются:

-   Имена входа, созданные для учетной записи службы Report Server для доступа к конфигурации и базам данных содержимого SharePoint. Для учетной записи службы сервера отчетов необходимо удалить все имена входа из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] экземпляра, используемого для размещения баз данных SharePoint.

-   Разрешения или группы, созданные для пользователей отчетов. Если были созданы пользовательские уровни разрешений или группы SharePoint для предоставления доступа к функциям сервера отчетов, можно отменить любые разрешения, необходимость в которых отпала.

-   Файлы данных, загруженные в библиотеку SharePoint, включая файл определения отчета (RDL), общего источника данных (RSDS) и элементы опубликованных отчетов (RSC). Они не удаляются, но их выполнение становится невозможным. Удаление файлов необходимо произвести вручную.

-   Программой установки не будет удалена база данных сервера отчетов или изменен экземпляр сервера отчетов, используемый для операций в режиме интеграции.

### <a name="to-uninstall-from-windows-control-panel"></a>Удаление с панели управления Windows
 Запуск мастера с панели управления [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и удаление надстройки

1.  На панели управления, в разделе **Программы**выберите **Удалить программу**.

2.  Выберите **Надстройка служб Microsoft SQL Server RS для SharePoint**. Также вы можете открыть мастер удаления, запустив файл **rssharepoint.msi** из командной строки без ключей.

3.  Щелкните **Удалить**.

### <a name="uninstall-from-the-command-line"></a>Удаление из командной строки
 Удаление надстройки из командной строки

1.  Откройте командную строку **с разрешениями администратора**.

2.  Выполните следующую команду:

    ```cmd
    msiexec.exe /uninstall rsSharePoint.msi
    ```

3.  Появится сообщение с запросом на подтверждение. Нажмите кнопку **Да**.

### <a name="uninstall-the-add-in-from-the-local-server-only"></a>Удаление надстройки только с локального сервера
 Рассмотренные выше методы удаления надстройки также удаляют объект и компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] из фермы. Если ферма состоит из нескольких серверов и требуется удалить надстройку только с локального компьютера, сохранив при этом ферму SharePoint а рабочем состоянии, выполните следующие шаги.

1.  Откройте командную строку **с разрешениями администратора**.

2.  Выполните следующую команду:

    ```cmd
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1
    ```

 При этом будет отменена регистрация компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в SharePoint и удалены файлы, но только на локальном компьютере.

 Если необходимо отменить регистрацию компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в SharePoint, но сохранить файлы на диске для последующего использования, выполните следующие шаги.

1.  Откройте командную строку **с разрешениями администратора**.

2.  Выполните следующую команду:

    ```cmd
    rsCustomAction.exe /p
    ```

 При этом предполагается, что установка MSI-файла была проведена с параметром SkipCA=1 и доступен файл rscusstomaction.exe. Дополнительные сведения см. в разделе с описанием установки только файлов.

##  <a name="how-to-repair-rssharepointmsi-from-the-command-line"></a><a name="bkmk_repair"></a>Восстановление rssharepoint.msi из командной строки
 Чтобы восстановить или удалить надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с использованием командной строки, выполните следующие действия.

1.  Откройте командную строку **с разрешениями администратора**.

2.  Выполните следующую команду:

    ```cmd
    msiexec.exe /f rssharepoint.msi
    ```

##  <a name="setup-log-files"></a><a name="bkmk_logfiles"></a>Файлы журналов установки
 При запуске программы установки она записывает сведения в файл журнала в папке **%temp%** пользователя, который устанавливает надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Например, **c:\Users \\<username \> \AppData\Local\Temp** . Имя файла — **RS_SP_ \<number> . log**, например **RS_SP_0. log**. Каждая запись об ошибке в журнале начинается со строки «SSRSCustomActionError».

> [!NOTE]
>  AppData — это скрытая папка в операционной системе Windows. Для отображения скрытых файлов и папок, возможно, потребуется изменить параметры папки в проводнике Windows.

#### <a name="view-a-log-file-with-windows-notepad"></a>Просмотр файла журнала в Блокноте Windows

1.  Следующие команды меняют путь в командной строке, выводят список RS-файлов журналов и открывают один из файлов в Блокноте Windows:

    ```cmd
    cd %temp%
    ```

    ```cmd
    dir rs_sp*.log
    ```

    ```cmd
    notepad rs_sp_3.log
    ```

#### <a name="view-a-log-file-with-powershell"></a>Просмотр файла журнала с помощью PowerShell

1.  Введите следующую команду в консоли управления SharePoint, чтобы получить из файла, содержащего подстроку "ssrscustomactionerror", отфильтрованный список строк.

    ```powershell
    Get-Content -Path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"
    ```

2.  Вывод имеет следующий вид:

     `2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.

##  <a name="upgrade"></a><a name="bkmk_upgrade"></a>Обновления
 Если надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] уже установлена, ее можно обновить до текущей версии. Программа установки надстройки обнаружит существующую версию и предложит подтвердить обновление. Сообщение имеет следующий вид:

 **В системе обнаружена более ранняя версия этого продукта. Вы хотите обновить существующую установку?**

 При получении подтверждения старая версия надстройки будет удалена, а новая установлена.

 Обратите внимание, что надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не привязана к экземпляру. Можно установить только один экземпляр надстройки на компьютер. Более ранние версии нельзя запускать параллельно с текущей версией.

##  <a name="rscustomactionexe"></a><a name="bkmk_rscustomaction"></a>RsCustomAction.exe
 В следующей таблице описываются параметры командной строки для программы rscustomaction.exe.

|Параметр|Описание|
|------------|-----------------|
|i|Устанавливает пользовательские действия. Регистрирует компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в SharePoint. Перезапускает службу W3SVCservice.|
|r|Восстановление|
|u|Удаление. Отменяет регистрацию компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] во всей ферме SharePoint, но оставляет файлы на диске. Перезапускает службу W3SVCservice.|
|p|Локальное удаление Отменяет регистрацию компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] только на локальном компьютере. Файлы останутся на диске. Перезапускает службу W3SVCservice.|
|t|Только SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005. Переключение проверяет, имеет ли сервер отчетов рабочее соединение с базой данных сервера отчетов.|

## <a name="configuring-reporting-services"></a>Настройка служб Reporting Services
 После установки надстройки на все нужные компьютеры настройте сервер отчетов с помощью центра администрирования SharePoint. Необходимые действия зависят от порядка установки разных технологий. Дополнительные сведения см. в статьях [установка Reporting Services SharePoint в режиме интеграции с sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) и [Reporting Services сервера отчетов &#40;режиме SharePoint&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)

## <a name="see-also"></a>См. также:
 [Установка Reporting Services режиме интеграции с SharePoint для sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) [Reporting Services сервере отчетов &#40;режиме SharePoint&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)
