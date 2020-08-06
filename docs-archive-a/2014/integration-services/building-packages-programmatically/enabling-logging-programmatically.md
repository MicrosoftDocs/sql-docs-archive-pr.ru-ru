---
title: Программное включение ведения журнала | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- Integration Services packages, logs
- SSIS logging
- log providers [Integration Services]
- logs [Integration Services], enabling
- LoggingMode property
- LogProvider object
- packages [Integration Services], logs
ms.assetid: 3222a1ed-83eb-421c-b299-a53b67bba740
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff7f81aca330960e4e94b0343080a37ded8c1273
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731977"
---
# <a name="enabling-logging-programmatically"></a>Программное включение ведения журнала
  Ядро выполнения предоставляет коллекцию объектов <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider>, которые позволяют перехватывать во время проверки и выполнения пакета сведения, относящиеся к конкретному событию. Объекты <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> доступны для объектов <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer>, включая объекты <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, <xref:Microsoft.SqlServer.Dts.Runtime.Package>, <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop> и <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>. Ведение журналов включается для индивидуальных контейнеров или пакета в целом.

 Существует несколько типов регистраторов, которые может использовать контейнер. Это повышает гибкость, позволяя создавать и сохранять сведения журнала во многих форматах. Включение журналирования для объекта-контейнера выполняется в два этапа: сначала включается ведение журнала, а потом выбирается регистратор журнала. Свойства контейнера <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> используются для указания записываемых в журнал событий и выбора регистратора.

## <a name="enabling-logging"></a>Включение журнала
 Свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A>, имеющееся у каждого контейнера, который может осуществлять ведение журнала, определяет, записывается ли информация о событиях контейнера в журнал событий. Этому свойству назначается значение из структуры <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>. По умолчанию оно наследуется от родительского контейнера. Если контейнер является пакетом и, следовательно, не имеет родителя, свойство использует значение <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>, которое по умолчанию равно `Disabled`.

### <a name="selecting-a-log-provider"></a>Выбор регистратора
 После того как свойству <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> присвоено значение `Enabled`, регистратор добавляется в коллекцию контейнера <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> для завершения процесса. Коллекция <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> доступна через объект <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> и содержит регистраторы, выбранные для данного контейнера. Метод <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> вызывается для создания регистратора и добавления его в коллекцию. После этого метод возвращает регистратор, добавленный в коллекцию. Каждый регистратор имеет уникальные параметры настройки, которые устанавливаются с помощью свойства <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A>.

 В следующей таблице перечислены доступные регистраторы и приведено их описание и значения их свойства <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A>.

|Поставщик|Description|Свойство ConfigString|
|--------------|-----------------|---------------------------|
|Приложение SQL Server Profiler|Создает трассировки SQL, которые могут перехватываться и просматриваться в приложении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler. По умолчанию для имени файла данного регистратора используется расширение TRC.|Настройка не требуется.|
|SQL Server|Записывает записи журнала событий в таблицу **sysssislog** любой базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Регистратор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требует указания соединения с базой данных, а также имени базы данных-получателя.|
|Текстовый файл|Записывает записи журнала событий в текстовые файлы в ASCII-кодировке в формате CSV (с разделителями-запятыми). По умолчанию для имени файла для данного регистратора используется расширение LOG.|Имя диспетчера соединения файлов.|
|Журнал событий Windows|Сохраняет журнальные записи в стандартном журнале событий Windows.|Настройка не требуется.|
|XML-файл|Записывает записи журнала событий в файл в формате XML. По умолчанию для имени файла данного регистратора используется расширение XML.|Имя диспетчера соединения файлов.|

 События включаются в журнал событий или исключаются из него путем задания свойств контейнера `EventFilterKind` и `EventFilter`. Структура `EventFilterKind` содержит два значения, `ExclusionFilter` и `InclusionFilter`, которые указывают, включаются ли в журнал событий события, добавленные в фильтр `EventFilter`. После этого свойству `EventFilter` назначается строковый массив, содержащий имена событий, подлежащих фильтрации.

 Следующий код включает ведение журнала для пакета, добавляет регистратор для текстовых файлов в коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> и указывает список событий, которые должны включаться в выход журнала.

## <a name="sample"></a>Образец

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Package p = new Package();

      ConnectionManager loggingConnection = p.Connections.Add("FILE");
      loggingConnection.ConnectionString = @"C:\SSISPackageLog.txt";

      LogProvider provider = p.LogProviders.Add("DTS.LogProviderTextFile.2");
      provider.ConfigString = loggingConnection.Name;
      p.LoggingOptions.SelectedLogProviders.Add(provider);
      p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion;
      p.LoggingOptions.EventFilter = new String[] { "OnPreExecute", 
         "OnPostExecute", "OnError", "OnWarning", "OnInformation" };
      p.LoggingMode = DTSLoggingMode.Enabled;

      // Add tasks and other objects to the package.

    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim p As Package = New Package()

    Dim loggingConnection As ConnectionManager = p.Connections.Add("FILE")
    loggingConnection.ConnectionString = "C:\SSISPackageLog.txt"

    Dim provider As LogProvider = p.LogProviders.Add("DTS.LogProviderTextFile.2")
    provider.ConfigString = loggingConnection.Name
    p.LoggingOptions.SelectedLogProviders.Add(provider)
    p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion
    p.LoggingOptions.EventFilter = New String() {"OnPreExecute", _
       "OnPostExecute", "OnError", "OnWarning", "OnInformation"}
    p.LoggingMode = DTSLoggingMode.Enabled

    ' Add tasks and other objects to the package.

  End Sub

End Module
```

![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.

## <a name="see-also"></a>См. также:
 [Ведение журналов в службах Integration Services (SSIS)](../performance/integration-services-ssis-logging.md)


