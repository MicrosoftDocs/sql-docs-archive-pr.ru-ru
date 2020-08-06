---
title: Запрос с полнотекстовым поиском | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d78707925303d5e19d93b170f257d76fb7d1747d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732522"
---
# <a name="query-with-full-text-search"></a>Запрос с полнотекстовым поиском
  Для определения полнотекстового поиска в полнотекстовых запросах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются полнотекстовые предикаты (CONTAINS и FREETEXT) и функции (CONTAINSTABLE и FREETEXTTABLE). Эти предикаты и функции поддерживают расширенный синтаксис [!INCLUDE[tsql](../../includes/tsql-md.md)] , который поддерживает разнообразные формы выражений запроса. Для создания полнотекстовых запросов нужно знать, когда и как использовать полнотекстовые предикаты и функции.  
  
##  <a name="overview-of-the-full-text-predicates-contains-and-freetext"></a><a name="OV_ft_predicates"></a>Общие сведения о полнотекстовых предикатах (CONTAINS и FREETEXT)  
 Предикаты CONTAINS и FREETEXT возвращают значение TRUE или FALSE. С их помощью можно задавать критерии выбора, чтобы определить, соответствует ли данная строка полнотекстовому запросу. Совпадающие строки возвращаются в результирующем наборе. Предикаты CONTAINS и FREETEXT задаются в предложении WHERE или HAVING инструкции SELECT. Они могут быть объединены с любым из других предикатов [!INCLUDE[tsql](../../includes/tsql-md.md)] , например LIKE и BETWEEN.  
  
> [!NOTE]  
>  Дополнительные сведения о синтаксисе и аргументах этих предикатов см. в разделах [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) и [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql).  
  
 При использовании предиката CONTAINS или FREETEXT можно указать, следует ли искать один столбец, список столбцов или все столбцы в таблице. Можно также указать язык, ресурсы которого будут использоваться данным полнотекстовым запросом для разбиения слов и морфологического поиска, поиска в тезаурусе и удаления неучитываемых слов.  
  
 Предикаты CONTAINS и FREETEXT используются для разных видов совпадений.  
  
