---
title: Использование файловых групп и файлов для хранения данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- filegroups [SMO]
- storing data [SMO]
- files [SMO]
- files [SMO], about files
- storage [SMO]
ms.assetid: 7e2327ce-e1a6-4904-83d1-0944b24a7b43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 15ac5fd0c43c9b58432a774ae11aeb6500f0403b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667657"
---
# <a name="using-filegroups-and-files-to-store-data"></a>Использование файловых групп и файлов для хранения данных
  Для хранения файлов базы данных используются файлы данных. Файлы данных делятся на файловые группы. Объект <xref:Microsoft.SqlServer.Management.Smo.Database> содержит свойство <xref:Microsoft.SqlServer.Management.Smo.Database.FileGroups%2A>, которое ссылается на объект <xref:Microsoft.SqlServer.Management.Smo.FileGroupCollection>. Каждый объект <xref:Microsoft.SqlServer.Management.Smo.FileGroup> в этой коллекции содержит свойство <xref:Microsoft.SqlServer.Management.Smo.FileGroup.Files%2A>. Это свойство ссылается на коллекцию <xref:Microsoft.SqlServer.Management.Smo.DataFileCollection>, которая содержит все файлы данных, принадлежащие базе данных. Файловые группы в основном используются для объединения файлов, используемых для хранения объекта базы данных. Одной из причин разделения объекта базы данных по нескольким файлам является повышение производительности, особенно если файлы хранятся на разных дисках.  
  
 В каждой созданной автоматически базе данных есть файловая группа с именем «Первичная» и файл данных, имя которого совпадает с именем базы данных. В коллекции можно добавлять дополнительные файлы и группы.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Создание проекта Visual C&#35; SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-visual-basic"></a>Добавление файловых групп и файлов данных в базу данных на языке Visual Basic  
 Основная файловая группа и файл данных создаются автоматически со значениями свойств по умолчанию. В этом примере кода задаются некоторые значения свойств, которые можно использовать. Иным образом, можно использовать значения свойств по умолчанию.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBFileGroups1](SMO How to#SMO_VBFileGroups1)]  -->  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-visual-c"></a>Добавление файловых групп и файлов данных в базу данных на языке Visual C#  
 Основная файловая группа и файл данных создаются автоматически со значениями свойств по умолчанию. В этом примере кода задаются некоторые значения свойств, которые можно использовать. Иным образом, можно использовать значения свойств по умолчанию.  
  
```csharp
{  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a FileGroup object called SECONDARY on the database.   
            FileGroup fg1 = default(FileGroup);  
            fg1 = new FileGroup(db, "SECONDARY");  
            //Call the Create method to create the file group on the instance of SQL Server.   
            fg1.Create();  
            //Define a DataFile object on the file group and set the FileName property.   
            DataFile df1 = default(DataFile);  
            df1 = new DataFile(fg1, "datafile1");  
            df1.FileName = "c:\\Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\Data\\datafile2.ndf";  
            //Call the Create method to create the data file on the instance of SQL Server.   
            df1.Create();  
        }  
```  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-powershell"></a>Добавление файловых групп и файлов данных в базу данных в PowerShell  
 Основная файловая группа и файл данных создаются автоматически со значениями свойств по умолчанию. В этом примере кода задаются некоторые значения свойств, которые можно использовать. Иным образом, можно использовать значения свойств по умолчанию.  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012.  
$db = get-item AdventureWorks2012  
  
#Create a new filegroup  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "SECONDARY"  
$fg1.Create()  
  
#Define a DataFile object on the file group and set the FileName property.   
$df1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.DataFile -argumentlist $fg1, "datafile1"  
  
#Make sure to have a directory created to hold the designated data file  
$df1.FileName = "c:\\TestData\\datafile2.ndf"  
  
#Call the Create method to create the data file on the instance of SQL Server.   
$df1.Create()  
```  
  
## <a name="creating-altering-and-removing-a-log-file-in-visual-basic"></a>Создание, изменение и удаление файла журнала на языке Visual Basic  
 В этом примере кода создается объект <xref:Microsoft.SqlServer.Management.Smo.LogFile>, изменяется одно из его свойств, а затем он удаляется из базы данных.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBFileGroups3](SMO How to#SMO_VBFileGroups3)]  -->  
  
## <a name="creating-altering-and-removing-a-log-file-in-visual-c"></a>Создание, изменение и удаление файла журнала на языке Visual C#  
 В этом примере кода создается объект <xref:Microsoft.SqlServer.Management.Smo.LogFile>, изменяется одно из его свойств, а затем он удаляется из базы данных.  
  
```csharp
//Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a LogFile object and set the database, name, and file name properties in the constructor.   
            LogFile lf1 = default(LogFile);  
            lf1 = new LogFile(db, "logfile1", "c:\\Program Files\\Microsoft SQL Server\\MSSQL.10_50.MSSQLSERVER\\MSSQL\\Data\\logfile1.ldf");  
            //Set the file growth to 6%.   
            lf1.GrowthType = FileGrowthType.Percent;  
            lf1.Growth = 6;  
            //Run the Create method to create the log file on the instance of SQL Server.   
            lf1.Create();  
            //Alter the growth percentage.
            lf1.Growth = 7;  
            lf1.Alter();  
            //Remove the log file.
            lf1.Drop();
```  
  
## <a name="creating-altering-and-removing-a-log-file-in-powershell"></a>Создание, изменение и удаление файла журнала в PowerShell  
 В этом примере кода создается объект <xref:Microsoft.SqlServer.Management.Smo.LogFile>, изменяется одно из его свойств, а затем он удаляется из базы данных.  
  
```powershell
#Load the assembly containing the enums used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlEnum")  
  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012  
$db = get-item AdventureWorks2012  
  
#Create a filegroup  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Secondary"  
  
#Call the Create method to create the file group on the instance of SQL Server.   
$fg1.Create()  
  
#Define a LogFile object on the file group and set the FileName property.   
$lf1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LogFile -argumentlist $db, "LogFile2"  
  
#Set a location for it - make sure the directory exists  
$lf1.FileName = "logfile1", "c:\\Program Files\\Microsoft SQL Server\\MSSQL.10_50.MSSQLSERVER\\MSSQL\\Data\\logfile1.ldf"  
  
#Set file growth to 6%  
$lf1.GrowthType = [Microsoft.SqlServer.Management.Smo.FileGrowthType]::Percent  
$lf1.Growth = 6.0  
  
#Call the Create method to create the data file on the instance of SQL Server.   
$lf1.Create()  
  
#Alter a value and drop the log file  
$lf1.Growth = 7.0  
$lf1.Alter()  
$lf1.Drop()
```  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.SqlServer.Management.Smo.FileGroup>   
 [Файлы и файловые группы базы данных](../../databases/database-files-and-filegroups.md)  
