---
title: Совместимость формул DAX в режиме DirectQuery (SSAS 2014) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: de83cfa9-9ffe-4e24-9c74-96a3876cb4bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: acaac82d6930787a45281c0e942def8df764f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658532"
---
# <a name="dax-formula-compatibility-in-directquery-mode-ssas-2014"></a>Совместимость формул DAX в режиме DirectQuery (SSAS 2014)
Язык выражений анализа данных (DAX) можно использовать для создания мер и других пользовательских формул для использования в Analysis Services табличных моделях, [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] моделях данных в книгах Excel и Power BI Desktop моделях данных. В большинстве случаев модели, создаваемые в этих средах, идентичны, и вы можете использовать одни и те же меры, отношения и ключевые показатели эффективности и т. д. Однако при создании Analysis Services табличной модели и развертывании ее в режиме DirectQuery существуют некоторые ограничения на формулы, которые можно использовать. В этом разделе представлен обзор этих различий, перечислены функции, которые не поддерживаются в SQL Server 2014 Analysis Services табличной модели на уровне совместимости 1100 или 1103 и в режиме DirectQuery, а также перечислены поддерживаемые функции, но могут возвращать различные результаты.  
  
В этом разделе мы используем термин « *модель в памяти* » для ссылки на табличные модели, которые являются полностью размещенными в памяти кэшированными данными на Analysis Services сервере, работающем в табличном режиме. Мы используем *модели DirectQuery* для обращения к табличным моделям, которые были созданы и (или) развернуты в режиме DirectQuery. Сведения о режиме DirectQuery см. в разделе [режим DirectQuery (табличные службы SSAS)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5).  
  
  
## <a name="differences-between-in-memory-and-directquery-mode"></a><a name="bkmk_SemanticDifferences"></a>Различия между режимами в памяти и DirectQuery  
При опросе модели, развернутой в режиме DirectQuery, могут возвращаться результаты, отличные от результатов, получаемых при развертывании той же самой модели в памяти. Это обусловлено тем, что при использовании DirectQuery данные запрашиваются непосредственно из реляционного хранилища данных, а агрегаты, необходимые для формул, выполняются с помощью соответствующего реляционного механизма, а не с помощью подсистемы аналитики в памяти xVelocity (VertiPaq) для хранения и вычисления.  
  
Например, существуют различия между тем, как некоторые реляционные хранилища данных обрабатывают цифровые значения, даты, значения NULL и т. п.  
  
По контрасту язык DAX предназначен для максимально приближенной эмуляции функций Microsoft Excel. Например, при обработке значений NULL, пустых строк и нулевых значений Excel выполняет попытку найти лучший ответ вне зависимости от точного типа данных, поэтому механизм xVelocity выполняет это же действие. Однако когда табличная модель развертывается в режиме DirectQuery и происходит передача формул в реляционный источник данных для их оценки, данные должны обрабатываться в соответствии с семантикой реляционного источника данных, в которой обычно требуется точно определенная обработка пустых строк, в отличие от значений NULL. По этой причине при обработке одной и той же формулы могут получаться различные результаты при оценке кэшируемых данных и данных, получаемых непосредственно от реляционного источника.  
  
Кроме того, некоторые функции нельзя использовать в режиме DirectQuery, поскольку вычисление потребует, чтобы данные в текущем контексте отправлялись в реляционный источник данных в качестве параметра. Например, меры в [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] книге часто используют функции логики операций со временем, которые ссылаются на диапазоны дат, доступные в книге. Такие формулы, как правило, не могут использоваться в режиме DirectQuery.  
  
## <a name="semantic-differences"></a>Семантические различия  
В этом разделе приведен список типов возможных семантических различий, а также описаны ограничения, применимые к способу использования функций или к результатам запроса.  
  
### <a name="comparisons"></a><a name="bkmk_Comparisons"></a>Сравнение  
Язык DAX в моделях, находящихся в памяти, поддерживает сравнения двух выражений, разрешающихся в скалярные значения различных типов данных. Однако модели, развертываемые в режиме DirectQuery, используют типы данных и операторы сравнения, заданные в реляционном механизме. Это может привести к различиям в результатах.  
  
