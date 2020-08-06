---
title: Редактор задачи «основная вставка» (страница «Параметры») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.options.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1751d1e0ac01d5459a8c76e6a48626c2ad6deafd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738642"
---
# <a name="bulk-insert-task-editor-options-page"></a>Редактор задачи «Массовая вставка» (страница «Параметры»)
  Страница **Параметры** диалогового окна **Редактор задачи «Массовая вставка»** используется для установки свойств операции массовой вставки. С помощью задачи "Массовая вставка" большой объем данных копируется в таблицу или представление [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Сведения о работе с массовой вставкой см. в разделах [Задача "Массовая вставка"](control-flow/bulk-insert-task.md) и [BULK INSERT(Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
## <a name="options"></a>Параметры  
 **CodePage**  
 Задает кодовую страницу данных в файле данных.  
  
 **DataFileType**  
 Задает значение типа данных, используемых в операции загрузки.  
  
 **BatchSize**  
 Задает количество строк в одном пакете. Значение по умолчанию равно количеству строк во всем файле данных. Если параметр **BatchSize** имеет значение ноль, данные загружаются в одном пакете.  
  
 **LastRow**  
 Задает последнюю строку для копирования.  
  
 **FirstRow**  
 Задает первую строку, с которой должно начинаться копирование.  
  
 **Параметры**  
 |Термин|Определение|  
|----------|----------------|  
|**Проверочные ограничения**|Выберите для проверки ограничений таблицы и столбца.|  
|**Сохранять значения NULL**|Выберите для сохранения значений NULL во время операции массовой вставки вместо вставки значений по умолчанию для пустых столбцов.|  
|**Разрешить вставку в столбец идентификаторов**|Выберите, чтобы вставлять существующие значения в столбец идентификаторов.|  
|**Блокировка таблицы**|Выберите для блокировки таблицы во время операции массовой вставки.|  
|**Запускать триггеры**|Выберите для срабатывания триггеров при вставке, обновлении или удалении в таблице.|  
  
 **SortedData**  
 Определяет предложение ORDER BY в инструкции массовой вставки. Указываемое имя столбца должно быть действительным столбцом в целевой таблице. Значение по умолчанию — `false`. Это означает, что данные не отсортированы с помощью предложения ORDER BY.  
  
 **MaxErrors**  
 Определяет максимальное количество ошибок, которое может произойти перед отменой операции массовой вставки. Значение «0» указывает на то, что допускается бесконечное количество ошибок.  
  
> [!NOTE]  
>  Каждая строка, которая не может быть импортирована операцией массовой загрузки, считается за одну ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "групповые вставки" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "Вставка в &#40;"&#41;страницу "соединение"](../../2014/integration-services/bulk-insert-task-editor-connection-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)   
 [Поток управления](control-flow/control-flow.md)  
  
  