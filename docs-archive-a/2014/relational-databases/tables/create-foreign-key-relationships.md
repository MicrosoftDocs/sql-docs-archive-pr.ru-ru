---
title: Создание связей по внешнему ключу | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], creating
ms.assetid: 867a54b8-5be4-46e6-9702-49ae6dabf67c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ee0de3311eb6abffcdb71ab725d0650fe96b04c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669356"
---
# <a name="create-foreign-key-relationships"></a>Создание связей по внешнему ключу
  В данном разделе описывается создание связей внешнего ключа в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Связь создается между двумя таблицами, чтобы связать строки одной таблицы со строками другой.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Создание связей внешнего ключа с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Ограничение внешнего ключа не обязательно должно быть связано только с ограничением первичного ключа в другой таблице. Кроме того, это ограничение может быть определено для ссылки на столбцы с ограничением UNIQUE в другой таблице.  
  
-   Если столбцу, имеющему ограничение внешнего ключа, задается значение, отличное от NULL, такое же значение должно существовать и в указываемом столбце; в противном случае будет возвращено сообщение о нарушении внешнего ключа. Для обеспечения проверки всех значений сложного ограничения внешнего ключа задайте параметр NOT NULL для всех столбцов, участвующих в индексе.  
  
-   Ограничения FOREIGN KEY могут ссылаться только на таблицы в пределах той же базы данных на том же сервере. Межбазовую ссылочную целостность необходимо реализовать посредством триггеров. Дополнительные сведения см. в разделе [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql).  
  
-   Ограничения FOREIGN KEY могут ссылаться на другие столбцы той же таблицы. Это называется самовызовом.  
  
-   Ограничение FOREIGN KEY, определенное на уровне столбцов, может содержать только один ссылочный столбец. Этот столбец должен принадлежать к тому же типу данных, что и столбец, для которого определяется ограничение.  
  
-   Ограничение FOREIGN KEY, определенное на уровне таблицы, должно содержать такое же число ссылочных столбцов, какое содержится в списке столбцов в ограничении. Тип данных каждого ссылочного столбца должен также совпадать с типом соответствующего столбца в списке столбцов.  
  
-   Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не имеет стандартного предела на количество ограничений FOREIGN KEY, содержащихся в таблице, ссылающейся на другие таблицы, или на количество ограничений FOREIGN KEY в других таблицах, ссылающихся на указанную таблицу. Тем не менее фактическое количество ограничений FOREIGN KEY, доступных для использования, ограничивается конфигурацией оборудования, базы данных и приложения. Рекомендуется, чтобы таблица содержала не более 253 ограничений FOREIGN KEY, а также чтобы на нее ссылалось не более 253 ограничений FOREIGN KEY.  
  
-   Ограничения FOREIGN KEY не применяются к временным таблицам.  
  
-   Если внешний ключ определен на столбце определяемого пользователем типа данных CLR, реализация этого типа должна поддерживать двоичную сортировку. Дополнительные сведения об определяемых пользователем типах данных CLR см. в разделе [Определяемые пользователем типы данных CLR](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
-   Столбец типа `varchar(max)` может участвовать в ограничении FOREIGN KEY только при условии, что первичный ключ, на который он ссылается, также имеет тип данных `varchar(max)`.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Создание новой таблицы с внешним ключом требует разрешения CREATE TABLE в базе данных и разрешения ALTER на схему, в которой создается таблица.  
  
 Создание внешнего ключа в существующей таблице требует разрешения ALTER на таблицу.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-foreign-key-relationship-in-table-designer"></a>Создание связи по внешнему ключу в конструкторе таблиц  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши таблицу, которая будет содержать внешний ключ для связи, и выберите пункт **Конструктор**.  
  
     Таблица откроется в окне **Конструктор таблиц**.  
  
2.  В меню **конструктора таблиц** выберите пункт **Связи**.  
  
3.  В диалоговом окне **Связи внешнего ключа** щелкните **Добавить**.  
  
     Связь появится в списке **Выбранные связи** с именем, установленным системой, в формате format FK_\<*tablename*>_\<*tablename*>, где *tablename* (имя таблицы) является именем внешнего ключа.  
  
4.  Щелкните нужную связь в списке **Выбранные связи** .  
  
5.  Щелкните **Спецификация таблиц и столбцов** в сетке справа и нажмите кнопку с многоточием ( **...** ) справа от свойства.  
  
6.  В диалоговом окне **Таблицы и столбы** в раскрывающемся списке **Первичный ключ** выберите таблицу, которая будет находиться на стороне первичного ключа связи.  
  
7.  В сетке внизу выберите столбцы, составляющие первичный ключ таблицы. В соседней ячейке сетки слева от каждого столбца выберите соответствующий столбец внешнего ключа таблицы внешнего ключа.  
  
     **Конструктор таблиц** автоматически предлагает имя для связи. Чтобы его изменить, отредактируйте содержимое текстового поля **Имя связи** .  
  
8.  Нажмите кнопку **OК** , чтобы создать связь.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-foreign-key-in-a-new-table"></a>Создание внешнего ключа в новой таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается таблица и определяется ограничение внешнего ключа для столбца `TempID` , ссылающегося на столбец `SalesReasonID` в таблице `Sales.SalesReason` . Предложения ON DELETE CASCADE и ON UPDATE CASCADE используются для обеспечения распространения изменений, вносимых в таблицу `Sales.SalesReason` на таблицу `Sales.TempSalesReason` .  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Sales.TempSalesReason (TempID int NOT NULL, Name nvarchar(50),   
    CONSTRAINT PK_TempSales PRIMARY KEY NONCLUSTERED (TempID),   
    CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    );GO  
  
    ```  
  
#### <a name="to-create-a-foreign-key-in-an-existing-table"></a>Создание внешнего ключа в существующей таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается внешний ключ для столбца `TempID`, ссылающийся на столбец `SalesReasonID` в таблице `Sales.SalesReason`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Sales.TempSalesReason   
    ADD CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    ;  
    GO  
  
    ```  
  
     Дополнительные сведения см. в разделах [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) и [table_constraint (Transact-SQL)](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).  
  
  
