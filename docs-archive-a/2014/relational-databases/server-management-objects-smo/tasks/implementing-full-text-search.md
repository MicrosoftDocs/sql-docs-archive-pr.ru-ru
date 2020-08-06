---
title: Реализация полнотекстового поиска | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- full-text search [SMO]
ms.assetid: 9ce9ad9c-f671-4760-90b5-e0c8ca051473
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8b797e2a38c9136c34b7058b539fca522e03229
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728158"
---
# <a name="implementing-full-text-search"></a>Реализация полнотекстового поиска
  Полнотекстовый поиск доступен для отдельных экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и представлен в SMO объектом <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A>. Объект <xref:Microsoft.SqlServer.Management.Smo.FullTextService> размещен в объекте `Server`. Он используется для управления параметрами конфигурации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] службы полнотекстового поиска. Объект <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> принадлежит объекту <xref:Microsoft.SqlServer.Management.Smo.Database> и является коллекцией объектов <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog>, представляющих полнотекстовые каталоги, определенные в базе данных. Для каждой таблицы можно определить только один полнотекстовый индекс (в отличие от обычных индексов). Индекс представлен объектом <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> в объекте <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
 Чтобы создать службу полнотекстового поиска, необходимо иметь полнотекстовый каталог, определенный в базе данных, и индекс полнотекстового поиска, определенный на одной из таблиц в базе данных.  
  
 Сначала создайте полнотекстовый каталог для базы данных, вызвав конструктор <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> и указав имя каталога. Затем создайте полнотекстовый индекс, вызвав конструктор и указав таблицу, по которой он будет создан. Затем для полнотекстового индекса можно добавить столбцы индекса с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn>, указав имя столбца в таблице. Потом укажите в свойстве <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> путь к созданному каталогу. Наконец, вызовите метод <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> и создайте полнотекстовый индекс для экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Создание проекта Visual C&#35; SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-full-text-search-service-in-visual-basic"></a>Создание службы полнотекстового поиска на языке Visual Basic  
 В этом примере кода создается каталог полнотекстового поиска для таблицы `ProductCategory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Затем создается индекс полнотекстового поиска на столбце имен в таблице `ProductCategory`. Для индекса полнотекстового поиска необходимо, чтобы для столбца уже был определен уникальный индекс.  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.SqlEnum.dll   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      ' Connect to the local, default instance of SQL Server.  
      Dim srv As Server = Nothing  
      srv = New Server()  
  
      ' Reference the AdventureWorks database.  
      Dim db As Database = Nothing  
      db = srv.Databases("AdventureWorks")  
  
      ' Reference the ProductCategory table.  
      Dim tb As Table = Nothing  
      tb = db.Tables("ProductCategory", "Production")  
  
      ' Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      Dim ftc As FullTextCatalog = Nothing  
      ftc = New FullTextCatalog(db, "Test_Catalog")  
      ftc.IsDefault = True  
  
      ' Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create()  
  
      ' Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      Dim fti As FullTextIndex = Nothing  
      fti = New FullTextIndex(tb)  
  
      ' Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      Dim ftic As FullTextIndexColumn = Nothing  
      ftic = New FullTextIndexColumn(fti, "Name")  
  
      ' Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic)  
      fti.ChangeTracking = ChangeTracking.Automatic  
  
      ' Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
      ' Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog"  
  
      ' Create the Full Text Search index on the instance of SQL Server.  
      fti.Create()  
   End Sub  
End Class  
```  
  
## <a name="creating-a-full-text-search-service-in-visual-c"></a>Создание службы полнотекстового поиска на языке Visual C#  
 В этом примере кода создается каталог полнотекстового поиска для таблицы `ProductCategory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Затем создается индекс полнотекстового поиска на столбце имен в таблице `ProductCategory`. Для индекса полнотекстового поиска необходимо, чтобы для столбца уже был определен уникальный индекс.  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.SqlEnum.dll   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.  
      Server srv = default(Server);  
      srv = new Server();  
  
      // Reference the AdventureWorks database.  
      Database db = default(Database);  
      db = srv.Databases ["AdventureWorks"];  
  
      // Reference the ProductCategory table.  
      Table tb = default(Table);  
      tb = db.Tables["ProductCategory", "Production"];  
  
      // Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      FullTextCatalog ftc = default(FullTextCatalog);  
      ftc = new FullTextCatalog(db, "Test_Catalog");  
      ftc.IsDefault = true;  
  
      // Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create();  
  
      // Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      FullTextIndex fti = default(FullTextIndex);  
      fti = new FullTextIndex(tb);  
  
      // Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      FullTextIndexColumn ftic = default(FullTextIndexColumn);  
      ftic = new FullTextIndexColumn(fti, "Name");  
  
      // Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic);  
      fti.ChangeTracking = ChangeTracking.Automatic;  
  
      // Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name";  
  
      // Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog";  
  
      // Create the Full Text Search index on the instance of SQL Server.  
      fti.Create();  
   }  
}  
```  
  
## <a name="creating-a-full-text-search-service-in-powershell"></a>Создание службы полнотекстового поиска в PowerShell  
 В этом примере кода создается каталог полнотекстового поиска для таблицы `ProductCategory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Затем создается индекс полнотекстового поиска на столбце имен в таблице `ProductCategory`. Для индекса полнотекстового поиска необходимо, чтобы для столбца уже был определен уникальный индекс.  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = Get-Item AdventureWorks2012  
  
CD AdventureWorks\tables  
  
#Get a reference to the table  
$tb = Get-Item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -ArgumentList $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -ArgumentList $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -ArgumentList $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
