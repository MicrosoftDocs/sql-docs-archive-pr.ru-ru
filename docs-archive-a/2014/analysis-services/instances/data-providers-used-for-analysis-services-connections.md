---
title: Поставщики данных, используемые для подключений Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36eacdfc9f4b3469ed28d7dc622c60ceb78ec5f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731078"
---
# <a name="data-providers-used-for-analysis-services-connections"></a>Поставщики данных, используемые для соединений со службами Analysis Services
  Службы Analysis Services предоставляют 3 поставщика данных для сервера и доступа к данным. Все приложения подключаются к службам Analysis Services с помощью одного из следующих поставщиков. Два из этих поставщиков, ADOMD.NET и управляющие объекты AMO служб Analysis Services, — управляемые поставщики данных. Поставщик OLE DB для служб Analysis Services (MSOLAP DLL) является собственным поставщиком данных.  
  
 В организациях, где работает несколько версий служб Analysis Services, может потребоваться установка более свежих версий поставщиков данных на пользовательских рабочих станциях, подключающихся к данным служб Analysis Services. Для подключения к более новым версиям служб Analysis Services необходимы поставщики данных из того же основного выпуска. Например, для подключения к службам [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]на каждой рабочей станции должен быть поставщик данных из выпуска 2014. Несмотря на то что Excel устанавливает поставщиков данных, которые нужны программе для подключения, поставщик часто имеет более старую версию по сравнению с используемыми экземплярами служб Analysis Services.  
  
 Этот раздел состоит из следующих подразделов:  
  
 [Как определить версию сервера](#bkmk_ServVers)  
  
 [Как определить версию поставщиков данных служб Analysis Services](#bkmk_LibUpdate)  
  
 [Получение обновленной версии поставщиков данных](#bkmk_downloadsite)  
  
 [Поставщик OLE DB служб Analysis Services](#bkmk_OLE)  
  
 [ADOMD.NET](#bkmk_ADOMD)  
  
 [Объекты AMO](#blkmk_AMO)  
  
##  <a name="how-to-determine-server-version"></a><a name="bkmk_ServVers"></a>Как определить версию сервера  
 Сведения о версии экземпляра служб Analysis Services позволяют определить, нужно ли устанавливать более новые версии поставщиков данных на рабочих станциях в организации.  
  
-   Установите соединение с экземпляром служб Analysis Services в среде SQL Server Management Studio. Щелкните правой кнопкой мыши экземпляр, который необходимо проверить, выберите пункт **отчеты**и щелкните **Общие**. В отчете будут приведены сведения о выпуске и сборке.  
  
 Номер основной сборки первоначального выпуска [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] — 12.0.2000.9.  
  
 Дополнительные сведения о получении данных о версии и сборке см. в разделе [Определение версий и выпусков SQL Server и его компонентов](https://support.microsoft.com/kb/321185).  
  
##  <a name="how-to-determine-the-version-of-the-analysis-services-data-providers"></a><a name="bkmk_LibUpdate"></a>Как определить версию поставщиков данных Analysis Services  
 Поставщики данных устанавливаются со службами Analysis Services, а также клиентскими приложениями, которые регулярно подключаются к базам данных служб Analysis Services, таким как Excel.  
  
 Office 2007 устанавливает поставщики данных из SQL Server 2005. Office 2010 устанавливает поставщики данных из SQL Server 2008. Office 2013 устанавливает поставщиков данных из SQL Server 2012. Если используется несколько версий Office или SQL Server, а доступность соединений или функций не соответствует ожиданиям, то, по-видимому, необходимо установить более новую версию поставщиков данных. На одном компьютере можно одновременно установить несколько основных версий каждого поставщика данных.  
  
#### <a name="find-the-file-version-of-the-oledb-provider"></a>Определение версии поставщика OLEDB  
  
1.  Перейдите в каталог «\Program Files\Microsoft Analysis Services\AS OLEDB\120».  
  
2.  Щелкните правой кнопкой мыши msolap120.dll и выберите пункт **Свойства**.  
  
 Если в этом местоположении нет файла либо если в пути к папке содержится «AS OLEDB\110» или «AS OLEDB\90», то используется старая библиотека и для подключения к [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]необходимо установить более новую версию (AS OLEDB\11).  
  
#### <a name="find-the-file-version-of-adomdnet-and-amo"></a>Определение версии ADOMD.NET и объектов AMO  
  
1.  Перейдите к папке «C:\Windows\Assembly»  
  
2.  Щелкните правой кнопкой мыши файл Microsoft.AnalysisServices.AdomdClient и выберите **Свойства**. Нажмите **Версия**.  
  
     Применительно к объектам AMO щелкните правой кнопкой мыши Microsoft.AnalysisServices.  
  
 Дополнительные сведения о номерах версий и выпусков см. в разделе [Сборки SQL Server на сайте Blogspot](http://sqlserverbuilds.blogspot.com).  
  
##  <a name="where-to-get-newer-version-data-providers"></a><a name="bkmk_downloadsite"></a>Где можно получить новые поставщики данных версии  
 Версия, установленная на клиентском компьютере, должна совпадать с основной версией сервера, поставляющего данные. Если установка сервера более новая, чем у поставщиков данных, установленных на рабочих станциях в сети, может потребоваться установить новые библиотеки.  
  
#### <a name="find-the-data-providers-on-the-download-site"></a>Поиск поставщиков данных на сайте загрузок  
  
1.  Перейдите в [центр загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkID=296473).  
  
2.  Разверните **инструкции по установке**.  
  
3.  Прокрутите страницу до раздела с компонентами служб Analysis Services. ADOMD.NET, поставщик OLE DB и объекты AMO находятся на втором, третьем и четвертом местах в списке. Каждая библиотека имеет 32- или 64-разрядную версию. Для серверов и новых рабочих станций, работающих под управлением 64-разрядной операционной системы, потребуется 64-разрядная версия.  
  
##  <a name="analysis-services-ole-db-provider"></a><a name="bkmk_OLE"></a>Поставщик Analysis Services OLE DB  
 Поставщик Analysis Services OLE DB — это собственный поставщик для подключения к базе данных Analysis Services. Как ADOMD.NET, так и объекты AMO косвенно используют MSOLAP, делегируя запросы соединений поставщику данных. Можно также вызвать поставщик OLE DB непосредственно из кода приложения, если требования к решению исключают использование управляемого API-интерфейса.  
  
 Поставщик Analysis Services OLE DB устанавливается автоматически программами установки SQL Server, Excel и других приложений, которые часто используются для осуществления доступа к базам данных служб Analysis Services. Его также можно установить вручную, загрузив поставщик из центра загрузки. По умолчанию поставщик находится в папке \Program Files\Microsoft Analysis Services. Поставщик должен быть установлен на любой рабочей станции, используемой для получения доступа к данным служб Analysis Services.  
  
 MSOLAP130.dll — это версия поставщика OLE DB служб Analysis Services, которая поставляется в составе [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. К другим более ранним версиям относятся MSOLAP10.dll (для SQL Server 2008 и 2008 R2) и MSOLAP90.dll (для SQL Server 2005).  
  
 Поставщики OLE DB часто указываются в строках подключения. В строке подключения Analysis Services используется другая номенклатура для ссылки на поставщик OLE DB: MSOLAP. \<version> . компоновки  
  
 MSOLAP.5.dll — это текущий поставщик Analysis Services OLE DB, устанавливаемый в составе Excel 2013. На рабочих станциях, где работают более старые версии Excel, часто можно найти предыдущие версии, например MSOLAP.4.dll или MSOLAP.3.dll. Для некоторых компонентов служб Analysis Services, таких как надстройка PowerPivot, требуются определенные версии поставщика OLE DB. Дополнительные сведения см. в разделе [Свойства строки подключения (службы Analysis Services)](connection-string-properties-analysis-services.md).  
  
##  <a name="adomdnet"></a><a name="bkmk_ADOMD"></a>ADOMD.NET  
 ADOMD.NET — управляемый поставщик данных, который используется для запроса данных из служб Analysis Services. Excel использует ADOMD.NET при подключении к определенному кубу служб Analysis Services. Строка подключения в Excel предназначена для подключения ADOMD.NET.  
  
 Компонент ADOMD.NET устанавливается программой установки SQL Server и используется клиентскими приложениями SQL Server для подключения к службам Analysis Services. Эта библиотека устанавливается в Office для поддержки подключения к данным из Excel. Как и в случае с другими поставщиками данных, входящими в состав SQL Server, если программист использует библиотеку в пользовательском коде, то может распространять ADOMD.NET самостоятельно. Можно также загрузить и установить ее вручную, чтобы получить более новую версию (см. подраздел [Как определить версию поставщиков данных служб Analysis Services](#bkmk_LibUpdate) этого раздела).  
  
 Для проверки информации о версии файла найдите ADOMD.NET в глобальном кэше сборок, где эта библиотека указана как `Microsoft.AnalysisServices.AdomdClient`.  
  
 При подключении к базе данных свойства строки подключения для всех трех библиотек во многом совпадают. Почти любая строка подключения, заданная для ADOMD.NET (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>), применима также для AMO и поставщика Analysis Services OLE DB. Дополнительные сведения см. в разделе [Свойства строки подключения (службы Analysis Services)](connection-string-properties-analysis-services.md).  
  
 Дополнительные сведения о подключении программным путем см. в разделе [Establishing Connections in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/connections-in-adomd-net).  
  
##  <a name="amo"></a><a name="blkmk_AMO"></a>AMO  
 Объекты AMO — это управляемый поставщик данных, используемый для администрирования сервера и определения данных. Например, объекты AMO используются в среде SQL Server Management Studio для подключения к службам Analysis Services.  
  
 Объекты AMO устанавливаются программой установки SQL Server и используются клиентскими приложениями SQL Server для подключения к службам Analysis Services. Можно также загрузить и установить объекты AMO вручную для применения в пользовательском коде (см. подраздел [Как определить версию поставщиков данных служб Analysis Services](#bkmk_LibUpdate) этого раздела). Объекты AMO можно найти в глобальном кэше сборок под названием `Microsoft.AnalysisServices`.  
  
 Соединение с помощью объектов AMO обычно является минимальным, состоящим из "Data Source = \<servername> ". Когда подключение будет установлено, этот API можно использовать для работы с коллекциями баз данных и основными объектами. SSDT и SSMS используют объекты AMO для подключения к экземпляру служб Analysis Services.  
  
 Дополнительные сведения о подключении программным путем см. в разделе [Programming AMO Fundamental Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-fundamental-objects).  
  
## <a name="see-also"></a>См. также:  
 [Подключение к службам Analysis Services](connect-to-analysis-services.md)  
  
  
