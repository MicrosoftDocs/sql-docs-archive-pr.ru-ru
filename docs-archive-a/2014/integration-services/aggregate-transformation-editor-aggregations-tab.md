---
title: Редактор преобразования "Статистическая обработка" (вкладка "агрегаты") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.aggregations.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30cafb68a69a061fe4b79e832f356b82926c9761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657241"
---
# <a name="aggregate-transformation-editor-aggregations-tab"></a><span data-ttu-id="84072-102">Редактор преобразования «Статистическая обработка» (вкладка «Агрегаты»)</span><span class="sxs-lookup"><span data-stu-id="84072-102">Aggregate Transformation Editor (Aggregations Tab)</span></span>
  <span data-ttu-id="84072-103">На вкладке **Агрегаты** диалогового окна **Редактор преобразования «Статистическая обработка»** можно указать столбцы для статистической обработки и свойства статистических выражений.</span><span class="sxs-lookup"><span data-stu-id="84072-103">Use the **Aggregations** tab of the **Aggregate Transformation Editor** dialog box to specify columns for aggregation and aggregation properties.</span></span> <span data-ttu-id="84072-104">Можно применять одновременно нескольких агрегатов.</span><span class="sxs-lookup"><span data-stu-id="84072-104">You can apply multiple aggregations.</span></span> <span data-ttu-id="84072-105">Это преобразование не приводит к формированию вывода ошибок.</span><span class="sxs-lookup"><span data-stu-id="84072-105">This transformation does not generate an error output.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84072-106">Если параметры числа ключей, масштаба ключей, числа различающихся ключей и масштаба различающихся ключей определены на вкладке **Дополнительно** , они действуют на уровне компонентов; если они определены в расширенном режиме просмотра вкладки **Агрегаты** — на уровне вывода; а если они определены в списке столбцов внизу на вкладке **Агрегаты** — на уровне столбцов.</span><span class="sxs-lookup"><span data-stu-id="84072-106">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="84072-107">В преобразовании «Статистическая обработка» свойства **Ключи** и **Порядок числа ключей** ссылаются на ожидаемое число групп, являющихся результатом операции **Группировать по** .</span><span class="sxs-lookup"><span data-stu-id="84072-107">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="84072-108">Свойства**Количество различных ключей** и **Порядок числа различных ключей** ссылаются на ожидаемое число различающихся значений, являющихся результатом операции **Подсчет различных объектов** .</span><span class="sxs-lookup"><span data-stu-id="84072-108">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="84072-109">Дополнительные сведения о преобразовании «Статистическая обработка» см. в разделе [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span><span class="sxs-lookup"><span data-stu-id="84072-109">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="84072-110">Варианты</span><span class="sxs-lookup"><span data-stu-id="84072-110">Options</span></span>  
 <span data-ttu-id="84072-111">**Дополнительные или Простые**</span><span class="sxs-lookup"><span data-stu-id="84072-111">**Advanced / Basic**</span></span>  
 <span data-ttu-id="84072-112">Отобразить или скрыть параметры настройки нескольких агрегатов для нескольких выходов.</span><span class="sxs-lookup"><span data-stu-id="84072-112">Display or hide options to configure multiple aggregations for multiple outputs.</span></span> <span data-ttu-id="84072-113">По умолчанию дополнительные параметры скрыты.</span><span class="sxs-lookup"><span data-stu-id="84072-113">By default, the Advanced options are hidden.</span></span>  
  
 <span data-ttu-id="84072-114">**Имя агрегата**</span><span class="sxs-lookup"><span data-stu-id="84072-114">**Aggregation Name**</span></span>  
 <span data-ttu-id="84072-115">В режиме просмотра дополнительных параметров введите понятное имя агрегата.</span><span class="sxs-lookup"><span data-stu-id="84072-115">In the Advanced display, type a friendly name for the aggregation.</span></span>  
  
 <span data-ttu-id="84072-116">**Группировать по столбцам**</span><span class="sxs-lookup"><span data-stu-id="84072-116">**Group By Columns**</span></span>  
 <span data-ttu-id="84072-117">В режиме просмотра дополнительных параметров выберите столбцы для группирования из списка **Доступные входные столбцы** , как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="84072-117">In the Advanced display, select columns for grouping by using the **Available Input Columns** list as described below.</span></span>  
  
 <span data-ttu-id="84072-118">**Порядок числа ключей**</span><span class="sxs-lookup"><span data-stu-id="84072-118">**Key Scale**</span></span>  
 <span data-ttu-id="84072-119">В режиме просмотра дополнительных параметров по выбору укажите примерное количество ключей, которое может записывать агрегат.</span><span class="sxs-lookup"><span data-stu-id="84072-119">In the Advanced display, optionally specify the approximate number of keys that the aggregation can write.</span></span> <span data-ttu-id="84072-120">По умолчанию значение этого параметра **Не указано**.</span><span class="sxs-lookup"><span data-stu-id="84072-120">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="84072-121">Если заданы оба свойства **Порядок числа ключей** и **Ключи** , приоритет имеет значение свойства **Ключи** .</span><span class="sxs-lookup"><span data-stu-id="84072-121">If both the **Key Scale** and **Keys** properties are set, the value of **Keys** takes precedence.</span></span>  
  
