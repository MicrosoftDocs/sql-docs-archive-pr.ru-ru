---
title: Вызов и определение событий в компоненте потока данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25f4572f8a8af829145da4e4d685f5dddad4a29a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729642"
---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a>Вызов и определение событий в компоненте потока данных
  Разработчики компонентов могут создавать подмножество событий, определенных в интерфейсе <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>, вызывая методы, доступ к которым определяется свойством <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. Можно также определять пользовательские события, используя коллекцию <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>, и создавать эти события с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>. В данном разделе описывается разработка и вызов событий, а также содержатся рекомендации по вызову событий во время разработки.

## <a name="raising-events"></a>Вызов событий
 Компоненты вызывают события с помощью методов **Fire\<X>** интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. События можно вызывать во время разработки и во время выполнения компонента. Обычно во время разработки методы <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> вызываются в процессе проверки компонента. Эти события выводят сообщения на панели **Список ошибок** среды [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] и обеспечивают отзыв для пользователей компонента в случаях, когда он неправильно настроен.

 Компоненты могут также вызывать события в любой момент во время выполнения. События позволяют разработчикам компонента предоставлять отзыв пользователям компонента в процессе его работы. Вызов метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> во время выполнения, скорее всего, приведет к аварийному завершению работы всего пакета.

## <a name="defining-and-raising-custom-events"></a>Определение и вызов пользовательских событий

### <a name="defining-a-custom-event"></a>Разработка пользовательского события
 Пользовательские события создаются с помощью метода <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>. Эта коллекция создается задачей потока данных и предоставляется разработчику компонента как свойство через базовый класс <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Этот класс содержит пользовательские события, определенные задачей потока данных, и пользовательские события, определенные компонентом с помощью вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>.

 Пользовательские события компонента не сохраняются в коде XML пакета. Поэтому метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> вызывается и во время разработки, и во время выполнения, чтобы компонент мог определить события, которые вызывает.

 Параметр *allowEventHandlers* метода <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> указывает, позволяет ли компонент создавать для этого события объекты <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>. Следует заметить, что объекты <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> являются синхронными. Поэтому компонент не возобновляет выполнение, пока объект <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>, принадлежащий пользовательскому событию, не закончил работу. Если параметр *allowEventHandlers* имеет значение `true` , каждый параметр события автоматически становится доступным для всех <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> объектов через переменные, создаваемые и заполняемые автоматически [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] средой выполнения.

### <a name="raising-a-custom-event"></a>Вызов пользовательского события
 Компоненты вызывают пользовательские события с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>, передавая ему имя, текст и параметры события. Если параметр *allowEventHandlers* имеет значение `true` , то все <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> , что создается для пользовательского события, выполняется [!INCLUDE[ssIS](../../../includes/ssis-md.md)] подсистемой среды выполнения.

### <a name="custom-event-sample"></a>Образец пользовательского события
 Следующий пример кода демонстрирует компонент, который определяет пользовательское событие с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>, а затем вызывает это событие во время выполнения с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>.

```csharp
public override void RegisterEvents()
{
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref parameterTypes, ref parameterDescriptions);
}
public override void ProcessInput(int inputID, PipelineBuffer buffer)
{
    while (buffer.NextRow())
    {
       // Process buffer rows.
    }

    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);
}
```

```vb
Public  Overrides Sub RegisterEvents() 
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"} 
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)} 
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."} 
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, parameterTypes, parameterDescriptions) 
End Sub 

Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer) 
  While buffer.NextRow 
  End While 
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort") 
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now} 
  ComponentMetaData.FireCustomEvent("StartingSort", _
    "Beginning sort operation.", arguments, _
    ComponentMetaData.Name, FireSortEventAgain) 
End Sub
```

![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.

## <a name="see-also"></a>См. также:
 [Integration Services &#40;служб SSIS&#41; обработчики событий](../../integration-services-ssis-event-handlers.md) [Добавление обработчика событий в пакет](../../add-an-event-handler-to-a-package.md)


