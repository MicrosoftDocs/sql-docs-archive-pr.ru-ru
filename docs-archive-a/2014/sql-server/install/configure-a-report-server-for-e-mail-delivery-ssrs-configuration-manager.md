---
title: Настройка сервера отчетов для доставки электронной почты (службы SSRS Configuration Manager) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], distributing
- report servers [Reporting Services], e-mail delivery
- remote SMTP service [Reporting Services]
- distributing reports [Reporting Services], e-mail
- CDO
- Collaboration Data Objects
- SMTP settings [Reporting Services]
- e-mail [Reporting Services]
- sending reports
- mail [Reporting Services]
- local SMTP service [Reporting Services]
ms.assetid: b838f970-d11a-4239-b164-8d11f4581d83
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3122dbbb5debc90afa73ca0f8ab0d8e23d38a0ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665782"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a>Настройка сервера отчетов для работы с электронной почтой (диспетчер конфигурации служб Reporting Services)


  Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль доставки по электронной почте, позволяющий распространять отчеты с помощью электронной почты. В зависимости от того, каким образом определена электронная подписка, рассылка может включать уведомление, ссылку, вложение или внедренный отчет. Модуль доставки по электронной почте работает с существующими технологиями почтовых серверов. Почтовый сервер должен быть либо SMTP-сервером, либо перенаправителем. Сервер отчетов соединяется с SMTP-сервером через объекты данных совместной работы (библиотека cdosys.dll), предоставляемых операционной системой.  
  
 Модуль доставки электронной почты сервера отчетов не настроен по умолчанию. Для минимальной настройки модуля следует воспользоваться диспетчером настройки служб Reporting Services. Чтобы указать дополнительные свойства, необходимо изменить файл конфигурации `RSReportServer.config` . Если нельзя настроить сервер отчетов на использование этого модуля, то вместо этого можно доставлять отчеты в общую папку. Дополнительные сведения см. в разделе [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим|  
  
 
  
##  <a name="configuration-requirements"></a><a name="bkmk_configuration_requirements"></a>Требования к конфигурации  
  
-   Доставка сервером отчетов по электронной почте реализована на основе объектов данных совместной работы и требует локального или удаленного SMTP-сервера или перенаправителя. Протокол SMTP поддерживается не для всех операционных систем Windows. В частности, он не поддерживается в выпуске Windows Server 2008 для платформы Itanium. Дополнительные сведения о параметрах конфигурации, предоставляемых объектами CDO, см. в MSDN, в статье [CoClass конфигурации](https://go.microsoft.com/fwlink/?LinkId=98237) .  
  
-   Учетная запись службы сервера отчетов должна иметь разрешение на отправку почты через SMTP-сервер.  
  
-   Модуль доставки по электронной почте использует во вложениях электронной почты кодировку UTF-8. Она не может быть изменена: модуль подготовки HTML поддерживает только UTF-8.  
  
> [!NOTE]  
>  Модуль доставки по электронной почте по умолчанию не поддерживает цифровые подписи или шифрование в исходящих сообщениях почты.  
  
 
  
##  <a name="configuring-a-report-server-for-local-or-remote-smtp-service"></a><a name="bkmk_configure_for_local_or_remote_SMTP"></a>Настройка сервера отчетов для локальной или удаленной службы SMTP  
 Для поддержки рассылки по электронной почте можно использовать локальную службу SMTP, удаленный сервер или SMTP-перенаправитель. Если есть доступ к существующему удаленному SMTP-серверу, следует рассмотреть возможность его использования. Если SMTP-сервер недоступен или впоследствии возникают ошибки при доставке отчетов, которые можно объяснить сбоями подключения к компьютеру, следует перейти к использованию локальной службы SMTP. Более подробные сведения о настройке сервера отчета для работы с локальной или удаленной службой приводятся ниже в этом разделе.  
  
  
  
##  <a name="setting-configuration-options-for-e-mail-delivery"></a><a name="bkmk_setting_email_delivery"></a>Установка параметров конфигурации для доставки электронной почты  
 Прежде чем будет можно использовать рассылку сервера отчетов по электронной почте, следует установить значения конфигурации, указывающие, какой SMTP-сервер использовать.  
  
 Для настройки сервера отчетов для доставки электронной почты выполните следующие действия:  
  
-   Воспользуйтесь диспетчером конфигурации служб Reporting Services, если вы задаете SMTP-сервер и учетную запись, имеющую разрешение на отправку сообщений электронной почты. Это минимальные установки, необходимые для настройки модуля доставки электронной почты сервера отчетов. Дополнительные сведения см. в разделе [Параметры электронной почты — Configuration Manager &#40;служб SSRS в собственном режиме&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) и [Доставка электронной почты в Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   С помощью текстового редактора укажите дополнительные параметры в файле конфигурации RSreportserver.config (необязательно). Этот файл содержит все параметры конфигурации доставки отчетов по электронной почте. Задание дополнительных установок в этих файлах необходимо, если используется локальный SMTP-сервер или если доставка сообщений электронной почты ограничивается определенными узлами. Дополнительные сведения о поиске и изменении файлов конфигурации см. в разделе [изменение файла конфигурации Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) в Электронная документация на SQL Server.  
  
> [!NOTE]  
>  Параметры электронной почты сервера отчетов основаны на объектах CDO. Если необходимы дальнейшие подробности о конкретных параметрах, можно обратиться к документации по приложениям CDO.  
  

  
##  <a name="example-report-server-e-mail-configuration"></a><a name="bkmk_example_config_file"></a>Пример конфигурации электронной почты сервера отчетов  
 В следующем примере иллюстрируются параметры файла RSreportserver.config для удаленного SMTP-сервера. Описания параметров и их допустимых значений см. в разделе [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onlэлектронной документации поe or the CDO product documentation.  
  
```  
<RSEmailDPConfiguration>  
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>  
     <SMTPServerPort></SMTPServerPort>  
     <SMTPAccountName></SMTPAccountName>  
     <SMTPConnectionTimeout></SMTPConnectionTimeout>  
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>  
     <SMTPUseSSL></SMTPUseSSL>  
     <SendUsing>2</SendUsing>  
     <SMTPAuthenticate></SMTPAuthenticate>  
     <From>my-rs-email-account@Adventure-Works.com</From>  
     <EmbeddedRenderFormats>  
          <RenderingExtension>MHTML</RenderingExtension>  
     </EmbeddedRenderFormats>  
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>  
     <ExcludedRenderFormats>  
          <RenderingExtension>HTMLOWC</RenderingExtension>  
          <RenderingExtension>NULL</RenderingExtension>  
     </ExcludedRenderFormats>  
     <SendEmailToUserAlias>True</SendEmailToUserAlias>  
     <DefaultHostName></DefaultHostName>  
     <PermittedHosts>  
          <HostName>Adventure-Works.com</HostName>  
          <HostName>hotmail.com</HostName>  
     </PermittedHosts>  
</RSEmailDPConfiguration>  
```  
  

  
##  <a name="configuration-options-for-setting-the-to-field-in-a-message"></a><a name="bkmk_setting_TO_field"></a>Параметры конфигурации для поля "Кому" в сообщении  
 Пользовательские подписки, создаваемые в соответствии с разрешениями, предоставленными задачей « **Управление отдельными подписками** », содержат предварительно заданное имя пользователя, основанное на учетной записи пользователя домена. Когда пользователь создает подписку, имя получателя в поле **Кому:** подставляется автоматически; используется учетная запись пользователя домена, создающего подписку.  
  
 Если использовать SMTP-сервер или перенаправитель, который использует учетные записи электронной почты, отличающиеся от учетной записи пользователя домена, то во время доставки отчета произойдет ошибка, когда SMTP-сервер попытается доставить отчет этому пользователю.  
  
 Чтобы обойти эту проблему, можно изменить настройки конфигурации так, чтобы пользователь мог ввести имя в поле **Кому:**  
  
1.  Откройте файл RSReportServer.config в текстовом редакторе.  
  
2.  Задайте для параметра `SendEmailToUserAlias` значение `False`.  
  
3.  Установите параметр `DefaultHostName` в DNS-имя или IP-адрес SMTP-сервера или перенаправителя.  
  
4.  Сохраните файл.  
  
  
  
##  <a name="configuration-options-for-remote-smtp-service"></a><a name="bkmk_options_remote_SMTP"></a>Параметры конфигурации для удаленной службы SMTP  
 Соединение между сервером отчетов и локальным SMTP-сервером или перенаправителем определяется следующими параметрами конфигурации:  
  
-   `SendUsing` указывает метод отправки сообщений. Возможен выбор между сетевой службой SMTP или локальным каталогом сбора службы SMTP. Чтобы использовать удаленную SMTP-службу, этому параметру в файле конфигурации RSReportServer.config должно быть присвоено значение **2** .  
  
-   `SMTPServer` указывает удаленный сервер или перенаправитель SMTP. Это значение обязательное, если нужно использовать удаленный сервер или перенаправитель SMTP.  
  
-   `From`задает значение, отображаемое в строке **от:** сообщения электронной почты. Это значение обязательное, если нужно использовать удаленный сервер или перенаправитель SMTP.  
  
 Другие значения, которые используются для удаленной службы SMTP, включают следующее (обратите внимание, что указывать их необязательно, если не нужно заменять ими значения по умолчанию).  
  
-   Параметр**SMTPServerPort** настроен для использования порта 25.  
  
-   Параметр**SMTPAuthenticate** указывает, как сервер отчетов подключается к удаленному SMTP-серверу. Значение по умолчанию равно 0 (отсутствие проверки подлинности). В этом случае соединение осуществляется через анонимный доступ. Может потребоваться, чтобы сервер отчетов и SMTP-сервер были элементами одного домена (в зависимости от конфигурации домена).  
  
     Для отправки электронной почты в списки рассылки с ограничениями (например, в списки рассылки, принимающие входящие сообщения только от учетных записей, прошедших проверку подлинности) установите значение **SMTPAuthenticate** равным **2**.  
  

  
##  <a name="configuration-options-for-local-smtp-service"></a><a name="bkmk_options_local_SMTP"></a>Параметры конфигурации для локальной службы SMTP  
 Настройка локальной службы SMTP полезна при тестировании или диагностике работы с электронной почтой сервера отчетов. Локальная служба SMTP по умолчанию отключена. Инструкции по включению см. в разделе [Настройка сервера отчетов для доставки электронной почты (SSRS Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) и [параметров электронной почты — Configuration Manager &#40;служб SSRS в основном режиме&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).  
  
 Соединение между сервером отчетов и локальным сервером или перенаправителем SMTP определяется следующими параметрами конфигурации:  
  
-   `SendUsing` получает значение **1**.  
  
-   В качестве значения**SMTPServerPickupDirectory** указана папка на локальном жестком диске.  
  
    > [!NOTE]  
    >  Убедитесь, что параметр не задан, `SMTPServer` Если используется локальный SMTP-сервер.  
  
-   `From`задает значение, отображаемое в строке **от:** сообщения электронной почты. Это значение обязательно.  
  
 
  
##  <a name="to-configure-report-server-e-mail-using-the-reporting-services-configuration-manager"></a><a name="bkmk_use_configuration_manager"></a>Настройка электронной почты сервера отчетов с помощью диспетчер конфигурации служб Reporting Services  
  
1.  Убедитесь, что у службы Windows сервера отчетов есть разрешения `Send As` на SMTP-сервере.  
  
2.  Запустите диспетчер конфигурации служб Reporting Services и подключитесь к экземпляру сервера отчетов.  
  
3.  На странице «Настройки электронной почты» введите имя SMTP-сервера. Это значение может быть IP-адресом, UNC-именем компьютера в корпоративной сети или полным доменным именем.  
  
4.  В поле **Адрес отправителя**введите имя учетной записи, имеющей разрешение на отправку электронной почты с SMTP-сервера.  
  
5.  Щелкните **Применить**.  
  

  
##  <a name="to-configure-a-remote-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_remote_SMTP"></a>Настройка удаленной службы SMTP для сервера отчетов  
  
1.  Убедитесь, что у службы Windows сервера отчетов есть разрешения `Send As` на SMTP-сервере.  
  
2.  Откройте файл RSReportServer.config в текстовом редакторе.  
  
3.  Убедитесь, что `UrlRoot` для параметра <> задан URL-адрес сервера отчетов. Это значение устанавливается при настройке сервера отчетов так, что оно должно быть уже заполнено. Если оно не установлено, введите URL-адрес сервера отчетов.  
  
4.  В разделе Доставка найдите <`ReportServerEmail`>.  
  
5.  В <`SMTPServer`> введите имя SMTP-сервера. Это значение может быть IP-адресом, UNC-именем компьютера в корпоративной сети или полным доменным именем.  
  
6.  Убедитесь, что `SendUsing` для параметра <> задано значение 2. Если задано другое значение, сервер отчетов не настроен для использования удаленной службы SMTP.  
  
7.  В <`From`> введите имя учетной записи, имеющей разрешение на отправку электронной почты с SMTP-сервера.  
  
8.  Сохраните файл.  
  
     Сервер отчетов автоматически будет использовать новые настройки; нет необходимости перезапускать службу. Можно указать дополнительные настройки SMTP для последующей конфигурации использования SMTP-сервера для доставки электронной почты на сервер отчетов. Дополнительные сведения см. в статье [Configurэлектронной документации поg a Report Server for E-Mail Delivery](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) и [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onlэлектронной документации поe.  
  

  
##  <a name="to-configure-a-local-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_local_SMTP"></a>Настройка локальной службы SMTP для сервера отчетов  
  
1.  На панели управления выберите **Установка и удаление программ**.  
  
2.  Выберите пункт **Установка компонентов Windows** , чтобы запустить мастер компонентов Windows.  
  
3.  Выберите пункт **Сервер приложений** и нажмите кнопку **Подробности**.  
  
4.  Выберите пункт **службы IIS** и нажмите кнопку **Подробности**.  
  
5.  Установите флажок **Служба SMTP** и нажмите кнопку **ОК**.  
  
6.  В мастере компонентов Windows нажмите кнопку **Далее**. Нажмите кнопку **Готово**.  
  
7.  Убедитесь в том, что служба запущена, в консоли **Службы** .  
  
8.  Откройте файл **RSReportServer.config** в текстовом редакторе.  
  
9. Убедитесь, что параметр `<UrlRoot>` настроен на URL-адрес сервера отчетов. Это значение устанавливается при настройке сервера отчетов так, что оно должно быть уже заполнено. Если оно не установлено, введите URL-адрес сервера отчетов.  
  
10. В разделе Delivery найдите параметр `<ReportServerEmail>.`  
  
11. В `<SMTPServer>`удалите значения параметра, но не удаляйте теги.  
  
12. Присвойте параметру `<SendUsing>` значение 1. Если задано другое значение, сервер отчетов не настроен для использования локальной службы SMTP.  
  
13. В качестве значения `<SMTPServerPickupDirectory>` задайте папку на локальном жестком диске.  
  
14. В качестве значения параметра `<From>` укажите учетную запись, имеющей разрешение на отправку электронной почты с SMTP-сервера.  
  
15. Сохраните файл.  
  
 
  
## <a name="see-also"></a>См. также:  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
