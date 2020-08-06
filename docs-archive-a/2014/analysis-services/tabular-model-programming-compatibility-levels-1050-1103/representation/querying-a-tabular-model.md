---
title: Запрос табличной модели | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: b01d45d9-4598-4ded-9a9e-e3419cc3df8e
author: minewiskan
ms.author: owend
ms.openlocfilehash: aa42e1125629ddef24e4815a2b1ed89283912832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657942"
---
# <a name="querying-a-tabular-model"></a>Отправка запроса для табличной модели
  Как разработчик, запросив табличную модель, означает получение данных из табличной базы данных; для этого можно воспользоваться двумя способами: использовать запросы к таблицам в DAX или использовать многомерные выражения и получить данные в том виде, в котором они поступили из куба. Однако, в зависимости от базового режима табличной модели может существовать ограничение на использование только табличных запросов DAX. В режиме DirectQuery можно использовать только табличные запросы DAX.  
  
## <a name="querying-with-adomdnet"></a>Отправка запросов с помощью ADOMD.Net  
 Использовать ADOMD.Net для отправки запросов для табличной модели просто и удобно. Для получения результатов можно отправлять как многомерные выражения, так и табличные выражения запроса из DAX на сервер.  
  
 В следующем коде показано, как передать инструкции запроса табличной модели и получить результаты.  
  
```csharp  
//Function: tabularQueryExecute(string qry, ADOMD.AdomdConnection cnx)  
//   - arg: qry, the tabular query or MDX expression to be evaluated  
//   - arg: cnx, an active and opened ADOMD connection to the database where 'qry' is to be evaluated  
//  
// This function takes a query or mdx expression -qry-, a connection -cnx-  
// and runs the query it against a Tabular Model using ADOMD.net  
//  
// Important note:  
//    If the MDX query contains more than 2 axes (ON COLUMNS, ON ROWS), each axis will come as a new column  
//    If the (All) value of the members in any axis have not been defined, a blank cell is returned. This might be misleading  
//    if the model also has missing values... which are also represented with blank cells.  
private DataTable tabularQueryExecute(string qry, ADOMD.AdomdConnection cnx)  
{  
    ADOMD.AdomdDataAdapter currentDataAdapter = new ADOMD.AdomdDataAdapter(qry, cnx);  
    DataTable tabularResults = new DataTable();  
    currentDataAdapter.Fill(tabularResults);  
    return tabularResults;  
}  
  
```  
  
### <a name="example"></a>Пример  
 Если указанный выше код используется со следующим многомерным выражением:  
  
```  
SELECT { [Measures].[Internet Total Sales], [Measures].[Reseller Total Sales], [Measures].[Total Sales] } ON COLUMNS  
     , NON EMPTY [Product Category].[Product Category Name].MEMBERS ON ROWS "  
     , NON EMPTY [Date].[Calendar Year].members ON 2 \n"  
FROM [Model]  
  
```  
  
 Для образца модели Adventure Works DW Tabular Denali CTP3 в результирующей таблице должны содержаться следующие значения:  
  
|Calendar Year|Имя категории продукта|общие продажи в Интернете|Общие продажи торгового посредника|Объем продаж|  
|-------------------|---------------------------|--------------------------|--------------------------|-----------------|  
|||$29 358 677,22|$80 450 596,98|$109 809 274,20|  
||Принадлежности|$700 759,96|$571 297,93|$1 272 057,89|  
||Велосипеды|$28 318 144,65|$66 302 381,56|$94 620 526,21|  
||Clothing|$339 772,61|$1 777 840,84|$2 117 613,45|  
||Components||$11 799 076,66|$11 799 076,66|  
|2001||$3 266 373,66|$8 065 435,31|$11 331 808,96|  
|2001|Принадлежности||$20 235,36|$20 235,36|  
|2001|Велосипеды|$3 266 373,66|$7 395 348,63|$10 661 722,28|  
|2001|Clothing||$34 376,34|$34 376,34|  
|2001|Components||$615 474,98|$615 474,98|  
|2002||$6 530 343,53|$24 144 429,65|$30 674 773,18|  
|2002|Принадлежности||$92 735,35|$92 735,35|  
|2002|Велосипеды|$6 530 343,53|$19 956 014,67|$26 486 358,20|  
|2002|Clothing||$485 587,15|$485 587,15|  
|2002|Components||$3 610 092,47|$3 610 092,47|  
|2003||$9 791 060,30|$32 202 669,43|$41 993 729,72|  
|2003|Принадлежности|$293 709,71|$296 532,88|$590 242,59|  
|2003|Велосипеды|$9 359 102,62|$25 551 775,07|$34 910 877,69|  
|2003|Clothing|$138 247,97|$871 864,19|$1 010 112,16|  
|2003|Components||$5 482 497,29|$5 482 497,29|  
|2004||$9 770 899,74|$16 038 062,60|$25 808 962,34|  
|2004|Принадлежности|$407 050,25|$161 794,33|$568 844,58|  
|2004|Велосипеды|$9 162 324,85|$13 399 243,18|$22 561 568,03|  
|2004|Clothing|$201 524,64|$386 013,16|$587 537,80|  
|2004|Components||$2 091 011,92|$2 091 011,92|  
  
 Если многомерное выражение заменяется следующим табличным выражением запроса DAX:  
  
```  
DEFINE  
   MEASURE 'Product Category'[Internet Sales] = SUM( 'Internet Sales'[Sales Amount])  
   MEASURE 'Product Category'[Reseller Sales] = SUM('Reseller Sales'[Sales Amount]) \n"  
   EVALUATE ADDCOLUMNS('Product Category', \"Internet Sales - All Years\", 'Product Category'[Internet Sales], \"Reseller Sales - All Years\", 'Product Category'[Reseller Sales])  
  
```  
  
 После отправки на сервер с помощью приведенного выше образца кода для образца модели Adventure Works DW Tabular Denali CTP3 в результирующей таблице должны содержаться следующие значения:  
  
|Идентификатор категории продукта|Альтернативный идентификатор категории продукта|Имя категории продукта|Internet Sales|Товарооборот посредников|  
|-------------------------|-----------------------------------|---------------------------|--------------------|--------------------|  
|4|4|Принадлежности|$700 759,96|$571 297,93|  
|1|1|Велосипеды|$28 318 144,65|$66 302 381,56|  
|3|3|Clothing|$339 772,61|$1 777 840,84|  
|2|2|Components||$11 799 076,66|  
  
  