В следующих примерах сравнения всегда будет выводиться ошибка при вычислении средствами источника данных DirectQuery:  
  
-   Числовой тип данных и любой тип строковых данных  
  
-   Числовой тип данных и логическое значение  
  
-   Любой строковый тип данных и логическое значение  
  
В общем и целом язык DAX более терпим по отношению к несовпадениям типов данных в моделях в памяти. Будет выполнена попытка имплицитного приведения значений до двух раз, как описано в этом разделе. Однако формулы, отправленные в реляционное хранилище данных в режиме DirectQuery, оцениваются более строго, согласно правилам реляционного механизма, при этом вероятность ошибки при их обработке более высока.  
  
**Сравнение строк и чисел**  
ПРИМЕР: `"2" < 3`  
  
Выполняется сравнение текстовой строки и числа при помощи формулы. Как в режиме DirectQuery, так и в модели в памяти выражение имеет значение **true** .  
  
В модели в памяти результат — **true** , поскольку результаты в виде строк неявно приводятся к численному типу данных для сравнения с другими числами. SQL также неявно приводит текстовые числа как числа для сравнения с числовыми типами данных.  
  
Обратите внимание, что это приводит к изменению поведения первой версии [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] , что возвращало бы **значение false**, поскольку текст "2" всегда будет считаться больше, чем любое число.  
  
**Сравнение текстовых и булевых значений**  
ПРИМЕР: `"VERDADERO" = TRUE`  
  
В этом выражении сравнивается текстовая строка с логическим значением. Главным образом для моделей DirectQuery или моделей в памяти сравнение строкового значения с логическим значением приводит к ошибке. Единственным исключением для данного правила являются случаи, когда строка содержит слово **true** или слово **false**. Если строка содержит любые значения true или false, выполняются преобразование в логическое значение и сравнение, приводящее к итоговому логическому результату.  
  
**Сравнение значений NULL**  
ПРИМЕР: `EVALUATE ROW("X", BLANK() = BLANK())`  
  
В этой формуле сравнивается эквивалент значения NULL в SQL со значением NULL. Возвращается значение **true** для модели в памяти и модели DirectQuery. Затем выполняется подготовка в модели DirectQuery, необходимая для того, чтобы гарантировать похожее поведение модели в памяти.  
  
Обратите внимание, что в Transact-SQL значение NULL никогда не равно NULL. Однако в DAX пустое значение равно другому пустому значению. Такое поведение является одинаковым для всех моделей в памяти. Важно заметить, что в режиме DirectQuery используется по большей части семантика SQL Server. Однако в этом случае она отделена от него так, что сравнения со значением NULL действуют по-другому.  
  
### <a name="casts"></a><a name="bkmk_Casts"></a>Приведения  
  
В языке DAX нет функции приведения как таковой, однако в ходе многих операций сравнения и арифметических операций выполняются неявные приведения. Сравнение или арифметическая операция определяет тип данных для полученного результата. например следующие.  
  
-   Логические значения обрабатываются как численные в ходе арифметических операций, например в виде TRUE + 1 или с применением функции к столбцу логических значений. Операция НЕ также возвращает числовое значение.  
  
-   Логические значения при сравнениях или с операторами EXACT, AND, OR, &amp;&amp;или || всегда обрабатываются как логические значения.  
  
**Приведение строковых данных в логические**  
В моделях в памяти и DirectQuery приведение разрешено к логическим значениям только из следующих строк: **""** (пустая строка), **"true"**, **"false"**; , где пустая строка приводится к значению false.  
  
Приведение к логическому типу данных любой другой строки приводит к ошибке.  
  
**Преобразование из строки в дату и время**  
В режиме DirectQuery преобразования из строковых представлений дат и времени в фактические значения **datetime** ведут себя так же, как и в сервере SQL Server.  
  