|<span data-ttu-id="84072-122">Значение</span><span class="sxs-lookup"><span data-stu-id="84072-122">Value</span></span>|<span data-ttu-id="84072-123">Описание</span><span class="sxs-lookup"><span data-stu-id="84072-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84072-124">Не указан</span><span class="sxs-lookup"><span data-stu-id="84072-124">Unspecified</span></span>|<span data-ttu-id="84072-125">Свойство «Масштаб ключей» не используется.</span><span class="sxs-lookup"><span data-stu-id="84072-125">The Key Scale property is not used.</span></span>|  
|<span data-ttu-id="84072-126">Низкий</span><span class="sxs-lookup"><span data-stu-id="84072-126">Low</span></span>|<span data-ttu-id="84072-127">Агрегат может записывать около 500 000 ключей.</span><span class="sxs-lookup"><span data-stu-id="84072-127">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="84072-128">Средний</span><span class="sxs-lookup"><span data-stu-id="84072-128">Medium</span></span>|<span data-ttu-id="84072-129">Агрегат может записывать около 5 000 000 ключей.</span><span class="sxs-lookup"><span data-stu-id="84072-129">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="84072-130">Высокий</span><span class="sxs-lookup"><span data-stu-id="84072-130">High</span></span>|<span data-ttu-id="84072-131">Агрегат может записывать более 25 000 000 ключей.</span><span class="sxs-lookup"><span data-stu-id="84072-131">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="84072-132">**Ключи**</span><span class="sxs-lookup"><span data-stu-id="84072-132">**Keys**</span></span>  
 <span data-ttu-id="84072-133">В режиме просмотра дополнительных параметров по выбору можно указать точное количество ключей, которое может записывать агрегат.</span><span class="sxs-lookup"><span data-stu-id="84072-133">In the Advanced display, optionally specify the exact number of keys that the aggregation can write.</span></span> <span data-ttu-id="84072-134">Если заданы оба свойства **Порядок числа ключей** и **Ключи** , приоритет имеет значение свойства **Ключи** .</span><span class="sxs-lookup"><span data-stu-id="84072-134">If both **Key Scale** and **Keys** are specified, **Keys** takes precedence.</span></span>  
  
 <span data-ttu-id="84072-135">**Доступные входные столбцы**</span><span class="sxs-lookup"><span data-stu-id="84072-135">**Available Input Columns**</span></span>  
 <span data-ttu-id="84072-136">Выберите столбцы из списка имеющихся входных столбцов, установив флажки в таблице.</span><span class="sxs-lookup"><span data-stu-id="84072-136">Select from the list of available input columns by using the check boxes in this table.</span></span>  
  
 <span data-ttu-id="84072-137">**Входной столбец**</span><span class="sxs-lookup"><span data-stu-id="84072-137">**Input Column**</span></span>  
 <span data-ttu-id="84072-138">Выберите входной столбец из списка имеющихся входных столбцов.</span><span class="sxs-lookup"><span data-stu-id="84072-138">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="84072-139">**Псевдоним вывода**</span><span class="sxs-lookup"><span data-stu-id="84072-139">**Output Alias**</span></span>  
 <span data-ttu-id="84072-140">Введите псевдоним для каждого столбца.</span><span class="sxs-lookup"><span data-stu-id="84072-140">Type an alias for each column.</span></span> <span data-ttu-id="84072-141">По умолчанию, используется имя входного столбца, однако можно выбрать любое уникальное описательное имя.</span><span class="sxs-lookup"><span data-stu-id="84072-141">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="84072-142">**Операция**</span><span class="sxs-lookup"><span data-stu-id="84072-142">**Operation**</span></span>  
 <span data-ttu-id="84072-143">Выберите операцию из списка доступных операций, руководствуясь следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="84072-143">Choose from the list of available operations, using the following table as a guide.</span></span>  
  
