---
title: Соединение с экземпляром SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, connections
- connections [SMO]
- instances of SQL Server, connections
- SMO [SQL Server], connections
ms.assetid: ad3cf354-b2e3-468b-b986-1232e375fd84
author: stevestein
ms.author: sstein
ms.openlocfilehash: efc21451f4a876c6edfe4a2389ca937d11bc5c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668216"
---
# <a name="connecting-to-an-instance-of-sql-server"></a>Соединение с экземпляром SQL Server
  Первым шагом программирования в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] приложении управляющих объектов является создание экземпляра <xref:Microsoft.SqlServer.Management.Smo.Server> объекта и установка его соединения с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Создать экземпляр <xref:Microsoft.SqlServer.Management.Smo.Server> и установить соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно тремя способами. Первый способ — использовать переменную объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection> для задания информации о соединении. Второй способ — задать информацию о соединении в явном виде, присвоив соответствующие значения свойствам объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Третий способ — передать имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в конструктор объекта <xref:Microsoft.SqlServer.Management.Smo.Server>.  
  
 **Использование объекта ServerConnection**  
  
 Преимущество использования переменной объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection> в том, что заданную информацию о соединении можно применять многократно. Объявите переменную объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Затем объявите объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> и задайте для его свойств значения информации соединения, такие как имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и режим проверки подлинности. Затем передайте переменную объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection> в качестве параметра конструктору объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Не рекомендуется использование одного соединения несколькими серверными объектами одновременно. Чтобы получить копию настроек существующего соединения, вызовите метод <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A>.  
  
 **Настройка свойств серверного объекта в явном виде**  
  
 Другая возможность — объявить переменную объекта <xref:Microsoft.SqlServer.Management.Smo.Server> и вызвать конструктор по умолчанию. Объект <xref:Microsoft.SqlServer.Management.Smo.Server> попытается соединиться с экземпляром по умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], используя все настройки соединения по умолчанию.  
  
 **Передача имени экземпляра SQL Server в конструктор объекта Server**  
  
 Объявите переменную объекта <xref:Microsoft.SqlServer.Management.Smo.Server> и передайте имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве строкового параметра конструктору объекта. Объект <xref:Microsoft.SqlServer.Management.Smo.Server> установит соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], используя значения настроек по умолчанию.  
  
## <a name="connection-pooling"></a>Объединение подключений в пул  
 Вызов метода <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection> обычно не требуется. SMO автоматически установит соединение, когда это потребуется, и освободит его, передав в пул соединений, после завершения операций. При вызове метода <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> соединение не передается в пул. Для освобождения соединения и его передачи в пул нужен явный вызов метода <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A>. Кроме этого, можно запросить соединение не из пула, установив свойство <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
## <a name="multithreaded-applications"></a>Многопоточные приложения  
 Для многопоточных приложений в каждом потоке должен использоваться отдельный объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
## <a name="connecting-to-an-instance-of-sql-server-for-rmo"></a>Соединение с экземпляром SQL Server для RMO  
 Объекты RMO используют несколько отличный от SMO подход для соединения с сервером репликации.  
  
 Программные объекты RMO требуют, чтобы соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] производилось с помощью объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>, реализованного в пространстве имен `Microsoft.SqlServer.Management.Common`. Это соединение с сервером производится независимо от программного объекта RMO. Затем оно передается объекту RMO либо во время создания экземпляра, либо присвоением его свойству <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> объекта. Это позволяет создать экземпляр объекта программирования RMO независимо от объекта соединения и разделить задачи их управления. Один объект соединения можно использовать с несколькими объектами программирования RMO. Для соединений с сервером репликации действуют следующие правила.  
  
