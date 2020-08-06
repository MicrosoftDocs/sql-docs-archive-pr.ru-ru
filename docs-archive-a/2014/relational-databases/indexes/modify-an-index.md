---
title: Изменение индекса | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], modifying
- modifying indexes
- index changes [SQL Server]
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af9293966afce8372f5b83a579418c546c82816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739968"
---
# <a name="modify-an-index"></a>Изменение индекса
  В этом разделе описывается изменение индекса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!IMPORTANT]  
>  Индексы, созданные в результате применения ограничения PRIMARY KEY или UNIQUE, изменить этим способом нельзя. Вместо этого необходимо изменить ограничение.  
  
 **В этом разделе**  
  
-   **Для изменения индекса используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-an-index"></a>Изменение индекса  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните **Базы данных**, затем базу данных, которой принадлежит таблица, и **Таблицы**.  
  
3.  Раскройте таблицу, которой принадлежит индекс, а затем — узел **Индексы**.  
  
4.  Щелкните правой кнопкой мыши индекс, который нужно изменить, и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства индекса** внесите необходимые изменения. Например, можно добавить или удалить столбец из ключа индекса или изменить значение параметра индекса.  
  
#### <a name="to-modify-index-columns"></a>Изменение столбцов индекса  
  
1.  Чтобы добавить столбец индекса, удалить его или изменить его позицию, выберите в диалоговом окне **Свойства индекса** страницу **Общие** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-modify-an-index"></a>Изменение индекса  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере индекс по столбцу `ProductID` таблицы `Production.WorkOrder` удаляется и создается вновь с помощью параметра `DROP_EXISTING` . Указываются также параметры `FILLFACTOR` и `PAD_INDEX`.  
  
     [!code-sql[IndexDDL#CreateIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/createindex.sql#createindex4)]  
  
     В следующем примере с помощью инструкции ALTER INDEX задаются несколько параметров для индекса `AK_SalesOrderHeader_SalesOrderNumber`.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
#### <a name="to-modify-index-columns"></a>Изменение столбцов индекса  
  
1.  Чтобы добавить, удалить или изменить позицию столбца индекса, необходимо удалить и повторно создать индекс.  
  
## <a name="see-also"></a>См. также:  
 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)   
 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)   
 [INDEXPROPERTY (Transact-SQL)](/sql/t-sql/functions/indexproperty-transact-sql)   
 [sys.indexes (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)   
 [sys.index_columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)   
 [Установка параметров индекса](set-index-options.md)   
 [Переименование индексов](indexes.md)  
  
  
