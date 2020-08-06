---
title: Фильтры для моделей интеллектуального анализа данных (Analysis Services-Data Mining) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- filter syntax [data mining]
- models [Analysis Services], filtering
- filters [data mining]
- filtering data [Analysis Services]
ms.assetid: 0f29c19c-4be3-4bc7-ab60-f4130a10d59c
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4e2c82c977f734948e107773e439ca154f6cfdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656035"
---
# <a name="filters-for-mining-models-analysis-services---data-mining"></a><span data-ttu-id="4d1cd-102">Фильтры для моделей интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)</span><span class="sxs-lookup"><span data-stu-id="4d1cd-102">Filters for Mining Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="4d1cd-103">Фильтрация моделей на основе данных помогает создавать модели интеллектуального анализа, использующие подмножества данных в структуре интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-103">Data-based model filtering helps you create mining models that use subsets of data in a mining structure.</span></span> <span data-ttu-id="4d1cd-104">Фильтрация обеспечивает гибкость при проектировании структур интеллектуального анализа и источников данных, поскольку это позволяет создать одну структуру интеллектуального анализа на основе всеобъемлющего представления источников данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-104">Filtering gives you flexibility when you design your mining structures and data sources, because you can create a single mining structure, based on a comprehensive data source view.</span></span> <span data-ttu-id="4d1cd-105">Затем можно создать фильтры для использования части данных для обучения и проверки различных моделей, а не строить отдельную структуру и связанную с ней модель для каждого подмножества данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-105">You can then create filters to use only a part of that data for training and testing a variety of models, instead of building a different structure and related model for each subset of data.</span></span>  
  
 <span data-ttu-id="4d1cd-106">Например, определяется представление источника данных для таблицы Customers и связанных с ней таблиц.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-106">For example, you define the data source view on the Customers table and related tables.</span></span> <span data-ttu-id="4d1cd-107">Далее определяется единая структура интеллектуального анализа данных, в состав которой входят все необходимые поля.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-107">Next, you define a single mining structure that includes all the fields you need.</span></span> <span data-ttu-id="4d1cd-108">Наконец, создается модель, которая фильтруется по определенному атрибуту покупателя, например по региону.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-108">Finally, you create a model that is filtered on a particular customer attribute, such as Region.</span></span> <span data-ttu-id="4d1cd-109">Это позволяет легко копировать данную модель либо создавать новые модели на основе различных регионов путем изменения только условий фильтра.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-109">You can then easily make a copy of that model, and change just the filter condition to generate a new model based on a different region.</span></span>  
  
 <span data-ttu-id="4d1cd-110">Ниже приведены некоторые реальные сценарии, когда данная функция может оказаться весьма полезной.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-110">Some real-life scenarios where you might benefit from this feature include the following:</span></span>  
  
-   <span data-ttu-id="4d1cd-111">Создание отдельных моделей для таких дискретных значений, как пол, регионы и т. д.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-111">Creating separate models for discrete values such as gender, regions, and so forth.</span></span> <span data-ttu-id="4d1cd-112">Например, магазин одежды может строить раздельные модели по признаку пола на основе демографических данных покупателей, даже если данные о продажах поступают из единого источника данных для всех покупателей.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-112">For example, a clothing store might use customer demographics to build separate models by gender, even though the sales data comes from a single data source for all customers.</span></span>  
  
-   <span data-ttu-id="4d1cd-113">Эксперименты с моделями путем создания и тестирования различного группирования одинаковых данных, например возраста 20-30 лет по сравнению с возрастом 20-40 лет и 20-25 лет.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-113">Experimenting with models by creating and then testing multiple groupings of the same data, such as ages 20-30 vs. ages 20-40 vs. ages 20-25.</span></span>  
  
-   <span data-ttu-id="4d1cd-114">Настройка сложных фильтров для содержимого вложенных таблиц, например требования, чтобы вариант включался в модель, только если покупатель приобрел не менее двух оопределенных наименований товара.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-114">Specifying complex filters on nested table contents, such as requiring that a case be included in the model only if the customer has purchased at least two of a particular item.</span></span>  
  
 <span data-ttu-id="4d1cd-115">В этом разделе описаны способы создания и использования фильтров для моделей интеллектуального анализа данных, а также управление этими фильтрами.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-115">This section explains how to build, use, and manage filters on mining models.</span></span>  
  
