---
title: Определение связи логических записей между статьями таблиц слияния | Документация Майкрософт
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60c92a237562704e5bc5d43717f863aa78a14b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750684"
---
# <a name="define-a-logical-record-relationship-between-merge-table-articles"></a>Определение связи логических записей между статьями таблиц слияния
  В данном разделе описывается процесс определения связи логических записей между статьями таблиц слияния в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO.  
  
 Репликация слиянием позволяет определить связь между связанными строками в различных таблицах. Эти строки затем могут быть обработаны во время синхронизации как элементы транзакции. Логическая запись может быть определена между двумя статьями независимо от наличия связи фильтров соединения между ними. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для определения связи логических записей между статьями таблиц слияния используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Если добавление, изменение или удаление логической записи выполняется после инициализации подписок на публикацию, следует создать новый моментальный снимок и повторно инициализировать все подписки после внесения изменений. Дополнительные сведения о требованиях к изменениям свойств см. в статье [Изменение свойств публикации и статьи](change-publication-and-article-properties.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Определите логические записи в диалоговом окне **Добавить соединение**, которое доступно в мастере создания публикаций и диалоговом окне **Свойства публикации — \<Publication>публикация >** . Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](create-a-publication.md) и [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
 Логические записи могут определяться в диалоговом окне **Добавление соединения** , только если они применяются к фильтру соединения в публикации слиянием и если публикация соответствует требованиям для использования предварительно вычисляемых секций. Чтобы определить логические записи, которые не применяются к фильтрам соединения, и чтобы установить обнаружение и разрешение конфликтов на уровне логических записей, следует использовать хранимые процедуры.  
  
#### <a name="to-define-a-logical-record-relationship"></a>Определение связи логических записей  
  
1.  На странице **Фильтрация строк** таблицы мастера создания публикаций или странице **Фильтрация строк** диалогового окна **Свойства публикации — \<Publication>** выберите фильтр строк в области **Отфильтрованные таблицы**.  
  
     Связь логических записей ассоциирована с фильтром соединения, который расширяет фильтр строк. Поэтому необходимо определить фильтр строк, прежде чем можно будет расширить фильтр с помощью фильтра соединения и применить связь логических записей. После того как определен один фильтр соединения, можно расширить этот фильтр соединения с помощью еще одного фильтра соединения. Дополнительные сведения об определении фильтров соединения см. в разделе [Определение и изменение фильтра соединения между статьями публикации слиянием](define-and-modify-a-join-filter-between-merge-articles.md).  
  
2.  Щелкните **Добавить**и выберите **Добавить соединение для расширения выбранного фильтра**.  
  
3.  Определите фильтр соединения в диалоговом окне **Добавление соединения** , а затем установите флажок **Логическая запись**.  
  
4.  Если вы находитесь в диалоговом окне **Свойства публикации — \<Publication>** , нажмите кнопку **OK**, чтобы сохранить результаты и закрыть диалоговое окно.  
  
#### <a name="to-delete-a-logical-record-relationship"></a>Удаление связи логических записей  
  
-   Удалите лишь связь логических записей или удалите и связь логических записей, и ассоциированный с ней фильтр соединения.  
  
     Чтобы удалить только связь логических записей.  
  
    1.  На странице **Фильтрация строк** мастера создания публикаций или странице **Фильтрация строк** диалогового окна **Свойства публикации — \<Publication>** выберите фильтр соединения, связанный с отношением логической записи, в области **Отфильтрованные таблицы**, а затем нажмите кнопку **Изменить**.  
  
    2.  В диалоговом окне **Изменить соединение** снимите флажок **Логическая запись**.  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Чтобы удалить связь логических записей и фильтр соединения, ассоциированный с этой связью, выполните следующие действия.  
  
    -   На странице **Фильтрация строк** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<Publication>** выберите фильтр в области **Отфильтрованные таблицы**, а затем нажмите кнопку **Удалить**. Если удаляемый фильтр соединения расширен за счет других фильтров, эти фильтры также будут удалены.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 С помощью хранимых процедур репликации можно программно задать связь логических записей между статьями.  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a>Определение связи логических записей без сопутствующего фильтра соединения  
  
1.  Если публикация содержит фильтруемые статьи, выполните хранимую процедуру [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)и проверьте значение параметра **use_partition_groups** в результирующем наборе.  
  
    -   Если значение равно **1**, то предварительно вычисляемые секции уже используются.  
  
    -   Если значение равно **0**, выполните хранимую процедуру [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) на издателе в базе данных публикации. Задайте **use_partition_groups** в качестве значения параметра **@property** и **true** в качестве значения параметра **@value**.  
  
        > [!NOTE]  
        >  Если публикация не поддерживает предварительно вычисляемые секции, то логические записи использовать нельзя. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
    -   Если это значение NULL, то необходимо запустить агент моментальных снимков для создания исходного моментального снимка для публикации.  
  
2.  Если статьи, входящие в логическую запись, не существуют, выполните хранимую процедуру [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) на издателе в базе данных публикации. Укажите один из приведенных ниже параметров определения и распознавания конфликтов в логической записи.  
  
    -   Для распознавания и разрешения конфликтов, возникающих в связанных строках логической записи, присвойте значение **true** в качестве значения параметра **@logical_record_level_conflict_detection** и **@logical_record_level_conflict_resolution**.  
  
    -   Чтобы использовать стандартное обнаружение и разрешение конфликтов на уровне строк или столбцов, укажите значение `false` для **@logical_record_level_conflict_detection** и **@logical_record_level_conflict_resolution** , которое является значением по умолчанию.  
  
3.  Повторите шаг 2 для каждой статьи, которая содержит логическую запись. Необходимо использовать в каждой статье логической записи одинаковые параметры определения и разрешения конфликтов. Дополнительные сведения см. в статье [Распознавание и разрешение конфликтов в логических записях](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql). Укажите **@publication** , имя одной статьи в связи для **@article** , имя второй статьи в параметре, **@join_articlename** имя для связи, **@filtername** предложение, определяющее связь между двумя статьями **@join_filterclause** , тип объединения для **@join_unique_key** и одно из следующих значений для **@filter_type** :  
  
    -   **2** — определяет логическую связь;  
  
    -   **3** — определят логическую связь с фильтром соединения.  
  
    > [!NOTE]  
    >  Фильтр соединения не используется, направление связи между двумя статьями несущественно.  
  
5.  Повторите шаг 2 для всех оставшихся связей логических записей в публикации.  
  
#### <a name="to-change-conflict-detection-and-resolution-for-logical-records"></a>Изменение способа определения и разрешения конфликтов логических записей  
  
1.  Для определения и разрешения конфликтов, возникающих в связанных строках логической записи, выполните следующие действия.  
  
    -   В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Задайте **@property** в качестве значения параметра **@property** и **true** в качестве значения параметра **@value**. Задайте **1** в качестве значения параметра **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
    -   В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Задайте **@property** в качестве значения параметра **@property** и **true** в качестве значения параметра **@value**. Задайте **1** в качестве значения параметра **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
2.  Для использования стандартного метода определения и разрешения конфликтов уровня строки и столбца выполните следующие действия.  
  
    -   В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Укажите значение **logical_record_level_conflict_detection** в **@property** параметре и значение для параметра `false` **@value** . Задайте **1** в качестве значения параметра **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
    -   В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Укажите значение **logical_record_level_conflict_resolution** в **@property** параметре и значение для параметра `false` **@value** . Задайте **1** в качестве значения параметра **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
#### <a name="to-remove-a-logical-record-relationship"></a>Удаление связи логических записей  
  
1.  На издателе в базе данных публикации выполните приведенный ниже запрос для получения сведений обо всех связях логических записей, определенных для указанной публикации:  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_returnmergelogicalrecords)]  
  
     Запомните имя удаляемой связи логических записей, содержащееся в столбце `filtername` результирующего набора.  
  
    > [!NOTE]  
    >  Этот запрос возвращает те же сведения, что и системная хранимая процедура [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql), однако системная хранимая процедура возвращает только сведения по тем связям логических записей, которые являются также фильтрами соединения.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql). Укажите **@publication** , имя одной из статей в связи для **@article** и имя связи из шага 1 в параметре **@filtername** .  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере разрешается использование предварительно вычисляемых секций в существующей публикации и создается логическая запись, в которую входят две новые статьи для таблиц `SalesOrderHeader` и `SalesOrderDetail` .  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_addmergelogicalrecord)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
  
