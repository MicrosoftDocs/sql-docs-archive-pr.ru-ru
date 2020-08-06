---
title: Создание, изменение и удаление таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- tables [SMO]
ms.assetid: ff0bcfff-812f-4999-b0c7-736a97804c2b
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce2053009b3cba44f061401061ef603f222d65f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668200"
---
# <a name="creating-altering-and-removing-tables"></a><span data-ttu-id="5fdd6-102">Создание, изменение и удаление таблиц</span><span class="sxs-lookup"><span data-stu-id="5fdd6-102">Creating, Altering, and Removing Tables</span></span>
  <span data-ttu-id="5fdd6-103">В управляющих объектах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) таблицы представлены объектом <xref:Microsoft.SqlServer.Management.Smo.Table>.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), tables are represented by the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span> <span data-ttu-id="5fdd6-104">В иерархии объектов SMO объект <xref:Microsoft.SqlServer.Management.Smo.Table> расположен ниже объекта <xref:Microsoft.SqlServer.Management.Smo.Database>.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-104">In the SMO object hierarchy, the <xref:Microsoft.SqlServer.Management.Smo.Table> object is below the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fdd6-105">Пример</span><span class="sxs-lookup"><span data-stu-id="5fdd6-105">Example</span></span>  
 <span data-ttu-id="5fdd6-106">Чтобы использовать какой-либо из представленных примеров кода, необходимо выбрать среду программирования, шаблон и язык, с помощью которых будет создаваться приложение.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-106">To use any code example that is provided, you have to choose the programming environment, template, and language in which to create your application.</span></span> <span data-ttu-id="5fdd6-107">Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Создание проекта Visual C&#35; SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span><span class="sxs-lookup"><span data-stu-id="5fdd6-107">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-table-in-visual-basic"></a><span data-ttu-id="5fdd6-108">Создание, изменение и удаление таблицы на языке Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fdd6-108">Creating, Altering, and Removing a Table in Visual Basic</span></span>  
 <span data-ttu-id="5fdd6-109">В этом примере кода создается таблица с несколькими столбцами разных типов и предназначений.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-109">This code example creates a table that has several columns with different types and purposes.</span></span> <span data-ttu-id="5fdd6-110">В этом коде также приведены примеры того, как создать поле идентификаторов, как создать первичный ключ и как изменить свойства таблицы.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-110">The code also provides examples of how to create an identity field, how to create a primary key, and how to alter table properties.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTable1](SMO How to#SMO_VBTable1)]  -->  
  
## <a name="creating-altering-and-removing-a-table-in-visual-c"></a><span data-ttu-id="5fdd6-111">Создание, изменение и удаление таблицы на языке Visual C#</span><span class="sxs-lookup"><span data-stu-id="5fdd6-111">Creating, Altering, and Removing a Table in Visual C#</span></span>  
 <span data-ttu-id="5fdd6-112">В этом примере кода создается таблица с несколькими столбцами разных типов и предназначений.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-112">This code example creates a table that has several columns with different types and purposes.</span></span> <span data-ttu-id="5fdd6-113">В этом коде также приведены примеры того, как создать поле идентификаторов, как создать первичный ключ и как изменить свойства таблицы.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-113">The code also provides examples of how to create an identity field, how to create a primary key, and how to alter table properties.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a Table object variable by supplying the parent database and table name in the constructor.   
        Table tb;   
        tb = new Table(db, "Test_Table");   
        //Add various columns to the table.   
        Column col1;   
        col1 = new Column(tb, "Name", DataType.NChar(50));   
        col1.Collation = "Latin1_General_CI_AS";   
        col1.Nullable = true;   
        tb.Columns.Add(col1);   
        Column col2;   
        col2 = new Column(tb, "ID", DataType.Int);   
        col2.Identity = true;   
        col2.IdentitySeed = 1;   
        col2.IdentityIncrement = 1;   
        tb.Columns.Add(col2);   
        Column col3;   
        col3 = new Column(tb, "Value", DataType.Real);   
        tb.Columns.Add(col3);   
        Column col4;   
        col4 = new Column(tb, "Date", DataType.DateTime);   
        col4.Nullable = false;   
        tb.Columns.Add(col4);   
        //Create the table on the instance of SQL Server.   
        tb.Create();   
        //Add another column.   
        Column col5;   
        col5 = new Column(tb, "ExpiryDate", DataType.DateTime);   
        col5.Nullable = false;   
        tb.Columns.Add(col5);   
        //Run the Alter method to make the change on the instance of SQL Server.   
        tb.Alter();   
        //Remove the table from the database.   
        tb.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-table-in-powershell"></a><span data-ttu-id="5fdd6-114">Создание, изменение и удаление таблицы в PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fdd6-114">Creating, Altering, and Removing a Table in PowerShell</span></span>  
 <span data-ttu-id="5fdd6-115">В этом примере кода создается таблица с несколькими столбцами разных типов и предназначений.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-115">This code example creates a table that has several columns with different types and purposes.</span></span> <span data-ttu-id="5fdd6-116">В этом коде также приведены примеры того, как создать поле идентификаторов, как создать первичный ключ и как изменить свойства таблицы.</span><span class="sxs-lookup"><span data-stu-id="5fdd6-116">The code also provides examples of how to create an identity field, how to create a primary key, and how to alter table properties.</span></span>  
  
```powershell
#Load the assembly containing the objects used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.Types")  
  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012.  
$db = Get-Item AdventureWorks2012  
  
#Create a SMO Table  
$tb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Table -argumentlist $db, "Test_Table"  
  
#Add various columns to the table.   
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::NChar(50)  
$col1 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Name", $Type  
$col1.Collation = "Latin1_General_CI_AS"  
$col1.Nullable = $true  
$tb.Columns.Add($col1)  
  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::Int  
$col2 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"ID", $Type  
$col2.Identity = $true  
$col2.IdentitySeed = 1  
$col2.IdentityIncrement = 1  
$tb.Columns.Add($col2)
  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::Real  
$col3 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Value", $Type  
$tb.Columns.Add($col3)
  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$col4 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Date", $Type  
$col4.Nullable = $false  
$tb.Columns.Add($col4)
  
#Create the table  
$tb.Create()  
  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$col5 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"ExpiryDate", $Type  
$col5.Nullable = $false  
$tb.Columns.Add($col5)
  
#Run the Alter method to make the change on the instance of SQL Server.
$tb.Alter()  
  
#Remove the table from the database.
$tb.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fdd6-117">См. также:</span><span class="sxs-lookup"><span data-stu-id="5fdd6-117">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Table>
