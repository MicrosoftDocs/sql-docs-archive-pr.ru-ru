---
title: Сравнение хранилища таблиц на диске с хранилищем таблиц, оптимизированных для памяти | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: eacf443c-001a-445f-ad1c-5f5a45eca6f4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 47cf84427b2f4f26a29f732575530b384d9c4fc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749908"
---
# <a name="comparing-disk-based-table-storage-to-memory-optimized-table-storage"></a>Сравнение хранилища таблиц на диске с хранилищем таблиц оптимизированным для памяти
  
  
|Категории|Дисковая таблица|Долговечная, оптимизированная для памяти таблица|  
|----------------|-----------------------|-------------------------------------|  
|DDL|Сведения о метаданных хранятся в системных таблицах в первичной файловой группе базы данных и доступны через представления каталога.|Сведения о метаданных хранятся в системных таблицах в первичной файловой группе базы данных и доступны через представления каталога.|  
|Структура|Строки хранятся в страницах размером 8 КБ. Страница содержит только строки из одной таблицы.|Строки хранятся в виде отдельных строк. Структура страницы не существует. Две последовательные строки в файле данных могут принадлежать к различным, оптимизированным для памяти таблицам.|  
|Индексы|Индексы хранятся в структуре страницы наподобие строк данных.|Сохраняется только определение индекса (не строки индекса). Индексы сохраняются в памяти и создаются повторно, когда оптимизированная для памяти таблица загружается в память при перезапуске базы данных. Так как строки индекса не сохраняются, то для изменений индекса журнал не ведется.|  
|Операция DML|Сначала нужно найти страницу и загрузить ее буферный пул.<br /><br /> Вставить<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вставляет строки на страницу с учетом порядка страниц для кластеризованного индекса.<br /><br /> DELETE<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет строки, которые нужно удалить, на странице и отмечает их как удаленные.<br /><br /> Update<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] находит строки на странице. Обновление для неключевых столбцов выполняется на месте. Обновление ключевого столбца выполняется с помощью операции удаления и вставки.<br /><br /> После завершения операции DML измененные страницы записываются на диск при фиксации политики буферного пула, контрольной точки или транзакции для операций с минимальным уровнем ведения журнала. И операции чтения, и операции записи на страницах приводят к ненужным операциям ввода-вывода.|Поскольку данные оптимизированных для памяти таблиц находятся в памяти, операции DML осуществляются непосредственно в памяти. Существует фоновый поток, который считывает записи журнала для оптимизированных для памяти таблиц и сохраняет их в файлы данных и разностные файлы. При обновлении создается новая версия строки. Но обновление записывается в журнал как операция удаления с последующей вставкой.|  
|Фрагментация данных|Фрагменты обработки данных, из-за которых появляются частично заполненные страницы и логически последовательные страницы, которые располагаются на диске непоследовательно. Это уменьшает скорость доступа к данным и может потребовать дефрагментации данных.|Оптимизированные для памяти данные не хранятся в страницах, поэтому фрагментации данных нет. Но при обновлении и удалении строк файлы данных и разностные файлы требуется сжимать. Этим занимается потоковый поток MERGE в соответствии с политикой слияния.|  
  
## <a name="see-also"></a>См. также:  
 [Создание и управление хранилищем для оптимизированных для памяти объектов](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  