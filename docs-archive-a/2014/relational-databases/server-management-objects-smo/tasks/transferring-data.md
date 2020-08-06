---
title: Передача данных | Документация Майкрософт
ms.custom: ''
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- data transfers [SMO]
- transferring data
ms.assetid: eea255c3-8251-40f0-973b-fe4ef6cb5261
author: stevestein
ms.author: sstein
ms.openlocfilehash: dcbcdc1e61c2d18f6a98f797385145f04dfecc7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732489"
---
# <a name="transferring-data"></a>Передача данных
  Класс <xref:Microsoft.SqlServer.Management.Smo.Transfer> является служебным классом, наделенным средствами для передачи объектов и данных.  
  
 Объекты в схеме базы данных передаются в ходе выполнения сформированного скрипта на целевом сервере. Данные <xref:Microsoft.SqlServer.Management.Smo.Table> передаются вместе с динамически созданным пакетом DTS.  
  
 Объект <xref:Microsoft.SqlServer.Management.Smo.Transfer> обладает всеми функциональными возможностями объектов <xref:Microsoft.SqlServer.Management.Smo.Transfer> в DMO и дополнительными функциональными возможностями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Однако в SMO в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Transfer> объект использует API [SQLBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy\(v=VS.90\).aspx) для перемещения данных. Кроме того, методы и свойства, используемые для передачи данных, располагаются в объекте <xref:Microsoft.SqlServer.Management.Smo.Transfer>, а не в объекте <xref:Microsoft.SqlServer.Management.Smo.Database>. Перенос функциональных возможностей с экземпляров классов на вспомогательные классы согласуется с облегченной объектной моделью, поскольку код для выполнения конкретных задач загружается только по мере необходимости.  
  
 Объект <xref:Microsoft.SqlServer.Management.Smo.Transfer> не поддерживает передачи данных в целевую базу данных, у которой <xref:Microsoft.SqlServer.Management.Smo.Database.CompatibilityLevel%2A> меньше, чем у версии экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-basic"></a>Передача схемы и данных из одной базы данных в другую на языке Visual Basic  
 Этот пример кода показывает, как передавать схему и данные из одной базы данных в другую с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.Transfer>.  
  
```vb
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Create a new database that is to be destination database.
Dim dbCopy As Database
dbCopy = New Database(srv, "AdventureWorks2012Copy")
dbCopy.Create()
'Define a Transfer object and set the required options and properties.
Dim xfr As Transfer
xfr = New Transfer(db)
xfr.CopyAllTables = True
xfr.Options.WithDependencies = True
xfr.Options.ContinueScriptingOnError = True
xfr.DestinationDatabase = "AdventureWorks2012Copy"
xfr.DestinationServer = srv.Name
xfr.DestinationLoginSecure = True
xfr.CopySchema = True
'Script the transfer. Alternatively perform immediate data transfer with TransferData method.
xfr.ScriptTransfer()
```
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-c"></a>Передача схемы и данных из одной базы данных в другую на языке Visual C#  
 Этот пример кода показывает, как передавать схему и данные из одной базы данных в другую с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.Transfer>.  
  
```csharp
{  
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Create a new database that is to be destination database.   
            Database dbCopy;  
            dbCopy = new Database(srv, "AdventureWorks2012Copy");  
            dbCopy.Create();  
            //Define a Transfer object and set the required options and properties.   
            Transfer xfr;  
            xfr = new Transfer(db);  
            xfr.CopyAllTables = true;  
            xfr.Options.WithDependencies = true;  
            xfr.Options.ContinueScriptingOnError = true;  
            xfr.DestinationDatabase = "AdventureWorks2012Copy";  
            xfr.DestinationServer = srv.Name;  
            xfr.DestinationLoginSecure = true;  
            xfr.CopySchema = true;  
            //Script the transfer. Alternatively perform immediate data transfer   
            // with TransferData method.   
            xfr.ScriptTransfer();  
        }   
```  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-powershell"></a>Передача схемы и данных из одной базы данных в другую в PowerShell  
 Этот пример кода показывает, как передавать схему и данные из одной базы данных в другую с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.Transfer>.  
  
```powershell
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks2012 database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a database to hold the copy of AdventureWorks  
$dbCopy = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Database -ArgumentList $srv, "AdventureWorksCopy"  
$dbCopy.Create()  
  
#Define a Transfer object and set the required options and properties.  
$xfr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Transfer -ArgumentList $db  
  
#Set this objects properties  
$xfr.CopyAllTables = $true  
$xfr.Options.WithDependencies = $true  
$xfr.Options.ContinueScriptingOnError = $true  
$xfr.DestinationDatabase = "AdventureWorksCopy"  
$xfr.DestinationServer = $srv.Name  
$xfr.DestinationLoginSecure = $true  
$xfr.CopySchema = $true  
"Scripting Data Transfer"  
#Script the transfer. Alternatively perform immediate data transfer with TransferData method.  
$xfr.ScriptTransfer()  
```  
