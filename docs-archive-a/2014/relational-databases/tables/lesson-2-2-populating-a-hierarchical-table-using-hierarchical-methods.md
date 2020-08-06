---
title: Заполнение иерархической таблицы с помощью иерархических методов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID
ms.assetid: 2c95fa60-5b8e-4a05-ac09-cffe2b05900a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef99d711a772a075f568a83f5d56fcecaaa598f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665917"
---
# <a name="populating-a-hierarchical-table-using-hierarchical-methods"></a>Заполнение иерархической таблицы с помощью иерархических методов
  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] работает 8 человек. Иерархический список сотрудников выглядит следующим образом.  
  
 **Дэвид**, **EmployeeID** 6, начальник отдела маркетинга. В подчинении у **Дэвида**находятся три специалиста по маркетингу:  
  
-   **Сара**, **EmployeeID** 46  
  
-   **Джон**, **EmployeeID** 271  
  
-   **Джил**, **EmployeeID** 119  
  
 Маркетолог **Ванида** (**EmployeeID** 269), подчиняется **Саре**, а маркетолог **Мэри** (**EmployeeID** 272) подчиняется **Джону**.  
  
### <a name="to-insert-the-root-of-the-hierarchy-tree"></a>Вставка корневого элемента иерархического дерева  
  
1.  В следующем примере запись **Дэвид** (начальник отдела маркетинга) вставляется таблицу в качестве корневого элемента иерархии. **OrdLevel** — вычисляемый столбец. Следовательно, он не является частью инструкции INSERT. Для вставки первой записи в вершину иерархии используется метод [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) .  
  
    ```  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  Для просмотра начальной строки таблицы используйте следующий код:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
 Как и на предыдущем занятии, для преобразования данных типа `hierarchyid` в более наглядный формат используется метод `ToString()`.  
  
### <a name="to-insert-a-subordinate-employee"></a>Вставка записи подчиненного  
  
1.  **Сара** подчиняется **Дэвиду**. Чтобы вставить узел **Sariya** , необходимо создать соответствующее значение **OrgNode** типа данных `hierarchyid` . Следующий код создает переменную типа `hierarchyid` и присваивает ей корневое значение OrgNode таблицы. Затем эта переменная используется методом [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) для вставки строки, представляющей подчиненный узел. `GetDescendant` принимает два аргумента. Вот список вариантов с разными значениями аргументов.  
  
    -   Если родительская запись — NULL, `GetDescendant` возвращает значение NULL.  
  
    -   Если родительская запись — не NULL, а потомки child1 и child2 — NULL, метод `GetDescendant` возвращает одного потомка данного родителя.  
  
    -   Если родительская запись и потомок child1 — не NULL, а потомок child2 равен NULL, метод `GetDescendant` возвращает значение потомка родителя, который больше чем child1.  
  
    -   Если родитель и потомок child2 — не NULL, а потомок child1 равен NULL, метод `GetDescendant` возвращает значение потомка родителя, который меньше child2.  
  
    -   Если родитель, child1 и child2 не равны NULL, метод `GetDescendant` возвращает потомка родителя, который больше child1 и меньше child2.  
  
     В следующем примере в качестве аргументов корневого родительского элемента используются значения `(NULL, NULL)` , так как таблица пока не содержит никаких строк, кроме корневой. Чтобы вставить запись **Сара**, выполните следующий код:  
  
    ```  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  Чтобы обратиться к таблице и просмотреть вставленные записи, повторите запрос из первой процедуры:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="to-create-a-procedure-for-entering-new-nodes"></a>Создание процедуры ввода новых узлов  
  
1.  Для упрощения ввода данных можно создать следующую хранимую процедуру, вставляющую данные о сотрудниках в таблицу **EmployeeOrg** . Входные данные процедуры — это данные о добавляемом сотруднике. Это **EmployeeID** руководителя нового сотрудника, **EmployeeID** самого сотрудника, а также их имена и должности. В процедуре используются методы `GetDescendant()` и [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) . Чтобы создать процедуру, выполните следующий код:  
  
    ```  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  В следующем примере вставляются записи об остальных 4 сотрудниках, прямо или косвенно подчиняющихся **Дэвиду**.  
  
    ```  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  Для просмотра строк таблицы **EmployeeOrg** выполните следующий запрос:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    /1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
 Теперь таблица полностью заполнена записями о сотрудниках отдела маркетинга.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание запросов к иерархической таблице с помощью иерархических методов](lesson-2-3-querying-a-hierarchical-table-using-hierarchy-methods.md)  
  
  