> [!NOTE]  
>  Репликация слиянием позволяет указывать, что конфликты должны отслеживаться и разрешаться на уровне логических записей, но эти параметры нельзя задать с помощью объектов RMO.  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a>Определение связи логических записей без сопутствующего фильтра соединения  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> , установите для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
3.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает `false`, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если свойство <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> имеет значение <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, укажите значение <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.  
  
5.  Если статьи, которые должны составить логическую запись, не существуют, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeArticle> и задайте следующие свойства.  
  
    -   Имя статьи для <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   Если статья отфильтрована горизонтально, задайте условие фильтра строк для свойства <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> (необязательно). Используйте это свойство для определения статического или параметризованного фильтра строк. Дополнительные сведения см. в разделе [Параметризованные фильтры строк](../merge/parameterized-filters-parameterized-row-filters.md).  
  
     Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Article.Create%2A> .  
  
7.  Повторите шаги 5 и 6 для каждой статьи, составляющей логическую запись.  
  
8.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> , чтобы определить связь логических записей между статьями. Затем установите следующие свойства.  
  
    -   Имя дочерней статьи в связи логических записей для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> .  
  
    -   Имя существующей, родительской статьи в связи логических записей для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> .  
  
    -   Имя связи логических записей для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> .  
  
    -   Выражение, определяющее связь для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> .  
  
    -   Значение <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> . Если связь логических записей является также фильтром соединения, укажите значение <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> для этого свойства. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../merge/group-changes-to-related-rows-with-logical-records.md).  
  
9. Вызовите метод <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> для объекта, представляющего дочернюю статью в этой связи. Передайте объект <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> из шага 8, чтобы определить связь.  
  
10. Повторите шаги 8 и 9 для каждой оставшейся связи логических записей в публикации.  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> Пример (объекты RMO)  
 В этом примере создается логическая запись, составленная из двух новых статей для таблиц `SalesOrderHeader` и `SalesOrderDetail` .  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## <a name="see-also"></a>См. также:  
 [Определение и изменение фильтра соединения между статьями публикации слиянием](define-and-modify-a-join-filter-between-merge-articles.md)   
 [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Определение и изменение статического строкового фильтра](define-and-modify-a-static-row-filter.md)   
 [Группирование изменений в связанных строках с помощью логических записей](../merge/group-changes-to-related-rows-with-logical-records.md)   
 [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)   
 [Группирование изменений в связанных строках с помощью логических записей](../merge/group-changes-to-related-rows-with-logical-records.md)  
  
  