-   Все свойства соединения определяются для конкретного объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
-   Каждое соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  должно иметь свой собственный объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
-   Все данные проверки подлинности, необходимые для установления соединения и входа на сервер, передаются в объекте <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
-   По умолчанию соединения устанавливаются с использованием проверки подлинности Windows. Для использования проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] свойство <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> должно иметь значение False, а свойства <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> и <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> должны содержать в качестве значений действующие имя пользователя и пароль [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Учетные данные безопасности нужно всегда защищать от возможного несанкционированного доступа и по возможности вводить только во время выполнения.  
  
-   До передачи соединения любому объекту программирования RMO следует вызвать метод <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A>.  
  
## <a name="examples"></a>Примеры  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a>Соединение с локальным экземпляром SQL Server с использованием проверки подлинности Windows на языке Visual Basic  
 Для соединения с локальным экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не нужно писать много программного кода. Вместо этого для метода проверки подлинности и сервера используются настройки по умолчанию. Первая операция, требующая получения данных, вызовет создание соединения.  
  
 В этом примере используется [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] код .NET, который подключается к локальному экземпляру с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] помощью проверки подлинности Windows.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB1](SMO How to#SMO_VB1)]  -->  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a>Соединение с локальным экземпляром SQL Server с использованием проверки подлинности Windows на языке Visual C#  
 Для соединения с локальным экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не нужно писать много программного кода. Вместо этого для метода проверки подлинности и сервера используются настройки по умолчанию. Первая операция, требующая получения данных, вызовет создание соединения.  
  
 Этот пример представляет собой программный код на языке Visual C# .NET, который производит подключение к локальному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//The connection is established when a property is requested.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a>Соединение с удаленным экземпляром SQL Server с использованием проверки подлинности Windows на языке Visual Basic  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows указывать тип проверки не нужно. По умолчанию используется проверка подлинности Windows.  
  
 В этом примере используется [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] код .NET, который подключается к удаленному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью проверки подлинности Windows. Строковая переменная *стрсервер* содержит имя удаленного экземпляра.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB2](SMO How to#SMO_VB2)]  -->  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a>Соединение с удаленным экземпляром SQL Server с использованием проверки подлинности Windows на языке Visual C#  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows указывать тип проверки не нужно. По умолчанию используется проверка подлинности Windows.  
  
 Этот пример представляет собой программный код на языке Visual C# .NET, который производит подключение к удаленному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows. Строковая переменная *стрсервер* содержит имя удаленного экземпляра.  
  
```  
{   
//Connect to a remote instance of SQL Server.   
Server srv;   
//The strServer string variable contains the name of a remote instance of SQL Server.   
srv = new Server(strServer);   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-basic"></a>Соединение с экземпляром SQL Server с использованием проверки подлинности SQL Server на языке Visual Basic  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] нужно указывать тип проверки. В данном примере демонстрируется альтернативный метод объявления переменной объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>, позволяющий повторно использовать информацию соединения.  
  
 В примере используется [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] код .NET, демонстрирующий, как соединиться с удаленным и *впассворд* содержит имя входа и пароль.  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll  
' /r:Microsoft.SqlServer.ConnectionInfo.dll  
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      Dim sqlServerLogin As [String] = "user_id"  
      Dim password As [String] = "pwd"  
      Dim instanceName As [String] = "instance_name"  
      Dim remoteSvrName As [String] = "remote_server_name"  
  
      ' Connecting to an instance of SQL Server using SQL Server Authentication  
      Dim srv1 As New Server()   ' connects to default instance  
      srv1.ConnectionContext.LoginSecure = False   ' set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin  
      srv1.ConnectionContext.Password = password  
      Console.WriteLine(srv1.Information.Version)   ' connection is established  
  
      ' Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      Dim srvConn As New ServerConnection()  
      srvConn.ServerInstance = ".\" & instanceName   ' connects to named instance  
      srvConn.LoginSecure = False   ' set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin  
      srvConn.Password = password  
      Dim srv2 As New Server(srvConn)  
      Console.WriteLine(srv2.Information.Version)   ' connection is established  
  
      ' For remote connection, remote server name / ServerInstance needs to be specified  
      Dim srvConn2 As New ServerConnection(remoteSvrName)  
      srvConn2.LoginSecure = False  
      srvConn2.Login = sqlServerLogin  
      srvConn2.Password = password  
      Dim srv3 As New Server(srvConn2)  
      Console.WriteLine(srv3.Information.Version)   ' connection is established  
   End Sub  
End Class  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-c"></a>Соединение с экземпляром SQL Server с использованием проверки подлинности SQL Server на языке Visual C#  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] нужно указывать тип проверки. В данном примере демонстрируется альтернативный метод объявления переменной объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>, позволяющий повторно использовать информацию соединения.  
  
 В примере используется код Visual C# .NET, демонстрирующий, как подключиться к удаленному и *впассворду* , содержащему имя входа и пароль.  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll  
// /r:Microsoft.SqlServer.ConnectionInfo.dll  
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {   
      String sqlServerLogin = "user_id";  
      String password = "pwd";  
      String instanceName = "instance_name";  
      String remoteSvrName = "remote_server_name";  
  
      // Connecting to an instance of SQL Server using SQL Server Authentication  
      Server srv1 = new Server();   // connects to default instance  
      srv1.ConnectionContext.LoginSecure = false;   // set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin;  
      srv1.ConnectionContext.Password = password;  
      Console.WriteLine(srv1.Information.Version);   // connection is established  
  
      // Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      ServerConnection srvConn = new ServerConnection();  
      srvConn.ServerInstance = @".\" + instanceName;   // connects to named instance  
      srvConn.LoginSecure = false;   // set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin;  
      srvConn.Password = password;  
      Server srv2 = new Server(srvConn);  
      Console.WriteLine(srv2.Information.Version);   // connection is established  
  
      // For remote connection, remote server name / ServerInstance needs to be specified  
      ServerConnection srvConn2 = new ServerConnection(remoteSvrName);  
      srvConn2.LoginSecure = false;  
      srvConn2.Login = sqlServerLogin;  
      srvConn2.Password = password;  
      Server srv3 = new Server(srvConn2);  
      Console.WriteLine(srv3.Information.Version);   // connection is established  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
