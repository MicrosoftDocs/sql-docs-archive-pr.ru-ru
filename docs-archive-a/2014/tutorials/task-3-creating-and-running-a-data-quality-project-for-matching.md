---
title: Задача 3. Создание и запуск проекта качества данных для сопоставления | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 221d6d583c61ee035c20fcb63f0ed5278f2b8678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656106"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>Задача 3. Создание и запуск проекта качества данных для сопоставления
  В этой задаче вы создадите проект служб DQS для операции сопоставления и выполните сопоставление очищенных данных поставщика, чтобы удалить все повторяющиеся значения.

1.  На главной странице **клиента DQS**нажмите кнопку **Создать проект качества данных**.

2.  Введите **Удаление повторений поставщика** в поле **Имя проекта**.

3.  Выберите **Поставщики** в списке баз знаний для поля **Использовать базу знаний** . Вы создали политику проверки соответствия в этой базе знаний на предыдущем занятии.

4.  Выберите **Сопоставление** в **списке действий** в нижней правой области.

     ![Новый проект служб DQS — выбрано сопоставление](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "Новый проект служб DQS — выбрано сопоставление")

5.  Нажмите кнопку **Далее**.

6.  На странице **Сопоставление** выберите **Файл Excel** как **Источник данных**.

7.  Нажмите кнопку **Обзор** и выберите выходной файл процедуры очистки **Cleansed Supplier List.xls**.

8.  Сопоставьте исходный столбец **SupplierID** с доменом **Идентификатор поставщика** , столбец **Имя поставщика** с доменом **Имя поставщика** , столбец **ContactEmailAddress** с доменом **Адрес электронной почты** .

9. Нажмите кнопку **Далее** , чтобы перейти к странице **Сопоставление** .

10. Нажмите кнопку **Запустить** , чтобы начать процесс сопоставления. Должны быть получены результаты, аналогичные результатам предыдущей задачи, поскольку для определения политики проверки соответствия использовался тот же входной файл.

11. Просмотрите все сопоставленные записи и соответствующие оценки в списке. Результаты должны быть такими же, как и в предыдущей задаче. Сведения об анализе результатов сопоставления см. в предыдущей задаче.

12. Нажмите кнопку **Далее** , чтобы перейти к странице **Экспорт** .

## <a name="next-step"></a>Следующий шаг
 [Задача 4. Экспорт результатов сопоставления в файл Excel](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)

