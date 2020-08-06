---
title: Создание, изменение и удаление внешних ключей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- foreign keys [SMO]
ms.assetid: d43c8dca-bb6b-4a41-8a79-c96fd546fc91
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3087dd9f521ce9fe7b57ec359dc8042afbfbb9a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739623"
---
# <a name="creating-altering-and-removing-foreign-keys"></a><span data-ttu-id="870d2-102">Создание, изменение и удаление внешних ключей</span><span class="sxs-lookup"><span data-stu-id="870d2-102">Creating, Altering, and Removing Foreign Keys</span></span>
  <span data-ttu-id="870d2-103">В иерархии управляющих объектов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) внешние ключи представлены объектом <xref:Microsoft.SqlServer.Management.Smo.ForeignKey>.</span><span class="sxs-lookup"><span data-stu-id="870d2-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), foreign keys are represented by the <xref:Microsoft.SqlServer.Management.Smo.ForeignKey> object.</span></span>  
  
 <span data-ttu-id="870d2-104">Чтобы создать в SMO внешний ключ, необходимо указать таблицу, в которой внешний ключ определен в конструкторе объекта <xref:Microsoft.SqlServer.Management.Smo.ForeignKey>.</span><span class="sxs-lookup"><span data-stu-id="870d2-104">To create a foreign key in SMO, you must specify the table on which the foreign key is defined in the constructor of the <xref:Microsoft.SqlServer.Management.Smo.ForeignKey> object.</span></span> <span data-ttu-id="870d2-105">В этой таблице надо выбрать хотя бы один столбец, который будет внешним ключом.</span><span class="sxs-lookup"><span data-stu-id="870d2-105">From the table, you must select at least one column to be the foreign key.</span></span> <span data-ttu-id="870d2-106">Для этого создайте объектную переменную <xref:Microsoft.SqlServer.Management.Smo.ForeignKeyColumn> и укажите имя столбца, который станет внешним ключом.</span><span class="sxs-lookup"><span data-stu-id="870d2-106">To do this, create a <xref:Microsoft.SqlServer.Management.Smo.ForeignKeyColumn> object variable and specify the name of the column that is the foreign key.</span></span> <span data-ttu-id="870d2-107">Теперь укажите таблицу и столбец, на которые будут выполняться ссылки.</span><span class="sxs-lookup"><span data-stu-id="870d2-107">Then, specify the referenced table and referenced column.</span></span> <span data-ttu-id="870d2-108">Воспользуйтесь методом <xref:Microsoft.SqlServer.Management.Smo.ForeignKeyColumnCollection.Add%2A> для добавления столбца в свойство объекта `Columns`.</span><span class="sxs-lookup"><span data-stu-id="870d2-108">Use the <xref:Microsoft.SqlServer.Management.Smo.ForeignKeyColumnCollection.Add%2A> method to add the column to the `Columns` object property.</span></span>  
  
 <span data-ttu-id="870d2-109">Столбцы, представляющие внешний ключ, перечислены в свойстве `Columns` объекта <xref:Microsoft.SqlServer.Management.Smo.ForeignKey>.</span><span class="sxs-lookup"><span data-stu-id="870d2-109">The columns that represent the foreign key are listed in the `Columns` object property of the <xref:Microsoft.SqlServer.Management.Smo.ForeignKey> object.</span></span> <span data-ttu-id="870d2-110">Первичный ключ, на который ссылается внешний ключ, представлен свойством <xref:Microsoft.SqlServer.Management.Smo.ForeignKey.ReferencedKey%2A>, которое находится в таблице, указанной в свойстве <xref:Microsoft.SqlServer.Management.Smo.ForeignKey.ReferencedTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="870d2-110">The primary key that is referenced by the foreign key is represented by the <xref:Microsoft.SqlServer.Management.Smo.ForeignKey.ReferencedKey%2A> property that is in the table specified in the <xref:Microsoft.SqlServer.Management.Smo.ForeignKey.ReferencedTable%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="870d2-111">Пример</span><span class="sxs-lookup"><span data-stu-id="870d2-111">Example</span></span>  
 <span data-ttu-id="870d2-112">Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение.</span><span class="sxs-lookup"><span data-stu-id="870d2-112">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="870d2-113">Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Создание проекта Visual C&#35; SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span><span class="sxs-lookup"><span data-stu-id="870d2-113">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-foreign-key-in-visual-basic"></a><span data-ttu-id="870d2-114">Создание, изменение и удаление внешнего ключа на языке Visual Basic</span><span class="sxs-lookup"><span data-stu-id="870d2-114">Creating, Altering, and Removing a Foreign Key in Visual Basic</span></span>  
 <span data-ttu-id="870d2-115">Этот пример кода показывает, как создать связь по внешнему ключу между одним или несколькими столбцами одной таблицы и первичным ключевым столбцом другой таблицы.</span><span class="sxs-lookup"><span data-stu-id="870d2-115">This code example shows how to create a foreign key relationship between one or more columns in one table to a primary key column in another table.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBForeignKeys1](SMO How to#SMO_VBForeignKeys1)]  -->  
  
## <a name="creating-altering-and-removing-a-foreign-key-in-visual-c"></a><span data-ttu-id="870d2-116">Создание, изменение и удаление внешнего ключа на языке Visual C#</span><span class="sxs-lookup"><span data-stu-id="870d2-116">Creating, Altering, and Removing a Foreign Key in Visual C#</span></span>  
 <span data-ttu-id="870d2-117">Этот пример кода показывает, как создать связь по внешнему ключу между одним или несколькими столбцами одной таблицы и первичным ключевым столбцом другой таблицы.</span><span class="sxs-lookup"><span data-stu-id="870d2-117">This code example shows how to create a foreign key relationship between one or more columns in one table to a primary key column in another table.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Declare another Table object variable and reference the EmployeeDepartmentHistory table.   
            Table tbea;  
            tbea = db.Tables["EmployeeDepartmentHistory", "HumanResources"];  
            //Define a Foreign Key object variable by supplying the EmployeeDepartmentHistory as the parent table and the foreign key name in the constructor.   
            ForeignKey fk;  
            fk = new ForeignKey(tbea, "test_foreignkey");  
            //Add BusinessEntityID as the foreign key column.   
            ForeignKeyColumn fkc;  
            fkc = new ForeignKeyColumn(fk, "BusinessEntityID", "BusinessEntityID");  
            fk.Columns.Add(fkc);  
            //Set the referenced table and schema.   
            fk.ReferencedTable = "Employee";  
            fk.ReferencedTableSchema = "HumanResources";  
            //Create the foreign key on the instance of SQL Server.   
            fk.Create();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-foreign-key-in-powershell"></a><span data-ttu-id="870d2-118">Создание, изменение и удаление внешнего ключа в PowerShell</span><span class="sxs-lookup"><span data-stu-id="870d2-118">Creating, Altering, and Removing a Foreign Key in PowerShell</span></span>  
 <span data-ttu-id="870d2-119">Этот пример кода показывает, как создать связь по внешнему ключу между одним или несколькими столбцами одной таблицы и первичным ключевым столбцом другой таблицы.</span><span class="sxs-lookup"><span data-stu-id="870d2-119">This code example shows how to create a foreign key relationship between one or more columns in one table to a primary key column in another table.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the FK table  
$tbea = get-item HumanResources.EmployeeDepartmentHistory  
  
# Define a Foreign Key object variable by supplying the EmployeeDepartmentHistory  
# as the parent table and the foreign key name in the constructor.   
$fk = New-Object -TypeName Microsoft.SqlServer.Management.SMO.ForeignKey `  
-argumentlist $tbea, "test_foreignkey"  
  
#Add BusinessEntityID as the foreign key column.   
$fkc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.ForeignKeyColumn `  
-argumentlist $fk, "BusinessEntityID", "BusinessEntityID"  
$fk.Columns.Add($fkc)  
  
#Set the referenced table and schema.   
$fk.ReferencedTable = "Employee"  
$fk.ReferencedTableSchema = "HumanResources"  
  
#Create the foreign key on the instance of SQL Server.   
$fk.Create()  
```  
  
## <a name="sample-foreign-keys-primary-keys-and-unique-constraint-columns"></a><span data-ttu-id="870d2-120">Образец. Внешние ключи, первичные ключи и столбцы с ограничением уникальности</span><span class="sxs-lookup"><span data-stu-id="870d2-120">Sample: Foreign Keys, Primary Keys, and Unique Constraint Columns</span></span>  
 <span data-ttu-id="870d2-121">В этом примере демонстрируются следующее:</span><span class="sxs-lookup"><span data-stu-id="870d2-121">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="870d2-122">Создать внешний ключ для существующего объекта.</span><span class="sxs-lookup"><span data-stu-id="870d2-122">Finding a foreign key on an existing object.</span></span>  
  
-   <span data-ttu-id="870d2-123">Создать первичный ключ.</span><span class="sxs-lookup"><span data-stu-id="870d2-123">How to create a primary key.</span></span>  
  
-   <span data-ttu-id="870d2-124">Создать столбец с ограничением уникальности.</span><span class="sxs-lookup"><span data-stu-id="870d2-124">How to create a unique constraint column.</span></span>  
  
 <span data-ttu-id="870d2-125">Версия на языке C#:</span><span class="sxs-lookup"><span data-stu-id="870d2-125">The C# version of this sample:</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:microsoft.sqlserver.management.sdk.sfc.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll  
// /r:Microsoft.SqlServer.SqlEnum.dll  
  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
using Microsoft.SqlServer.Management.Common;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // PK Table  
      Table tab1 = new Table(db, "Table1");  
  
      // Define Columns and add them to the table  
      Column col1 = new Column(tab1, "Col1", DataType.Int);  
  
      col1.Nullable = false;  
      tab1.Columns.Add(col1);  
      Column col2 = new Column(tab1, "Col2", DataType.NVarChar(50));  
      tab1.Columns.Add(col2);  
      Column col3 = new Column(tab1, "Col3", DataType.DateTime);  
      tab1.Columns.Add(col3);  
  
      // Create the ftable  
      tab1.Create();  
  
      // Define Index object on the table by supplying the Table1 as the parent table and the primary key name in the constructor.  
      Index pk = new Index(tab1, "Table1_PK");  
      pk.IndexKeyType = IndexKeyType.DriPrimaryKey;  
  
      // Add Col1 as the Index Column  
      IndexedColumn idxCol1 = new IndexedColumn(pk, "Col1");  
      pk.IndexedColumns.Add(idxCol1);  
  
      // Create the Primary Key  
      pk.Create();  
  
      // Create Unique Index on the table  
      Index unique = new Index(tab1, "Table1_Unique");  
      unique.IndexKeyType = IndexKeyType.DriUniqueKey;  
  
      // Add Col1 as the Unique Index Column  
      IndexedColumn idxCol2 = new IndexedColumn(unique, "Col2");  
      unique.IndexedColumns.Add(idxCol2);  
  
      // Create the Unique Index  
      unique.Create();  
  
      // Create Table2                    
      Table tab2 = new Table(db, "Table2");  
      Column col21 = new Column(tab2, "Col21", DataType.NChar(20));  
      tab2.Columns.Add(col21);  
      Column col22 = new Column(tab2, "Col22", DataType.Int);  
      tab2.Columns.Add(col22);  
      tab2.Create();  
  
      // Define a Foreign Key object variable by supplying the Table2 as the parent table and the foreign key name in the constructor.   
      ForeignKey fk = new ForeignKey(tab2, "Table2_FK");  
  
      // Add Col22 as the foreign key column.   
      ForeignKeyColumn fkc = new ForeignKeyColumn(fk, "Col22", "Col1");  
      fk.Columns.Add(fkc);  
      fk.ReferencedTable = "Table1";  
  
      // Create the foreign key on the instance of SQL Server.   
      fk.Create();                    
  
      // Get list of Foreign Keys on Table2  
      foreach (ForeignKey f in tab2.ForeignKeys) {  
            Console.WriteLine(f.Name + " " + f.ReferencedTable + " " + f.ReferencedKey);  
      }  
  
      // Get list of Foreign Keys referencing table1  
      foreach (Table tab in db.Tables) {  
         if (tab == tab1)  
            continue;  
            foreach (ForeignKey f in tab.ForeignKeys) {  
               if (f.ReferencedTable.Equals(tab1.Name))  
                  Console.WriteLine(f.Name + " " + f.Parent.Name);  
            }  
      }  
   }  
}  
```  
  
 <span data-ttu-id="870d2-126">Версия на языке Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="870d2-126">The Visual Basic version of the sample:</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:microsoft.sqlserver.management.sdk.sfc.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll  
' /r:Microsoft.SqlServer.SqlEnum.dll  
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
      Dim db As New Database(svr, "TESTDB")  
      db.Create()  
  
      ' PK Table  
      Dim tab1 As New Table(db, "Table1")  
  
      ' Define Columns and add them to the table  
      Dim col1 As New Column(tab1, "Col1", DataType.Int)  
  
      col1.Nullable = False  
      tab1.Columns.Add(col1)  
      Dim col2 As New Column(tab1, "Col2", DataType.NVarChar(50))  
      tab1.Columns.Add(col2)  
      Dim col3 As New Column(tab1, "Col3", DataType.DateTime)  
      tab1.Columns.Add(col3)  
  
      ' Create the ftable  
      tab1.Create()  
  
      ' Define Index object on the table by supplying the Table1 as the parent table and the primary key name in the constructor.  
      Dim pk As New Index(tab1, "Table1_PK")  
      pk.IndexKeyType = IndexKeyType.DriPrimaryKey  
  
      ' Add Col1 as the Index Column  
      Dim idxCol1 As New IndexedColumn(pk, "Col1")  
      pk.IndexedColumns.Add(idxCol1)  
  
      ' Create the Primary Key  
      pk.Create()  
  
      ' Create Unique Index on the table  
      Dim unique As New Index(tab1, "Table1_Unique")  
      unique.IndexKeyType = IndexKeyType.DriUniqueKey  
  
      ' Add Col1 as the Unique Index Column  
      Dim idxCol2 As New IndexedColumn(unique, "Col2")  
      unique.IndexedColumns.Add(idxCol2)  
  
      ' Create the Unique Index  
      unique.Create()  
  
      ' Create Table2                    
      Dim tab2 As New Table(db, "Table2")  
      Dim col21 As New Column(tab2, "Col21", DataType.NChar(20))  
      tab2.Columns.Add(col21)  
      Dim col22 As New Column(tab2, "Col22", DataType.Int)  
      tab2.Columns.Add(col22)  
      tab2.Create()  
  
      ' Define a Foreign Key object variable by supplying the Table2 as the parent table and the foreign key name in the constructor.   
      Dim fk As New ForeignKey(tab2, "Table2_FK")  
  
      ' Add Col22 as the foreign key column.   
      Dim fkc As New ForeignKeyColumn(fk, "Col22", "Col1")  
      fk.Columns.Add(fkc)  
      fk.ReferencedTable = "Table1"  
  
      ' Create the foreign key on the instance of SQL Server.   
      fk.Create()  
  
      ' Get list of Foreign Keys on Table2  
      For Each f As ForeignKey In tab2.ForeignKeys  
         Console.WriteLine((f.Name + " " + f.ReferencedTable & " ") + f.ReferencedKey)  
      Next  
  
      ' Get list of Foreign Keys referencing table1  
      For Each tab As Table In db.Tables  
         If (tab.Name.Equals(tab1.Name)) Then  
            Continue For  
         End If  
         For Each f As ForeignKey In tab.ForeignKeys  
            If f.ReferencedTable.Equals(tab1.Name) Then  
               Console.WriteLine(f.Name + " " + f.Parent.Name)  
            End If  
         Next  
      Next  
   End Sub  
End Class  
```  
