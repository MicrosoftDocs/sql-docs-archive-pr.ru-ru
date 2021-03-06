---
title: Задача "Выполнение SQL" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- batches [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e77b9f442ae8478c57d5b0e68955b541eda38aff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729709"
---
# <a name="execute-sql-task"></a>Задача "Выполнение SQL"
  Задача «Выполнение SQL» выполняет инструкции SQL или хранимые процедуры из пакета. Задача может содержать одну инструкцию SQL или несколько инструкций, запускаемых последовательно. Задача «Выполнение SQL» может быть использована для следующих целей:  
  
-   усечение таблицы или представления в процессе подготовки для вставки данных;  
  
-   создание, изменение и удаление объектов базы данных, таких как таблицы и представления;  
  
-   повторное создание таблиц фактов и таблиц измерений перед загрузкой данных;  
  
-   выполнение хранимых процедур; Если инструкция SQL вызывает хранимую процедуру, возвращающую результаты из временной таблицы, используйте параметр WITH RESULT SETS для определения метаданных набора результатов.  
  
-   сохранение набора строк, возвращенного в переменную из запроса.  
  
 Задача «Выполнение SQL» может использоваться в сочетании с контейнерами «цикл по каждому элементу» и «цикл по элементам» для выполнения нескольких инструкций SQL. Эти контейнеры выполняют повторяющиеся потоки управления в пакете и могут запускать задачу «Выполнение SQL» повторно. Например, с помощью контейнера «цикл по каждому элементу» пакет может перечислять файлы в папке и повторно запускать задачу «Выполнение SQL» с инструкциями SQL из каждого файла.  
  
## <a name="connecting-to-a-data-source"></a>Подключение к источнику данных  
 Задача «Выполнение SQL» может использовать разные типы диспетчеров соединений для подключения к источнику данных, где требуется выполнить инструкцию SQL или хранимую процедуру. Задача может использовать типы соединений, перечисленные в следующей таблице.  
  
|Тип соединений|Диспетчер соединений|  
|---------------------|------------------------|  
|EXCEL|[Диспетчер подключений Excel](../connection-manager/excel-connection-manager.md)|  
|OLE DB|[Диспетчер соединений OLE DB](../connection-manager/ole-db-connection-manager.md)|  
|ODBC|[Диспетчер подключений ODBC](../connection-manager/odbc-connection-manager.md)|  
|ADO|[Диспетчер подключений объектов данных ActiveX](../connection-manager/ado-connection-manager.md)|  
|ADO.NET|[Диспетчер подключений ADO.NET](../connection-manager/ado-net-connection-manager.md)|  
|SQLMOBILE|[Диспетчер подключений SQL Server Compact Edition](../connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## <a name="creating-sql-statements"></a>Создание инструкций SQL  
 Источником инструкций SQL для этой задачи может быть свойство задачи, которое содержит инструкцию, соединение с файлом, содержащим инструкции, или имя переменной, хранящей инструкцию. Для написания инструкций SQL необходимо использовать разновидность языка SQL, используемую системой управления базой данных-источником (СУБД). Дополнительные сведения см. в разделе [Запросы в службах Integration Services (SSIS)](../integration-services-ssis-queries.md).  
  
 Если инструкции SQL хранятся в файле, задача использует диспетчер подключения файлов для подключения к файлу. Дополнительные сведения см. в статье [File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 В конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] можно использовать диалоговое окно **Редактор задачи «Выполнение SQL»** для ввода инструкций SQL или **построитель запросов**— графический пользовательский интерфейс для создания запросов SQL. Дополнительные сведения см. в разделе [Execute SQL Task Editor &#40;General Page&#41;](../execute-sql-task-editor-general-page.md) и [построитель запросов](../query-builder.md).  
  
> [!NOTE]  
>  Задача «Выполнение SQL» не может провести синтаксический анализ допустимых инструкций SQL, созданных за ее пределами.  
  
> [!NOTE]  
>  Задача «Выполнение SQL» использует значение перечисления `RecognizeAll` ParseMode. Дополнительные сведения см. в разделе [Пространство имен ManagedBatchParser](https://go.microsoft.com/fwlink/?LinkId=223617).  
  
## <a name="sending-multiple-statements-in-a-batch"></a>Отправка нескольких инструкций в пакете  
 Если в задачу «Выполнение SQL» включить несколько инструкций, их можно сгруппировать и запускать как пакет. Для обозначения окончания пакета используется команда GO. Все инструкции SQL, находящиеся между двумя командами GO, отправляются в одном пакете поставщику OLE DB для выполнения. Команда SQL может содержать несколько пакетов, разделенных командами GO.  
  
 Существуют ограничения на тип инструкций SQL, которые могут объединяться в пакеты. Дополнительные сведения см. в разделе [Batches of Statements](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md).  
  
 Если задача «Выполнение SQL» выполняет пакет инструкций SQL, к пакету применяются следующие правила:  
  
-   Только одна инструкция может возвращать результирующий набор. Эта инструкция должна быть первой в пакете.  
  
-   Если в результирующем наборе содержатся связанные столбцы, запросы должны возвращать такое же количество столбцов. Если запросы возвращают разное количество столбцов, происходит сбой выполнения задачи. Тем не менее, даже в случае сбоя выполнения задачи ее запросы, такие как DELETE или INSERT могут быть выполнены успешно.  
  
-   Если в результирующих связываниях участвуют имена столбцов, запросы должны возвращать столбцы с такими же именами, как в результирующем наборе, используемом задачей. Если столбцы отсутствуют, происходит сбой выполнения задачи.  
  
-   Если в задаче используются связывания параметров, у всех запросов в пакете должны быть одинаковые типы параметров и их количество.  
  
## <a name="running-parameterized-sql-commands"></a>Выполнение параметризованных команд SQL  
 В инструкциях SQL и хранимых процедурах часто используются входные параметры, выходные параметры и коды возврата. Задача «Выполнение SQL» поддерживает типы параметров `Input`, `Output` и `ReturnValue`. Используйте тип `Input` для входных параметров, `Output` — для выходных и `ReturnValue` — для кодов возврата.  
  
> [!NOTE]  
>  В задаче «Выполнение SQL» параметры могут использоваться, только если их поддерживает поставщик данных.  
  
 Дополнительные сведения об использовании параметров в задаче "Выполнение SQL" и ее кодах возврата см. в разделе [Параметры и коды возврата в задаче "Выполнение SQL"](execute-sql-task.md).  
  
## <a name="specifying-a-result-set-type"></a>Указание типа результирующего набора  
 В зависимости от команды SQL задаче «Выполнение SQL» может быть возвращен (или не возвращен) результирующий набор. Например, инструкция SELECT обычно возвращает результирующий набор, а инструкция INSERT нет. Результирующий набор инструкции SELECT может не содержать ни одной строки, содержать одну строку или несколько строк. Хранимые процедуры возвращают целочисленные значения, называемые кодом возврата, который отражает состояние выполнения процедуры. В этом случае результирующий набор состоит из одной строки.  
  
 Дополнительные сведения о получении результирующих наборов команд SQL в задаче "Выполнение SQL" см. в разделе [Результирующие наборы в задаче "Выполнение SQL"](../result-sets-in-the-execute-sql-task.md).  
  
## <a name="troubleshooting-the-execute-sql-task"></a>Устранение неполадок, связанных с задачей «Выполнение SQL»  
 Вызовы, сделанные задачей «Выполнение SQL» к внешним источникам данных, можно записывать в журнал. Эта новая возможность протоколирования может быть использована для устранения неполадок, связанных с командами SQL, которые выполняются задачей «Выполнение SQL». Чтобы протоколировать вызовы, которые задача «Выполнение SQL» формирует к внешнему поставщику данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 Иногда команда SQL или хранимая процедура возвращает несколько результирующих наборов. Эти результирующие наборы включают не только наборы строк, которые являются результатом запросов `SELECT`, но и отдельные значения, являющиеся результатом ошибок инструкций `RAISERROR` или `PRINT`. От типа используемого диспетчера соединений зависит, пропускает ли задача ошибки в результирующих наборах, следующих за первым.  
  
-   Если используются диспетчеры соединений OLE DB и ADO, задача пропускает результирующие наборы, следующие за первым результирующим набором. Поэтому задача с этими диспетчерами соединений не обрабатывает ошибку, возвращенную командой SQL или хранимой процедурой, если эта ошибка не является частью первого результирующего набора.  
  
-   Если используются диспетчеры соединений ODBC и ADO.NET, задача не пропускает результирующие наборы, следующие за первым результирующим набором. Задача с этими диспетчерами соединений завершается ошибкой, если один из результирующих наборов, следующих за первым, содержит ошибку.  
  
### <a name="custom-log-entries"></a>Пользовательские записи журнала  
 В следующей таблице перечислены пользовательские записи журнала для задачи «Выполнение SQL». Дополнительные сведения см. в разделах [Ведение журналов в службах Integration Services (SSIS)](../performance/integration-services-ssis-logging.md) и [Пользовательские сообщения для ведения журнала](../custom-messages-for-logging.md).  
  
|Запись журнала|Описание|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|Предоставляет сведения об этапах выполнения инструкции SQL. Записи журнала формируются в тот момент, когда задача устанавливает соединение с базой данных, когда задача приступает к подготовке инструкции SQL, и после того, как завершается выполнение инструкции SQL. Запись журнала для этапа подготовки содержит инструкцию SQL, которая используется задачей.|  
  
## <a name="configuring-the-execute-sql-task"></a>Настройка задачи «Выполнение SQL»  
 Настроить задачу «Выполнение SQL» можно одним из следующих способов:  
  
-   Указать тип диспетчера соединений для подключения к базе данных.  
  
-   Указать тип результирующего набора, возвращаемого инструкцией SQL.  
  
-   Указать время ожидания для инструкции SQL.  
  
-   Указать источник для инструкции SQL.  
  
-   Указать, должна ли задача пропустить фазу подготовки инструкции SQL.  
  
-   При использовании типа соединения ADO необходимо указать, является ли инструкция SQL хранимой процедурой. Для других типов соединений это свойство доступно только для чтения и всегда имеет значение `false`.  
  
 Свойства задаются программно или через конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Редактор задачи «Выполнение SQL» &#40;страница «Общие»&#41;](../execute-sql-task-editor-general-page.md)  
  
-   [Редактор задачи "Выполнение SQL" &#40;страница "Сопоставление параметров"&#41;](../execute-sql-task-editor-parameter-mapping-page.md)  
  
-   [Редактор задачи "Выполнение SQL" &#40;страница "результирующий набор"&#41;](../execute-sql-task-editor-result-set-page.md)  
  
-   [Страница «Выражения»](../expressions/expressions-page.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="configuring-the-execute-sql-task-programmatically"></a>Программная настройка задачи «Выполнение SQL»  
 Дополнительные сведения об установке этих свойств программными средствами см. в следующем разделе.  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Сопоставление параметров запроса с переменными в задаче «Выполнение SQL»](../map-query-parameters-to-variables-in-an-execute-sql-task.md)  
  
-   [Сопоставьте результирующие наборы с переменными в задаче «Выполнение SQL»](../map-result-sets-to-variables-in-an-execute-sql-task.md)  
  
## <a name="related-content"></a>См. также  
  
-   [Параметры и коды возврата в задаче «Выполнение SQL»](execute-sql-task.md)  
  
-   [Результирующие наборы в задаче "Выполнение SQL"](../result-sets-in-the-execute-sql-task.md)  
  
-   [Справочник по Transact-SQL &#40;ядро СУБД&#41;](/sql/t-sql/language-reference)  
  
-   Запись в блоге [Новые функции даты и времени в SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=239783)на сайте mssqltips.com  
  
  
