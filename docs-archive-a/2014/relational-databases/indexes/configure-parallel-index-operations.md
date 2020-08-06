---
title: Настройка параллельных операций с индексами | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index parallel operations [SQL Server]
- processors [SQL Server], parallel index operations
- max degree of parallelism option
- MAXDOP index option, parallel index operations
- parallel index operations [SQL Server]
ms.assetid: 8ec8c71e-5fc1-443a-92da-136ee3fc7f88
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8831aadae15af03a05f4ab03cfe514e54566df1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655153"
---
# <a name="configure-parallel-index-operations"></a>Настройка параллельных операций с индексами
  В этом разделе определяется параметр max degree of parallelism и описывается порядок изменения этого параметра в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. На многопроцессорных компьютерах, где установлен выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition или более многофункциональный, индексные инструкции могут использовать несколько процессоров для выполнения операций просмотра, сортировки и операций с индексами, связанных с индексной инструкцией, аналогично другим запросам. Число процессоров, задействованных при выполнении одной индексной инструкции, определяется параметром конфигурации [max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) , текущей рабочей нагрузкой и статистикой индекса. Параметр max degree of parallelism определяет максимальное число процессоров, используемых при параллельном выполнении плана. Если компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] определяет, что система загружена, степень параллелизма операции с индексами автоматически уменьшается перед началом выполнения инструкции. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] уменьшает также степень параллелизма, если ведущий ключевой столбец несекционированного индекса имеет ограниченное число различных значений или частота появления таких значений существенно изменяется.  
  
> [!NOTE]  
>  Параллельные операции с индексами доступны не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. [в разделе функции, поддерживаемые различными Выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для настройки параметра max degree of parallelism используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Число процессоров, используемых оптимизатором запросов, как правило, обеспечивает оптимальную производительность. Однако некоторые операции, например создание, перестроение или удаление очень больших индексов, требуют большого количества ресурсов и могут привести к нехватке ресурсов для других приложений и операций базы данных на время выполнения операции с индексами. При возникновении этой проблемы можно вручную установить максимальное количество процессоров, которые используются при выполнении индексной инструкции, ограничив число процессоров, используемых в операции с индексами.  
  
-   Параметр индекса MAXDOP замещает параметр конфигурации max degree of parallelism только для запросов, указывающих этот параметр. В следующей таблице перечислены действительные целочисленные значения, которые могут быть установлены для параметра конфигурации максимальной степени параллелизма и параметра индекса MAXDOP.  
  
    |Значение|Описание|  
    |-----------|-----------------|  
    |0|Указывает, что сервер определяет число используемых процессоров в зависимости от текущей рабочей нагрузки. Это значение по умолчанию, которое рекомендуется использовать.|  
    |1|Подавляет формирование параллельных планов. Операция будет выполнена последовательно.|  
    |2–64|Ограничивает число процессоров указанным значением. Может быть использовано меньше процессоров, в зависимости от рабочей нагрузки. Если указано значение, превышающее количество доступных процессоров, будет использоваться реальное количество доступных процессоров.|  
  
-   Параллельное выполнение индексов и параметр индекса MAXDOP применяются в следующих инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
    -   CREATE INDEX  
  
    -   ALTER INDEX REBUILD  
  
    -   DROP INDEX (применяется только для кластеризованных индексов)  
  
    -   ALTER TABLE ADD (индекс) CONSTRAINT  
  
    -   ALTER TABLE DROP (кластеризованный индекс) CONSTRAINT  
  
-   Параметр индекса MAXDOP не может быть задан в инструкции ALTER INDEX REORGANIZE.  
  
-   Операции с секционированными индексами, для которых необходима сортировка, могут требовать больше памяти, если оптимизатор запросов применяет степени параллелизма к операциям построения. Чем выше степень параллелизма, тем больше требуется памяти. Дополнительные сведения см. в разделе [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER для таблицы или представления.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-index"></a>Задание параметра max degree of parallelism для индекса  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть базу данных, содержащую таблицу, в которой необходимо указать параметр max degree of parallelism для индекса.  
  
2.  Разверните папку **Таблицы**.  
  
3.  Щелкните знак «плюс», чтобы развернуть таблицу, в которой необходимо указать параметр max degree of parallelism для индекса.  
  
4.  Разверните папку **Индексы**.  
  
5.  Щелкните правой кнопкой мыши индекс, для которого нужно задать параметр max degree of parallelism, и выберите пункт **Свойства**.  
  
6.  В разделе **Выбор страницы**щелкните **Параметры**.  
  
7.  Выберите свойство **Максимальная степень параллелизма**и введите значение от 1 до 64.  
  
8.  Нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-existing-index"></a>Задание параметра max degree of parallelism для существующего индекса  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Alters the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table so that, if the server has eight or more processors, the Database Engine will limit the execution of the index operation to eight or fewer processors.  
    */  
    ALTER INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor  
    REBUILD WITH (MAXDOP=8);   
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql).  
  
#### <a name="set-max-degree-of-parallelism-on-a-new-index"></a>Задание параметра max degree of parallelism для нового индекса  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE INDEX IX_ProductVendor_NewVendorID   
    ON Purchasing.ProductVendor (BusinessEntityID)  
    WITH (MAXDOP=8);  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql).  
  
  
