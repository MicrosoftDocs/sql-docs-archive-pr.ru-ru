---
title: Добавление или изменение соединения | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.addeditjoin.f1
ms.assetid: 3b546560-720f-48b8-9d63-cf159290e9d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3e17b084a232375734601b515821273d482fcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655676"
---
# <a name="add-or-edit-join"></a><span data-ttu-id="6cfe8-102">Добавление или изменение соединения</span><span class="sxs-lookup"><span data-stu-id="6cfe8-102">Add or Edit Join</span></span>
  <span data-ttu-id="6cfe8-103">Диалоговые окна **Добавить соединение** и **Изменить соединение** позволяют добавлять и редактировать фильтры соединения для публикаций слиянием.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-103">The **Add Join** and **Edit Join** dialog boxes allow you to add and edit join filters for merge publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6cfe8-104">Для редактирования фильтра в существующей публикации необходим новый моментальный снимок для этой публикации.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-104">Editing a filter in an existing publication requires a new snapshot for the publication.</span></span> <span data-ttu-id="6cfe8-105">Если публикация содержит подписки, эти подписки должны быть повторно инициализированы.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-105">If a publication has subscriptions, the subscriptions must be reinitialized.</span></span> <span data-ttu-id="6cfe8-106">Дополнительные сведения об изменении свойств см. в статье [Изменение свойств публикации и статьи](publish/change-publication-and-article-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6cfe8-106">For more information about property changes, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="6cfe8-107">Фильтр соединения позволяет фильтровать таблицу на основе фильтрации связанной таблицы в публикации.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-107">A join filter allows a table to be filtered based on how a related table in the publication is filtered.</span></span> <span data-ttu-id="6cfe8-108">Обычно родительская таблица фильтруется с использованием параметризованного фильтра строк, затем определяются один или несколько фильтров соединений, практически аналогично определению соединения между таблицами.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-108">Typically a parent table is filtered using a parameterized row filter; then one or more join filters are defined in much the same way that you define a join between tables.</span></span> <span data-ttu-id="6cfe8-109">Фильтры соединений расширяют фильтр строк таким образом, что данные в связанных таблицах реплицируются, только когда они соответствуют предложению фильтра соединения.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-109">The join filters extend the row filter so that the data in the related tables is replicated only if it matches the join filter clause.</span></span>  
  
 <span data-ttu-id="6cfe8-110">Фильтры соединений, как правило, следуют связям «первичный-внешний ключ», определенным для таблиц, к которым они применяются, но не ограничиваются только этими связями.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-110">Join filters typically follow the primary key/foreign key relationships defined for the tables to which they are applied, but they are not limited strictly to primary key/foreign key relationships.</span></span> <span data-ttu-id="6cfe8-111">Фильтр соединения может быть основан на любой логике, сравнивающей взаимосвязанные данные в двух таблицах статей.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-111">The join filter can be based on any logic that compares related data in two article tables.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6cfe8-112">Фильтры соединений могут включать бесконечное количество таблиц, но фильтры с большим количеством таблиц могут повлиять на производительность во время обработки слияния.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-112">Join Filters can involve an unlimited number of tables, but filters with a large number of tables can impact performance during merge processing.</span></span> <span data-ttu-id="6cfe8-113">При создании фильтров соединения из пяти и более таблиц рассмотрите другие решения: не фильтруйте маленькие таблицы, таблицы, которые не изменяются или служат в основном таблицами подстановки.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-113">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="6cfe8-114">Используйте фильтры соединений только между таблицами, которые должны быть разделены среди подписчиков.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-114">Use join filters only between tables that must be partitioned among Subscribers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6cfe8-115">Параметры</span><span class="sxs-lookup"><span data-stu-id="6cfe8-115">Options</span></span>  
 <span data-ttu-id="6cfe8-116">Данное диалоговое окно содержит процесс создания фильтра соединения между двумя таблицами, состоящий из трех шагов.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-116">This dialog box involves a three-step process to create a join filter between two tables.</span></span> <span data-ttu-id="6cfe8-117">Создание нескольких фильтров соединений требует повторного выполнения последовательности действий в этом диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-117">Creating more than one join filter requires more than one pass through the dialog box.</span></span>  
  
1.  <span data-ttu-id="6cfe8-118">**Проверьте отфильтрованную таблицу и выберите соединяемую таблицу**</span><span class="sxs-lookup"><span data-stu-id="6cfe8-118">**Verify filtered table and select the joined table**</span></span>  
  
    -   <span data-ttu-id="6cfe8-119">При добавлении нового соединения проверьте, что таблица в текстовом поле **Отфильтрованная таблица** указана правильно (если она указана неправильно, нажмите кнопку **Отмена**, выберите правильную таблицу на странице **Фильтрация строк таблицы** и нажмите кнопку **Добавить соединение** , чтобы вернуться к данному диалоговому окну).</span><span class="sxs-lookup"><span data-stu-id="6cfe8-119">If you are adding a new join, verify that the table in the **Filtered table** text box is correct (if it is not correct, click **Cancel**, select the correct table on the **Filter Table Rows** page, and click **Add Join** to return to this dialog box).</span></span> <span data-ttu-id="6cfe8-120">Затем выберите таблицу из раскрывающегося списка **Соединяемая таблица** .</span><span class="sxs-lookup"><span data-stu-id="6cfe8-120">Then select a table from the **Joined table** drop-down list box.</span></span>  
  
    -   <span data-ttu-id="6cfe8-121">При редактировании существующего соединения имена таблиц будут уже указаны и их нельзя изменить.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-121">If you are editing an existing join, the table names will be specified already and cannot be changed.</span></span> <span data-ttu-id="6cfe8-122">Для изменения таблиц, участвующих в соединении, необходимо удалить существующий фильтр соединения на странице **Фильтрация строк таблицы** и создать новый фильтр соединения между другими таблицами.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-122">To change the tables involved in the join, you must delete the existing join filter on the **Filter Table Rows** page and create a new join between different tables.</span></span>  
  
2.  <span data-ttu-id="6cfe8-123">**Создайте инструкцию соединения**</span><span class="sxs-lookup"><span data-stu-id="6cfe8-123">**Create the join statement**</span></span>  
  
    -   <span data-ttu-id="6cfe8-124">При добавлении нового соединения выберите или **Использовать конструктор для создания инструкции** , или **Написать инструкцию соединения вручную**.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-124">If you are adding a new join, select either **Use the builder to create the statement** or **Write the join statement manually**.</span></span> <span data-ttu-id="6cfe8-125">Если начато написание соединения вручную, то нельзя использовать конструктор.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-125">If you begin writing the join manually, you cannot use the builder.</span></span>  
  
         <span data-ttu-id="6cfe8-126">Если решено применить конструктор, то для создания инструкции соединения используйте столбцы в сетке (**Сопряжение**, **Фильтруемый столбец таблицы**, **Оператор**и **Столбец соединяемой таблицы**).</span><span class="sxs-lookup"><span data-stu-id="6cfe8-126">If you select to use the builder, use the columns in the grid (**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**) to build a join statement.</span></span> <span data-ttu-id="6cfe8-127">Каждый столбец в сетке содержит раскрывающийся список, позволяющий выбрать два столбца и оператор ( **=** , **<>** , **<=** , **\<**, **>=** , **>** , **like**).</span><span class="sxs-lookup"><span data-stu-id="6cfe8-127">Each column in the grid contains a drop-down list box, allowing you to select two columns and an operator (**=**, **<>**, **<=**, **\<**, **>=**, **>**, **like**).</span></span> <span data-ttu-id="6cfe8-128">Результаты выводятся в текстовом поле **Предварительный просмотр** .</span><span class="sxs-lookup"><span data-stu-id="6cfe8-128">The results are displayed in the **Preview** text area.</span></span> <span data-ttu-id="6cfe8-129">Если в соединении участвуют несколько пар столбцов, выберите конъюнкцию (**AND** или **OR**) в столбце **Сопряжение** , а затем введите еще два столбца и другой оператор.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-129">If the join involves more than one pair of columns, select a conjunction (**AND** or **OR**) from the **Conjunction** column, and then enter two more columns and another operator.</span></span>  
  
         <span data-ttu-id="6cfe8-130">Если нужно написать инструкцию вручную, введите ее в текстовом поле **Инструкция соединения** .</span><span class="sxs-lookup"><span data-stu-id="6cfe8-130">If you select to write the statement manually, write the join statement in the **Join statement** text area.</span></span> <span data-ttu-id="6cfe8-131">Используйте списки **Фильтруемые столбцы таблицы** и **Столбцы соединяемой таблицы** для перетаскивания столбцов в текстовое поле **Инструкция соединения** .</span><span class="sxs-lookup"><span data-stu-id="6cfe8-131">Use the **Filtered table columns** list box and **Joined table columns** list box to drag and drop columns to the **Join statement** text area.</span></span>  
  
    -   <span data-ttu-id="6cfe8-132">При изменении существующего соединения правки производятся вручную.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-132">If you are editing an existing join, you must make edits manually.</span></span>  
  
3.  <span data-ttu-id="6cfe8-133">**Укажите параметры соединения**</span><span class="sxs-lookup"><span data-stu-id="6cfe8-133">**Specify join options**</span></span>  
  
    -   <span data-ttu-id="6cfe8-134">Если столбец, по которому нужно соединить отфильтрованную таблицу, является уникальным, выберите **Уникальный ключ**.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-134">If the column on which you join in the filtered table is unique, select **Unique key**.</span></span> <span data-ttu-id="6cfe8-135">Если столбец уникален, то для процесса слияния будут доступны специальные способы оптимизации производительности.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-135">The merge process has special performance optimizations available if the column is unique.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="6cfe8-136">Выбор этого параметра указывает, что связь между дочерней и родительской таблицей в фильтре соединения — «одна к одной» или «одна к нескольким».</span><span class="sxs-lookup"><span data-stu-id="6cfe8-136">Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many.</span></span> <span data-ttu-id="6cfe8-137">Выберите этот параметр только при наличии ограничения на соединяющийся столбец в родительской таблице, гарантирующий уникальность.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-137">Only select this option if you have a constraint on the joining column in the parent table that guarantees uniqueness.</span></span> <span data-ttu-id="6cfe8-138">Если параметр задан неправильно, может возникнуть потеря конвергенции данных.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-138">If the option is set incorrectly, non-convergence of data can occur.</span></span>  
  
    -   <span data-ttu-id="6cfe8-139">Только для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-139">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="6cfe8-140">По умолчанию во время синхронизации процесс репликации слиянием обрабатывает изменения построчно.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-140">By default, merge replication processes changes on a row-by-row basis during synchronization.</span></span> <span data-ttu-id="6cfe8-141">Чтобы связанные изменения обрабатывались в виде блока, выберите **Логическая запись**.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-141">To have related changes processed as a unit, select **Logical record**.</span></span> <span data-ttu-id="6cfe8-142">Этот параметр доступен, только если удовлетворяются требования статьи и публикации на использование логических записей.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-142">This option is available only if the article and publication requirements for using logical records are met.</span></span> <span data-ttu-id="6cfe8-143">Дополнительные сведения см. в подразделе "Вопросы использования логических записей" раздела [Изменения группирования связанных строк с логическими записями](merge/group-changes-to-related-rows-with-logical-records.md).</span><span class="sxs-lookup"><span data-stu-id="6cfe8-143">For more information, see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
 <span data-ttu-id="6cfe8-144">После добавления или редактирования фильтра нажмите кнопку **ОК** для сохранения изменений и закрытия диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-144">After you have added or edited a filter, click **OK** to save changes and close the dialog box.</span></span> <span data-ttu-id="6cfe8-145">Проводится синтаксический анализ указанного фильтра, после чего фильтр применяется к таблице в предложении SELECT.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-145">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="6cfe8-146">Если оператор фильтра содержит синтаксические ошибки или встречаются другие проблемы, пользователь уведомляется, после чего может отредактировать эту инструкцию фильтра.</span><span class="sxs-lookup"><span data-stu-id="6cfe8-146">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfe8-147">См. также:</span><span class="sxs-lookup"><span data-stu-id="6cfe8-147">See Also</span></span>  
 <span data-ttu-id="6cfe8-148">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="6cfe8-148">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="6cfe8-149">[Просмотр и изменение свойств публикации](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6cfe8-149">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="6cfe8-150">[Фильтрация опубликованных данных](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="6cfe8-150">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="6cfe8-151">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="6cfe8-151">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="6cfe8-152">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="6cfe8-152">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="6cfe8-153">Публикация данных и объектов базы данных</span><span class="sxs-lookup"><span data-stu-id="6cfe8-153">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  