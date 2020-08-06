---
title: Установка ADOMD.NET на серверах клиентского веб-интерфейса под управлением центра администрирования | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0d9f52bf612c4878a8dacd4f5acfdcc135ae115e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655546"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>Установка ADOMD.NET на веб-серверах, обслуживающих клиентские запросы, под управлением центра администрирования
  При установке PowerPivot для SharePoint в ферму с топологией центра администрирования без служб Excel или PowerPivot для SharePoint загрузите и установите клиентскую библиотеку Microsoft ADOMD.NET, если желаете иметь полный доступ к встроенным на панели управления PowerPivot отчетам. Некоторые отчеты с панели мониторинга используют ADOMD.NET для доступа к внутренним данным, предоставляющим сведения об обработке запросов PowerPivot и исправности сервера в ферме.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010  
  
 Для SharePoint 2013 поставщик включен в пакет дополнительных компонентов SQL Server. Сведения о загрузке spPowerPivot.msi см. в статье [пакет дополнительных компонентов Microsoft SQL Server 2014](https://www.microsoft.com/download/details.aspx?id=35577) .  
  
### <a name="download-and-install-the-client-library"></a>Загрузка и установка клиентской библиотеки  
  
1.  На [странице пакета дополнительных компонентов SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296473)найдите Microsoft ADOMD.NET.  
  
2.  Загрузите пакет x64 программы установки `SQL_AS_ADOMD.msi`.  
  
3.  Запустите MSI-файл, чтобы установить библиотеку.  
  
4.  По завершении установки сбросьте IIS. Откройте административную командную строку и введите команду **iisreset**.  
  
### <a name="verify-installation"></a>Проверка установки  
  
1.  Перейдите к папке Windows\Assembly.  
  
2.  Щелкните правой кнопкой мыши Microsoft. AnalysisServices. AdomdClient и выберите пункт **Свойства**.  
  
3.  Нажмите **Версия**.  
  
4.  Убедитесь, что версия включает 12,00.\<build number> и это описание — Microsoft. AnalysisService. AdomdClient.  
  
## <a name="see-also"></a>См. также:  
 [Панель мониторинга управления PowerPivot и данные об использовании](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data)  
  
  
