---
title: Занятие 3. Определение набора данных для табличного отчета (службы Reporting Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 33fe48a60db2e7d15d205a4bff6205347f95c61c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657570"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>Занятие 3. Определение набора данных для табличного отчета (службы Reporting Services)
  После определения источника данных необходимо определить набор данных. В службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]данные, используемые в отчетах, содержатся в *наборе данных*. Набор данных содержит указатель на источник данных и запрос, используемый в отчете, а также вычисляемые поля и переменные.  
  
 Чтобы создать запрос, можно использовать «Конструктор запросов». В этом учебнике будет создан запрос, извлекающий сведения о заказах на продажу из [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных **2008** .  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>Определение запроса Transact-SQL для данных отчета  
  
1.  В области **данных отчета** нажмите кнопку **создать**, а затем выберите **набор данных...**. Откроется диалоговое окно **Свойства набора данных** .  
  
2.  В поле **Имя** введите **AdventureWorksDataset**.  
  
3.  Выберите **Использовать набор данных, внедренный в отчет**.  
  
4.  Убедитесь, что имя источника данных, AdventureWorks2012, находится в текстовом поле **источник данных** , а **тип запроса** — **Text**.  
  
5.  Введите или скопируйте и вставьте приведенный ниже запрос Transact-SQL в поле **Запрос** .  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
6.  Нажмите кнопку **Конструктор запросов** (необязательно). В текстовом конструкторе запросов будет отображен запрос. Вы можете переключиться к графическому конструктору запросов, нажав кнопку **Изменить как текст**. Просмотрите результаты запроса, нажав кнопку выполнить **(!)** на панели инструментов конструктора запросов.  
  
     Будут показаны данные из шести полей четырех различных таблиц из базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . В запросе используется возможность псевдонимов языка Transact-SQL. Например, таблица SalesOrderHeader называется soh.  
  
     Нажмите кнопку **ОК** для выхода из конструктора запросов.  
  
7.  Нажмите кнопку **ОК** для выхода из диалогового окна **Свойства набора данных** .  
  
     Поля и набор данных **AdventureWorksDataset** появятся в области данных отчета.  
  
## <a name="next-task"></a>Следующая задача  
 Определен запрос, получающий данные для отчета. Далее предстоит создать макет отчета. См. [Занятие 4. Добавление таблицы в отчет (службы Reporting Services)](lesson-4-adding-a-table-to-the-report-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Средства проектирования запросов в конструктор отчетов SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md)   
 [Тип подключения SQL Server &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md)   
 [Руководство. Составление инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
