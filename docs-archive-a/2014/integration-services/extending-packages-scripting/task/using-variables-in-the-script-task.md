---
title: Использование переменных в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2cd8fee5741c3d0e28e52c8712c3896428a05e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752283"
---
# <a name="using-variables-in-the-script-task"></a>Использование переменных в задаче «Скрипт»
  Переменные позволяют задаче «Скрипт» обмениваться данными с другими объектами в пакете. Дополнительные сведения см. в разделе [Переменные служб Integration Services (SSIS)](../../integration-services-ssis-variables.md).  
  
 В задаче «Скрипт» используется свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> объекта `Dts` для чтения из объектов <xref:Microsoft.SqlServer.Dts.Runtime.Variable> в пакете и записи в них.  
  
> [!NOTE]  
>  Свойство <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> класса <xref:Microsoft.SqlServer.Dts.Runtime.Variable> имеет тип `Object`. В задаче «Скрипт» включен параметр `Option Strict`, поэтому необходимо привести свойство <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> к соответствующему типу, прежде чем можно будет его использовать.  
  
 Необходимо добавить существующие переменные в списки <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> и <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> в **редакторе задачи "скрипт"** , чтобы сделать их доступными в пользовательском скрипте. Помните, что в именах переменных учитывается регистр. В скрипте можно получить доступ к переменным обоих типов с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> объекта `Dts`. Используйте свойство `Value`, чтобы считывать значения отдельных переменных и записывать значения в них. Задача «Скрипт» обеспечивает прозрачное для пользователя управление блокировкой во время считывания и изменение значений переменных в скрипте.  
  
 Чтобы проверить наличие переменной перед ее использованием в коде, можно использовать метод <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Variables>, возвращенной свойством <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 Для работы с переменными в задаче "скрипт" можно также использовать свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> (Dts.VariableDispenser). При использовании свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> необходимо обрабатывать в коде и семантику блокирования, и приведение типов данных для значений переменных. Может потребоваться использовать свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> вместо свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>, если возникает необходимость работать с переменной, недоступной во время разработки, но создаваемой программным путем во время выполнения.  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Использование задачи «Скрипт» в контейнере «цикл по каждому элементу»  
 Если задача «Скрипт» неоднократно запускается в контейнере «цикл по каждому элементу», то в скрипте обычно требуется обеспечить работу с содержимым текущего элемента в перечислителе. Например, при использовании перечислителя с циклом по каждому файлу в скрипте требуется определить имя текущего файла, а при использовании перечислителя ADO по каждой строке в скрипте необходимо получать содержимое столбцов в текущей строке данных.  
  
 Переменные делают возможной такую связь между контейнером «цикл по каждому элементу» и задачей «Скрипт». На странице **Сопоставления переменной** окна **Редактор циклов по каждому элементу** необходимо присвоить переменные каждому элементу данных, возвращаемому одним перечисленным элементом. Например, перечислитель с циклом по каждому файлу возвращает только имя файла из позиции с индексом 0 и поэтому требует сопоставления лишь с одной переменной, а перечислитель, который возвращает несколько столбцов данных из каждой строки, требует сопоставить отдельную переменную с каждым столбцом, предназначенным для использования в задаче «Скрипт».  
  
 После сопоставления перечисленных элементов с переменными необходимо добавить сопоставленные переменные в `ReadOnlyVariables` свойство на странице **Скрипт** в **редакторе задачи «Скрипт** », чтобы сделать их доступными для скрипта. Пример применения задачи "Скрипт" в контейнере "цикл по каждому элементу" для обработки файлов изображений в папке см. в разделе [Работа с изображениями в задаче "Скрипт"](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).  
  
## <a name="variables-example"></a>Пример использования переменных  
 В следующем примере показано, как получить доступ и использовать переменные в задаче «Скрипт», чтобы определить пути рабочего процесса пакета. В примере предполагается, что вы создали целочисленные переменные с именем `CustomerCount` и `MaxRecordCount` добавили их в `ReadOnlyVariables` коллекцию в **редакторе задачи «Скрипт**». Переменная `CustomerCount` содержит количество записей с данными заказчиков, которые должны быть импортированы. Если это значение больше значения `MaxRecordCount`, задача «Скрипт» сообщает о неудачном завершении. Если неудачное завершение возникает из-за превышения порогового значения `MaxRecordCount`, в пути обработки ошибок рабочего процесса можно реализовать все необходимые операции очистки.  
  
 Чтобы успешно откомпилировать этот образец, необходимо добавить ссылку на сборку Microsoft.SqlServer.ScriptTask.  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Переменные в службах Integration Services (SSIS)](../../integration-services-ssis-variables.md)   
 [Использование переменных в пакетах](../../use-variables-in-packages.md)  
  
  
