---
title: Файлы форматирования для импорта или экспорта данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], format files
- bulk importing [SQL Server], format files
- format files [SQL Server]
ms.assetid: b7b97d68-4336-4091-aee4-1941fab568e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1143690f0322fef2612fde51eebcb7427ee237ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666603"
---
# <a name="format-files-for-importing-or-exporting-data-sql-server"></a>Файлы форматирования для импорта или экспорта данных (SQL Server)
  Если выполняется массовый импорт данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или массовый экспорт данных из таблицы, можно использовать *файл форматирования* для сохранения всех сведений о формате, необходимых для массового экспорта или массового импорта данных. Это включает сведения о формате каждого поля в файле данных для этой таблицы.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживает два типа файлов форматирования: XML-файлы и файлы форматирования в формате, отличном от XML. Файлы форматирования как в XML, так и в другом формате, содержат описания каждого поля в файле данных, а XML-файлы форматирования содержат еще описания соответствующих столбцов таблицы. Как правило, XML-файлы и файлы форматирования в формате, отличном от XML взаимозаменяемы. Однако рекомендуется пользоваться XML-синтаксисом новых файлов форматирования, так как он обеспечивает ряд преимуществ перед файлами форматирования в формате, отличном от XML. Дополнительные сведения см. в разделе [XML-файлы форматирования (SQL Server)](xml-format-files-sql-server.md).  
  
 
  
##  <a name="benefits-of-format-files"></a><a name="Benefits"></a> Преимущества файлов форматирования  
  
-   Предоставляет гибкую систему записи файлов данных, которая вообще не требует или требует лишь небольших правок для совместимости с другими форматами данных или для чтения файлов данных, созданных в другом программном обеспечении.  
  
-   Позволяет выполнять массовый импорт данных без необходимости добавлять или удалять ненужные данные, а также изменять порядок существующих данных в файле данных. Файлы форматирования особенно полезны в том случае, если существует несоответствие между полями в файле данных и столбцами в таблице.  
  
##  <a name="examples-of-format-files"></a><a name="ExamplesOfFFs"></a> Примеры файлов форматирования  
 В следующих примерах показана структура файлов форматирования в формате, отличном от XML, и XML-файлов форматирования. Эти файлы форматирования соответствуют таблице `HumanResources.myTeam` в образце базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Эта таблица содержит четыре столбца: `EmployeeID`, `Name`, `Title`и `ModifiedDate`.  
  
> [!NOTE]  
>  Дополнительные сведения о таблице и способе ее создания см. в разделе [Образец таблицы HumanResources.myTeam (SQL Server)](humanresources-myteam-sample-table-sql-server.md).  
  
### <a name="a-using-a-non-xml-format-file"></a>A. Использование файла форматирования в формате, отличном от XML  
 Следующий файл форматирования в формате, отличном от XML использует собственный формат данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для таблицы `HumanResources.myTeam` . Этот файл форматирования был создан с помощью следующей команды `bcp` :  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Fmt -n -T   
The contents of this format file are as follows: 9.0  
4  
1       SQLSMALLINT   0       2       ""   1     EmployeeID               ""  
2       SQLNCHAR      2       100     ""   2     Name                     SQL_Latin1_General_CP1_CI_AS  
3       SQLNCHAR      2       100     ""   3     Title                    SQL_Latin1_General_CP1_CI_AS  
4       SQLNCHAR      2       100     ""   4     Background               SQL_Latin1_General_CP1_CI_AS  
```  
  
 Дополнительные сведения см в разделе [Файлы формата, отличные от XML (SQL Server)](non-xml-format-files-sql-server.md).  
  
 
  
### <a name="b-using-an-xml-format-file"></a>Б. Использование XML-файла форматирования  
 Следующий XML-файл форматирования использует собственный формат данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для таблицы `HumanResources.myTeam` . Этот файл форматирования был создан с помощью следующей команды `bcp` :  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Xml -x -n -T   
```  
  
 Файл форматирования содержит:  
  
```  
 <?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="EmployeeID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Title" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Background" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 Дополнительные сведения см. в разделе [XML-файлы форматирования (SQL Server)](xml-format-files-sql-server.md).  
  

  
##  <a name="when-is-a-format-file-required"></a><a name="WhenFFrequired"></a> Когда необходим файл форматирования?  
 Инструкция INSERT... SELECT * FROM OPENROWSET(BULK...) всегда требует наличия файла форматирования.  
  
-   Для **bcp** или BULK INSERT использование файла форматирования в простых ситуациях необязательно, и в этом редко возникает необходимость. Однако при выполнении сложных операций массового импорта файл форматирования очень часто необходим.  
  
 Файлы форматирования необходимы, если:  
  
-   один и тот же файл данных используется в качестве источника для нескольких таблиц с разными схемами;  
  
-   число полей в файле данных отличается от числа столбцов в целевой таблице, например:  
  
    -   целевая таблица содержит по крайней мере один столбец, для которого либо задано значение по умолчанию, либо разрешено значение NULL;  
  
    -   пользователи не имеют разрешений на выполнение инструкций SELECT/INSERT в одном или нескольких столбцах таблицы;  
  
    -   один и тот же файл данных используется для двух или более таблиц с разными схемами.  
  
-   порядок столбцов в файле данных отличается от порядка столбцов в таблице;  
  
-   завершающие символы или длины префиксов отличаются в столбцах файла данных.  
  
> [!NOTE]  
>  Если файл форматирования отсутствует и в команде **bcp** задан параметр формата данных ( **-n**, **-c**, **-w**или **-N**) либо в операции BULK INSERT задан параметр DATAFILETYPE, указанный формат данных используется как метод интерпретации полей в файле данных по умолчанию.  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Использование файла форматирования для пропуска поля данных (SQL Server)](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  

  
## <a name="see-also"></a>См. также:  
 [Файлы формата, отличные от XML (SQL Server)](non-xml-format-files-sql-server.md)   
 [XML-файлы форматирования (SQL Server)](xml-format-files-sql-server.md)   
 [Форматы данных для массового экспорта или импорта (SQL Server)](data-formats-for-bulk-import-or-bulk-export-sql-server.md)  
  
  
