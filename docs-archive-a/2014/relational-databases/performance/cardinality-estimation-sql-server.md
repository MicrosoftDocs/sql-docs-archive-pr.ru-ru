---
title: Оценка количества элементов (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 11/24/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: aa56127f649d71bfcc8825322f8bf729175d41df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668836"
---
# <a name="cardinality-estimation-sql-server"></a>Оценка количества элементов (SQL Server)
  Логика оценки количества элементов, называемая механизмом оценки количества элементов, переработана в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] в целях улучшения качества планов запросов и тем самым повышения производительности запросов. Новый механизм оценки количества элементов состоит из предположений и алгоритмов, которые отлично подходят для современных рабочих нагрузок OLTP и хранилища данных. Он основан на глубоком исследовании оценки количества элементов для современных рабочих нагрузок и нашем опыте усовершенствования этого механизма, накопленном за последние 15 лет. Отзывы от клиентов свидетельствуют, что эти изменения положительно сказываются на большинстве запросов либо все остается по прежнему, хотя производительность небольшого числа запросов может снизиться по сравнению с использованием предыдущего механизма оценки количества элементов.  
  
> [!NOTE]  
>  Оценка количества элементов — это прогноз количества строк в результате запроса. Оптимизатор запросов использует эти оценки, чтобы выбрать план выполнения запроса. Качество плана запроса имеет прямое влияние на повышение производительности запроса.  
  
## <a name="performance-testing-and-tuning-recommendations"></a>Рекомендации по тестированию и настройке производительности  
 В [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]новый механизм оценки количества элементов включается для всех вновь создаваемых баз данных. Однако при обновлении до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] новый механизм оценки количества элементов не включается для существующих баз данных.  
  
 Чтобы обеспечить наилучшую производительность запросов, следуйте приведенным ниже рекомендациям по тестированию рабочей нагрузки с помощью нового механизма оценки количества элементов, прежде чем включать его в работающей системе.  
  
1.  Обновите все существующие базы данных, чтобы они использовали новый механизм оценки количества элементов. Для этого используйте [уровень совместимости ALTER database &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) , чтобы установить уровень совместимости базы данных 120.  
  
2.  Запустите тестовую рабочую нагрузку с новым механизмом оценки количества элементов и устраните все выявленные проблемы производительности таким же образом, как это делается в настоящее время.  
  
