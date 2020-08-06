---
title: Описание кластеризованных и некластеризованных индексов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- query optimizer [SQL Server], index usage
- index concepts [SQL Server]
ms.assetid: b7d6b323-728d-4763-a987-92e6292f6f7a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c9eb51a24000b8af4a466fe4330644a722ad325b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749867"
---
# <a name="clustered-and-nonclustered-indexes-described"></a>Описания кластеризованных и некластеризованных индексов
  Индекс является структурой на диске, которая связана с таблицей или представлением и ускоряет получение строк из таблицы или представления. Индекс содержит ключи, построенные из одного или нескольких столбцов в таблице или представлении. Эти ключи хранятся в виде структуры сбалансированного дерева, которая поддерживает быстрый поиск строк по их ключевым значениям в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Таблица или представление может иметь индексы следующих типов.  
  
-   Кластеризованный  
  
    -   Кластеризованные индексы сортируют и хранят строки данных в таблицах или представлениях на основе их ключевых значений. Этими значениями являются столбцы, включенные в определение индекса. Существует только один кластеризованный индекс для каждой таблицы, потому что строки данных могут быть отсортированы только в единственном порядке.  
  
    -   Строки данных в таблице хранятся в порядке сортировки только в том случае, если таблица содержит кластеризованный индекс. Если у таблицы есть кластеризованный индекс, то таблица называется кластеризованной. Если у таблицы нет кластеризованного индекса, то строки данных хранятся в неупорядоченной структуре, которая называется кучей.  
  
-   Некластеризованный  
  
    -   Некластеризованные индексы имеют структуру, отдельную от строк данных. В некластеризованном индексе содержатся значения ключа некластеризованного индекса, и каждая запись значения ключа содержит указатель на строку данных, содержащую значение ключа.  
  
    -   Указатель из строки индекса в некластеризованном индексе, который указывает на строку данных, называется указателем строки. Структура указателя строки зависит от того, хранятся ли страницы данных в куче или в кластеризованной таблице. Для кучи указатель строки является указателем на строку. Для кластеризованной таблицы указатель строки данных является ключом кластеризованного индекса.  
  
    -   Можно добавить неключевые столбцы на конечный уровень некластеризованного индекса и обойти существующее ограничение на ключи индексов (900 байт и 16 ключевых столбцов) и выполнять полностью индексированные запросы. Дополнительные сведения см. в статье [Create Indexes with Included Columns](create-indexes-with-included-columns.md).  
  
 Как кластеризованные, так и некластеризованные индексы могут быть уникальными. Это означает, что никакие две строки не имеют одинаковое значение для ключа индекса. В противном случае индекс не является уникальным, и несколько строк могут содержать одно и то же значение. Дополнительные сведения см. в статье [Создание уникальных индексов](create-unique-indexes.md).  
  
 Обслуживание индексов таблиц и представлений происходит автоматически при любом изменении данных в таблице.  
  
 Дополнительные типы специальных индексов см. в разделе [Indexes](indexes.md) .  
  
## <a name="indexes-and-constraints"></a>Индексы и ограничения  
 Индексы создаются автоматически при определении ограничений PRIMARY KEY или UNIQUE на основе столбцов таблицы. Например, при создании таблицы и указании конкретного столбца в качестве первичного ключа, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] автоматически создает на основе этого столбца ограничение PRIMARY KEY и индекс. Дополнительные сведения см. в разделах [Create Primary Keys](../tables/create-primary-keys.md) и [Create Unique Constraints](../tables/create-unique-constraints.md).  
  
## <a name="how-indexes-are-used-by-the-query-optimizer"></a>Как оптимизатор запросов использует индексы  
 Правильно построенные индексы могут сократить количество дисковых операций ввода-вывода, уменьшить потребление системных ресурсов, таким образом улучшая производительность запроса. Индексы могут быть полезны во множестве запросов, содержащих инструкции SELECT, UPDATE, DELETE или MERGE. Рассмотрим запрос `SELECT Title, HireDate FROM HumanResources.Employee WHERE EmployeeID = 250` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . При выполнении этого запроса оптимизатор запросов оценивает все доступные методы получения данных и выбирает наиболее эффективный метод. Этим методом может являться просмотр таблицы или просмотр одного или более индексов, если они существуют.  
  
 При выполнении просмотра таблицы оптимизатор запросов считывает все строки таблицы и извлекает строки, удовлетворяющие критериям запроса. Просмотр таблицы формирует много дисковых операций ввода-вывода и может быть ресурсоемкой операцией. Но если результирующий набор запроса содержит высокий процент строк таблицы, то просмотр таблицы может оказаться самым эффективным методом.  
  
 Когда оптимизатор запросов использует индекс, он выполняет поиск по ключевым столбцам индекса, находит место хранения запрашиваемых строк и извлекает оттуда совпадающие строки. В основном поиск по индексу протекает намного быстрее, чем поиск по таблице, так как в отличие от таблицы индекс часто содержит мало столбцов в каждой строке и строки расположены в отсортированном порядке.  
  
 Оптимизатор запросов обычно выбирает наиболее эффективный метод при выполнении запросов. Но если отсутствуют доступные индексы, оптимизатор запросов должен использовать просмотр таблицы. Ваша задача — спроектировать и создать индексы, которые лучше всего подходят для конкретной среды, чтобы оптимизатор запросов мог выбирать из нескольких эффективных индексов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает [помощник по настройке ядра СУБД](../performance/database-engine-tuning-advisor.md) , который может помочь при анализе среды базы данных и при выборе соответствующих индексов.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Создание кластеризованных индексов](create-clustered-indexes.md)  
  
 [Создание некластеризованных индексов](create-nonclustered-indexes.md)  
  
  