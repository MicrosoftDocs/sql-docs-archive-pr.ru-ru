---
title: Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- mapping columns to fields during import [SQL Server]
- format files [SQL Server], mapping columns to fields
ms.assetid: e7ee4f7e-24c4-4eb7-84d2-41e57ccc1ef1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7de0b5ce486f187a1bdd27197984aa3c411f4a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657103"
---
# <a name="use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server"></a><span data-ttu-id="81a06-102">Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="81a06-102">Use a Format File to Map Table Columns to Data-File Fields (SQL Server)</span></span>
  <span data-ttu-id="81a06-103">Файл данных может содержать поля, выстроенные в порядке, отличном от порядка соответствующих столбцов в таблице.</span><span class="sxs-lookup"><span data-stu-id="81a06-103">A data file can contain fields arranged in a different order from the corresponding columns in the table.</span></span> <span data-ttu-id="81a06-104">В этом подразделе описывается изменение файлов форматирования в формате XML и в формате, отличном от XML для импорта файла данных, поля которого выстроены в ином порядке, нежели столбцы таблицы.</span><span class="sxs-lookup"><span data-stu-id="81a06-104">This topic presents both non-XML and XML format files that have been modified to accommodate a data file whose fields are arranged in a different order from the table columns.</span></span> <span data-ttu-id="81a06-105">Измененный файл форматирования сопоставляет поля данных соответствующим столбцам таблицы.</span><span class="sxs-lookup"><span data-stu-id="81a06-105">The modified format file maps the data fields to their corresponding table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81a06-106">Файл форматирования в формате, отличном от XML, или XML-файл форматирования можно использовать для выполнения операций импорта файла данных в таблицу с помощью команды **bcp** , BULK INSERT инструкции или INSERT... SELECT \* FROM OPENROWSET (BULK...).</span><span class="sxs-lookup"><span data-stu-id="81a06-106">Either a non-XML format file or an XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="81a06-107">Дополнительные сведения см. в разделе [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="81a06-107">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="81a06-108">Образец таблицы и файла данных</span><span class="sxs-lookup"><span data-stu-id="81a06-108">Sample Table and Data File</span></span>  
 <span data-ttu-id="81a06-109">В примерах этого подраздела используются следующие таблица и файл данных.</span><span class="sxs-lookup"><span data-stu-id="81a06-109">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="81a06-110">Образец таблицы</span><span class="sxs-lookup"><span data-stu-id="81a06-110">Sample Table</span></span>  
 <span data-ttu-id="81a06-111">Для работы примеров этого раздела необходимо, чтобы в образце базы данных `myTestOrder` в схеме [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] была создана таблица `dbo` .</span><span class="sxs-lookup"><span data-stu-id="81a06-111">The examples in this topic require that a table named `myTestOrder` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="81a06-112">Чтобы создать эту таблицу, в редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните:</span><span class="sxs-lookup"><span data-stu-id="81a06-112">To create this table, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestOrder   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) ,  
   Col3 nvarchar(50) ,   
   Col4 nvarchar(50)   
   );  
GO  
  
```  
  
### <a name="data-file"></a><span data-ttu-id="81a06-113">Файл данных</span><span class="sxs-lookup"><span data-stu-id="81a06-113">Data File</span></span>  
 <span data-ttu-id="81a06-114">Файл данных `myTestOrder-c.txt`содержит следующие записи:</span><span class="sxs-lookup"><span data-stu-id="81a06-114">The data file, `myTestOrder-c.txt`, contains the following records:</span></span>  
  
```  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
  
