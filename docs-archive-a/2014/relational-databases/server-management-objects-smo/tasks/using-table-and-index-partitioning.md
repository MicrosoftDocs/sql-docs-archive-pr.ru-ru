---
title: Использование секционирования таблиц и индексов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- partitions [SMO]
- storing data [SMO]
- partitioned tables [SQL Server], SMO
- partitioned indexes [SQL Server], SMO
ms.assetid: 0e682d7e-86c3-4d73-950d-aa692d46cb62
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e05087f63da163b8fa339befae039eb5e7e8245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657045"
---
# <a name="using-table-and-index-partitioning"></a>Использование секционирования таблиц и индексов
  Хранение данных может осуществляться с помощью алгоритмов хранения, указанных в разделе [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md). Секционирование может улучшить управляемость и масштабируемость больших таблиц и индексов.  
  
## <a name="index-and-table-partitioning"></a>Секционирование таблиц и индексов  
 Эта функция позволяет распространять данные индексов и таблиц по нескольким файловым группам в секциях. Функция секционирования на основе значений некоторых столбцов, называемых столбцами секционирования, определяет, каким образом строки таблицы или индекса сопоставляются секциям. Схема секционирования сопоставляет каждую из секций, определенных функцией секционирования, с файловой группой. Это дает возможность разрабатывать стратегии архивирования, позволяющие масштабировать таблицы по файловым группам и, следовательно, по физическим устройствам.  
  
 Объект <xref:Microsoft.SqlServer.Management.Smo.Database> содержит коллекцию объектов <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction>, представляющих реализованные функции секционирования, и коллекцию объектов <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme>, описывающих способ сопоставления данных группам файлов.  
  
 Каждый из объектов <xref:Microsoft.SqlServer.Management.Smo.Table> и <xref:Microsoft.SqlServer.Management.Smo.Index> указывает в свойстве <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme>, какую схему секционирования он использует, а в свойстве <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection> ─ столбцы.  
  
## <a name="example"></a>Пример  
 В следующем примере кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Создание проекта Visual C&#35; SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-basic"></a>Настройка схемы секционирования для таблицы на языке Visual Basic  
 В примере кода показано, как создать функцию секционирования и схему секционирования для таблицы `TransactionHistory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . Секции разделяются по дате, чтобы отделить старые записи в таблицу `TransactionHistoryArchive` .  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBPartition1](SMO How to#SMO_VBPartition1)]  -->  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-c"></a>Настройка схемы секционирования для таблицы на языке Visual C#  
 В примере кода показано, как создать функцию секционирования и схему секционирования для таблицы `TransactionHistory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . Секции разделяются по дате, чтобы отделить старые записи в таблицу `TransactionHistoryArchive` .  
  
```csharp
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Define and create three new file groups on the database.   
FileGroup fg2;   
fg2 = new FileGroup(db, "Second");   
fg2.Create();   
FileGroup fg3;   
fg3 = new FileGroup(db, "Third");   
fg3.Create();   
FileGroup fg4;   
fg4 = new FileGroup(db, "Fourth");   
fg4.Create();   
//Define a partition function by supplying the parent database and name arguments in the constructor.   
PartitionFunction pf;   
pf = new PartitionFunction(db, "TransHistPF");   
//Add a partition function parameter that specifies the function uses a DateTime range type.   
PartitionFunctionParameter pfp;   
pfp = new PartitionFunctionParameter(pf, DataType.DateTime);   
pf.PartitionFunctionParameters.Add(pfp);   
//Specify the three dates that divide the data into four partitions.   
object[] val;   
val = new object[] {"1/1/2003", "1/1/2004", "1/1/2005"};   
pf.RangeValues = val;   
//Create the partition function.   
pf.Create();   
//Define a partition scheme by supplying the parent database and name arguments in the constructor.   
PartitionScheme ps;   
ps = new PartitionScheme(db, "TransHistPS");   
//Specify the partition function and the filegroups required by the partition scheme.   
ps.PartitionFunction = "TransHistPF";   
ps.FileGroups.Add("PRIMARY");   
ps.FileGroups.Add("second");   
ps.FileGroups.Add("Third");   
ps.FileGroups.Add("Fourth");   
//Create the partition scheme.   
ps.Create();   
}   
```  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-powershell"></a>Настройка схемы секционирования для таблицы в PowerShell  
 В примере кода показано, как создать функцию секционирования и схему секционирования для таблицы `TransactionHistory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . Секции разделяются по дате, чтобы отделить старые записи в таблицу `TransactionHistoryArchive` .  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
$db = $srv.Databases["AdventureWorks"]  
#Create four filegroups  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "First"  
$fg2 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Second"  
$fg3 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Third"  
$fg4 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Fourth"  
  
#Define a partition function by supplying the parent database and name arguments in the constructor.  
$pf =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunction -argumentlist $db, "TransHistPF"  
$T = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$T  
$T.GetType()  
#Add a partition function parameter that specifies the function uses a DateTime range type.  
$pfp =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunctionParameter -argumentlist $pf, $T  
  
#Specify the three dates that divide the data into four partitions.
#Create an array of type object to hold the partition data  
$val = "1/1/2003"."1/1/2004","1/1/2005"  
$pf.RangeValues = $val  
$pf  
#Create the partition function  
$pf.Create()  
  
#Create partition scheme  
$ps = New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionScheme -argumentlist $db, "TransHistPS"  
$ps.PartitionFunction = "TransHistPF"  
  
#add the filegroups to the scheme
$ps.FileGroups.Add("PRIMARY")  
$ps.FileGroups.Add("Second")  
$ps.FileGroups.Add("Third")  
$ps.FileGroups.Add("Fourth")  
  
#Create it at the server  
$ps.Create()  
```  
  
## <a name="see-also"></a>См. также:  
 [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md)  
