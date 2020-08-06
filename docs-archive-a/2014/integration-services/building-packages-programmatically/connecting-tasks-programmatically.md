---
title: Соединение задач программным образом | Документы Майкрософт
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
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- constraints [Integration Services]
ms.assetid: 23668e88-cef4-4009-a9cf-38e607eab7a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5aeeb70ed5741cc7372fdfc63e637fd53d932f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658357"
---
# <a name="connecting-tasks-programmatically"></a>Соединение задач программным образом
  Управление очередностью, представленное в объектной модели классом <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, устанавливает порядок запуска объектов <xref:Microsoft.SqlServer.Dts.Runtime.Executable> в пакете. Управление очередностью позволяет установить зависимость выполнения контейнеров и задач в пакете от результата выполнения предыдущего контейнера или задачи. Элементы управления очередностью устанавливаются между парами объектов <xref:Microsoft.SqlServer.Dts.Runtime.Executable> путем вызова метода <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> коллекции <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> объекта-контейнера. После создания ограничения между двумя исполняемыми объектами необходимо задать значение свойства <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>, устанавливающего критерии выполнения второго исполняемого объекта, определенного в ограничении.  
  
 В зависимости от значения, заданного свойству <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A>, можно использовать одновременно и ограничение, и выражение в одном и том же управлении очередностью, как описано в следующей таблице.  
  
|Значение свойства EvalOp|Description|  
|----------------------------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Constraint>|Указывает, что результат выполнения определяет, будет ли запущен связанный ограничением контейнер или задача. Задайте свойству <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> необходимое значение из перечисления <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Expression>|Указывает, что значение выражения определяет, будет ли запущен связанный ограничением контейнер или задача. Задайте значение свойства <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionAndConstraint>|Указывает, что связанный ограничением контейнер или задача будут выполнены, если выполнится ограничение и выражение вернет положительный результат. Установите свойства <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, а свойство <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> установите в значение `true`.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionOrConstraint>|Указывает, что связанный ограничением контейнер или задача будут выполнены, если выполнится ограничение либо выражение вернет положительный результат. Установите свойства <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, а свойство <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> установите в значение `false`.|  
  
 Следующий образец кода демонстрирует добавление двух задач в пакет. Между ними создается управление очередностью <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, препятствующее выполнению второй задачи до завершения первой.  
  
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
  
      // Add a File System task.  
      Executable eFileTask1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost1 = eFileTask1 as TaskHost;  
  
      // Add a second File System task.  
      Executable eFileTask2 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost2 = eFileTask2 as TaskHost;  
  
      // Put a precedence constraint between the tasks.  
      // Set the constraint to specify that the second File System task cannot run  
      // until the first File System task finishes.  
      PrecedenceConstraint pcFileTasks =   
        p.PrecedenceConstraints.Add((Executable)thFileHost1, (Executable)thFileHost2);  
      pcFileTasks.Value = DTSExecResult.Completion;  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task.  
    Dim eFileTask1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost1 As TaskHost = CType(eFileTask1, TaskHost)  
  
    ' Add a second File System task.  
    Dim eFileTask2 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost2 As TaskHost = CType(eFileTask2, TaskHost)  
  
    ' Put a precedence constraint between the tasks.  
    ' Set the constraint to specify that the second File System task cannot run  
    ' until the first File System task finishes.  
    Dim pcFileTasks As PrecedenceConstraint = _  
      p.PrecedenceConstraints.Add(CType(thFileHost1, Executable), CType(thFileHost2, Executable))  
    pcFileTasks.Value = DTSExecResult.Completion  
  
  End Sub  
  
End Module  
```  
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Добавление задачи потока данных программным образом](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
  
