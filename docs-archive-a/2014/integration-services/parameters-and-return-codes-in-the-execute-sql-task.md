---
title: Параметры и коды возврата в задаче "Выполнение SQL" | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- return codes [Integration Services]
- parameters [Integration Services]
- parameterized SQL statements [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: a3ca65e8-65cf-4272-9a81-765a706b8663
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cdc32e103642e086e81f6499bf56e5fbb71c3bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667800"
---
# <a name="parameters-and-return-codes-in-the-execute-sql-task"></a>Параметры и коды возврата в задаче «Выполнение SQL»
  В инструкциях SQL и хранимых процедурах часто используются входные параметры `input`, выходные параметры `output` и коды возврата. В службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] задача «Выполнение SQL» поддерживает типы параметров `Input`, `Output` и `ReturnValue`. Используйте тип `Input` для входных параметров, `Output` — для выходных и `ReturnValue` — для кодов возврата.  
  
> [!NOTE]  
>  В задаче «Выполнение SQL» параметры могут использоваться, только если их поддерживает поставщик данных.  
  
 Параметры команд SQL, включая запросы и хранимые процедуры, сопоставлены с пользовательскими переменными, созданными в области задачи «Выполнение SQL», в области родительского контейнера или в области пакета. Значения переменных можно задать во время разработки или динамически заполнить во время выполнения. Также можно сопоставить параметры системным переменным. Дополнительные сведения см. в разделах [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md) и [Системные переменные](system-variables.md).  
  
 Однако для работы с параметрами и кодами возврата задачи «Выполнение SQL» необходимо знать больше, чем поддерживаемые задачей типы параметров и как сопоставлены эти параметры. Существуют дополнительные требования и рекомендации для успешного использования параметров и кодов возврата в задаче «Выполнение SQL». В оставшейся части раздела приведены эти требования и рекомендации.  
  