3.  Если после запуска рабочей нагрузки с новым механизмом оценки количества элементов (при уровне совместимости базы данных в 120 (SQL Server 2014)) производительность конкретного запроса снизилась, можно выполнить запрос с флагом трассировки 9481 для использования версии средства оценки количества элементов, представленного в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более ранних выпусках. Описание выполнения запроса с флагом трассировки см. в статье базы знаний [Включение оптимизатора запросов SQL Server, влияющего на план выполнения, которым можно управлять с помощью разных флагов трассировки на уровне конкретного запроса](https://support.microsoft.com/kb/2801413).  
  
4.  Если вы не можете изменить все базы данных одновременно, чтобы использовать новый механизм оценки количества элементов, можно использовать бывший механизм оценки количества элементов для всех баз данных, используя [уровень совместимости ALTER database &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) , чтобы установить уровень совместимости базы данных 110.  
  
5.  Если рабочая нагрузка работает при уровне совместимости базы данных, равном 110, и требуется протестировать или выполнить определенный запрос с новым механизмом оценки количества элементов, то можно выполнить этот запрос с флагом трассировки 2312 для использования версии средства оценки количества элементов, представленной в SQL Server 2014.  Описание выполнения запроса с флагом трассировки см. в статье базы знаний [Включение оптимизатора запросов SQL Server, влияющего на план выполнения, которым можно управлять с помощью разных флагов трассировки на уровне конкретного запроса](https://support.microsoft.com/kb/2801413).  
  
## <a name="new-xevents"></a>Новые события XEvent  
 Для поддержки новых планов запросов появились два новых события XEvents query_optimizer_estimate_cardinality.  
  
-   *query_optimizer_estimate_cardinality* возникает, когда оптимизатор запросов определяет количество элементов в реляционном выражении.  
  
-   *query_optimizer_force_both_cardinality_estimation*_behaviors возникает, когда включены оба флага трассировки 2312 и 9481 с целью заставить одновременно работать и старый и новый механизмы оценки количества элементов.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показаны некоторые изменения, реализованные в новом механизме оценки количества элементов. Код оценки количества элементов был переписан. Логика этого сложна, поэтому предоставлять полный список всех изменений невозможно.  
  
> [!NOTE]  
>  Эти образцы приведены в качестве основополагающих сведений. Каких-либо действий со стороны пользователя для изменения методов проектирования баз данных и запросов не требуется.  
  
### <a name="example-a-new-cardinality-estimates-use-an-average-cardinality-for-recently-added-ascending-data"></a>Пример А. В новых механизмах оценки количества элементов используется среднее количество элементов для недавно добавленных восходящих данных  
 В этом примере показано, как с помощью нового механизма оценки количества элементов можно улучшить оценку количества элементов для данных по возрастанию, которые превышают максимальное значение в таблице во время последнего обновления статистики.  
  
```  
SELECT item, category, amount FROM dbo.Sales AS s WHERE Date = '2013-12-19';  
```  
  
 В данном примере новые строки добавляются в таблицу продаж каждый день, запрос возвращает данные, полученные в 19.12.2013, а статистика последний раз обновлялась 18.12.2013. Предыдущий механизм оценки количества элементов предполагает, что значения от 19.12.2013 отсутствуют, поскольку эта дата следует после максимальной даты, а значения за 19.12.2013 отсутствуют, так как статистика не обновлялась. Эта ситуация, известная как проблема ключа по возрастанию, возникает, когда данные загружаются в течение дня, а затем к ним выполняются запросы до обновления статистики.  
  
 Это поведение изменено. Теперь, даже если статистика не обновлена для данных, которые были добавлены с момента последнего обновления статистики, в новом механизме оценки количества элементов предполагается, что значения существуют, и в качестве оценки количества элементов используется среднее количество элементов для каждого значения в столбце.  
  
### <a name="example-b-new-cardinality-estimates-assume-filtered-predicates-on-the-same-table-have-some-correlation"></a>Пример Б. Новые средства оценки количества элементов предполагают, что отфильтрованные предикаты из одной таблицы имеют определенную корреляцию.  
 Для данного примера предположим, что число строк в таблице «Автомобили» равно 1000. Запрос «Марка» имеет 200 совпадений для «Honda», запрос «Модель» имеет 50 совпадений для «Civic», а все модели Civic относятся к марке Honda. Поэтому 20% значений из столбца «Марка» — это Honda, 5% значений из столбца «Модель» — это Civic и фактическое количество вариантов Honda Civic равно 50. В предыдущих оценках количества элементов предполагается, что значения из столбцов «Марка» и «Модель» не зависят друг от друга. В предыдущих оценках оптимизатора запросов имеется 10 Honda граждан (. 05 * .20 \* 1000 строк = 10 строк).  
  
```  
SELECT year, purchase_price FROM dbo.Cars WHERE Make = 'Honda' AND Model = 'Civic';  
```  
  
 Это поведение изменено. Теперь при формировании новых оценок количества элементов предполагается, что столбцы марки и модели имеют *некоторую* корреляцию. Оптимизатор запросов определяет, что количество элементов больше, путем добавления экспоненциального компонента в формулу оценки. Теперь оптимизатор запросов вычисляет, что 22,36 строк (05 * SQRT (. 20) \* 1000 строк = 22,36 строк) соответствует предикату. Для этого варианта и определенного распределения данных оценка в 22,36 строки более близка к фактическим 50 строкам, которые будут возвращены запросом.  
  
 Обратите внимание, что новая логика механизма оценки количества элементов предусматривает сортировку по избирательности предиката и увеличивает экспоненту. Например, если предикат избирательности был 05, .20 и .25, то оценка количества элементов будет равна (. 05 * SQRT (. 20) \* Sqrt (sqrt (. 25))).  
  
### <a name="example-c-new-cardinality-estimates-assume-filtered-predicates-on-different-tables-are-independent"></a>Пример В. В новых механизмах оценки количества элементов предполагается, что отфильтрованные предикаты из разных таблиц не зависят друг от друга  
 В этом примере в предыдущем механизме оценки количества элементов предполагается, что фильтры предикатов s.type и r.date связаны друг с другом. Однако результаты теста современных рабочих нагрузок показали, что фильтры предикатов для столбцов из различных таблиц обычно не связаны друг с другом.  
  
```  
SELECT s.ticket, s.customer, r.store FROM dbo.Sales AS s CROSS JOIN dbo.Returns AS r  
WHERE s.ticket = r.ticket AND s.type = 'toy' AND r.date = '2013-12-19';  
```  
  
 Это поведение изменено. Теперь в новой логике механизма оценки количества элементов предполагается, что фильтр s.type не связан с фильтром r.date. На практике это означает, что возврат игрушек происходит каждый день, а не только в какой-то определенный день. В этом случае новые оценки количества элементов будут выражаться меньшим числом, чем предыдущие оценки количества элементов.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение и настройка производительности](monitor-and-tune-for-performance.md)  
  
  