|<span data-ttu-id="84072-144">Операция</span><span class="sxs-lookup"><span data-stu-id="84072-144">Operation</span></span>|<span data-ttu-id="84072-145">Описание</span><span class="sxs-lookup"><span data-stu-id="84072-145">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84072-146">**GroupBy**</span><span class="sxs-lookup"><span data-stu-id="84072-146">**GroupBy**</span></span>|<span data-ttu-id="84072-147">Разделение наборов данных на группы.</span><span class="sxs-lookup"><span data-stu-id="84072-147">Divides datasets into groups.</span></span> <span data-ttu-id="84072-148">Для группирования подходят столбцы любого типа данных.</span><span class="sxs-lookup"><span data-stu-id="84072-148">Columns with any data type can be used for grouping.</span></span> <span data-ttu-id="84072-149">Дополнительные сведения см. в описании ключевого слова GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="84072-149">For more information, see GROUP BY.</span></span>|  
|<span data-ttu-id="84072-150">**Функции**</span><span class="sxs-lookup"><span data-stu-id="84072-150">**Sum**</span></span>|<span data-ttu-id="84072-151">Суммирование значений в столбце.</span><span class="sxs-lookup"><span data-stu-id="84072-151">Sums the values in a column.</span></span> <span data-ttu-id="84072-152">Допускается суммирование только столбцов, содержащих числовые данные.</span><span class="sxs-lookup"><span data-stu-id="84072-152">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="84072-153">Дополнительные сведения см. в описании ключевого слова SUM.</span><span class="sxs-lookup"><span data-stu-id="84072-153">For more information, see SUM.</span></span>|  
|<span data-ttu-id="84072-154">**Среднее**</span><span class="sxs-lookup"><span data-stu-id="84072-154">**Average**</span></span>|<span data-ttu-id="84072-155">Определение среднего арифметического значения по столбцу.</span><span class="sxs-lookup"><span data-stu-id="84072-155">Returns the average of the column values in a column.</span></span> <span data-ttu-id="84072-156">Допускается определение среднего значения только по столбцам, содержащим числовые данные.</span><span class="sxs-lookup"><span data-stu-id="84072-156">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="84072-157">Дополнительные сведения см. в описании ключевого слова AVG.</span><span class="sxs-lookup"><span data-stu-id="84072-157">For more information, see AVG.</span></span>|  
|<span data-ttu-id="84072-158">**Count**</span><span class="sxs-lookup"><span data-stu-id="84072-158">**Count**</span></span>|<span data-ttu-id="84072-159">Возвращает количество элементов в группе.</span><span class="sxs-lookup"><span data-stu-id="84072-159">Returns the number of items in a group.</span></span> <span data-ttu-id="84072-160">Дополнительные сведения см. в описании ключевого слова COUNT.</span><span class="sxs-lookup"><span data-stu-id="84072-160">For more information, see COUNT.</span></span>|  
|<span data-ttu-id="84072-161">**CountDistinct**</span><span class="sxs-lookup"><span data-stu-id="84072-161">**CountDistinct**</span></span>|<span data-ttu-id="84072-162">Определение числа уникальных ненулевых значений в группе.</span><span class="sxs-lookup"><span data-stu-id="84072-162">Returns the number of unique nonnull values in a group.</span></span> <span data-ttu-id="84072-163">Дополнительные сведения см. в описании ключевых слов COUNT и Distinct.</span><span class="sxs-lookup"><span data-stu-id="84072-163">For more information, see COUNT and Distinct.</span></span>|  
|<span data-ttu-id="84072-164">**Минимальные**</span><span class="sxs-lookup"><span data-stu-id="84072-164">**Minimum**</span></span>|<span data-ttu-id="84072-165">Возвращает минимальное значение в группе.</span><span class="sxs-lookup"><span data-stu-id="84072-165">Returns the minimum value in a group.</span></span> <span data-ttu-id="84072-166">Допускается поиск только среди числовых данных.</span><span class="sxs-lookup"><span data-stu-id="84072-166">Restricted to numeric data types.</span></span>|  
|<span data-ttu-id="84072-167">**Максимум**</span><span class="sxs-lookup"><span data-stu-id="84072-167">**Maximum**</span></span>|<span data-ttu-id="84072-168">Возвращает максимальное значение в группе.</span><span class="sxs-lookup"><span data-stu-id="84072-168">Returns the maximum value in a group.</span></span> <span data-ttu-id="84072-169">Допускается поиск только среди числовых данных.</span><span class="sxs-lookup"><span data-stu-id="84072-169">Restricted to numeric data types.</span></span>|  
  
 <span data-ttu-id="84072-170">**Флаги сравнения**</span><span class="sxs-lookup"><span data-stu-id="84072-170">**Comparison Flags**</span></span>  
 <span data-ttu-id="84072-171">Если выбран параметр **Группировать по**, для управления параметрами сравнения при преобразовании используются флажки.</span><span class="sxs-lookup"><span data-stu-id="84072-171">If you choose **Group By**, use the check boxes to control how the transformation performs the comparison.</span></span> <span data-ttu-id="84072-172">Дополнительные сведения о параметрах сравнения строк см. в разделе [Comparing String Data](data-flow/comparing-string-data.md).</span><span class="sxs-lookup"><span data-stu-id="84072-172">For information on the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="84072-173">**Количество различных масштабов**</span><span class="sxs-lookup"><span data-stu-id="84072-173">**Count Distinct Scale**</span></span>  
 <span data-ttu-id="84072-174">Дополнительно можно указать приблизительное количество различающихся значений, которое может записывать агрегат.</span><span class="sxs-lookup"><span data-stu-id="84072-174">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="84072-175">По умолчанию значение этого параметра **Не указано**.</span><span class="sxs-lookup"><span data-stu-id="84072-175">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="84072-176">Если `CountDistinctScale` указаны и **CountDistinctKeys** , то **CountDistinctKeys** имеет приоритет.</span><span class="sxs-lookup"><span data-stu-id="84072-176">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
