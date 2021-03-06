---
title: Пользовательский интерфейс текстового конструктора запросов | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1647d69246ba85dfbe0718799441c3687c0beca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739074"
---
# <a name="text-based-query-designer-user-interface"></a>Пользовательский интерфейс текстового конструктора запросов
  Текстовый конструктор запросов предназначен для ввода запроса на языке запросов, поддерживаемом источником данных, его выполнения и просмотра результатов во время разработки. Можно указать несколько инструкций, запросов или команд языка [!INCLUDE[tsql](../includes/tsql-md.md)] для создания собственных модулей обработки данных, а также указать запросы, заданные как выражения. Поскольку текстовый конструктор запросов не выполняет предварительную обработку запроса и позволяет использовать любой синтаксис запросов, он представляет собой стандартное средство конструктора запросов для источников данных многих типов.

 В окне текстового конструктора запросов отображаются панель инструментов и следующие две области.

-   **Запрос** Отображает текст запроса, имя таблицы или имя хранимой процедуры.

-   **Результат** Показывает результаты выполнения запроса во время разработки.

## <a name="text-based-query-designer-toolbar"></a>Панель инструментов текстового конструктора запросов
 Текстовый конструктор запросов предоставляет одну панель инструментов для всех типов команд. В следующей таблице перечислены все кнопки панели инструментов и их функции.

|Кнопка|Описание|
|------------|-----------------|
|**Редактировать как текст**|Переключиться из текстового конструктора запросов в графический и обратно. Не все источники данных поддерживают графические конструкторы запросов.|
|**Импорт**|Импорт существующего запроса из файла или отчета. Поддерживаются только SQL и RDL-файлы. Дополнительные сведения см. в разделе [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|
|![Выполнить запрос](../analysis-services/media/rsqdicon-run.gif "Выполнить запрос")|Выполнить запрос и показать результирующий набор в панели результатов.|
|**Тип команды**|Выберите **Text**, **StoredProcedure**или **TableDirect**. Если хранимая процедура имеет параметры, при нажатии на панели инструментов кнопки **Выполнить** появится диалоговое окно **Определение параметров запроса** , в котором можно ввести значения параметров. Обратите внимание, что если хранимая процедура возвращает более одного результирующего набора, для заполнения набора данных используется только первый результирующий набор.<br /><br /> Поддержка типов команд зависит от типа источника данных. Например, **TableDirect**поддерживают только OLE DB и ODBC.|

### <a name="command-type-text"></a>Тип команды Text
 Если создается набор данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], конструктор отчетов по умолчанию отображает графический конструктор запросов. Чтобы переключиться в текстовый конструктор запросов, нажмите кнопку переключателя **Редактировать как текст** на панели инструментов. В окне текстового конструктора запросов отображаются две панели: панель запросов и область результатов. На следующем рисунке показана каждая панель.

 ![Простой конструктор запросов для запросов к реляционным данным](../analysis-services/media/rsqd-dsaw-sql-generic.gif "Простой конструктор запросов для запросов к реляционным данным")

 В следующей таблице описываются функции каждой панели.

|Панель|Компонент|
|----------|--------------|
|Запрос|Отображает текст запроса [!INCLUDE[tsql](../includes/tsql-md.md)] . Используйте эту панель, чтобы написать или изменить запрос [!INCLUDE[tsql](../includes/tsql-md.md)] .|
|Результат|Отображает результаты запроса. Чтобы выполнить запрос, щелкните правой кнопкой мыши любую область и выберите команду **Выполнить**либо нажмите кнопку **Выполнить** на панели инструментов.|

#### <a name="example"></a>Пример
 Следующий запрос возвращает список фамилий из таблицы `Contact` базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)], .

```
SELECT LastName FROM Person.Person;
```

 Для типа команды Text можно использовать любую инструкцию [!INCLUDE[tsql](../includes/tsql-md.md)], включая инструкции `EXEC`. Следующий запрос вызывает [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] хранимую процедуру `uspGetEmployeeManagers` и возвращает цепочку команд для сотрудника с идентификационным номером 1.

```
EXEC uspGetEmployeeManagers 1;
```

 При нажатии кнопки **Выполнить** на панели инструментов выполняется команда на панели **Запрос** , а результаты выводятся на панели **Результат** .

### <a name="command-type-storedprocedure"></a>Тип команды StoredProcedure
 Если выбран **Тип команды StoredProcedure**, то текстовый конструктор запросов содержит две панели: панель запросов и область результатов. Введите имя хранимой процедуры в области «Запрос» и нажмите кнопку **Выполнить** на панели инструментов. Откроется диалоговое окно «Определение параметров запроса». Введите значения параметров для хранимой процедуры. Параметр отчета создается для каждого параметра хранимой процедуры.

#### <a name="example"></a>Пример
 В следующем запросе в базе данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] вызывается хранимая процедура `uspGetEmployeeManagers`. При запуске этого запроса необходимо задать значение параметра с идентификационным номером сотрудника.

```
uspGetEmployeeManagers;
```

### <a name="command-type-tabledirect"></a>Тип команды TableDirect
 Если выбран **Тип команды TableDirect**, то текстовый конструктор запросов содержит две панели: панель запросов и область результатов. Если ввести имя таблицы и нажать кнопку **Выполнить** , возвращаются все столбцы этой таблицы.

#### <a name="example"></a>Пример
 Следующий запрос возвращает результирующий набор, содержащий всех клиентов в базе данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)].

 `Sales.Customer`

 При вводе имени таблицы Sales. Customer это эквивалентно созданию [!INCLUDE[tsql](../includes/tsql-md.md)] инструкции `SELECT * FROM Sales.Customer;` .

## <a name="see-also"></a>См. также:
 [Средства проектирования запросов в конструктор отчетов SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) [отчетов внедренные наборы данных и общие наборы данных &#40;построитель отчетов и SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [SQL Server тип соединения &#40;ssrs&#41;](report-data/sql-server-connection-type-ssrs.md) [OLE DB тип подключения &#40;ssrs&#41;](report-data/ole-db-connection-type-ssrs.md) [тип подключения ODBC &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md) [отчетов внедренные наборы данных и общие наборы данных &#40;построитель отчетов и SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [RSReportDesigner файл конфигурации](report-server/rsreportdesigner-configuration-file.md)