## <a name="creating-model-filters"></a><span data-ttu-id="4d1cd-116">Создание фильтров моделей</span><span class="sxs-lookup"><span data-stu-id="4d1cd-116">Creating Model Filters</span></span>  
 <span data-ttu-id="4d1cd-117">Создавать и применять фильтры можно следующими способами.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-117">You can create and apply filters in the following ways:</span></span>  
  
-   <span data-ttu-id="4d1cd-118">Создание условий с помощью диалоговых окон редактора фильтров на вкладке **Модели интеллектуального анализа данных** в конструкторе интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-118">Using the **Mining Models** tab in Data Mining Designer to build conditions with the help of filter editor dialog boxes.</span></span>  
  
-   <span data-ttu-id="4d1cd-119">Ввод критерия фильтра непосредственно в `Filter` свойство модели интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-119">Typing a filter expression directly into the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="4d1cd-120">Программная настройка условий фильтра в модели с помощью объектов AMO.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-120">Setting filter conditions on a model programmatically, by using AMO.</span></span>  
  
### <a name="creating-model-filters-using-data-mining-designer"></a><span data-ttu-id="4d1cd-121">Создание фильтров моделей с помощью конструктора интеллектуального анализа данных</span><span class="sxs-lookup"><span data-stu-id="4d1cd-121">Creating Model Filters using Data Mining Designer</span></span>  
 <span data-ttu-id="4d1cd-122">Модель в конструкторе интеллектуального анализа данных фильтруется путем изменения свойства `Filter` в этой модели.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-122">You filter a model in Data Mining Designer by changing the `Filter` property of the mining model.</span></span> <span data-ttu-id="4d1cd-123">Можно ввести критерий фильтра непосредственно на панели **Свойства** либо открыть диалоговое окно фильтра для построения условий.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-123">You can either type a filter expression directly into the **Properties** pane, or you can open a filter dialog box to build conditions.</span></span>  
  
 <span data-ttu-id="4d1cd-124">Есть два диалоговых окна фильтра.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-124">There are two filter dialog boxes.</span></span> <span data-ttu-id="4d1cd-125">В первом создаются условия, применяемые к таблице вариантов.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-125">The first lets you create conditions that are applied to the case table.</span></span> <span data-ttu-id="4d1cd-126">Если источник данных содержит несколько таблиц, то сначала нужно выбрать таблицу, затем столбец, после чего следует указать операторы и условия, которые должны к нему применяться.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-126">If the data source contains multiple tables, first you select a table, and then you select a column and specify operators and conditions that apply to that column.</span></span> <span data-ttu-id="4d1cd-127">Можно связать несколько условий с помощью `AND` / `OR` операторов.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-127">You can link multiple conditions by using `AND`/`OR` operators.</span></span> <span data-ttu-id="4d1cd-128">Операторы, доступные в качестве определяемых значений, зависят от значений в столбце: дискретных или непрерывных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-128">The operators that are available for defining values depend on whether the column contains discrete or continuous values.</span></span> <span data-ttu-id="4d1cd-129">Например, в случае непрерывных значений можно использовать операторы `greater than` и `less than`.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-129">For example, with continuous values, you can use `greater than` and `less than` operators.</span></span> <span data-ttu-id="4d1cd-130">Однако для дискретных значений можно использовать только операторы `= (equal to)`, `!= (not equal to)` и `is null`.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-130">However, for discrete values, you can only use `= (equal to)`, `!= (not equal to)`, and `is null` operators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d1cd-131">Ключевое слово `LIKE` не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-131">The `LIKE` keyword is not supported.</span></span> <span data-ttu-id="4d1cd-132">Для включения нескольких дискретных атрибутов необходимо создать несколько отдельных условий и связать их с помощью оператора `OR`.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-132">If you want to include multiple discrete attributes, you must create separate conditions and link them by using the `OR` operator.</span></span>  
  
 <span data-ttu-id="4d1cd-133">Если условия сложные, можно работать одновременно только с одной таблицей с помощью второго диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-133">If the conditions are complex, you can use the second filter dialog box to work with one table at a time.</span></span> <span data-ttu-id="4d1cd-134">При закрытии второго диалогового окна фильтра выражение вычисляется, а затем сочетается с условиями фильтра других столбцов в таблице вариантов.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-134">When you close the second filter dialog box, the expression is evaluated and then combined with filter conditions that have been set on other columns in the case table.</span></span>  
  
