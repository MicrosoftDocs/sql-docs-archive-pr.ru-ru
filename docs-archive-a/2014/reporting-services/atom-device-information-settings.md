---
title: Настройки сведений об устройстве ATOM | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdbac1500063accf868d4b538b82ba9f3b5aebb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664036"
---
# <a name="atom-device-information-settings"></a>Настройки сведений об устройстве ATOM
  Настройки сведений об устройстве для модуля подготовки отчетов Atom включают параметры отправки имени веб-канала Atom и используемую кодировку.  
  
 В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в документе службы данных.  
  
|Параметр|Значение|  
|-------------|-----------|  
|`DataFeed`|Если указано, веб-канал Atom подготавливается к просмотру в соответствии с именем канала, указанным в этой настройке. В противном случае производится подготовка к просмотру сервисного документа Atom для отчета. Уникальный автоматически сформированный идентификатор канала данных. Это значение используется для внутренних целей и не подлежит изменению.|  
|**Кодирование**|Определенное комитетом по цифровым адресам в Интернете (IANA) название кодировки символов, поддерживаемой платформой .NET Framework. Значение по умолчанию — `UTF-8`. В качестве примеров других значений можно привести ASCII, UTF-7 и UTF-16.|  
  
## <a name="see-also"></a>См. также:  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве в модули подготовки отчетов](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модуля подготовки отчетов в RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
