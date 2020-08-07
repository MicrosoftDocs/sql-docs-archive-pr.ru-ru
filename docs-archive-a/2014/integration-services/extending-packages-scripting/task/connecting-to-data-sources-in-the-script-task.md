---
title: Соединение с источниками данных в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2c8374271c7972498361a83e4bbe87ad12265827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731909"
---
# <a name="connecting-to-data-sources-in-the-script-task"></a>Соединение с источниками данных в задаче «Скрипт»
  Диспетчеры соединений обеспечивают доступ к источникам данных, которые были настроены в пакете. Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](../../connection-manager/integration-services-ssis-connections.md).  
  
 Задача "Скрипт" может обращаться к диспетчерам соединений через свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> объекта **Dts**. Каждый диспетчер соединений в коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Connections> хранит сведения о том, как соединиться с базовым источником данных.  
  
 При вызове метода <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> диспетчера соединений диспетчер соединяется с источником данных, если соединение еще не было установлено, и возвращает соответствующее соединение или сведения о соединении для использования в коде задачи «Скрипт».  
  
> [!NOTE]  
>  Прежде чем вызывать метод `AcquireConnection`, необходимо знать тип соединения, возвращаемого диспетчером соединений. Поскольку в задаче «Скрипт» включен параметр `Option Strict`, перед использованием необходимо привести соединение, возвращаемое с типом `Object`, к подходящему типу соединения.  
  
 Можно воспользоваться методом <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Connections>, возвращаемой свойством <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>, чтобы выполнить поиск существующего соединения, прежде чем использовать соединение в коде.  
  
> [!IMPORTANT]  
>  В управляемом коде задачи "Скрипт" нельзя вызывать метод AcquireConnection диспетчеров соединений, возвращающих неуправляемые объекты, например диспетчера соединений OLE DB или диспетчера соединений Excel. Тем не менее можно прочитать свойство ConnectionString этих диспетчеров соединений и подключиться к источнику данных непосредственно в коде, используя строку подключения `OledbConnection` из пространства имен **System. Data. OLEDB** .  
>   
>  Если необходимо вызвать метод AcquireConnection диспетчера соединений, возвращающего неуправляемый объект, используйте диспетчер соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. При настройке диспетчера соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] для использования поставщика OLE DB, он соединяется с помощью поставщика данных [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] для OLE DB. В этом случае метод AcquireConnection возвращает `System.Data.OleDb.OleDbConnection` вместо неуправляемого объекта. Чтобы настроить диспетчер соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] для работы с источником данных Excel, выберите поставщик OLE DB [!INCLUDE[msCoName](../../../includes/msconame-md.md)] для Jet (Майкрософт), укажите книгу Excel, а затем введите `Excel 8.0` (для Excel 97 и более поздних версий) в качестве значения параметра **Расширенные свойства** на странице **Все** диалогового окна **Диспетчер соединений**.  
  
## <a name="connections-example"></a>Пример соединений  
 В следующем примере демонстрируется, как получить доступ к диспетчерам соединений из задачи «Скрипт». В образце предполагается, что был создан и настроен диспетчер соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] с именем **Test ADO.NET Connection** и диспетчер соединений с неструктурированными файлами с именем **Test Flat File Connection**. Обратите внимание, что диспетчер соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] возвращает объект `SqlConnection`, который можно использовать немедленно для соединения с источником данных. Диспетчер соединений с неструктурированными файлами, в то же время, возвращает лишь строку, содержащую путь и имя файла. Необходимо использовать методы из пространства имен `System.IO`, чтобы открыть неструктурированный файл и работать с ним.  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;соединений&#41; SSIS](../../connection-manager/integration-services-ssis-connections.md)   
 [Создание диспетчеров соединений](../../create-connection-managers.md)  
  
  
