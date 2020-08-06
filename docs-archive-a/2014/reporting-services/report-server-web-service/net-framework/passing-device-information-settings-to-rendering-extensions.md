---
title: Передача параметров сведений об устройстве для модулей подготовки отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea50de3955ab152cbd92d5fd50ef8b2281a67eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730130"
---
# <a name="passing-device-information-settings-to-rendering-extensions"></a>Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру
  В службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]настройки сведений об устройстве используются для передачи параметров подготовки к просмотру модуля подготовки отчетов. Настройки веб-службы сервера отчетов передаются как XML-элемент **DeviceInfo** и обрабатываются сервером отчетов. Поскольку у настроек сведений об устройстве есть значения по умолчанию, в процессе подготовки к просмотру эти аргументы являются необязательными. Однако настройки сведений об устройстве можно использовать для настройки процесса подготовки к просмотру и переопределения значений по умолчанию, передаваемых сервером.  
  
 Настройки сведений об устройстве можно задавать различными способами. Для задания программным путем можно использовать метод Render. Если доступ к отчету осуществляется по URL-адресу, сведения об устройстве можно задать как параметры URL-адреса. Можно также редактировать настройки сведений об устройстве в файлах конфигурации служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] , чтобы задать глобальные значения параметров подготовки к просмотру. Дополнительные сведения об указании глобальных параметров подготовки отчетов см. в разделе [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
## <a name="passing-device-information-using-the-render-method"></a>Передача сведений об устройстве с помощью метода Render  
 Для передачи сведений об устройстве в модуль подготовки отчетов используется метод <xref:ReportExecution2005.ReportExecutionService.Render%2A>. Например, при подготовке к просмотру в формате HTML методу <xref:ReportExecution2005.ReportExecutionService.Render%2A> можно передать следующую строку в формате XML для создания фрагмента HTML:  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 При подготовке отчета в виде фрагмента HTML содержимое отчета находится в элементе TABLE, а элементы HTML и BODY не используются. Фрагмент HTML можно использовать для внедрения отчета в существующий HTML-документ. Дополнительные сведения о параметрах сведений об устройстве для вывода в формате HTML см. в разделе [Настройки сведений об устройстве HTML](../../html-device-information-settings.md).  
  
## <a name="passing-device-information-using-url-access"></a>Передача сведений об устройстве с помощью доступа через URL-адрес  
 Настройки сведений об устройстве можно также передать с помощью доступа по URL-адресу. Настройки сведений об устройстве передаются как параметры URL-адреса. Чтобы создать готовый для просмотра отчет без панели инструментов средства просмотра HTML-страниц, можно передать серверу отчетов следующую строку доступа к URL-адресу:  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 Дополнительные сведения см. в разделе [Указание настроек сведений об устройстве в URL-адресе](../../specify-device-information-settings-in-a-url.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройки сведений об устройстве для модулей подготовки отчетов &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md)   
 [Настройка параметров модуля подготовки отчетов в RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