### <a name="creating-filters-on-nested-tables"></a><span data-ttu-id="4d1cd-135">Создание фильтров во вложенных таблицах</span><span class="sxs-lookup"><span data-stu-id="4d1cd-135">Creating Filters on Nested Tables</span></span>  
 <span data-ttu-id="4d1cd-136">Если представление источника данных содержит вложенные таблицы, то во втором диалоговом окне фильтров можно создавать условия для строк во вложенных таблицах.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-136">If the data source view contains nested tables, you can use the second filter dialog box to build conditions on the rows in the nested tables.</span></span>  
  
 <span data-ttu-id="4d1cd-137">Например, если таблица вариантов связана с покупателями, а во вложенной таблице показаны продукты, приобретенные покупателями, то можно создать фильтр для покупателей, которые приобрели определенные товары. Это можно сделать с помощью приведенного синтаксиса в фильтре вложенной таблицы: `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-137">For example, if your case table is related to customers, and the nested table shows the products that a customer has purchased, you can create a filter for customers who have purchased particular items by using the following syntax in the nested table filter: `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`.</span></span>  
  
 <span data-ttu-id="4d1cd-138">Кроме того, можно отфильтровать данные по существованию определенного значения во вложенной таблице с помощью ключевых слов `EXISTS` или `NOT EXISTS` и вложенного запроса.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-138">You can also filter on the existence of a particular value in the nested table by using the `EXISTS` or `NOT EXISTS` keywords and a subquery.</span></span> <span data-ttu-id="4d1cd-139">Это позволяет создавать такие условия, как `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-139">This lets you create conditions such as `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`.</span></span> <span data-ttu-id="4d1cd-140">Условие `EXISTS SELECT(<subquery>)` возвращает значение `true`, если вложенная таблица содержит хотя бы одну строку, включающую значение `Water Bottle`.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-140">The `EXISTS SELECT(<subquery>)` returns `true` if the nested table contains at least one row that includes the value, `Water Bottle`.</span></span>  
  
 <span data-ttu-id="4d1cd-141">Можно сочетать условия в таблице вариантов с условиями во вложенной таблице.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-141">You can combine conditions on the case table with conditions on the nested table.</span></span> <span data-ttu-id="4d1cd-142">Например, в показанном ниже синтаксисе приведены условие в таблице вариантов (`Age > 30` ), вложенный запрос к вложенной таблице (`EXISTS (SELECT * FROM Products)`), а также несколько условий к вложенной таблице (`WHERE ProductName='Milk'  AND Quantity>2`).</span><span class="sxs-lookup"><span data-stu-id="4d1cd-142">For example, the following syntax includes a condition on the case table (`Age > 30` ), a subquery on the nested table (`EXISTS (SELECT * FROM Products)`), and multiple conditions on the nested table (`WHERE ProductName='Milk'  AND Quantity>2`) ).</span></span>  
  
```  
(Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity>2) )  
```  
  
 <span data-ttu-id="4d1cd-143">Когда построение фильтра завершено, текст фильтра вычисляется службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], переводится в DMX-выражение и после этого сохраняется в модели.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-143">When you have finished building the filter, the filter text is evaluated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], translated to a DMX expression, and then saved with the model.</span></span>  
  
 <span data-ttu-id="4d1cd-144">Инструкции по применению диалоговых окон фильтра в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]см. в разделе [Применение фильтра к модели интеллектуального анализа данных](apply-a-filter-to-a-mining-model.md).</span><span class="sxs-lookup"><span data-stu-id="4d1cd-144">For instructions on how to use the filter dialog boxes in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
## <a name="managing-mining-model-filters"></a><span data-ttu-id="4d1cd-145">Управление фильтрами моделей интеллектуального анализа данных</span><span class="sxs-lookup"><span data-stu-id="4d1cd-145">Managing Mining Model Filters</span></span>  
 <span data-ttu-id="4d1cd-146">Фильтрация моделей на основе данных значительно упрощает задачу управления структурами и моделями интеллектуального анализа данных за счет возможности создавать несколько моделей на основе одной структуры.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-146">Data-based model filtering greatly simplifies the task of managing mining structures and mining models, because you can easily create multiple models that are based on the same structure.</span></span> <span data-ttu-id="4d1cd-147">Кроме того, можно быстро создавать копии существующих моделей интеллектуального анализа данных и затем изменять только условия фильтра.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-147">You can also quickly make copies of existing mining models and then change only the filter condition.</span></span> <span data-ttu-id="4d1cd-148">Однако из-за фильтров может возникнуть определенная путаница.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-148">However, filters can lead to some confusion.</span></span>  
  
 <span data-ttu-id="4d1cd-149">Далее приведены некоторые часто задаваемые вопросы о том, как управлять фильтрами и интерпретировать фильтры для моделей интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-149">Here are some frequently asked questions about how to manage and interpret filters on mining models:</span></span>  
  
