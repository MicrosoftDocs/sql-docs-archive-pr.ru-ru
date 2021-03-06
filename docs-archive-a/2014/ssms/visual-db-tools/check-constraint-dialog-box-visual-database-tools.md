---
title: Диалоговое окно "Проверочное ограничение" (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraint
ms.assetid: ad0bbf7f-b0de-406a-bd0a-cb779816b101
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7244984b869a1c68e597984a1cd03e16e53d0306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654006"
---
# <a name="check-constraint-dialog-box-visual-database-tools"></a>Диалоговое окно «Проверочное ограничение» (визуальные инструменты для баз данных)
  Это диалоговое окно выводится, если в конструкторе таблиц щелкнуть правой кнопкой мыши сетку определения таблицы и выбрать пункт **Проверочные ограничения**. Диалоговое окно содержит набор свойств для ограничений, отличных от ограничений уникальности, присоединенных к таблицам базы данных. Свойства, применяемые к ограничениям уникальности, отображаются в диалоговом окне **Индексы/Ключи** .  
  
> [!NOTE]  
>  Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.  
  
## <a name="options"></a>Параметры  
 **Выбранные проверочные ограничения**  
 Перечисляет имеющиеся проверочные ограничения. Для просмотра свойств ограничения выберите это ограничение в списке.  
  
 **Добавление**  
 Создается новое ограничение для выбранной таблицы базы данных и предоставляется имя по умолчанию и другие значения для ограничения. Ограничение не будет действительным, пока не будет введено выражение для ограничения.  
  
 **Удаление**  
 Удалить выбранное ограничение из таблицы. Для отмены добавления проверочного ограничения используйте эту кнопку удаления ограничения.  
  
 **Общая категория**  
 Откройте для отображения поля свойства **Выражение** .  
  
 **Выражение**  
 Отображается выражение для выбранного проверочного ограничения. При создании новых ограничений перед выходом из этого диалогового окна необходимо ввести выражение. Можно также изменить имеющиеся проверочные ограничения. Дополнительные сведения см. в статье [Ограничения уникальности и проверочные ограничения](../../relational-databases/tables/unique-constraints-and-check-constraints.md).  
  
 **Категория «Идентификатор»**  
 Разверните для отображения свойств **Имя** и **Описание**.  
  
 **Название**  
 Отображает имя выбранного проверочного ограничения. Для изменения имени этого ограничения введите текст непосредственно в поле свойства.  
  
 **Описание**  
 Содержит описание проверочного ограничения. Можно отредактировать описание прямо в этом поле либо нажать кнопку с многоточием ( **...** ), находящуюся справа от поля, и редактировать описание в диалоговом окне **Свойство описания**.  
  
 **Категория конструктора таблиц**  
 Разверните, чтобы просмотреть свойства для **Проверить существующие данные при создании или повторном включении**, **Применять для INSERT и UPDATE**и **Включить использование для репликации**.  
  
 **Check Existing Data On Creation or Re-Enabling**  
 Определяет, проверяются ли все уже существующие данные (данные, существовавшие в таблице до создания ограничения) на соответствие ограничению.  
  
 **Применять для INSERT и UPDATE**  
 Определяет, действует ли ограничение при вставке или изменении данных в таблице.  
  
 **Принудительное применение для репликации**  
 Показывает, действует ли ограничение, когда агент репликации производит вставку или изменение в этой таблице.  
  
## <a name="see-also"></a>См. также:  
 [Ограничения UNIQUE и проверочные ограничения](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Диалоговое окно "индексы и ключи" &#40;визуальных инструментов для баз данных&#41;](visual-database-tools.md)  
  
  
