---
title: Изменение модуля доставки отчетов Reporting Services по умолчанию | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], default delivery extension
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cc1b3af2a4fe3038b761d0b48030062da06d354e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734921"
---
# <a name="change-the-default-reporting-services-delivery-extension"></a>Изменение модуля доставки отчетов служб Reporting Services по умолчанию
  Вы можете изменить настройки конфигурации [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] , чтобы сменить модуль доставки по умолчанию, который отображается в списке **Доставлено** , на странице определения подписки. Например, можно изменить конфигурацию так, чтобы при создании пользователями новой подписки по умолчанию выбиралась доставка в общую папку, а не доставка по почте. Можно также изменить порядок модулей доставки в пользовательском интерфейсе.

 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в собственном режиме | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включают модуль доставки по электронной почте и модуль доставки в общую папку Windows. У сервера отчетов могут быть дополнительные модули доставки, если развернуть пользовательские модули или модули сторонних производителей для поддержки пользовательской доставки. Доступность модуля доставки зависит от того, развернут ли он на сервере отчетов.

## <a name="default-native-mode-report-server-configuration"></a>Настройка сервера отчетов в собственном режиме по умолчанию
 Порядок, в котором модули доставки отображаются в списке **Доставлено** в диспетчере отчетов, основан на порядке записей модулей доставки в файле **RSReportServer.config** . Например, на следующем рисунке электронная почта находится вначале в списке, и она выбрана по умолчанию.

 ![заданный по умолчанию список модулей доставки](../media/ssrs-default-delivery.png "заданный по умолчанию список модулей доставки")

 Ниже приведен раздел **RSReportServer.config** по умолчанию, управляющий модулем доставки по умолчанию и порядком отображения модулей в диспетчере отчетов. Обратите внимание, что электронная почта отображается в файле первой и выбрана как параметр по умолчанию.

```xml
<DeliveryUI>
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
               <Configuration>
               <RSEmailDPConfiguration>
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
               </RSEmailDPConfiguration>
               </Configuration>
     </Extension>
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>
</DeliveryUI>
```

#### <a name="configure-file-share-delivery-as-the-default-delivery-extension-in-report-manager"></a>Настройка доставки в общую папку в качестве модуля доставки по умолчанию диспетчера отчетов

1.  В этой процедуре конфигурация изменяется так, чтобы доставка в общую папку была указана в качестве первого параметра в пользовательском интерфейсе и была параметром по умолчанию.

     Откройте файл RSReportServer.config в текстовом редакторе. Дополнительные сведения о файле конфигурации см. в разделе [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md). После изменения конфигурации пользовательский интерфейс будет выглядеть как на следующем рисунке:

     ![измененный список модулей доставки](../media/ssrs-modified-delivery.png "измененный список модулей доставки")

2.  Измените раздел DeliveryUI, как в следующем примере, и обратите внимание на основные изменения.

    1.  Модуль доставки в общую папку находится перед модулем электронной почты. Это приведет к изменению порядка модулей доставки в диспетчере отчетов.

    2.  Модуль доставки в общую папку содержит тег DefaultExtension `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` , также был добавлен закрывающий тег модуля `</Extension>`.

    3.  Модуль доставки по почте больше не задан по умолчанию. `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`

    ```
    <DeliveryUI>
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
         </Extension>
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>
         <Configuration>
              <RSEmailDPConfiguration>
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
              </RSEmailDPConfiguration>
         </Configuration>
         </Extension>
    </DeliveryUI>
    ```

3.  Сохраните файл конфигурации.

4.  В течение нескольких минут сервер отчетов перезагрузит файл конфигурации, и новые параметры вступят в силу. Вы можете перезапустить службу сервера отчетов для принудительной загрузки файла конфигурации.

     Следующее событие записывается в журнал событий Windows при чтении конфигурации.

     **Идентификатор события:** 109

     **Источник**: служба Windows для сервера отчетов (имя экземпляра)

     Файл RSReportServer.config был изменен.

## <a name="sharepoint-mode-report-servers"></a>Серверы отчетов в режиме интеграции с SharePoint
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в режиме интеграции SharePoint сведения о модулях доставки хранятся в базах данных приложения-службы, а не в файле RsrReportServer.config. В режиме интеграции с SharePoint настройки модуля доставки изменяются с помощью PowerShell.

#### <a name="configure-the-default-delivery-extension"></a>Настройка модуля доставки по умолчанию

1.  Откройте **консоль управления SharePoint**.

2.  Этот шаг можно пропустить, если вам известно имя приложения-службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . Используйте следующие команды PowerShell, чтобы получить список приложений-служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в ферме SharePoint.

    ```powershell
    Get-SPRSServiceApplication | Format-List *
    ```

3.  Выполните следующие команды PowerShell для проверки текущего модуля доставки по умолчанию для приложения-службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] "ssrsapp".

    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -Like "ssrsapp*"};
    Get-SPRSExtension -Identity $app | Where {$_.ServerDirectivesXML -Like "<DefaultDelivery*"} | Format-List *
    ```

## <a name="see-also"></a>См. также:
 Файл [конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md) [Конфигурация RSReportServer](../report-server/rsreportserver-config-configuration-file.md) файлового [ресурса доставка в Reporting Services](file-share-delivery-in-reporting-services.md) [доставки электронной почты в Reporting Services](e-mail-delivery-in-reporting-services.md) [настройка сервера отчетов для доставки электронной почты &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)