-   [Применение имен и маркеров параметров](#Parameter_names_and_markers)  
  
-   [Использование параметров с типами данных даты и времени](#Date_and_time_data_types)  
  
-   [Использование параметров в предложениях WHERE](#WHERE_clauses)  
  
-   [Использование параметров с хранимыми процедурами](#Stored_procedures)  
  
-   [Возвращение значений кодов возврата](#Return_codes)  
  
-   [Настройка параметров и кодов возврата в редакторе задачи «Выполнение SQL»](#Configure_parameters_and_return_codes)  
  
##  <a name="using-parameter-names-and-markers"></a><a name="Parameter_names_and_markers"></a>Использование имен и маркеров параметров  
 В зависимости от типа соединения, который использует задача «Выполнение SQL», синтаксис команды SQL использует различные маркеры параметров. Например, для типа диспетчера подключений [!INCLUDE[vstecado](../includes/vstecado-md.md)] требуется, чтобы команда SQL использовала маркер параметра в формате **\@varParameter**, в то время как для типа OLE DB требуется, чтобы в качестве маркера параметра использовался символ вопросительного знака (?).  
  
 Имена, которые можно использовать как имена параметров в сопоставлениях между переменными и параметрами, также зависят от типа диспетчера соединений. Например, тип диспетчера подключений [!INCLUDE[vstecado](../includes/vstecado-md.md)] использует определенные пользователем имена, начинающиеся с префикса \@, в то время как для типа OLE DB требуется, чтобы в качестве имени параметра использовалось числовое значение (начинающееся с нуля).  
  
 В следующей таблице подведен итог требованиям для команд SQL для различных типов диспетчеров соединений, которые может использовать задача «Выполнение SQL».  
  
|Тип соединений|Маркер параметра|Имя параметра|Пример команды SQL|  
|---------------------|----------------------|--------------------|-------------------------|  
|ADO|?|Param1, Param2, …|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|\@\<parameter name>|\@\<parameter name>|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = \@parmContactID|  
|ODBC|?|1, 2, 3, ...|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
|EXCEL и OLE DB|?|0, 1, 2, 3, ...|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
  
### <a name="using-parameters-with-adonet-and-ado-connection-managers"></a>Использование параметров с ADO.NET и диспетчерами соединений ADO  
 Диспетчеры подключений [!INCLUDE[vstecado](../includes/vstecado-md.md)] и ADO предъявляют особые требования к командам SQL, использующим параметры:  
  
-   Диспетчер соединений [!INCLUDE[vstecado](../includes/vstecado-md.md)] требует, чтобы команда SQL использовала имена параметров в качестве маркеров параметров. Это означает, что переменные могут быть прямо сопоставлены с параметрами. Например, переменная `@varName` сопоставляется с параметром по имени `@parName` и предоставляет значение параметру `@parName`.  
  
-   Диспетчеры соединений ADO требуют, чтобы в команде SQL в качестве маркеров параметров использовались вопросительные знаки (?). Однако в качестве имен параметров можно использовать любые имена, за исключением целых чисел.  
  
 Чтобы предоставить параметрам значения, переменные сопоставляются с именами параметров. Затем задача «Выполнение SQL» использует для загрузки значений из переменных параметры значения порядкового номера имени параметра в списке параметров.  
  
### <a name="using-parameters-with-excel-odbc-and-ole-db-connection-managers"></a>Использование параметров с диспетчерами соединений EXCEL, ODBC и OLE DB  
 Диспетчеры соединений EXCEL, ODBC и OLE DB требуют, чтобы команды SQL использовали символы знака вопроса (?) в качестве маркеров параметров и числовые значения (начиная с нуля или с единицы) в качестве имен параметров. Если задача «Выполнение SQL» использует диспетчер соединений ODBC, то именем параметра, сопоставляемым первому параметру в запросе, является 1. В противном случае именем параметра будет 0. Для последующих параметров числовое значение имени параметра указывает на параметр в команде SQL, которому сопоставлено это имя параметра. Например, параметр под именем 3 сопоставлен с третьим параметром, который представляется третьим знаком вопроса (?) в команде SQL.  
  
 Чтобы предоставить параметрам значения, переменные сопоставляются с именами параметров и задача «Выполнение SQL» использует порядковое значение имени параметра для загрузки значения из переменных в параметры.  
  
 В зависимости от поставщика, который используют диспетчеры соединений, некоторые типы данных OLE DB могут не поддерживаться. Например, драйвер Excel распознает только ограниченный набор типов данных. Дополнительные сведения о поведении поставщика Jet с драйвером Excel см. в разделе [Excel Source](data-flow/excel-source.md).  
  
#### <a name="using-parameters-with-ole-db-connection-managers"></a>Использование параметров с диспетчерами соединений OLE DB  
 Если в задаче "Выполнение SQL" используется диспетчер соединений OLE DB, становится доступным свойство BypassPrepare задачи. Этому свойству необходимо присвоить значение `true`, если задача «Выполнение SQL» использует инструкции SQL с параметрами.  
  
 При использовании диспетчера соединений OLE DB нельзя применять параметризованные вложенные запросы, поскольку в задаче «Выполнение SQL» нельзя получить путем анализа информацию о параметрах через поставщик OLE DB. Однако можно использовать выражение, чтобы объединить значения параметров в строку запроса и задать свойство SqlStatementSource этой задачи.  
  
##  <a name="using-parameters-with-date-and-time-data-types"></a><a name="Date_and_time_data_types"></a>Использование параметров с типами данных даты и времени  
  
### <a name="using-date-and-time-parameters-with-adonet-and-ado-connection-managers"></a>Использование параметров даты и времени с ADO.NET и диспетчерами соединений ADO  
 При считывании данных типов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]`time` и `datetimeoffset` задача «Выполнение SQL», которая использует диспетчер соединений [!INCLUDE[vstecado](../includes/vstecado-md.md)] или ADO, имеет следующие дополнительные требования.  
  
-   Для `time` данных [!INCLUDE[vstecado](../includes/vstecado-md.md)] Диспетчер соединений требует, чтобы эти данные хранились в параметре, тип параметра которого — `Input` или `Output` , а тип данных — `string` .  
  
-   Для данных типа `datetimeoffset` диспетчер соединений [!INCLUDE[vstecado](../includes/vstecado-md.md)] требует, чтобы они хранились в одном из следующих параметров.  
  
    -   Параметр типа `Input` имеет тип данных `string`.  
  
    -   Параметр типа `Output` или `ReturnValue` имеет тип данных `datetimeoffset`, `string` или `datetime2`. Если выбран параметр с типом данных `string` или `datetime2`, то службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] преобразуют данные в тип string или datetime2.  
  
-   Диспетчер соединений ADO требует, чтобы данные `time` или `datetimeoffset` хранились в параметре типа `Input` или `Output`, имеющем тип данных `adVarWchar`.  
  
 Дополнительные сведения о типах данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и их сопоставлении с типами данных [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) и [Типы данных службы Integration Services](data-flow/integration-services-data-types.md).  
  
### <a name="using-date-and-time-parameters-with-ole-db-connection-managers"></a>Использование параметров даты и времени с диспетчерами соединений OLE DB  
 При использовании диспетчера соединений OLE DB задача «Выполнение SQL» имеет особые требования по хранению данных типа данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]: `date`, `time`, `datetime`, `datetime2` и `datetimeoffset`. Эти данные необходимо хранить в параметре одного из следующих типов.  
  
-   Входной параметр типа данных NVARCHAR.  
  
-   Выходной параметр соответствующего типа данных, как показано в следующей таблице.  
  
    |Тип параметра `Output`|Тип данных «date»|  
    |-------------------------------|--------------------|  
    |DBDATE|`date`|  
    |DBTIME2|`time`|  
    |DBTIMESTAMP|`datetime`, `datetime2`|  
    |DBTIMESTAMPOFFSET|`datetimeoffset`|  
  
 Если данные не хранятся в соответствующем входном или выходном параметре, выполнение пакета завершается с ошибкой.  
  
### <a name="using-date-and-time-parameters-with-odbc-connection-managers"></a>Использование параметров даты и времени с диспетчерами соединений ODBC  
 При использовании диспетчера соединений ODBC задача «Выполнение SQL» имеет особые требования по хранению данных одного из следующих типов данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]: `date`, `time`, `datetime`, `datetime2` и `datetimeoffset`. Эти данные необходимо хранить в параметре одного из следующих типов.  
  
-   Входной параметр `input` типа данных SQL_WVARCHAR.  
  
-   Выходной параметр `output` соответствующего типа данных, как показано в следующей таблице.  
  
    |Тип параметра `Output`|Тип данных «date»|  
    |-------------------------------|--------------------|  
    |SQL_DATE|`date`|  
    |SQL_SS_TIME2|`time`|  
    |SQL_TYPE_TIMESTAMP<br /><br /> -или-<br /><br /> SQL_TIMESTAMP|`datetime`, `datetime2`|  
    |SQL_SS_TIMESTAMPOFFSET|`datetimeoffset`|  
  
 Если данные не хранятся в соответствующем входном или выходном параметре, выполнение пакета завершается с ошибкой.  
  
##  <a name="using-parameters-in-where-clauses"></a><a name="WHERE_clauses"></a>Использование параметров в предложениях WHERE  
 Команды SELECT, INSERT, UPDATE и DELETE часто включают в себя предложение WHERE для задания фильтров, которые определяют условия, которым должна удовлетворять каждая строка в исходной таблице, чтобы попасть под действие команды SQL. Параметры предоставляют значения фильтра в предложениях WHERE.  
  
 Можно использовать маркеры параметров для динамического предоставления значений параметрам. Правила для каждого маркера параметра и имени параметра, которые могут быть использованы в инструкции SQL, зависят от типа диспетчера соединений, который используется задачей «Выполнение SQL».  
  
 В следующей таблице приведен список примеров команды SELECT для разных типов диспетчеров соединений. Те же самые правила относятся и к инструкциям INSERT, UPDATE и DELETE. В примерах инструкции SELECT возвращают из таблицы **Product** базы данных [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] продукты, для которых значение **ProductID** больше и меньше значений, указанных двумя параметрами.  
  
|Тип соединений|Синтаксис SELECT|  
|---------------------|-------------------|  
|EXCEL, ODBC и OLEDB|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
|ADO|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
 Для примеров необходимы параметры со следующими именами.  
  
-   Диспетчеры соединений EXCEL и OLED DB используют параметры с именами 0 и 1. Для типа соединения ODBC понадобятся параметры с именами 1 и 2.  
  
-   Для типа соединения ADO можно использовать любые два имени параметра, такие как Param1 и Param2, но эти параметры должны быть сопоставлены со своими порядковыми номерами в списке параметров.  
  
-   Для типа соединения [!INCLUDE[vstecado](../includes/vstecado-md.md)] используются имена параметров \@parmMinProductID и \@parmMaxProductID.  
  
##  <a name="using-parameters-with-stored-procedures"></a><a name="Stored_procedures"></a>Использование параметров с хранимыми процедурами  
 В командах SQL, выполняющих хранимые процедуры, тоже может использоваться сопоставление параметров. Правила использования маркеров и имен параметров зависят от типа диспетчера соединений, который используется задачей «Выполнение SQL», точно так же, как и правила для параметризованных запросов.  
  
 В следующей таблице приведен список примеров команды EXEC для разных типов диспетчеров соединений. Примеры выполняют хранимую процедуру **uspGetBillOfMaterials** в базе данных [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]. Хранимая процедура использует `@StartProductID` Параметры и `@CheckDate` `input` .  
  
|Тип соединений|Синтаксис EXEC|  
|---------------------|-----------------|  
|EXCEL и OLEDB|`EXEC uspGetBillOfMaterials ?, ?`|  
|ODBC|`{call uspGetBillOfMaterials(?, ?)}`<br /><br /> Дополнительные сведения о синтаксисе вызова ODBC см. в разделе [Параметры процедур](https://go.microsoft.com/fwlink/?LinkId=89462)справочника по программированию ODBC в библиотеке MSDN.|  
|ADO|Если для для параметра isquerystoredprocedure задано значение `False` ,`EXEC uspGetBillOfMaterials ?, ?`<br /><br /> Если для для параметра isquerystoredprocedure задано значение `True` ,`uspGetBillOfMaterials`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Если для для параметра isquerystoredprocedure задано значение `False` ,`EXEC uspGetBillOfMaterials @StartProductID, @CheckDate`<br /><br /> Если для для параметра isquerystoredprocedure задано значение `True` ,`uspGetBillOfMaterials`|  
  
 Чтобы использовать выходные параметры, синтаксис требует, чтобы ключевое слово OUTPUT следовало за каждым маркером параметров. Например, следующий синтаксис выходного параметра является верным: `EXEC myStoredProcedure ? OUTPUT`.  
  
 Дополнительные сведения об использовании входных и выходных параметров с хранимыми процедурами Transact-SQL см. в разделе [EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql).  
  
##  <a name="getting-values-of-return-codes"></a><a name="Return_codes"></a>Получение значений кодов возврата  
 Хранимая процедура может возвращать целочисленное значение, называемое кодом возврата, чтобы указать состояние выполнения процедуры. Чтобы реализовать коды возврата в задаче «Выполнение SQL», используйте параметры типа `ReturnValue`.  
  
 В следующей таблице приведен список типов соединений с примерами команды EXEC, которая реализует коды возврата. Все примеры используют входной параметр `input`. Правила использования маркеров параметров и имен параметров одинаковы для всех типов параметров — `Input` , `Output` и `ReturnValue` .  
  
 Некоторые типы синтаксиса не поддерживают литералы параметров. В этом случае необходимо предоставить значение параметра с помощью переменной.  
  
|Тип соединений|Синтаксис EXEC|  
|---------------------|-----------------|  
|EXCEL и OLEDB|`EXEC ? = myStoredProcedure 1`|  
|ODBC|`{? = call myStoredProcedure(1)}`<br /><br /> Дополнительные сведения о синтаксисе вызова ODBC см. в разделе [Параметры процедур](https://go.microsoft.com/fwlink/?LinkId=89462)справочника по программированию ODBC в библиотеке MSDN.|  
|ADO|Если для для параметра isquerystoreprocedure задано значение `False` ,`EXEC ? = myStoredProcedure 1`<br /><br /> Если для для параметра isquerystoreprocedure задано значение `True` ,`myStoredProcedure`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Для параметра Set для параметра isquerystoreprocedure задано значение `True` .<br /><br /> `myStoredProcedure`|  
  
 В описании синтаксиса, показанном в предыдущей таблице, задача «Выполнение SQL» использует для запуска хранимой процедуры тип источника **Прямой ввод** . Задача «Выполнение SQL» может также пользоваться для выполнения хранимой процедуры типом источника **Соединение с файлом** . Независимо от того, использует ли задача «Выполнение SQL» тип источника « **прямой вход** » или « **соединение с файлом** », используйте параметр `ReturnValue` типа для реализации кода возврата. Дополнительные сведения о настройке типа источника для инструкции SQL, выполняемой задачей "Выполнение SQL", см. в разделе [Редактор задачи "Выполнение SQL" (страница "Общие")](general-page-of-integration-services-designers-options.md).  
  
 Дополнительные сведения об использовании кодов возврата с хранимыми процедурами Transact-SQL см. в разделе [RETURN (Transact-SQL)](/sql/t-sql/language-elements/return-transact-sql).  
  
##  <a name="configuring-parameters-and-return-codes-in-the-execute-sql-task"></a><a name="Configure_parameters_and_return_codes"></a>Настройка параметров и кодов возврата в задаче «Выполнение SQL»  
 Дополнительные сведения о свойствах параметров и кодов возврата, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Редактор задачи "Выполнение SQL" &#40;страница "Сопоставление параметров"&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Задание свойств задач или контейнеров](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a>См. также  
  
-   Запись в блоге, [Хранимые процедуры с выходными параметрами](https://go.microsoft.com/fwlink/?LinkId=157786), на сайте blogs.msdn.com  
  
-   Образец CodePlex, [Параметры задачи «Выполнение SQL» и результирующие наборы](https://go.microsoft.com/fwlink/?LinkId=157863), на сайте msftisprodsamples.codeplex.com  
  
## <a name="see-also"></a>См. также:  
 [Задача «Выполнение SQL»](control-flow/execute-sql-task.md)   
 [Результирующие наборы в задаче "Выполнение SQL"](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)  
  
  
