---
title: Включение отслеживания удаленных ошибок (службы Reporting Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- remote data source [Reporting Services]
- EnableRemoteError server property
ms.assetid: 5f05022b-d557-43e0-b50a-f5e2a1846b83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d2a7e7e0b38b38bf563dfc2a8cff65c897c5293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665795"
---
# <a name="enable-remote-errors-reporting-services"></a>Включение отслеживания удаленных ошибок (службы Reporting Services)
  Можно задать свойства сервера на сервере отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , чтобы возвращались дополнительные сведения об ошибках, возникающих на удаленных серверах. Если сообщение об ошибке содержит текст «Чтобы получить дополнительные сведения об этой ошибке, перейдите к серверу отчетов на локальном сервере или включите отслеживание удаленных ошибок», то можно задать свойство `EnableRemoteErrors`, чтобы получить доступ к дополнительным сведениям, которые могут помочь в устранении возникшей неполадки. Дополнительные сведения см. в разделе [Системные свойства сервера отчетов](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **В этом разделе:**  
  
-   [Включение отслеживания удаленных ошибок для режима SharePoint](#bkmk_sharepoint)  
  
-   [Включение отслеживания удаленных ошибок в среде SQL Server Management Studio (собственный режим)](#bkmk_mgtStudio)  
  
-   [Включение отслеживания удаленных ошибок с помощью скрипта (собственный режим)](#bkmk_script)  
  
-   [Изменение таблицы ConfigurationInfo (собственный режим)](#bkmk_ConfigurationInfo)  
  
##  <a name="enable-remote-errors-for-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> Включение отслеживания удаленных ошибок для режима SharePoint  
 Существуют две различные процедуры для включения отслеживания удаленных ошибок для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме совместимости с SharePoint. Процедуры для двух разных архитектур сервера отчетов отличаются. В выпуске [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] была представлена новая архитектура, основанная на службах SharePoint. В ней используются настройки, которые могут быть изменены для каждого приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Прежняя архитектура использовала общие настройки на уровне веб-сайта.  
  
#### <a name="enable-remote-errors-for-a-reporting-services-service-application"></a>Включение отслеживания удаленных ошибок для приложения службы Reporting Services  
  
1.  Для сервера отчетов в режиме интеграции с SharePoint, установленном с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или обновленной версией [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], включите настройку приложения службы **Включение удаленного контроля ошибок**. Настройка может быть изменена для каждого приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  В центре администрирования SharePoint в разделе **Управление приложениями** выберите **Управление приложениями служб** .  
  
3.  Найдите нужное приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и щелкните его название.  
  
4.  Нажмите кнопку **Системные параметры**.  
  
5.  В разделе **Безопасность** нажмите кнопку **Включить отслеживание удаленных ошибок** .  
  
6.  Нажмите кнопку **ОК**.  
  
#### <a name="enable-remote-errors-for-a-sharepoint-site"></a>Включение отслеживания удаленных ошибок для сайта SharePoint  
  
1.  Для сервера отчетов в режиме интеграции с SharePoint, установленном с версией [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], включите настройку сайта **Включение удаленного контроля ошибок в локальном режиме**.  
  
2.  В области **Действия сайта** выберите **Настройки сайта** для сайта, который необходимо изменить.  
  
3.  Выберите **Настройки сайта служб Reporting Services** в группе **Reporting Services** .  
  
4.  Выберите **Включить отслеживание удаленных ошибок в локальном режиме**.  
  
5.  Нажмите кнопку **ОК**.  
  
##  <a name="enable-remote-errors-through-sql-server-management-studio-native-mode"></a><a name="bkmk_mgtStudio"></a> Включение отслеживания удаленных ошибок в среде SQL Server Management Studio (собственный режим)  
  
1.  Запустите среду Management Studio и соединитесь с экземпляром сервера отчетов. Дополнительные сведения см. в разделе [Подключение к серверу отчетов в среде Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Щелкните правой кнопкой мыши узел сервера отчетов и выберите пункт **Свойства**.  
  
3.  Нажмите кнопку **Дополнительно** , чтобы открыть страницу свойств. Дополнительные сведения см. в разделе [Свойства сервера (страница "Дополнительно") — службы Reporting Services](../tools/server-properties-advanced-page-reporting-services.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  В `EnableRemoteErrors` выберите `True` .  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="enable-remote-errors-through-script-native-mode"></a><a name="bkmk_script"></a> Включение отслеживания удаленных ошибок с помощью скрипта (собственный режим)  
  
1.  Создайте текстовый файл и скопируйте в него следующий скрипт.  
  
    ```  
    Public Sub Main()  
      Dim P As New [Property]()  
      P.Name = "EnableRemoteErrors"  
      P.Value = True  
      Dim Properties(0) As [Property]  
      Properties(0) = P  
      Try  
        rs.SetSystemProperties(Properties)  
        Console.WriteLine("Remote errors enabled.")  
      Catch SE As SoapException  
        Console.WriteLine(SE.Detail.OuterXml)  
      End Try  
    End Sub  
    ```  
  
2.  Сохраните файл с именем EnableRemoteErrors.rss.  
  
3.  Нажмите кнопку **Пуск**, укажите команду **Выполнить**, введите **cmd**и нажмите кнопку **ОК** , чтобы открыть окно командной строки.  
  
4.  Перейдите к каталогу, содержащему только что созданный файл RSS.  
  
5.  Введите в командной строке следующую команду, заменив местозаполнитель *имя_сервера* реальным именем сервера:  
  
    ```  
    rs -i EnableRemoteErrors.rss -s http://servername/ReportServer  
    ```  
  
6.  Дополнительные сведения см. в разделе [Программа RS.exe (SSRS)](../tools/rs-exe-utility-ssrs.md).  
  
##  <a name="modifying-the-configurationinfo-table-native-mode"></a><a name="bkmk_ConfigurationInfo"></a> Изменение таблицы ConfigurationInfo (собственный режим)  
  
1.  > [!NOTE]  
    >  Можно изменить таблицу **ConfigurationInfo** в базе данных сервера отчетов, чтобы задать `EnableRemoteErrors` для значение `True` , но если сервер отчетов используется активно, следует использовать SQL Server Management Studio или сценарий для изменения параметров. При изменении настроек базы данных необходимо перезапустить службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , чтобы изменения вступили в силу.  
  
  
