---
title: MSSQLSERVER_207 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 207 (Database Engine error)
ms.assetid: d1ab00c7-0331-437a-84fe-bae53b82feec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd6044c08ecd5a73f539bfbc1139d6257c2db9d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730714"
---
# <a name="mssqlserver_207"></a>MSSQLSERVER_207
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|207|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQ_BADCOL|  
|Текст сообщения|Недопустимое имя столбца «%.*ls».|  
  
## <a name="explanation"></a>Объяснение  
 Возможны следующие причины возникновения этой ошибки запроса.  
  
-   Имя столбца неправильно указано, либо столбец не существует ни в одной указанной таблице.  
  
-   Параметры сортировки базы данных учитывают регистр, а регистр имени столбца, указанный в запросе, не совпадает с регистром столбца, определенного в таблице. Например, если столбец определен в таблице как **LastName**, а для базы данных используются параметры сортировки с учетом регистра, при выполнении запросов, в которых для этого столбца указано имя **Lastname** или **lastname**, возникнет ошибка 207, так как имена столбцов не совпадают.  
  
-   Псевдоним столбца, определенный в предложении SELECT, упоминается в другом предложении, например WHERE или GROUP BY. Например, следующий запрос определяет псевдоним столбца `Year` в предложении SELECT и упоминает его в предложении GROUP BY.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year, SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY Year;  
    ```  
  
     Порядок логической обработки предложений запросов вызывает возвращение ошибки 207. Далее приводится порядок обработки.  
  
    1.  FROM  
  
    2.  ON  
  
    3.  JOIN  
  
    4.  WHERE  
  
    5.  GROUP BY  
  
    6.  WITH CUBE или WITH ROLLUP  
  
    7.  HAVING  
  
    8.  SELECT  
  
    9. DISTINCT  
  
    10. ORDER BY  
  
    11. В начало  
  
     Поскольку псевдоним столбца не определяется до обработки предложения SELECT, псевдоним неизвестен при обработке предложения GROUP BY.  
  
-   Инструкция MERGE выдает эту ошибку, когда исходная таблица в предложении WHEN NOT MATCHED BY SOURCE не возвращает строк, а предложение *<merge_matched>* ссылается на столбцы в исходной таблице. Данная ошибка возникает из-за того, что невозможно обратиться к столбцам в исходной таблице, если запрос не возвратил строк. Например, предложение `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` может стать причиной ошибки инструкции из-за недоступности столбца `Col1` в исходной таблице.  
  
## <a name="user-action"></a>Действие пользователя  
 Проверьте следующую информацию и исправьте инструкцию соответствующим образом.  
  
-   Наличие имени столбца в таблице и правильность его указания. В следующем примере запрос к представлению каталога **sys.columns** возвращает все имена столбцов для этой таблицы.  
  
    ```  
    SELECT name FROM sys.columns WHERE object_id = OBJECT_ID('schema_name.table_name');  
    ```  
  
-   Учет регистра в параметрах сортировки базы данных. Следующая инструкция возвращает параметры сортировки для указанной базы данных.  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     Аббревиатура CS в имени параметров сортировки означает, что учитывается регистр символов. Например, Latin1_General_CS_AS определяет параметры сортировки с учетом диакритических знаков и с учетом регистра. Измените имя столбца, чтобы оно совпадало с тем именем столбца, которое было определено в таблице, вплоть до регистра.  
  
-   Неправильное упоминание псевдонима столбца. Измените инструкцию, повторив выражение, определяющее псевдоним, в соответствующем предложении или использовав производную таблицу. В следующем примере в предложении GROUP BY повторяются выражения, определяющие псевдоним `Year`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year ,SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY DATEPART(yyyy,OrderDate);  
    ```  
  
     В следующем примере производная таблица используется для того, чтобы сделать псевдоним доступным для других предложений в запросе. Следует заметить, что псевдоним `Year` определяется в предложении FROM, которое обрабатывается в первую очередь, что делает псевдоним доступным для использования в других предложениях запроса.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT d.Year, SUM(TotalDue) AS Total  
    FROM (SELECT DATEPART(yyyy,OrderDate) AS Year, TotalDue  
          FROM Sales.SalesOrderHeader)AS d  
    GROUP BY Year;  
    ```  
  
-   В предложении WHEN NOT MATCHED BY SOURCE инструкции MERGE упоминается значение к которому может осуществляться доступ. Измените инструкцию MERGE, чтобы по крайней мере одна строка была возвращена исходной таблицей в предложении WHEN NOT MATCHED BY SOURCE. Например, может потребоваться добавить или изменить условие поиска, указанное для предложения. В качестве альтернативы можно изменить предложение, чтобы указать значение, не ссылающееся на исходную таблицу. Например, `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>`.  
  
## <a name="see-also"></a>См. также:  
 [MERGE (Transact-SQL)](/sql/t-sql/statements/merge-transact-sql)   
 [FROM (Transact-SQL)](/sql/t-sql/queries/from-transact-sql)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql)  
  
  