|<span data-ttu-id="84072-177">Значение</span><span class="sxs-lookup"><span data-stu-id="84072-177">Value</span></span>|<span data-ttu-id="84072-178">Описание</span><span class="sxs-lookup"><span data-stu-id="84072-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84072-179">Не указан</span><span class="sxs-lookup"><span data-stu-id="84072-179">Unspecified</span></span>|<span data-ttu-id="84072-180">Свойство `CountDistinctScale` не используется.</span><span class="sxs-lookup"><span data-stu-id="84072-180">The `CountDistinctScale` property is not used.</span></span>|  
|<span data-ttu-id="84072-181">Низкий</span><span class="sxs-lookup"><span data-stu-id="84072-181">Low</span></span>|<span data-ttu-id="84072-182">Статистическая функция может записывать примерно 500 000 уникальных ключей.</span><span class="sxs-lookup"><span data-stu-id="84072-182">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="84072-183">Средний</span><span class="sxs-lookup"><span data-stu-id="84072-183">Medium</span></span>|<span data-ttu-id="84072-184">Агрегат может записывать примерно 5 000 000 различных значений.</span><span class="sxs-lookup"><span data-stu-id="84072-184">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="84072-185">Высокий</span><span class="sxs-lookup"><span data-stu-id="84072-185">High</span></span>|<span data-ttu-id="84072-186">Агрегат может записывать более 25 000 000 различающихся ключей.</span><span class="sxs-lookup"><span data-stu-id="84072-186">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="84072-187">**Количество различных ключей**</span><span class="sxs-lookup"><span data-stu-id="84072-187">**Count Distinct Keys**</span></span>  
 <span data-ttu-id="84072-188">При необходимости можно указать точное количество различающихся значений, которое может записывать агрегат.</span><span class="sxs-lookup"><span data-stu-id="84072-188">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="84072-189">Если `CountDistinctScale` указаны и **CountDistinctKeys** , то **CountDistinctKeys** имеет приоритет.</span><span class="sxs-lookup"><span data-stu-id="84072-189">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84072-190">См. также:</span><span class="sxs-lookup"><span data-stu-id="84072-190">See Also</span></span>  
 <span data-ttu-id="84072-191">[Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="84072-191">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="84072-192">[Редактор преобразования "Статистическая обработка" &#40;вкладка "Дополнительно"&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="84072-192">[Aggregate Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="84072-193">Статистическая обработка значений в наборе данных с помощью преобразования «Агрегатная обработка»</span><span class="sxs-lookup"><span data-stu-id="84072-193">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  