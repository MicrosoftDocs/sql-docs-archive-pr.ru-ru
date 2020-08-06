---
title: Изменения в работе функций ядро СУБД в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- behavior changes [SQL Server]
- Database Engine [SQL Server], what's new
- Transact-SQL behavior changes
ms.assetid: 65eaafa1-9e06-4264-b547-cbee8013c995
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9072b851f3512113b23dedc91f8c9b7151136a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732034"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a>Изменения в работе функций компонента Database Engine в SQL Server 2014
  В этом разделе описаны изменения в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)]. Изменения в работе оказывают влияние на способ выполнения функций или взаимодействие между ними в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] по сравнению с предыдущими версиями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="behavior-changes-in-sssql14"></a><a name="SQL14"></a>Изменения в работе[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 В предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запросы к XML-документу, содержащие строки длиннее определенной длины (более 4020 символов), могут возвращать неверные результаты. В [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] такие результаты возвращаются верно.  
  
## <a name="behavior-changes-in-sssql11"></a><a name="Denali"></a>Изменения в работе[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="metadata-discovery"></a>Обнаружение метаданных  
 Усовершенствования в, [!INCLUDE[ssDE](../includes/ssde-md.md)] начиная с, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] позволяют SQLDescribeCol получить более точные описания ожидаемых результатов, чем возвращенные SQLDescribeCol в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Обнаружение метаданных](../relational-databases/native-client/features/metadata-discovery.md).  
  
 Параметр [SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql) для определения формата ответа без фактического выполнения запроса заменяется на [sp_describe_first_result_set &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql), [sp_describe_undeclared_parameters &#40;Transact ](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql)-sql&#41;, [sys. dm_exec_describe_first_result_set &#40;transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql)и [sys. dm_exec_describe_first_result_set_for_object &#40;Transact-SQL ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql)&#41;.  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a>Изменения в работе скриптов для задач агента SQL Server  
Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , если создать задание путем копирования скрипта из существующего задания, новое задание может случайно повлиять на существующее задание. Чтобы создать новое задание с помощью скрипта из существующего задания, вручную удалите параметр * \@ schedule_uid* который обычно является последним параметром раздела, который создает расписание задания в существующем задании. При этом для нового задания будет создано независимое расписание, которое не окажет влияния на существующие задания.  
  
### <a name="constant-folding-for-clr-user-defined-functions-and-methods"></a>Свертка констант для определяемых пользователем функций и методов среды CLR  
Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , теперь свертываемые следующие пользовательские объекты CLR:  

-   детерминированные, определяемые пользователем функции среды CLR, возвращающие скалярное значение;  
-   детерминированные методы определяемых пользователем типов данных CLR.  
  
 Это улучшение должно повысить производительность при многократном вызове этих функций и методов с одинаковыми аргументами. Однако это изменение может приводить к непредвиденным результатам, когда недетерминированные функции или методы были ошибочно отмечены как детерминированные. Детерминированность функции или метода среды CLR задается значением свойства `IsDeterministic` атрибута `SqlFunctionAttribute` или `SqlMethodAttribute`.  
  
### <a name="behavior-of-stenvelope-method-has-changed-with-empty-spatial-types"></a>Изменение работы метода STEnvelope() с пустыми пространственными типами  
 Метод `STEnvelope` с пустыми объектами теперь выполняется так же, как и другие пространственные методы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 В [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] метод `STEnvelope` при вызове с пустыми объектами возвращал следующие результаты:  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns POINT EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns LINESTRING EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns POLYGON EMPTY  
```  
  
 В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] метод `STEnvelope` при вызове с пустыми объектами возвращает следующие результаты:  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
```  
  
 Чтобы определить, является ли пространственный объект пустым, вызовите метод [STIsEmpty &#40;Geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) .  
  
### <a name="log-function-has-new-optional-parameter"></a>Новый необязательный параметр функции LOG  
 `LOG`Теперь функция имеет необязательный *базовый* параметр. Дополнительные сведения см. в разделе [LOG &#40;Transact-SQL&#41;](/sql/t-sql/functions/log-transact-sql).  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a>Изменение статистических вычислений во время операций с секционированным индексом  
Статистические данные в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] не создаются путем сканирования всех строк таблицы при создании или перестроении секционированного индекса. Вместо этого оптимизатор запросов использует для создания статистики алгоритм выборки по умолчанию. После обновления базы данных с секционированными индексами можно заметить разницу в гистограммах для этих индексов. Это изменение в поведении может не влиять на время выполнения запросов. Для получения статистики по секционированным индексам путем сканирования всех строк таблицы используйте инструкции `CREATE STATISTICS` или `UPDATE STATISTICS` с предложением `FULLSCAN`.  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a>Изменение преобразования типов данных XML-методом value  
Скрытое поведение метода `value` типа данных `xml` изменилось. Этот метод выполняет запрос XQuery к XML-данным и возвращает скалярное значение указанного типа данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Тип xs необходимо преобразовать в тип данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Прежде метод `value` в скрытом режиме преобразовывал исходное значение в xs:string, а затем xs:string — в тип данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] преобразование в xs:string опускается для следующих типов:  
  
|Исходный тип данных XS|Целевой тип данных SQL Server|  
|-------------------------|--------------------------------------|  
|byte<br /><br /> short<br /><br /> int<br /><br /> целочисленный<br /><br /> long<br /><br /> unsignedByte<br /><br /> unsignedShort<br /><br /> unsignedInt<br /><br /> unsignedLong<br /><br /> positiveInteger<br /><br /> nonPositiveInteger<br /><br /> negativeInteger<br /><br /> nonNegativeInteger|tinyint<br /><br /> smallint<br /><br /> int<br /><br /> BIGINT<br /><br /> Decimal<br /><br /> NUMERIC|  
|Decimal|Decimal<br /><br /> NUMERIC|  
|FLOAT|real|  
|double|FLOAT|  
  
 Новые правила повышают производительность, если можно пропустить промежуточное преобразование. Однако при сбое преобразования данных появляются сообщения об ошибке, отличные от тех, которые возникают при преобразовании из промежуточного значения xs:string. Например, если метод value не смог преобразовать значение 100 000 типа `int` в `smallint`, то предыдущее сообщение об ошибке будет выглядеть так:  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] без промежуточного преобразования в xs:string сообщение об ошибке выглядит следующим образом:  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a>Изменение в работе программы sqlcmd.exe в режиме XML  
 Существуют изменения в работе, если используется sqlcmd.exe с режимом XML (команда: XML ON) при выполнении команды SELECT * FROM T FOR XML...  
  