### <a name="how-can-i-tell-whether-a-filter-is-being-used"></a><span data-ttu-id="4d1cd-150">Как узнать, используется ли фильтр?</span><span class="sxs-lookup"><span data-stu-id="4d1cd-150">How can I tell whether a filter is being used?</span></span>  
 <span data-ttu-id="4d1cd-151">Существует несколько способов определения того, применен ли фильтр к модели.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-151">There are multiple ways to determine whether a filter is applied to a model:</span></span>  
  
-   <span data-ttu-id="4d1cd-152">В конструкторе перейдите на вкладку **модели интеллектуального анализа данных** , откройте **свойства**и просмотрите `Filter` свойство модели интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-152">In the designer, click the **Mining Models** tab, open **Properties**, and view the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="4d1cd-153">Динамическое административное представление DMSCHEMA_MINING_MODELS выдает столбец с текстом фильтра.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-153">The DMV, DMSCHEMA_MINING_MODELS, outputs a column that contains the text of the filter.</span></span> <span data-ttu-id="4d1cd-154">С помощью следующего запроса к динамическому административному представлению можно возвратить имена моделей и примененные к ним фильтры:</span><span class="sxs-lookup"><span data-stu-id="4d1cd-154">You can use the following query on a DMV to return the names of models and their filters:</span></span>  
  
    ```  
    SELECT MODEL_NAME, [FILTER]   
    FROM $SYSTEM.DMSCHEMA_MINING_MODELS  
  
    ```  
  
-   <span data-ttu-id="4d1cd-155">Можно получить значение свойства Filter объекта MiningModel в объектах AMO или найти элемент Filter XML для аналитики.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-155">You can get the value of the Filter property of the MiningModel object in AMO, or inspect the Filter element in XMLA.</span></span>  
  
 <span data-ttu-id="4d1cd-156">Также можно установить соглашение об именовании для моделей, чтобы в имени отражалось содержимое фильтра.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-156">You might also establish a naming convention for models to reflect the contents of the filter.</span></span> <span data-ttu-id="4d1cd-157">Это упростит различение связанных моделей.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-157">This can make it easier to tell related models apart.</span></span>  
  
### <a name="how-can-i-save-a-filter"></a><span data-ttu-id="4d1cd-158">Как сохранить фильтр?</span><span class="sxs-lookup"><span data-stu-id="4d1cd-158">How can I save a filter?</span></span>  
 <span data-ttu-id="4d1cd-159">Критерий фильтра сохраняется в виде скрипта, который хранится в связанной модели интеллектуального анализа данных или во вложенной таблице.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-159">The filter expression is saved as a script that is stored with the associated mining model or nested table.</span></span> <span data-ttu-id="4d1cd-160">Если удалить текст фильтра, его можно восстановить только вручную путем повторного создания критерия фильтра.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-160">If you delete the filter text, it can only be restored by manually re-creating the filter expression.</span></span> <span data-ttu-id="4d1cd-161">Таким образом, при создании сложных критериев фильтра следует создавать также резервные копии текста фильтра.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-161">Therefore, if you create complex filter expressions, you should create a backup copy of the filter text.</span></span>  
  
### <a name="why-cant-i-see-any-effects-from-the-filter"></a><span data-ttu-id="4d1cd-162">Почему в фильтре не отображаются эффекты?</span><span class="sxs-lookup"><span data-stu-id="4d1cd-162">Why can't I see any effects from the filter?</span></span>  
 <span data-ttu-id="4d1cd-163">Всякий раз при изменении или добавлении критерия фильтра необходимо выполнять повторную обработку структуры и модели, чтобы изменения вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-163">Whenever you change or add a filter expression, you must reprocess the structure and model before you can view the effects of the filter.</span></span>  
  