-   Использование предиката CONTAINS (или CONTAINSTABLE) для нахождения точного или неточного (менее точного) совпадения с отдельными словами и фразами, сходства слов на определенном расстоянии друг от друга или взвешенных совпадений. При использовании предиката CONTAINS необходимо указать по крайней мере одно условие поиска, в котором задается искомый текст и условия, определяющие совпадения.  
  
     Между условиями поиска можно использовать логическую операцию. Дополнительные сведения см. в подразделе [Использование логических операторов-and, OR и not (в Contains и CONTAINSTABLE)](#Using_Boolean_Operators)далее в этой статье.  
  
-   Использование предикатов FREETEXT (или FREETEXTTABLE) для поиска совпадения по смыслу, а не буквального совпадения задаваемых слов, фраз или предложений ( *текст в свободной форме*). Соответствие регистрируется, если в полнотекстовом индексе указанного столбца найден любой из терминов в любой форме.  
  
 Четырехкомпонентное имя может использоваться в предикате CONTAINS или FREETEXT для запроса по столбцам полнотекстового индекса целевых таблиц на связанном сервере. Чтобы подготовить удаленный сервер к приему полнотекстовых запросов, сначала необходимо создать полнотекстовые индексы для целевых таблиц и столбцов на удаленном сервере, а затем добавить удаленный сервер в качестве связанного сервера.  
  
> [!NOTE]  
>  Полнотекстовые предикаты не допускаются в [предложении OUTPUT](/sql/t-sql/queries/output-clause-transact-sql) , если уровень совместимости базы данных установлен в 100.  
  
 
  
### <a name="examples"></a>Примеры  
  
#### <a name="a-using-contains-with-simple_term"></a>A. Использование CONTAINS с <simple_term>  
 В следующем примере выполняется поиск всех продуктов с ценой `$80.99` , которые содержат слово `"Mountain"`.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
#### <a name="b-using-freetext-to-search-for-words-containing-specified-character-values"></a>Б. Использование инструкции FREETEXT для поиска слов, содержащих определенные значения символов  
 Следующий пример просматривает все документы, содержащие слова, которые связаны со словами «vital», «safety», «components».  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```  
  
 
  
##  <a name="overview-of-the-full-text-functions-containstable-and-freetexttable"></a><a name="OV_ft_functions_CONTAINSTABLE_FREETEXTTABLE"></a>Общие сведения о полнотекстовых функциях (CONTAINSTABLE и FREETEXTTABLE)  
 На функции CONTAINSTABLE и FREETEXTTABLE можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы. Они возвращают пустую таблицу, либо таблицу с одной или несколькими строками, соответствующими полнотекстовому запросу. Возвращаемая таблица содержит только строки базовой таблицы, которые соответствуют критерию выбора, задаваемому в условии полнотекстового поиска функции.  
  
> [!NOTE]  
>  Дополнительные сведения о синтаксисе и аргументах этих функций см. в разделах [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) и [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql).  
  
 Запросы, использующие одну из этих функций, возвращают ранжирующие по релевантности значения (RANK) и полнотекстовый ключ (KEY) для каждой строки.  
  
-   Столбец KEY  
  
     Столбец KEY возвращает уникальные значения возвращаемых строк. С помощью столбца KEY можно задавать критерии выбора.  
  
-   RANK, столбец  
  
     Столбец RANK содержит *ранжирующее значение* для каждой строки, указывающее степень соответствия этой строки критериям выбора. Чем выше ранжирующее значение текста или документа в строке, тем больше она релевантна данному полнотекстовому запросу. Следует отметить, что разные строки могут ранжироваться одинаково. Можно ограничить число возвращаемых совпадений. Для этого нужно задать необязательный параметр *top_n_by_rank* . Дополнительные сведения см. в разделе [Ограничение количества результатов поиска с использованием функции RANK](limit-search-results-with-rank.md).  
  
 При использовании любой из этих функций необходимо задавать базовую таблицу, в которой производится полнотекстовый поиск. Как и для предикатов, в таблице, где выполняется поиск, можно задавать один столбец, список столбцов или все столбцы и при необходимости язык, ресурсы которого будут использоваться данным полнотекстовым запросом.  
  
 Функция CONTAINSTABLE используется для тех же видов совпадений, что и предикат CONTAINS, а функция FREETEXTTABLE — для тех же видов совпадений, что и предикат FREETEXT. Дополнительные сведения см. в подразделе [Обзор полнотекстовых предикатов (CONTAINS и FREETEXT)](#OV_ft_predicates)выше в этом разделе. При выполнении запросов, использующих функции CONTAINSTABLE и FREETEXTTABLE, необходимо явно соединять возвращаемые строки со строками в базовой таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Обычно результат функций CONTAINSTABLE или FREETEXTTABLE необходимо соединять с базовой таблицей. В таких случаях необходимо знать уникальное имя ключевого столбца. Этот столбец, который находится в каждой таблице с поддержкой полнотекстового выполнения, используется для принудительного применения уникальных строк в таблице ( *уникальный * * ключевой столбец*). Дополнительные сведения см. в разделе [Управление полнотекстовыми индексами](../indexes/indexes.md).  
  
 
  
### <a name="examples"></a>Примеры  
  
#### <a name="a-using-containstable"></a>A. Использование CONTAINSTABLE  
 В следующем примере возвращается идентификатор описания и описание всех товаров, для которых столбец **Description** содержит слово «aluminum» рядом со словом «light» или «lightweight». Возвращаются только строки с рангом 2 и выше.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
#### <a name="b-using-freetexttable"></a>Б. Использование FREETEXTTABLE  
 В следующем примере запрос FREETEXTTABLE расширяется таким образом, чтобы он возвратил первыми строки с самыми высокими ранжирующими значениями и добавил ранг каждой строки к списку выбора. Чтобы указать запрос, необходимо убедиться, что **столбец productdescriptionid** является уникальным ключевым столбцом для `ProductDescription` таблицы.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 Ниже приведено расширение того же запроса, которое возвращает только строки с ранжирующим значением 10 или выше.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 
  
##  <a name="using-boolean-operators---and-or-and-not---in-contains-and-containstable"></a><a name="Using_Boolean_Operators"></a>Использование логических операторов AND, OR и NOT IN-in CONTAINS и CONTAINSTABLE  
 Функция CONTAINSTABLE и предикат CONTAINS используют одинаковые условия поиска. Обе функции поддерживают сочетание нескольких терминов поиска с помощью логических операторов — AND, OR и NOT — для выполнения логических операций. Например, оператор AND можно использовать для поиска строк, содержащих и «латте», и «пирожное с кремом». Например, с помощью оператора AND NOT можно находить строки, которые содержат слово «бублик», но не содержат «мак».  
  
> [!NOTE]  
>  Предикаты FREETEXT и FREETEXTTABLE, напротив, обрабатывают логические термины как слова, которые следует искать.  
  
 Сведения о сочетании предиката CONTAINS с другими предикатами, которые используют логические операторы AND, OR и NOT, см. в разделе [Условие поиска (Transact-SQL)](/sql/t-sql/queries/search-condition-transact-sql).  
  
### <a name="example"></a>Пример  
 В следующем примере используется таблица ProductDescription базы данных [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] . Запрос использует предикат CONTAINS для поиска описаний, в которых идентификатор описания не равен 5 и описание содержат слова «Aluminum» и «spindle». Условие поиска использует логический оператор AND.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
 
  
##  <a name="additional-considerations-for-full-text-queries"></a><a name="Additional_Considerations"></a>Дополнительные рекомендации для полнотекстовых запросов  
 При написании полнотекстовых запросов необходимо учитывать следующее.  
  
-   Параметр LANGUAGE  
  
     Многие выражения запроса в значительной степени зависят от поведения средства разбиения по словам. Чтобы гарантировать использование правильного средства разбиения по словам (и парадигматического модуля) и файла тезауруса, рекомендуется указывать параметр LANGUAGE. Дополнительные сведения см. в разделе [Выбор языка при создании полнотекстового индекса](choose-a-language-when-creating-a-full-text-index.md).  
  
-   Стоп-слова  
  
     При определении полнотекстового запроса следует иметь в виду, что средство полнотекстового поиска не учитывает стоп-слова (также известные как пропускаемые слова), указанные в критерии поиска. Стоп-слова — это часто встречающиеся слова, которые не повышают эффективность поиска конкретного текста. Примерами могут служить слова «и», «или», «о» и «в». Стоп-слова перечислены в списке стоп-слов. Каждый полнотекстовый индекс связан с конкретным списком стоп-слов, который определяет, какие стоп-слова не указываются в запросе или в индексе во время индексирования. Дополнительные сведения см. в разделе [Настройка стоп-слов и списков стоп-слов для полнотекстового поиска и управление ими](full-text-search.md).  
  
-   Тезаурус  
  
     По умолчанию тезаурус используется в запросах FREETEXT и FREETEXTTABLE. Предикат CONTAINS и функция CONTAINSTABLE поддерживают необязательный аргумент THESAURUS.  
  
-   Чувствительность к регистру  
  
     В запросах полнотекстового поиска не учитывается регистр букв. Однако в японском языке есть несколько фонетических орфографий, в которых концепция орфографической нормализации аналогична нечувствительности к регистру (например, японская азбука = нечувствительность). Этот тип орфографической нормализации не поддерживается.  
  

  
##  <a name="querying-varbinarymax-and-xml-columns"></a><a name="varbinary"></a>Запросы к столбцам varbinary (max) и XML  
 Если для столбца типа `varbinary(max)`, `varbinary` или `xml` создан полнотекстовый индекс, то обращаться к нему с запросами можно при использовании полнотекстовых предикатов (CONTAINS и FREETEXT) и функций (CONTAINSTABLE и FREETEXTTABLE), как и к любым другим столбцам с полнотекстовым индексом.  
  
> [!IMPORTANT]  
>  Полнотекстовый поиск работает также со столбцами типа image. Однако тип данных `image` в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет удален. Избегайте использования этого типа данных в новых разработках и предусмотрите изменение приложений, использующих этот тип в настоящий момент. Вместо этого пользуйтесь типом данных `varbinary(max)`.  
  
### <a name="varbinarymax-or-varbinary-data"></a>данные типа varbinary(max) и varbinary  
 В одном столбце типа `varbinary(max)` или `varbinary` могут храниться документы различных типов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает любые типы документов, для которых в операционной системе доступен установленный фильтр. Тип каждого документа определяется по расширению имени файла этого документа. Например, при работе с DOC-файлом при полнотекстовом поиске будет использоваться фильтр, который поддерживает документы Microsoft Word. Чтобы получить список доступных типов документов, выполните запрос к представлению каталога [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) .  
  
 Учтите, что средство полнотекстового поиска может использовать имеющиеся фильтры, которые установлены в операционной системе. Перед использованием фильтров операционной системы, средств разбиения по словам и парадигматических модулей их необходимо загрузить на экземпляр сервера следующим образом.  
  
```  
EXEC sp_fulltext_service @action='load_os_resources', @value=1  
```  
  
 Для создания полнотекстового индекса на столбце типа `varbinary(max)` средству полнотекстового поиска требуется доступ к расширениям файлов документов в столбце типа `varbinary(max)`. Эта информация должна быть сохранена в столбце таблицы, который называется столбцом типов и должен быть связан со столбцом `varbinary(max)` в полнотекстовом индексе. Во время индексирования документа средство полнотекстового поиска по расширению файла в столбце типа определяет, какой фильтр следует использовать.  
  
 
  
### <a name="xml-data"></a>XML-данные  
 Столбец с данными типа `xml` содержит только документы и фрагменты XML, и для таких документов используется только фильтр XML. Поэтому столбец типов не требуется. Для столбцов типа `xml` можно создать полнотекстовый индекс, который индексирует содержимое XML-элементов, но пропускает XML-разметку. К значениям атрибута, если они не являются числовыми значениями, применяется полнотекстовый индекс. Теги элементов используются в качестве границ токенов. Поддерживаются XML- или HTML-документы и фрагменты правильного формата, содержащие несколько языков.  
  
 Дополнительные сведения о запросах к `xml` столбцу см. в разделе [Использование полнотекстового поиска с XML-столбцами](../xml/use-full-text-search-with-xml-columns.md).  
  
 
  
##  <a name="supported-forms-of-query-terms"></a><a name="supported"></a>Поддерживаемые формы терминов запроса  
 В данном разделе описана поддержка для каждой формы запроса в полнотекстовых предикатах и функциях, возвращающих наборы строк.  
  
> [!NOTE]  
>  Синтаксис терминов запросов см. по соответствующим ссылкам в столбце **Поддерживаются** в приведенной ниже таблице.  
  
|Форма выражений запросов|Описание|Поддерживаются|  
|----------------------|-----------------|------------------|  
|Одно или несколько конкретных слов или фраз (*простое выражение*)|В полнотекстовом поиске слово (или *маркер*) представляет собой строку, границы которой определяются соответствующими словами согласно лингвистическим правилам указанного языка. Допустимая фраза состоит из нескольких слов со знаками препинания между ними или без них.<br /><br /> Например, "круассан" — это слово, а "КАФ?? Au кофе с молоком "— это фраза. Такие слова и фразы называются простыми выражениями.<br /><br /> Дополнительные сведения см. в подразделе [Поиск конкретного слова или фразы (простое выражение)](#Simple_Term)далее в этом разделе.|Функции[CONTAINS](/sql/t-sql/queries/contains-transact-sql) и [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) выполняют поиск точного соответствия для фразы.<br /><br /> Функции[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) и [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) разбивают фразу на отдельные слова.|  
|Слова, начинающиеся заданным текстом, или фразы с такими словами (*префиксные выражения*)|Для создания производного слова или словоформ префиксное выражение обращается к строке, прикрепленной к началу слова.<br /><br /> Для единственного префиксного выражения частью результирующего набора будет любое слово, начинающееся с указанного выражения. Например, для префиксного выражения «auto*» совпадениями будут «automatic», «automobile» и т. д.<br /><br /> Внутри фразы каждое слово считается префиксным выражением. Например, выражение "авто тран\*" соответствует фразам "автоматическая трансмиссия" и "автомобильный транспорт", но не "автомобильный личный транспорт".<br /><br /> Дополнительные сведения см. в подразделе [Поиск префиксных форм слов или фраз (префиксное выражение)](#Prefix_Term)далее в этом разделе.|[CONTAINS](/sql/t-sql/queries/contains-transact-sql) и [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
|Формы с формами в определенном слове (*терм поколения — перегиб*)|Словоформы — это глаголы в форме различных времен и лиц или существительные в формах единственного или множественного числа. Примером такого поиска может служить поиск словоформ слова «водить». Если разные строки таблицы содержат слова «водить», «водит», «водят», «водил» и «водите», все они войдут в результирующий набор, потому что каждое из этих слов можно образовать флективным способом от слова «водить».<br /><br /> Дополнительные сведения см. в подразделе [Поиск флективных форм конкретного слова (производного терма)](#Inflectional_Generation_Term)далее в этом разделе.|[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) и [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) по умолчанию ищут условия с точки зрения всех указанных слов.<br /><br /> Запросы[CONTAINS](/sql/t-sql/queries/contains-transact-sql) и [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) поддерживают необязательный аргумент INFLECTIONAL.|  
|Синонимы определенного слова (*Условный терм-тезаурус*)|В тезаурусе определяются пользовательские синонимы терминов. Например, если в тезаурусе есть запись «{машина, автомобиль, грузовик, фургон}», можно искать синонимическую форму слова «машина». В результирующий набор войдут все строки таблицы, содержащие слова «автомобиль», «грузовик», «фургон» или «машина», потому что каждое из этих слов входит в состав расширяющего набора синонимов, содержащего и слово «машина».<br /><br /> Дополнительные сведения о структуре файлов тезауруса см. в разделе [Настройка и управление файлами тезауруса для полнотекстового поиска](configure-and-manage-thesaurus-files-for-full-text-search.md).|[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) и [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) по умолчанию используют тезаурус.<br /><br /> [Contains](/sql/t-sql/queries/contains-transact-sql) и [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) поддерживают НЕобязательный аргумент тезауруса.|  
|Слова или фразы, находящиеся рядом с другими словами или фразами (*выражения с учетом расположения*)|Выражение с учетом расположения указывает слова или фразы, находящиеся рядом друг с другом. Также можно указать максимальное количество не относящихся к поиску выражений, отделяющих первое и последнее поисковые выражения. Кроме того, можно искать два слова или две фразы в любом порядке или в порядке, в котором они указаны.<br /><br /> Примером может служить поиск строк, в которых слово «лед» находится рядом со словом «хоккей» или фраза «хоккей на льду» — рядом с фразой «катание на коньках».<br /><br /> Дополнительные сведения см. в разделе [Поиск слов близких к другим с использованием оператора NEAR](search-for-words-close-to-another-word-with-near.md).|[CONTAINS](/sql/t-sql/queries/contains-transact-sql) и [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
|Слова или фразы со взвешенными значениями (*взвешенное выражение*)|Взвешенное значение показывает уровень важности каждого слова и фразы в наборе слов и фраз. Значение веса 0,0 является самым низким, значение 1,0 — самым высоким.<br /><br /> Например, в запросе для поиска нескольких выражений можно задать вес для каждого искомого слова, обозначающий его значимость по сравнению с другими словами в условии поиска. Результат выполнения такого типа запроса будет в начале содержать наиболее релевантные строки, исходя из соответствующего веса, присвоенного искомым словам. В результирующих наборах содержатся документы или строки с любыми из указанных выражений (или содержимым, которое находится между ними), однако некоторые из результатов будут считаться важнее остальных ввиду разницы во взвешенных значениях, связанных с различными выражениями, по которым выполнялся поиск.<br /><br /> Дополнительные сведения см. в подразделе [Поиск слов или фраз с использованием взвешенных величин (взвешенное выражение)](#Weighted_Term)далее в этом разделе.|[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
  

  
###  <a name="searching-for-specific-word-or-phrase-simple-term"></a><a name="Simple_Term"></a>Поиск конкретного слова или фразы (простое выражение)  
 Для поиска конкретной фразы в таблице можно использовать запросы [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)или [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) . Например, для поиска в таблице `ProductReview` базы данных [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] всех комментариев о продукции, содержащих фразу «learning curve», можно использовать предикат CONTAINS следующим образом.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 Условие поиска (в данном случае «learning curve») может быть весьма сложным и включать один или несколько термов.  
  
 
  
###  <a name="performing-prefix-searches-prefix-term"></a><a name="Prefix_Term"></a>Выполнение поиска префикса (префиксное выражение)  
 Для поиска слов и фраз с указанным префиксом можно использовать функции [CONTAINS](/sql/t-sql/queries/contains-transact-sql) или [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) . Будут возвращены все записи в столбце, содержащие текст, который начинается с заданного префикса. Например, чтобы найти все строки, содержащие префикс `top`-, как в `top``ple`, `top``ping`и `top`. Этот запрос выглядит следующим образом.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 При выполнении этого запроса будут возвращены все фрагменты текста, соответствующие тексту, указанному перед звездочкой (*). Если текст и звездочка не ограничены двойными кавычками (например, `CONTAINS (DESCRIPTION, 'top*')`), звездочка не считается символом-шаблоном.  
  
 Если префиксный терм является фразой, каждый токен, составляющий фразу, считается отдельным префиксным термом. При выполнении такого запроса будут возвращены все строки со словами, начинающимися на префиксные термы. Например, если запрос включает префиксное выражение "light bread*", будут возвращены строки с текстом "light breaded", "lightly breaded" и "light bread", но не "Lightly toasted bread".  
  
 
  
###  <a name="searching-for-inflectional-forms-of-a-specific-word-generation-term"></a><a name="Inflectional_Generation_Term"></a>Поиск форм-слов определенного слова (терм поколения)  
 С помощью функций [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)или [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) можно найти все грамматические формы глаголов и существительных (поиск словоформ) или синонимы указанного слова (поиск по тезаурусу).  
  
 В следующем примере выполняется поиск любых форм слова «foot» («foot», «feet» и т. д.) в столбце `Comments` таблицы `ProductReview` в базе данных `AdventureWorks` .  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
> [!NOTE]  
>  В полнотекстовом поиске используются парадигматические модули, которые позволяют найти глагол в формах различных времен и лиц или существительное в формах единственного или множественного числа. Дополнительные сведения о парадигматических модулях см. в разделе [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  

  
###  <a name="searching-for-words-or-phrases-using-weighted-values-weighted-term"></a><a name="Weighted_Term"></a>Поиск слов или фраз с использованием взвешенных значений (взвешенное выражение)  
 Для поиска слов и фраз можно использовать функцию [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) с взвешенными значениями. Вес, измеряемый числом от 0,0 до 1,0, обозначает степень важности каждого слова и фразы в наборе слов или фраз. Значение веса 0,0 является самым низким, значение 1,0 — самым высоким.  
  
 В следующем примере показан запрос, выполняющий поиск (с использованием взвешенных значений) всех адресов заказчиков, в которых текст, начинающийся со строки «Bay», продолжается строкой «Street» или «View». В результатах более высокий ранг назначается тем строкам, в которых встречается больше заданных слов.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 Взвешенное выражение можно использовать в сочетании с любым простым выражением, префиксным выражением, производным выражением или выражением с учетом расположения.  
  

  
##  <a name="viewing-the-tokenization-result-of-a-word-breaker-thesaurus-and-stoplist-combination"></a><a name="tokens"></a>Просмотр результатов разметки для сочетания "средство разбиения по словам", тезауруса и списка стоп-слов  
 После применения сочетания данного средства разбиения текста на слова, тезауруса и списка стоп-слов к строковым входным данным запроса итоговый результат разметки можно просмотреть с помощью динамического административного представления **sys.dm_fts_parser**. Дополнительные сведения см. в разделе [sys.dm_fts_parser (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).  
  
 
  
## <a name="see-also"></a>См. также:  
 [CONTAINS (Transact-SQL)](/sql/t-sql/queries/contains-transact-sql)   
 [CONTAINSTABLE (Transact-SQL)](/sql/relational-databases/system-functions/containstable-transact-sql)   
 [FREETEXT (Transact-SQL)](/sql/t-sql/queries/freetext-transact-sql)   
 [FREETEXTTABLE (Transact-SQL)](/sql/relational-databases/system-functions/freetexttable-transact-sql)   
 [Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/visual-database-tools.md)   
 [Улучшение производительности полнотекстовых запросов](improve-the-performance-of-full-text-queries.md)  
  
  