```  
  
 <span data-ttu-id="81a06-115">При массовом импорте данных из `myTestSkipCol2-c.dat` в таблицу `myTestSkipCol` файл форматирования должен сопоставить первое поле данных со столбцом `Col3`, второе поле данных — со столбцом `Col2`, третье поле данных — со столбцом `Col1`, а четвертое поле данных — со столбцом `Col4`.</span><span class="sxs-lookup"><span data-stu-id="81a06-115">To bulk import data from `myTestSkipCol2-c.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col3`, the second data field to `Col2`, the third data field to `Col1`, and the fourth data field to `Col4`.</span></span>  
  
## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="81a06-116">Использование файла форматирования в формате, отличном от XML</span><span class="sxs-lookup"><span data-stu-id="81a06-116">Using a Non-XML Format File</span></span>  
 <span data-ttu-id="81a06-117">Изменение порядка сопоставления столбцов достигается путем изменения значения порядка, чтобы указать для столбца позицию соответствующего поля данных.</span><span class="sxs-lookup"><span data-stu-id="81a06-117">You can change the order of a column mapping by changing the order value for the column to indicate the position of the corresponding data field.</span></span>  
  
 <span data-ttu-id="81a06-118">В следующем образце файла форматирования формата, отличного от XML присутствует файл форматирования `myTestOrder.fmt`, который сопоставляет поля в файле `myTestOrder-c.txt` со столбцами таблицы `myTestOrder`.</span><span class="sxs-lookup"><span data-stu-id="81a06-118">The following sample non-XML format file presents a format file, `myTestOrder.fmt`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table.</span></span> <span data-ttu-id="81a06-119">Дополнительные сведения о создании файлов данных и таблиц см. в находящемся выше разделе «Образец таблицы и файла данных».</span><span class="sxs-lookup"><span data-stu-id="81a06-119">For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="81a06-120">Файл форматирования имеет символьный формат данных.</span><span class="sxs-lookup"><span data-stu-id="81a06-120">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="81a06-121">В нем содержатся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="81a06-121">The format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       100     ","     3     Col3               SQL_Latin1_General_CP1_CI_AS  
2       SQLCHAR       0       100     ","     2     Col2               SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       7       ","     1     Col1               ""  
4       SQLCHAR       0       100     "\r\n"  4     Col4               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="81a06-122">Дополнительные сведения о структуре файлов форматирования в формате, отличном от XML, см. в статье [Файлы формата, отличные от XML (SQL Server)](xml-format-files-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="81a06-122">For more information about the layout of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="81a06-123">Пример</span><span class="sxs-lookup"><span data-stu-id="81a06-123">Example</span></span>  
 <span data-ttu-id="81a06-124">В следующем примере инструкция `BULK INSERT` производит массовый импорт данных из файла данных `myTestOrder-c.txt` в образец таблицы `myTestOrder` с использованием файла форматирования в формате, отличном от XML: `myTestOrder.fmt`.</span><span class="sxs-lookup"><span data-stu-id="81a06-124">The following example uses a `BULK INSERT` statement to bulk import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.fmt` non-XML format file.</span></span>  
  
 <span data-ttu-id="81a06-125">В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните:</span><span class="sxs-lookup"><span data-stu-id="81a06-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestOrder  
FROM 'C:\myTestOrder-c.txt'   
WITH (formatfile='C:\myTestOrder.fmt');  
GO  
  
```  
  
## <a name="using-an-xml-format-file"></a><span data-ttu-id="81a06-126">Использование XML-файла форматирования</span><span class="sxs-lookup"><span data-stu-id="81a06-126">Using an XML Format File</span></span>  
 <span data-ttu-id="81a06-127">Следующий образец файла форматирования в формате, отличном от XML представляет файл форматирования `myTestOrder.xml`, который сопоставляет поля в файле `myTestOrder-c.txt` столбцам таблицы `myTestOrder` (сведения о создании таблицы и файла данных см. в расположенном выше разделе «Образец таблицы и файла данных»).</span><span class="sxs-lookup"><span data-stu-id="81a06-127">The following sample non-XML format file presents a format file, `myTestOrder.xml`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="81a06-128">В файле форматирования `myTestOrder.xml` содержатся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="81a06-128">The `myTestOrder.xml` format file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="3" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="1" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="81a06-129">Дополнительные сведения о синтаксисе XML-схемы и дополнительные образцы XML-файлов форматирования см. в статье [XML-файлы форматирования (SQL Server)](xml-format-files-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="81a06-129">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="81a06-130">Пример</span><span class="sxs-lookup"><span data-stu-id="81a06-130">Example</span></span>  
 <span data-ttu-id="81a06-131">Следующий пример использует поставщик массового набора строк `OPENROWSET` для импорта данных из файла данных `myTestOrder-c.txt` в образец таблицы `myTestOrder` с использованием XML-файла форматирования `myTestOrder.xml` .</span><span class="sxs-lookup"><span data-stu-id="81a06-131">The following example uses the `OPENROWSET` bulk rowset provider to import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.xml` XML format file.</span></span> <span data-ttu-id="81a06-132">Инструкция `INSERT... SELECT` задает список столбцов в списке выборки.</span><span class="sxs-lookup"><span data-stu-id="81a06-132">The `INSERT... SELECT` statement specifies the column list in the select list.</span></span>  
  
 <span data-ttu-id="81a06-133">В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните:</span><span class="sxs-lookup"><span data-stu-id="81a06-133">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestOrder   
  SELECT Col1, Col2, Col3, Col4  
      FROM  OPENROWSET(BULK  'C:\myTestOrder-c.txt',  
      FORMATFILE='C:\myTestOrder.Xml'    
       ) AS t1;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="81a06-134">См. также:</span><span class="sxs-lookup"><span data-stu-id="81a06-134">See Also</span></span>  
 <span data-ttu-id="81a06-135">[Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="81a06-135">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="81a06-136">Использование файла форматирования для пропуска поля данных (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="81a06-136">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
  
