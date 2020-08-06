---
title: Добавление пользовательского статистического выражения в измерение | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed843b8b0005ff62f05b13ebd20024d528857388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655413"
---
# <a name="add-a-custom-aggregation-to-a-dimension"></a><span data-ttu-id="35473-102">Добавление нестандартного статистического выражения к измерению</span><span class="sxs-lookup"><span data-stu-id="35473-102">Add a Custom Aggregation to a Dimension</span></span>
  <span data-ttu-id="35473-103">Добавление нестандартного статистического выражения к кубу или измерению для статистических вычислений, связанных с элементом измерения, производится по умолчанию другим унарным оператором.</span><span class="sxs-lookup"><span data-stu-id="35473-103">Add a custom aggregation enhancement to a cube or dimension to replace the default aggregations that are associated with a dimension member with a different unary operator.</span></span> <span data-ttu-id="35473-104">Эта функция задает в таблице измерения столбец унарных операторов, который определяет сдвиг элементов в иерархии родители-потомки.</span><span class="sxs-lookup"><span data-stu-id="35473-104">This enhancement specifies a unary operator column in the dimension table that defines rollup for members in a parent-child hierarchy.</span></span> <span data-ttu-id="35473-105">Унарный оператор действует в качестве родительского атрибута в иерархии родители-потомки.</span><span class="sxs-lookup"><span data-stu-id="35473-105">The unary operator acts on the parent attribute in a parent-child hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35473-106">Нестандартное статистическое выражение доступно только для измерений, основанных на существующих источниках данных.</span><span class="sxs-lookup"><span data-stu-id="35473-106">A custom aggregation is available only for dimensions that are based on existing data sources.</span></span> <span data-ttu-id="35473-107">Для измерений, созданных без использования источника данных, необходимо запустить мастер формирования схем, чтобы создать представление источника данных перед тем, как добавить нестандартное статистическое выражение.</span><span class="sxs-lookup"><span data-stu-id="35473-107">For dimensions that were created without using a data source, you must run the Schema Generation Wizard to create a data source view before adding the custom aggregation.</span></span>  
  
 <span data-ttu-id="35473-108">Чтобы добавить нестандартное статистическое выражение, используя мастер бизнес-аналитики, выберите параметр **Указать унарный оператор** на странице **Выбор расширения** .</span><span class="sxs-lookup"><span data-stu-id="35473-108">To add a custom aggregation, you use the Business Intelligence Wizard, and select the **Specify a unary operator** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="35473-109">После этого мастер отобразит шаги, позволяющие выбрать измерение, к которому необходимо применить нестандартное статистическое выражение и шаги, идентифицирующие его.</span><span class="sxs-lookup"><span data-stu-id="35473-109">This wizard then guides you through the steps of selecting a dimension to which you want to apply a custom aggregation and identifying the custom aggregation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35473-110">Перед запуском мастера бизнес-аналитики для добавления нестандартного статистического выражения убедитесь, что измерение, которое необходимо расширить, содержит иерархию атрибутов «родители-потомки».</span><span class="sxs-lookup"><span data-stu-id="35473-110">Before you run the Business Intelligence Wizard to add a custom aggregation, make sure that the dimension that you want to enhance contains a parent-child attribute hierarchy.</span></span> <span data-ttu-id="35473-111">Дополнительные сведения см. в разделе [Иерархия "родители-потомки](parent-child-dimension.md)".</span><span class="sxs-lookup"><span data-stu-id="35473-111">For more information, see [Parent-Child Hierarchy](parent-child-dimension.md).</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="35473-112">Выбор измерения</span><span class="sxs-lookup"><span data-stu-id="35473-112">Selecting a Dimension</span></span>  
 <span data-ttu-id="35473-113">На первой странице мастера **Определение унарного оператора** задайте измерение, к которому необходимо применить нестандартное статистическое выражение.</span><span class="sxs-lookup"><span data-stu-id="35473-113">On the first **Specify a Unary Operator** page of the wizard, you specify the dimension to which you want to apply a custom aggregation.</span></span> <span data-ttu-id="35473-114">Добавление нестандартного статистического выражения к этому выбранному измерению приведет к изменению измерения.</span><span class="sxs-lookup"><span data-stu-id="35473-114">The custom aggregation added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="35473-115">Эти изменения будут наследоваться всеми кубами, включающими выбранное измерение.</span><span class="sxs-lookup"><span data-stu-id="35473-115">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="adding-custom-aggregation-unary-operator"></a><span data-ttu-id="35473-116">Добавление нестандартного статистического выражения (унарного оператора)</span><span class="sxs-lookup"><span data-stu-id="35473-116">Adding Custom Aggregation (Unary Operator)</span></span>  
 <span data-ttu-id="35473-117">На второй странице мастера **Определение унарного оператора** задается родительский атрибут, необходимый для нестандартного статистического выражения, и исходный столбец для унарного оператора из таблицы измерения.</span><span class="sxs-lookup"><span data-stu-id="35473-117">On the second **Specify a Unary Operator** page, you specify the parent attribute that you want for the custom aggregation and the source column in the dimension table for the unary operator.</span></span> <span data-ttu-id="35473-118">**Родительский атрибут** перечисляет атрибуты, свойство которых имеет `Usage` значение `Parent` .</span><span class="sxs-lookup"><span data-stu-id="35473-118">**Parent attribute** lists attributes that have their `Usage` property set to `Parent`.</span></span> <span data-ttu-id="35473-119">При наличии нескольких родительских атрибутов выберите тот, который соответствует отношению родители-потомки, которое необходимо использовать.</span><span class="sxs-lookup"><span data-stu-id="35473-119">If there is more than one parent attribute, choose the parent attribute that corresponds to the parent-child relationship that you want to use.</span></span> <span data-ttu-id="35473-120">Отсутствие родительских атрибутов в списке означает, что у измерения нет допустимой иерархии типа «родители-потомки».</span><span class="sxs-lookup"><span data-stu-id="35473-120">If there is no parent attribute listed, then the dimension does not have a valid parent-child hierarchy.</span></span>  
  
 <span data-ttu-id="35473-121">В поле **Исходный столбец**выбирается строковый столбец, содержащий унарные операторы.</span><span class="sxs-lookup"><span data-stu-id="35473-121">In **Source column**, you select the string column that contains the unary operators.</span></span> <span data-ttu-id="35473-122">(Этот выбор устанавливает `UnaryOperatorColumn` свойство родительского атрибута.) Таблица измерения также должна иметь строковый столбец, указывающий унарный оператор свертки.</span><span class="sxs-lookup"><span data-stu-id="35473-122">(This selection sets the `UnaryOperatorColumn` property on the parent attribute.) The dimension table should also have a string column that specifies the unary rollup operator.</span></span> <span data-ttu-id="35473-123">Строковые значения в этом столбце должны содержать допустимые операторы агрегатов.</span><span class="sxs-lookup"><span data-stu-id="35473-123">The string values in this column should contain valid aggregation operators.</span></span> <span data-ttu-id="35473-124">Если строка не пуста, то соответствующий элемент вычисляется обычным образом.</span><span class="sxs-lookup"><span data-stu-id="35473-124">If a row is empty, the corresponding member is calculated normally.</span></span> <span data-ttu-id="35473-125">Если формула в столбце не является допустимой, то при извлечении значения ячейки, которая использует этот элемент, возникает ошибка времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="35473-125">If the formula in a column is not valid, a run-time error occurs when a cell value that uses the member is retrieved.</span></span> <span data-ttu-id="35473-126">Дополнительные сведения см. в разделе [Унарные операторы в измерениях "родители-потомки"](parent-child-dimension-attributes-unary-operators.md).</span><span class="sxs-lookup"><span data-stu-id="35473-126">For more information, see [Unary Operators in Parent-Child Dimensions](parent-child-dimension-attributes-unary-operators.md).</span></span>  
  
  