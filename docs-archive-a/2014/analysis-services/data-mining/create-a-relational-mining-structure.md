---
title: Создание реляционной структуры интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], data mining
- data mining [Analysis Services], structure
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
- OLAP mining models [Analysis Services]
ms.assetid: 5547d639-377d-4ca7-88fc-ce1f9e2babc5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34316c0e462a922abf5c5ab069e5150e61db232d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656049"
---
# <a name="create-a-relational-mining-structure"></a>Создание реляционной структуры интеллектуального анализа данных
  Большинство моделей интеллектуального анализа данных основано на реляционных источниках данных. Преимуществом создания реляционной модели интеллектуального анализа данных является возможность собирать неорганизованные данные, а также проводить обучение и обновление модели, не решая сложную задачу построения куба.  
  
 Реляционная структура интеллектуального анализа данных может основываться на данных из разрозненных источников. Необработанные данные могут храниться в таблицах, файлах или системах реляционных баз данных при условии, что эти данные можно определить в составе представления источников данных. Например, реляционную структуру интеллектуального анализа данных следует использовать, если данные находятся в Excel, в хранилище данных SQL Server, в базе данных отчетов SQL Server или во внешних источниках, доступ к которым осуществляется посредством поставщиков OLE DB или ODBC.  
  
 В этом разделе приводятся общие сведения об использовании мастера интеллектуального анализа данных для создания реляционной структуры интеллектуального анализа данных.  
  
 [Требования](#BKMK_Relational_Structure)  
  
 [Процедура создания реляционной структуры интеллектуального анализа данных](#BKMK_Relational_Structure)  
  
 [Выбор источников данных](#BKMK_ChooseRelData)  
  
 [Указание типа содержимого и типа данных](#bkmk_ContentDataType)  
  
 [Создание набора контрольных данных](#bkmk_Holdout)  
  
 [Включение детализации](#BKMK_DrillThru)  
  
## <a name="requirements"></a>Требования  
 Сначала требуется существующий источник данных. Если источник не существует, его можно настроить в конструкторе источников данных. Дополнительные сведения см. в разделе [Создание источника данных (многомерные службы SSAS)](../multidimensional-models/create-a-data-source-ssas-multidimensional.md).  
  
 Затем в мастере представлений источников данных соберите необходимые данные в одно представление. Дополнительные сведения о выборе, преобразовании и фильтрации данных в представлениях источника данных, а также об управлении данными см. в разделе [Представления источников данных в многомерных моделях](../multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
##  <a name="overview-of-process"></a><a name="BKMK_Relational_Structure"></a>Общие сведения о процессе  
 Запустите мастер интеллектуального анализа данных. Для этого щелкните правой кнопкой мыши узел **Структуры интеллектуального анализа данных** в обозревателе решений и выберите команду **Добавить новую структуру интеллектуального анализа данных**. Мастер помогает выполнить следующие шаги по созданию структуры для новой реляционной модели интеллектуального анализа данных.  
  
1.  **Выбор метода определения**. Здесь в качестве типа источника данных выберите **На основе существующей реляционной базы данных или хранилища данных**.  
  
2.  **Создание структуры интеллектуального анализа данных**. Определите, что следует создавать: просто структуру или структуру с моделью интеллектуального анализа данных.  
  
     Также выбирает алгоритм для начальной модели. Советы по выбору алгоритма для определенных целей см. в разделе [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](data-mining-algorithms-analysis-services-data-mining.md).  
  
3.  **Выбор представления источника данных**. Выберите представление источников данных, которое будет использоваться для обучения модели. Представление источника данных также может содержать данные, используемые для тестирования, и не связанные с анализом данные. Можно выбрать, какие данные будут фактически использоваться в структуре и в модели. Позднее к данным можно применить фильтры.  
  
4.  **Определение типов таблиц**. Выберите таблицу, содержащую варианты для анализа. Для некоторых наборов данных, особенно для тех, которые используются в построении моделей покупательского поведения, также можно включить связанную таблицу для использования в качестве вложенной.  
  
     Для каждой таблицы необходимо указать ключ, чтобы дать алгоритму возможность определить уникальную запись, а также связанные записи, если добавлена вложенная таблица.  
  
     Дополнительные сведения см. в статье [Mining Structure Columns](mining-structure-columns.md).  
  
5.  **Определение обучающих данных**. На этой странице выбирается *таблица вариантов*, которая содержит наиболее важные данные для анализа.  
  
     Для некоторых наборов данных, особенно для тех, которые используются в построении моделей покупательского поведения, также можно включить связанную таблицу. Значения в этой вложенной таблице будут обрабатываться в виде нескольких значений, связанных с одной строкой (вариантом) в главной таблице.  
  
6.  **Определение содержимого и типа данных столбцов**. Для каждого столбца, используемого в структуре, необходимо выбрать *тип данных* и *тип содержимого*.  
  
     Мастер автоматически обнаружит возможные типы данных, но не обязательно использовать тип данных, рекомендуемый мастером. Например, даже если данные содержат числа, их можно представить в виде категориальных. Столбцы, указанные в качестве ключей, автоматически получают тип данных, соответствующий типу модели. Дополнительные сведения см. в разделах [Столбцы модели интеллектуального анализа данных](mining-model-columns.md) и [Типы данных (интеллектуальный анализ данных)](data-types-data-mining.md).  
  
     *Тип содержимого* , выбираемый для каждого столбца, который используется в модели, сообщает алгоритму, каким образом следует обрабатывать данные.  
  
     Например, можно выполнять дискретизацию чисел вместо использования непрерывных значений. Также можно задать в алгоритме автоматическое определение типа содержимого, наиболее подходящего для столбца. Дополнительные сведения см. в разделе [Типы содержимого (интеллектуальный анализ данных)](content-types-data-mining.md).  
  
7.  **Создание проверочного набора**. На этой странице указывается, какой объем данных следует выделить для использования в тестировании модели. Если данные будут поддерживать несколько моделей, то разумно создать набор контрольных данных, чтобы тестировать все модели по одним и тем же данным.  
  
     Дополнительные сведения см. в разделе [Тестирование и проверка (интеллектуальный анализ данных)](testing-and-validation-data-mining.md).  
  
8.  **Завершение работы мастера**. На этой странице задается имя новой структуры интеллектуального анализа данных и имя связанной модели интеллектуального анализа данных, а затем структура и модель сохраняются.  
  
     Также можно задать ряд важных параметров, зависящих от типа модели. Например, можно включить детализацию в структуре.  
  
     На данном этапе структура интеллектуального анализа данных и ее модель представляют собой лишь метаданные. Для получения результатов необходимо обработать структуру и модель.  
  
##  <a name="how-to-choose-relational-data"></a><a name="BKMK_ChooseRelData"></a>Выбор реляционных данных  
 Реляционные структуры интеллектуального анализа данных могут быть основаны на любых данных, доступных с помощью источника данных OLE DB. Если исходные данные содержатся в нескольких таблицах, то можно использовать представление источника данных, объединяющее необходимые таблицы и столбцы.  
  
 Если таблицы включают связи типа «один ко многим» (например, у вас есть несколько записей о покупках для каждого клиента, который необходимо проанализировать), можно добавить обе таблицы, а затем использовать одну таблицу в качестве таблицы вариантов, связав данные на стороне «многие» связи как вложенную таблицу.  
  
 Данные из структуры интеллектуального анализа данных получаются на основе существующего представления источников данных. В представлении источников данных данные можно изменять нужны образом, добавляя связи или производные столбцы, которые отсутствуют в базовых реляционных данных. В представлении источника данных также можно создавать именованные вычисления или агрегаты. Такие возможности оказываются очень удобными, если нет возможности изменять организацию данных в источнике данных или если нужно проверить различные схемы агрегатной обработки для моделей интеллектуального анализа данных.  
  
 Не обязательно использовать все доступные данные, можно выбрать столбцы, которые будут включены в структуру интеллектуального анализа данных. Затем эти столбцы можно будет использовать во всех моделях, основанных на этой структуре. Из отдельных моделей можно исключать отдельные столбцы, задавая для них метку `Ignore`. Можно также позволить пользователям модели интеллектуального анализа детализировать результаты модели углублением с целью просмотра дополнительных столбцов структуры интеллектуального анализа данных, не включенных в саму модель.  
  
##  <a name="how-to-specify-content-type-and-data-type"></a><a name="bkmk_ContentDataType"></a>Указание типа содержимого и типа данных  
 Типы данных во многом совпадают с типами данных, задаваемыми в интерфейсе SQL Server и других приложений: дата и время, числа разного размера, логические значения, текст и другие дискретные данные.  
  
 Типы содержимого важны для интеллектуального анализа данных и влияют на результат анализа. Тип содержимого сообщает алгоритму, что нужно делать с данными: обрабатывать числа как непрерывные или сегментировать. Сколько имеется потенциальных значений? Является ли каждое значение уникальным? Если значение является ключом, то какой тип ключа — это то, что он указывает на значение даты/времени, последовательность или какой-либо другой ключ?  
  
 Учтите, что выбор источника данных может ограничить возможный выбор типов содержимого. Например, нечисловые значения нельзя дискретизировать. Если нужный тип содержимого не отображается, нажмите кнопку **Назад** , чтобы вернуться на страницу типов данных и выбрать другой тип.  
  
 Не нужно опасаться неправильно указать тип содержимого. Создать новую модель и изменить тип содержимого очень легко, если новый тип содержимого поддерживается для типа данных, заданного в структуре интеллектуального анализа данных. Также очень часто создается несколько моделей с разными типами содержимого — в целях эксперимента или для соблюдения требований разных алгоритмов.  
  
 Например, если данные содержат столбец дохода, то можно создать две разные модели, использующие алгоритм дерева принятия решений (Майкрософт), и в одной из них использовать столбец как содержащий непрерывные числа, а в другой — дискретные диапазоны. Однако если добавлена модель, использующая упрощенный алгоритм Байеса (Майкрософт), то необходимо изменить столбец на дискретизированные значения, поскольку данный алгоритм не поддерживает непрерывные числа.  
  
##  <a name="why-and-how-to-split-data-into-training-and-testing-sets"></a><a name="bkmk_Holdout"></a>Почему и как разделить данные на обучающие и проверочные наборы  
 Ближе к концу работы мастера необходимо выбрать, будут ли данные разделяться на обучающий и проверочный наборы. Возможность выделять случайно выбираемую часть данных для проверки очень удобна, поскольку обеспечивает доступность согласованного набора проверочных данных для использования со всеми моделями интеллектуального анализа данных, связанными с новой структурой интеллектуального анализа данных.  
  
> [!WARNING]  
>  Учтите, что эта возможность доступна не для всех типов моделей. Например, при создании модели прогнозирования вы не сможете использовать контрольные данные, так как для алгоритма временных рядов требуется отсутствие пробелов в данных. Список типов моделей, поддерживающих наборы контрольных данных, см. в разделе [Обучающие и проверочные наборы данных](training-and-testing-data-sets.md).  
  
 Для создания такого набора контрольных данных указывается процент данных, которые будут использоваться в тестировании. Все остальные данные будут использоваться в обучении. Также можно задать максимальное число вариантов, которые будут использоваться в тестировании, или задать начальное значение, определяющее процесс случайного выбора.  
  
 Определение набора контрольных данных хранится в структуре интеллектуального анализа данных, поэтому каждый раз при создании новой модели на основе этой структуры набор проверочных данных будет доступен для оценки точности модели. Если удалить кэш структуры интеллектуального анализа данных, то также будут удалены сведения о том, какие варианты использовались для обучения, а какие — для тестирования.  
  
##  <a name="why-and-how-to-enable-drillthrough"></a><a name="BKMK_DrillThru"></a>Почему и как включить детализацию  
 Почти в самом конце работы мастера можно включить *детализацию*. Этот вариант легко пропустить, но он является важным. Детализация позволяет просматривать данные источника в структуре интеллектуального анализа данных с помощью запросов к модели интеллектуального анализа данных.  
  
 Чем это полезно? Допустим, при просмотре результатов модели кластеризации нужно узнать, какие клиенты помещены в тот или иной кластер. Детализация позволяет просмотреть такие данные, как контактная информация.  
  
> [!WARNING]  
>  Чтобы использовать детализацию, нужно включить ее при создании структуры интеллектуального анализа данных. Детализацию для моделей можно включить позднее, задав свойство модели, однако для структур интеллектуального анализа данных эту возможность следует задавать с самого начала. Дополнительные сведения см. в разделе [Запросы детализации (интеллектуальный анализ данных)](drillthrough-queries-data-mining.md).  
  
## <a name="see-also"></a>См. также  
 [Конструктор интеллектуального анализа данных](data-mining-designer.md)   
 [Мастер интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](data-mining-wizard-analysis-services-data-mining.md)   
 [Свойства модели интеллектуального анализа данных](mining-model-properties.md)   
 [Свойства структуры интеллектуального анализа данных и столбцов структуры](properties-for-mining-structure-and-structure-columns.md)   
 [Задачи и инструкции по структуре интеллектуального анализа данных](mining-structure-tasks-and-how-tos.md)  
  
  