### <a name="dbcc-checkident-revised-message"></a>Измененное сообщение DBCC CHECKIDENT  
 В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] сообщение, возвращенное командой DBCC CHECKIDENT, изменилось, только если оно используется с *new_reseed_value* повторного заполнения для изменения текущего значения идентификатора. Новое сообщение — *"Проверка сведений об удостоверении: текущее значение идентификатора" \<current identity value> "*. Выполнение инструкции DBCC завершено. Если инструкция DBCC выдает сообщения об ошибках, обратитесь к системному администратору».  
  
 В более ранних версиях сообщение *"проверяет сведения об удостоверении: текущее значение идентификатора" \<current identity value> ", текущее значение столбца" \<current column value> ". Выполнение DBCC завершено. Если команда DBCC выводит сообщения об ошибках, обратитесь к системному администратору».* Сообщение не изменяется `DBCC CHECKIDENT` , если указывается с `NORESEED` параметром, без второго параметра или без переначального значения. Дополнительные сведения см. в разделе [DBCC CHECKIDENT (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a>Изменилась работа функции exist() типа данных XML  
 Поведение `exist()` функции изменилось при сравнении типа данных XML со значением NULL, равным 0 (нулю). Рассмотрим следующий пример:  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 0;  
```  
  
 В более ранних версиях это сравнение возвращает 1 (true). Теперь это сравнение возвращает значение 0 (нуль, false).  
  
 Не изменились следующие сравнения:  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 1; -- 0 expected, 0 returned  
SELECT COUNT(1) WHERE @test.exist('/dogs') IS NULL; -- 1 expected, 1 returned  
```  
  
## <a name="see-also"></a>См. также:  
 [Критические изменения в функциях ядро СУБД в SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md)   
 [Устаревшие функции ядро СУБД в SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md)   
 [Неподдерживаемые функции ядро СУБД в SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
