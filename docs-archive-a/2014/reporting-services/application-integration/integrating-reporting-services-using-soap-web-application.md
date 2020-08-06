---
title: Использование API SOAP в веб-приложении | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e228f01915df633f50b23bf93e892446863c28ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729149"
---
# <a name="using-the-soap-api-in-a-web-application"></a>Использование API SOAP в веб-приложении
  С помощью API SOAP служб Reporting Services можно получить доступ ко всем функциональным возможностям сервера отчетов. Поскольку API SOAP является веб-службой, к нему легко получить доступ, чтобы предоставить для пользовательских бизнес-приложений функции создания отчетов в масштабе предприятия. Доступ к веб-службе сервера отчетов из веб-приложения осуществляется во многом аналогично доступу к API SOAP из приложения [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. С помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] можно создать класс-посредник, который предоставляет доступ к свойствам и методам веб-службы сервера отчетов и позволяет использовать знакомую инфраструктуру и средства для создания бизнес-приложений на основе [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] технологий.  
  
 Функции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по управлению отчетами доступны из веб-приложения так же легко, как из приложения Windows. Из веб-приложения можно добавлять элементы в базу данных сервера отчетов и удалять из нее элементы, задавать параметры безопасности элемента, изменять элементы базы данных сервера отчетов, управлять планированием и доставкой, а также выполнять другие действия.  
  
## <a name="enabling-impersonation"></a>Включение олицетворения  
 Первым шагом в настройке веб-приложения является включение олицетворения со стороны клиента веб-службы. Олицетворение позволяет приложениям [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] выполняться с удостоверением клиента, от имени которого они работают. [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] с помощью служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS проверяет подлинность пользователя и передает в приложение [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] проверенный токен или (если не удалось проверить подлинность пользователя) непроверенный токен. Если включено олицетворение, приложение [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] в любом случае выполняет олицетворение любого полученного токена. Можно включить олицетворение на клиенте, изменив файл Web.config клиентского приложения следующим образом:  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  По умолчанию олицетворение отключено.  
  
 Дополнительные сведения об [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] олицетворении см [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . в документации по пакету SDK.  
  
## <a name="managing-the-report-server-using-soap-api"></a>Управление сервером отчетов с помощью API SOAP  
 С помощью веб-приложения также можно управлять сервером отчетов и его содержимым. Диспетчер отчетов, входящий в состав служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], служит примером веб-приложения, которое целиком построено с помощью [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] и API SOAP служб Reporting Services. Можно добавить функции управления отчетами, доступные в диспетчере отчетов, в пользовательские веб-приложения. Например, может потребоваться возвратить список доступных отчетов в базе данных сервера отчетов и отображать их в [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` элементе управления для выбора пользователями. В следующем коде устанавливается соединение с базой данных сервера отчетов и возвращается список элементов в базе данных сервера отчетов. Затем доступные отчеты добавляются в элемент управления Listbox, в котором отображается путь к каждому отчету.  
  
```vb  
Private Sub Page_Load(sender As Object, e As System.EventArgs)  
   ' Create a Web service proxy object and set credentials  
   Dim rs As New ReportingService2005()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return a list of catalog items in the report server database  
   Dim items As CatalogItem() = rs.ListChildren("/", True)  
  
   ' For each report, display the path of the report in a Listbox  
   Dim ci As CatalogItem  
   For Each ci In  items  
      If ci.Type = ItemTypeEnum.Report Then  
         catalogListBox.Items.Add(ci.Path)  
      End If  
   Next ci  
End Sub ' Page_Load   
```  
  
```csharp  
private void Page_Load(object sender, System.EventArgs e)  
{  
   // Create a Web service proxy object and set credentials  
   ReportingService2005 rs = new ReportingService2005();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return a list of catalog items in the report server database  
   CatalogItem[] items = rs.ListChildren("/", true);  
  
   // For each report, display the path of the report in a Listbox  
   foreach(CatalogItem ci in items)  
   {  
      if (ci.Type == ItemTypeEnum.Report)  
         catalogListBox.Items.Add(ci.Path);  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Интеграция Reporting Services в приложения](../application-integration/integrating-reporting-services-into-applications.md)   
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](../report-manager-ssrs-native-mode.md)   
 [Использование API SOAP в приложении Windows](integrating-reporting-services-using-soap-windows-application.md)  
  
  
