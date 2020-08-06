---
title: Вызов и определение событий в пользовательской задаче | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS events, custom
- status information [SQL Server], task events
- custom tasks [Integration Services], events
- SSIS custom tasks, events
- IDTSComponentEvents interface
- events [Integration Services], custom
- events [Integration Services], runtime
- custom events [Integration Services]
- SSIS events, runtime
- IDTSEvents interface
ms.assetid: e0898aa1-e90c-4c4e-99d4-708a76efddfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb41ee60543a05b6cf10b3acda43372e20288d13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666175"
---
# <a name="raising-and-defining-events-in-a-custom-task"></a>Вызов и определение событий в пользовательской задаче
  Обработчиком среды выполнения служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] предоставляется коллекция событий, обозначающих состояние обработки задачи в ходе ее проверки и выполнения. Интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> определяет эти события. Он передается задачам в качестве параметра методов <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A>.  
  
 Имеется также другой набор событий, определяемых интерфейсом <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents>, которые вызываются от имени задачи сервером задач <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>. Сервер задач <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> вызывает события, происходящие до и после проверки и выполнения, а задача вызывает события, происходящие непосредственно во время выполнения и проверки.  
  
## <a name="creating-custom-events"></a>Создание пользовательских событий  
 Разработчики пользовательских задач могут определять новые пользовательские события, создавая новый объект <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> в своей переопределенной реализации метода <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A>. После создания объект <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> добавляется в коллекцию `EventInfos` с помощью метода <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A>. Подпись метода <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> выглядит следующим образом:  
  
 `public void Add(string eventName, string description, bool allowEventHandlers, string[] parameterNames, TypeCode[] parameterTypes, string[] parameterDescriptions);`  
  
 В следующем образце кода демонстрируется метод `InitializeTask` пользовательской задачи при создании двух пользовательских событий и указании их свойств. Затем новые события добавляются в коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos>.  
  
 Первому событию присваивается имя *eventName* "**OnBeforeIncrement**" и описание *description* "**Fires after the initial value is updated**". (Срабатывает после обновления исходного значения.) Следующий параметр, имеющий значение `true`, указывает, что для обработки этого события разрешено создание контейнера обработчика событий. Обработчик событий представляет собой контейнер, обеспечивающий структуру пакета и службы для задач, как и другие контейнеры, например, пакет, Sequence, ForLoop и ForEachLoop. Если параметр *allowEventHandlers* имеет значение `true` , <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> для события создаются объекты. Любые параметры, определенные для события, становятся доступными для <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> в его коллекции <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.  
  
```csharp  
public override void InitializeTask(Connections connections,  
   VariableDispenser variables, IDTSInfoEvents events,  
   IDTSLogging log, EventInfos eventInfos,  
   LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
{  
    this.eventInfos = eventInfos;  
    string[] paramNames = new string[1];  
    TypeCode[] paramTypes = new TypeCode[1]{TypeCode.Int32};  
    string[] paramDescriptions = new string[1];  
  
    paramNames[0] = "InitialValue";  
    paramDescriptions[0] = "The value before it is incremented.";  
  
    this.eventInfos.Add("OnBeforeIncrement",   
      "Fires before the task increments the value.",  
      true,paramNames,paramTypes,paramDescriptions);  
    this.onBeforeIncrement = this.eventInfos["OnBeforeIncrement"];  
  
    paramDescriptions[0] = "The value after it has been incremented.";  
    this.eventInfos.Add("OnAfterIncrement",  
      "Fires after the initial value is updated.",  
      true,paramNames, paramTypes,paramDescriptions);  
    this.onAfterIncrement = this.eventInfos["OnAfterIncrement"];  
}  
```  
  