Сведения о правилах, регулирующих приведение строковых значений к типам данных **DateTime** в [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] моделях, см. в [справочнике по синтаксису DAX](/dax/dax-syntax-reference).
  
Модели, в которых используется хранение данных в памяти, поддерживают более ограниченный диапазон текстовых форматов для дат, чем строковые форматы для дат, поддерживаемые в SQL Server. Однако язык DAX поддерживает настраиваемые форматы даты и времени.  
  
**Преобразование из строки в другие нелогические значения**  
При преобразовании из строк в нелогические значения режим DirectQuery ведет себя так же, как SQL Server. Дополнительные сведения см. в разделе [Функции CAST и CONVERT (Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8).  
  
**Преобразование из чисел в строку не разрешено**  
ПРИМЕР: `CONCATENATE(102,",345")`  
  
Преобразование из чисел в строки в SQL Server не допускается.  
  
Эта формула возвращает ошибку в табличных моделях и в режиме DirectQuery. Однако в [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]она дает результат.  
  
**Две попытки преобразования не поддерживаются в DirectQuery**  
Модели в памяти часто пытаются выполнить вторую попытку преобразования после первой неудачной попытки. Этого никогда не происходит в режиме DirectQuery.  
  
ПРИМЕР: `TODAY() + "13:14:15"`  
  
В этом выражении первый параметр принадлежит к типу **datetime** , а второй параметр принадлежит к типу **string**. Однако преобразования при комбинировании операндов обрабатываются по-разному. DAX выполняет неявное преобразование из **string** в **double**. В моделях в памяти в ядре формулы предпринимается попытка преобразования в **double**напрямую и при неудачной попытке последует попытка преобразования в **datetime**.  
  
В режиме DirectQuery будут применены только преобразования из **string** в **double** . Если такое преобразование завершается неудачно, при использовании формулы будет возвращена ошибка.  
  
### <a name="math-functions-and-arithmetic-operations"></a><a name="bkmk_Math"></a>Математические функции и арифметические операции  
При использовании некоторых математических функций в режиме DirectQuery будут возвращены другие результаты. Это происходит из-за различий в базовом типе данных или преобразований, которые применяются во время операций. Также вышеописанные ограничения в пределах допустимых значений могут отразиться на результате арифметических операций.  
  
**Порядок сложения**  
При создании формулы, в которой происходит сложение последовательности чисел, модель в памяти может обработать эти числа в ином порядке, чем модель DirectQuery.  Поэтому при совершении операций с очень большими положительными и отрицательными числами может произойти ошибка в одной операции, хотя в другой может быть выдан результат.  
  
**Использование функции возведения в степень**  
ПРИМЕР: `POWER(-64, 1/3)`  
  
В режиме DirectQuery при использовании функции возведения в степень не допускается использование отрицательных значений в качестве основания при возведении в дробную степень. В SQL Server такое поведение ожидаемо.  
  
В модели в памяти формула возвращает -4.  
  
**Операции численного переполнения**  
В Transact-SQL операции, приводящие к численному переполнению, возвращают ошибку переполнения, поэтому формулы, которые приводят к переполнению, также выдают ошибку в режиме DirectQuery.  
  
Однако эта же формула при использовании в модели в памяти возвращает 8-байтовое целое. Это происходит потому, что механизм обработки формул не выполняет проверок в случае численного переполнения.  
  
**Функции LOG с пробелами возвращают другие результаты**  
SQL Server обрабатывает значения NULL и пустые значения иначе, чем механизм xVelocity. В результате Следующая формула возвращает ошибку в режиме DirectQuery, но возвращают бесконечное значение (-INF) в режиме в памяти.  
  
`EXAMPLE: LOG(blank())`  
  
Те же ограничения применяются к другим логарифмическим функциям, LOG10 и LN.  
  
Дополнительные сведения о типе данных **blank** в DAX см. в разделе [Справочник по синтаксису DAX](/dax/dax-syntax-reference).
  
**Деление на 0 и деление на пустые данные**  
В режиме DirectQuery при делении на нуль (0) или при делении на пустые данные (BLANK) всегда выдается ошибка. SQL Server не поддерживает концепцию бесконечности, и, поскольку естественным результатом при делении на нуль становится бесконечность, происходит ошибка. Однако SQL Server поддерживает деление на значения NULL, а результат всегда должно равняться NULL.  
  
Вместо того чтобы возвращать различные результаты для этих операций, в режиме DirectQuery оба типа операций (деление на нуль и деление на значение NULL) возвращают ошибку.  
  
Обратите внимание, что в моделях [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] и PowerPivot при делении на нуль также возвращается ошибка. При делении на пустые данные возвращаются пустые данные.  
  
Все следующие выражения допустимы для моделей в памяти, однако при их обработке в режиме DirectQuery произойдет ошибка:  
  
`1/BLANK`  
  
`1/0`  
  
`0.0/BLANK`  
  
`0/0`  
  
Выражение `BLANK/BLANK` — особый вариант, при котором возвращается `BLANK` как в модели в памяти, так и в режиме DirectQuery.  
  
### <a name="supported-numeric-and-date-time-ranges"></a><a name="bkmk_Ranges"></a>Поддерживаемые числовые диапазоны и диапазоны даты и времени  
В формулах [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] и табличных моделях в памяти действуют те же ограничения, что и в Excel, в отношении максимально допустимого числа и дат. Однако при возврате максимального значения при операции вычисления или запроса или при преобразовании, приведении, округлении или усечении значений.  
  
-   При умножении значений типов **Currency** и **Real** , когда результат превышает максимально допустимое значение, в режиме DirectQuery это не приводит к ошибке и возвращается значение NULL.  
  
-   При использовании модели в памяти ошибка не возникает и возвращается максимальное значение.  
  
В общем, поскольку приемлемый диапазон дат различается для Excel и SQL Server, совпадение результатов можно гарантировать только тогда, когда даты находятся в схожих допустимых пределах, что справедливо и по отношению к следующим датам:  
  
-   Наиболее ранняя дата: 1 марта 1990 года  
  
-   Наиболее поздняя дата: 31 декабря 9999 года  
  
Если любые даты, используемые в формулах, не попадают в этот диапазон, при выполнении формулы либо произойдет ошибка, либо результаты не будут одинаковыми для двух описываемых случаев.  
  
**Поддержка функции CEILING для вычислений с плавающей запятой**  
ПРИМЕР: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`  
  
Эквивалент Transact-SQL для функции DAX CEILING поддерживает вычисления с числами 10^19 или меньшими. Основное правило состоит в том, что значения с плавающей запятой должны подходить для **bigint**.  
  
**Функции datepart с датами вне диапазона**  
Результаты обработки данных в режиме DirectQuery гарантированно совпадают с аналогичными результатами для моделей в памяти только тогда, когда дата, используемая в качестве аргумента, принадлежит диапазону допустимых дат. Если эти условия не удовлетворяются, либо возникает ошибка, либо при обработке формулы в режиме DirectQuery и в модели в памяти будут получены разные результаты.  
  
Пример: `MONTH(0)` или `YEAR(0)`  
  
В режиме DirectQuery выражения возвращают 12 и 1899 соответственно.  
  
В моделях в памяти выражения возвращают 1 и 1900 соответственно.  
  
ПРИМЕР:  `EOMONTH(0.0001, 1)`  
  
Результаты этих выражений будут совпадать, только если переданные в качестве параметра данные принадлежат диапазону допустимых дат.  
  
Пример: `EOMONTH(blank(), blank())` или `EDATE(blank(), blank())`  
  
Результаты этого выражения должны совпадать в режиме DirectQuery и в режиме в памяти.  
  
**Усечение временных значений**  
ПРИМЕР: `SECOND(1231.04097222222)`  
  
В режиме DirectQuery результат усекается в соответствии с правилами SQL Server и результатом выполнения выражения будет 59.  
  
В моделях в памяти результаты каждой промежуточной операции округляются, поэтому выражение принимает значение 0.  
  
В следующем примере показано, как вычисляется это значение:  
  
1.  Дробный ввод (0,04097222222) умножается на 24.  
  
2.  Результирующее значение часа (0,98333333328) умножается на 60.  
  
3.  Полученное значение в минутах — 58,9999999968.  
  
4.  Дробное значение в минутах (0,9999999968) умножается на 60.  
  
5.  Полученное второе значение (59,999999808) округляется до 60.  
  
6.  60 является эквивалентом 0.  
  
**Тип данных SQL Time не поддерживается**  
Для моделей в памяти не поддерживается использование нового типа данных SQL **Time** . В режиме DirectQuery формулы, которые ссылаются на столбцы с этим типом данных, будут возвращать ошибку. Столбцы данных времени не могут быть импортированы в модель в памяти.  
  
Однако в [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] и в кэшированных моделях иногда подсистема приводит значение времени к допустимому типу данных, а формула возвращает результат.  
  
Такое поведение затрагивает все функции, которые используют столбец дат в качестве параметра.  
  
### <a name="currency"></a><a name="bkmk_Currency"></a>Режиме  
В режиме DirectQuery, если результат арифметической операции имеет тип **Currency**, значение должно принадлежать следующему диапазону:  
  
-   Минимум: -922337203685477,5808  
  
-   Максимум: 922337203685477,5807  
  
**Сочетание типов данных «Валюта» и «REAL»**  
ПРИМЕР: `Currency sample 1`  
  
Если умножить типы данных **Currency** и **Real** и результат окажется выше значения 9223372036854774784 (0x7ffffffffffffc00), в режиме DirectQuery не произойдет ошибки.  
  
В модели в памяти происходит ошибка, если абсолютное значение результата превышает 922337203685477,4784.  
  
**Выполнение операции приводит к возникновению значения, не принадлежащего допустимому диапазону**  
ПРИМЕР: `Currency sample 2`  
  
Если операции с любыми двумя значениями типа «Валюта» приводят к значению, не принадлежащему указанному диапазону, в моделях в памяти возникает ошибка, которой, однако, не возникает в случае с моделями DirectQuery.  
  
**Сочетание типа данных «Валюта» с другими типами данных**  
Деление значений валюты на значения другого числового типа может привести к различным результатам.  
  
### <a name="aggregation-functions"></a><a name="bkmk_Aggregations"></a>Агрегатные функции  
Статистические функции в таблице с одной строкой возвращают разные результаты. Поведение агрегатных функций, выполняемых в отношении пустых таблиц, также отличается для моделей в памяти и моделей DirectQuery.  
  
**Статистические функции, выполняемые в таблице с одной строкой**  
Если таблица, используемая в качестве аргумента, содержит один ряд, в режиме DirectQuery статистические функции, такие как STDEV и VAR, возвращают значение NULL.  
  
В модели в памяти формула, в которой используются функции STDEV или VAR для таблицы с одним рядом, возвращает ошибку деления на нуль.  
  
### <a name="text-functions"></a><a name="bkmk_Text"></a>Текстовые функции  
Поскольку реляционные хранилища данных предоставляют типы текстовых данных, отличные от Excel, могут получиться другие результаты при поиске строк либо при работе с подстроками. Длина строк также может отличаться.  
  
В общем, любые функции работы со строками, в которых в качестве аргументов используются столбцы фиксированного размера, могут возвращать различные результаты.  
  
Кроме того, в SQL Server некоторые текстовые функции поддерживают дополнительные аргументы, которые отсутствуют в Excel. Если формула требует отсутствующего аргумента, при использовании модели в памяти можно получить различные результаты или ошибки.  
  
**В операциях, символ в которых возвращается с помощью функций LEFT, RIGHT и т. п., возможен возврат верного символа, но в другом регистре или результатов может не получиться.**  
ПРИМЕР: `LEFT(["text"], 2)`  
  
В режиме DirectQuery регистр возвращаемого символа всегда точно такой же, как у буквы, сохраненной в базе данных. Однако подсистема xVelocity использует другой алгоритм для сжатия и индексирования значений с целью улучшения производительности.  
  
По умолчанию используются параметры сортировки Latin1_General, которые не учитывают регистр, однако учитывают диакритические знаки. Поэтому при наличии нескольких экземпляров текста в нижнем регистре, верхнем регистре или в смешанном регистре все экземпляры считаются одной и той же строкой, а в индексе сохраняется только первый экземпляр строки. Все текстовые функции, выполняемые для сохраненных строк, будут получать указанную порцию проиндексированной формы. Потому при использовании формулы-примера будет возвращено одно значение для всего столбца с использованием первого экземпляра в качестве входа.  
  
[Хранение строк и параметры сортировки в табличных моделях](https://msdn.microsoft.com/8516f0ad-32ee-4688-a304-e705143642ca)  
  
Это также относится к другим текстовым функции, в том числе к функциям RIGHT, MID и т. п.  
  
**Длина строки влияет на результаты**  
ПРИМЕР: `SEARCH("within string", "sample target  text", 1, 1)`  
  
При поиске строки с использованием функции SEARCH (поиск), при котором искомая строка длиннее внутренней строки, в режиме DirectQuery возникнет ошибка.  
  
Для модели в памяти возвращается искомая строка, однако ее длина усекается до длины строки &lt;внутри текста&gt;.  
  
ПРИМЕР: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`  
  
Если длина строки-заменителя превышает длину первоначальной строки в режиме DirectQuery, формула возвратит значение NULL.  
  
В моделях в памяти формула повторяет режим работы в Excel, в котором исходная строка объединяется со строкой для замены, причем возвращается значение CACalifornia.  
  
**Неявное выполнение функции TRIM в середине строк**  
ПРИМЕР: `TRIM(" A sample sentence with leading white space")`  
  
В режиме DirectQuery функция DAX TRIM переводится в инструкцию SQL `LTRIM(RTRIM(<column>))`. В результате удаляется только ведущий и замыкающий пробелы.  
  
Однако та же формула в модели в памяти удалит пробелы внутри строки, подобно поведению Excel.  
  
**Неявное выполнение функции RTRIM с использованием функции LEN**  
ПРИМЕР: `LEN('string_column')`  
  
Как и в SQL Server, в режиме DirectQuery автоматически удаляются пробелы в конце строковых столбцов, то есть выполняется неявная функция RTRIM. Поэтому формулы, использующие функцию LEN, могут возвращать различные значения при наличии конечных пробелов в строке.  
  
**Подсистема в памяти поддерживает дополнительные параметры функции SUBSTITUTE**  
ПРИМЕР: `SUBSTITUTE([Title],"Doctor","Dr.")`  
  
ПРИМЕР: `SUBSTITUTE([Title],"Doctor","Dr.", 2)`  
  
В режиме DirectQuery можно использовать только версию этой функции, которая содержит три (3) параметра: ссылку на столбец, старый текст и новый текст. Если использовать вторую формулу, возникает ошибка.  
  
При использовании моделей в памяти можно использовать дополнительный четвертый параметр для указания номера экземпляра для строки, которую необходимо заменить. Например, можно заменить только второй экземпляр и т. п.  
  
**Ограничения длины строки для операций REPT**  
В моделях в памяти длина строки, получаемой при выполнении операции, использующей функцию REPT, не должна превышать 32 767 символов.  
  
Это ограничение не применяется в режиме DirectQuery.  
  
**Операции с подстроками возвращают различные результаты в зависимости от типа символов**  
ПРИМЕР: `MID([col], 2, 5)`  
  
Если вводимый текст принадлежит к типам **varchar** или **nvarchar**, результат формулы всегда один и тот же.  
  
Однако если текст является символом фиксированной длины, а значение * &lt; num_chars &gt; * больше длины целевой строки, в режиме DirectQuery добавляется пустая строка в конец результирующей строки.  
  
В модели в памяти результат завершается на последнем строковом символе без заполнения.  
  
## <a name="functions-supported-in-directquery-mode"></a><a name="bkmk_SupportedFunc"></a>Функции, поддерживаемые в режиме DirectQuery  
С учетом условий, описанных в предыдущем разделе, следующие функции DAX можно использовать в режиме DirectQuery.  
  
**Текстовые функции**  
  
CONCATENATE  
  
FIND  
  
LEFT  
  
LEN  
  
MID  
  
REPLACE  
  
REPT  
  
RIGHT  
  
SUBSTITUTE  
  
TRIM  
  
**Статистические функции**  
  
COUNT  
  
STDEV.P  
  
STDEV.S  
  
STDEVX.P  
  
STDEVX.S  
  
VAR.P  
  
VAR.S  
  
VARX.P  
  
VARX.S  
  
**Функции даты и времени**  
  
DATE  
  
EDATE  
  
EOMONTH  
  
DATE  
  
TIME  
  
SECOND  
  
**Математические и численные функции**  
  
CEILING  
  
LN  
  
LOG  
  
LOG10  
  
POWER  
  
**Запросы к таблицам DAX**  
  
При оценке формул для модели DirectQuery при помощи запросов к таблицам в DAX существуют некоторые ограничения. DirectQuery не поддерживает ссылок на тот же столбец дважды в предложении ORDER BY. В этой ситуации не удастся создать эквивалентную инструкцию Transact-SQL, поэтому запрос завершится неудачей.  
  
Для модели в памяти повтор предложения ORDER BY на результаты не повлияет.  
  
## <a name="functions-not-supported-in-directquery-mode"></a><a name="bkmk_NotSupportedFunc"></a>Функции, не поддерживаемые в режиме DirectQuery  
Некоторые функции DAX не поддерживаются в моделях, развернутых в режиме DirectQuery. Среди причин отсутствия поддержки той или иной функции могут быть следующие, как в отдельности, так и в сочетании:  
  
-   Базовый реляционный механизм не может выполнять вычисления, эквивалентные функциям подсистемы xVelocity.  
  
-   Формула не может быть преобразована в эквивалент выражения SQL.  
  
-   Производительность преобразованного выражения и итог вычислений будут неприемлемыми.  
  
Следующие функции DAX не могут использоваться в моделях DirectQuery.  
  
**Функции пути**  
  
PATH  
  
PATHCONTAINS  
  
PATHITEM  
  
PATHITEMREVERSE  
  
PATHLENGTH  
  
**Прочие функции**  
  
COUNTBLANK  
  
FIXED  
  
FORMAT  
  
RAND  
  
RANDBETWEEN  
  
**Функции логики операций со временем: даты начала и окончания**  
  
DATESQTD  
  
DATESYTD  
  
DATESMTD  
  
DATESQTD  
  
DATESINPERIOD  
  
TOTALMTD  
  
TOTALQTD  
  
TOTALYTD  
  
DATESINPERIOD  
  
SAMEPERIODLASTYEAR  
  
PARALLELPERIOD  
  
**Функции логики операций со временем: балансы**  
  
OPENINGBALANCEMONTH  
  
OPENINGBALANCEQUARTER  
  
OPENINGBALANCEYEAR  
  
CLOSINGBALANCEMONTH  
  
CLOSINGBALANCEQUARTER  
  
CLOSINGBALANCEYEAR  
  
**Функции логики операций со временем: предыдущий и следующий периоды**  
  
PREVIOUSDAY  
  
PREVIOUSMONTH  
  
PREVIOUSQUARTER  
  
PREVIOUSYEAR  
  
NEXTDAY  
  
NEXTMONTH  
  
NEXTQUARTER  
  
NEXTYEAR  
  
**Функции логики операций со временем: периоды и вычисления для периодов**  
  
STARTOFMONTH  
  
STARTOFQUARTER  
  
STARTOFYEAR  
  
ENDOFMONTH  
  
ENDOFQUARTER  
  
ENDOFYEAR  
  
FIRSTDATE  
  
LASTDATE  
  
DATEADD  
  
## <a name="see-also"></a>См. также раздел  
[Режим DirectQuery (табличные службы SSAS)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)  
  