### <a name="why-do-i-see-filtered-attributes-in-prediction-query-results"></a><span data-ttu-id="4d1cd-164">Почему в результатах прогнозирующего запроса присутствуют отфильтрованные атрибуты?</span><span class="sxs-lookup"><span data-stu-id="4d1cd-164">Why do I see filtered attributes in prediction query results?</span></span>  
 <span data-ttu-id="4d1cd-165">При применении фильтра к модели он действует только на выборку вариантов, которые использовались для обучения модели.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-165">When you apply a filter to a model, it affects only the selection of cases used for training the model.</span></span> <span data-ttu-id="4d1cd-166">Фильтр не затрагивает атрибуты, которые известны модели, а также не меняет и не подавляет данные, которые имеются в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-166">The filter does not affect the attributes known to the model, or change or suppress data that is present in the data source.</span></span> <span data-ttu-id="4d1cd-167">В результате этого запросы к модели могут возвращать прогнозы для вариантов других типов, а в раскрывающихся списках значений, используемых моделью, могут присутствовать значения атрибутов, исключенных фильтром.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-167">As a result, queries against the model can return predictions for other types of cases, and dropdown lists of values used by the model might show attribute values excluded by the filter.</span></span>  
  
 <span data-ttu-id="4d1cd-168">Например, предположим, что производится обучение модели [Покупатель велосипеда] с использованием только вариантов, включающих женщин в возрасте 20–30 лет.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-168">For example, suppose you train the [Bike Buyer] model using only cases involving women aged 20-30.</span></span> <span data-ttu-id="4d1cd-169">При этом можно выполнить прогнозирующий запрос, который предсказывает вероятность покупки велосипеда мужчиной либо вероятность покупки женщиной в возрасте 30–40 лет.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-169">You can still run a prediction query that predicts the probability of a man buying a bike, or predict the outcome for a woman aged 30-40.</span></span> <span data-ttu-id="4d1cd-170">Происходит это потому, что атрибуты и значения, имеющиеся в источнике данных, определяют то, что теоретически возможно, тогда как варианты определяют совершенные действия, используемые для обучения.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-170">That is because the attributes and values present in the data source define what is theoretically possible, while the cases define the occurrences used for training.</span></span> <span data-ttu-id="4d1cd-171">Однако такие запросы возвратят очень незначительные вероятности, поскольку обучающие данные не содержат никаких вариантов с целевыми значениями.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-171">However, these queries would return very small probabilities, because the training data does not contain any cases with the target values.</span></span>  
  
 <span data-ttu-id="4d1cd-172">Если требуется полностью скрыть или сделать анонимными значения атрибутов в модели, то для этого существуют различные варианты.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-172">If you need to completely hide or anonymize attribute values in the model, there are various options:</span></span>  
  
-   <span data-ttu-id="4d1cd-173">Фильтрация входящих данных в рамках определения представления источника данных или в реляционном источнике данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-173">Filter the incoming data as part of the definition of the data source view, or in the relational data source.</span></span>  
  
-   <span data-ttu-id="4d1cd-174">Экранирование или кодировка значения атрибута.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-174">Mask or encode the attribute value.</span></span>  
  
-   <span data-ttu-id="4d1cd-175">Сворачивание исключенных значений в категорию в рамках определения структуры интеллектуального анализа данных.</span><span class="sxs-lookup"><span data-stu-id="4d1cd-175">Collapse excluded values into a category as part of the mining structure definition.</span></span>  
  
## <a name="related-resources"></a><span data-ttu-id="4d1cd-176">Связанные ресурсы</span><span class="sxs-lookup"><span data-stu-id="4d1cd-176">Related Resources</span></span>  
 <span data-ttu-id="4d1cd-177">Дополнительные сведения о синтаксисе фильтров и примеры выражений фильтра см. в разделе [Синтаксис и примеры фильтра модели (службы Analysis Services — интеллектуальный анализ данных)](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span><span class="sxs-lookup"><span data-stu-id="4d1cd-177">For more information about filter syntax, and examples of filter expressions, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="4d1cd-178">Сведения об использовании фильтров модели при тестировании модели интеллектуального анализа данных см. в разделе [Выбор типа диаграммы точности и задание параметров диаграммы](choose-an-accuracy-chart-type-and-set-chart-options.md).</span><span class="sxs-lookup"><span data-stu-id="4d1cd-178">For information about how to use model filters when you are testing a mining model, see [Choose an Accuracy Chart Type and Set Chart Options](choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1cd-179">См. также:</span><span class="sxs-lookup"><span data-stu-id="4d1cd-179">See Also</span></span>  
 <span data-ttu-id="4d1cd-180">[Синтаксис и примеры фильтров моделей &#40;Analysis Services — интеллектуальный анализ данных&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="4d1cd-180">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="4d1cd-181">Тестирование и проверка (интеллектуальный анализ данных)</span><span class="sxs-lookup"><span data-stu-id="4d1cd-181">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  