```vb  
Public Overrides Sub InitializeTask(ByVal connections As Connections, _  
ByVal variables As VariableDispenser, ByVal events As IDTSInfoEvents, _  
ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, _  
ByVal logEntryInfos As LogEntryInfos, ByVal refTracker As ObjectReferenceTracker)   
  
    Dim paramNames(0) As String  
    Dim paramTypes(0) As TypeCode = {TypeCode.Int32}  
    Dim paramDescriptions(0) As String  
  
    Me.eventInfos = eventInfos  
  
    paramNames(0) = "InitialValue"  
    paramDescriptions(0) = "The value before it is incremented."  
  
    Me.eventInfos.Add("OnBeforeIncrement", _  
      "Fires before the task increments the value.", _  
      True, paramNames, paramTypes, paramDescriptions)  
    Me.onBeforeIncrement = Me.eventInfos("OnBeforeIncrement")  
  
    paramDescriptions(0) = "The value after it has been incremented."  
    Me.eventInfos.Add("OnAfterIncrement", _  
      "Fires after the initial value is updated.", True, _  
      paramNames, paramTypes, paramDescriptions)  
    Me.onAfterIncrement = Me.eventInfos("OnAfterIncrement")  
  
End Sub  
```  
  
## <a name="raising-custom-events"></a>Вызов пользовательских событий  
 Пользовательские события вызываются с помощью метода <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>. В следующей строке кода вызывается пользовательское событие.  
  
```csharp  
componentEvents.FireCustomEvent(this.onBeforeIncrement.Name,  
   this.onBeforeIncrement.Description, ref arguments,  
   null, ref bFireOnBeforeIncrement);  
```  
  
```vb  
componentEvents.FireCustomEvent(Me.onBeforeIncrement.Name, _  
Me.onBeforeIncrement.Description, arguments, _  
Nothing,  bFireOnBeforeIncrement)  
```  
  
## <a name="sample"></a>Образец  
 В следующем примере демонстрируется задача, которая определяет пользовательское событие в методе `InitializeTask`, добавляет пользовательское событие в коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos>, а затем вызывает пользовательское событие при выполнении метода `Execute` посредством вызова метода <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>.  
  
```csharp  
[DtsTask(DisplayName = "CustomEventTask")]  
    public class CustomEventTask : Task  
    {  
        public override DTSExecResult Execute(Connections connections,   
          VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,  
           IDTSLogging log, object transaction)  
        {  
            bool fireAgain;  
            object[] args = new object[1] { "The value of the parameter." };  
            componentEvents.FireCustomEvent( "MyCustomEvent",   
              "Firing the custom event.", ref args,  
              "CustomEventTask" , ref fireAgain );  
            return DTSExecResult.Success;  
        }  
  
        public override void InitializeTask(Connections connections,  
          VariableDispenser variableDispenser, IDTSInfoEvents events,  
          IDTSLogging log, EventInfos eventInfos,  
          LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
        {  
            string[] names = new string[1] {"Parameter1"};  
            TypeCode[] types = new TypeCode[1] {TypeCode.String};  
            string[] descriptions = new string[1] {"Parameter description." };  
  
            eventInfos.Add("MyCustomEvent",  
             "Fires when my interesting event happens.",  
             true, names, types, descriptions);  
  
        }  
   }  
```  
  
```vb  
<DtsTask(DisplayName = "CustomEventTask")> _   
    Public Class CustomEventTask  
     Inherits Task  
        Public Overrides Function Execute(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser, _  
          ByVal componentEvents As IDTSComponentEvents, _  
          ByVal log As IDTSLogging, ByVal transaction As Object) _  
          As DTSExecResult  
  
            Dim fireAgain As Boolean  
            Dim args() As Object =  New Object(1) {"The value of the parameter."}  
  
            componentEvents.FireCustomEvent("MyCustomEvent", _  
              "Firing the custom event.", args, _  
              "CustomEventTask" ,  fireAgain)  
            Return DTSExecResult.Success  
        End Function  
  
        Public Overrides  Sub InitializeTask(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser,  
          ByVal events As IDTSInfoEvents,  
          ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, ByVal logEnTryInfos As LogEnTryInfos, ByVal refTracker As ObjectReferenceTracker)  
  
            Dim names() As String =  New String(1) {"Parameter1"}  
            Dim types() As TypeCode =  New TypeCode(1) {TypeCode.String}  
            Dim descriptions() As String =  New String(1) {"Parameter description."}  
  
            eventInfos.Add("MyCustomEvent", _  
              "Fires when my interesting event happens.", _  
              True, names, types, descriptions)  
  
        End Sub  
  
    End Class  
```  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Обработчики событий в службах Integration Services (SSIS)](../../integration-services-ssis-event-handlers.md)   
 [Добавление обработчика событий к пакету](../../add-an-event-handler-to-a-package.md)  
  
  
