---
title: Источник CDC | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.f1
ms.assetid: 99775608-e177-44ed-bb44-aaccb0f4f327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 064c25b129364dfcd813d71a462586303dd4ff60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667841"
---
# <a name="cdc-source"></a>CDC-источник
  Источник CDC считывает диапазон информации об изменениях из таблиц изменений [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и доставляет изменения другим нижестоящим компонентам SSIS.  
  
 Диапазон информации об изменениях, считанный источником CDC, именуется диапазоном обработки CDC и определяется задачей «Управление CDC», которая выполняется до запуска текущего потока данных. Диапазон обработки CDC определяется с помощью значения переменной пакета, которая поддерживает состояние обработки CDC для группы таблиц.  
  
 Источник CDC извлекает данные из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием таблицы базы данных, представления или инструкции SQL.  
  
 Источник CDC использует следующие конфигурации.  
  
-   Диспетчер соединений ADO.NET [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для получения доступа к базе данных CDC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о настройке соединения с источником CDC см. в разделе [Редактор источника "CDC" (страница "Диспетчер соединений")](../cdc-source-editor-connection-manager-page.md).  
  
-   Таблица, включенная для CDC.  
  
-   Имя экземпляра отслеживания выбранной таблицы (если таковых существует несколько).  
  
-   Режим обработки изменений.  
  
-   Имя переменной пакета состояния CDC, на основе которой определен диапазон обработки CDC. Источник CDC не изменяет значение этой переменной.  
  
 Данные, возвращенные источником CDC, являются теми же, что возвращают следующие функции CDC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** или **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (если они доступны). Единственным необязательным добавлением является столбец **__$initial_processing** , который указывает, может ли текущий диапазон обработки перекрывать диапазон начальной загрузки таблицы. Дополнительные сведения о начальной обработке см. в разделе [CDC Control Task](../control-flow/cdc-control-task.md).  
  
 Источник CDC имеет один обычный вывод и один вывод ошибок.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Источник CDC имеет вывод ошибок. Вывод ошибок компонента включает следующие выходные столбцы.  
  
-   **Код ошибки**. Значение всегда равно -1.  
  
-   **Столбец с ошибкой**. Входной столбец, вызывающий ошибку (это относится к ошибкам преобразования).  
  
-   **Столбцы строки с ошибкой**. Данные записи, которые вызывают ошибку.  
  
 В зависимости от настройки поведения в случае ошибки, источник CDC поддерживает возврат ошибок (преобразование данных, усечение), которые обнаруживаются в процессе извлечения в выводе ошибок. Дополнительные сведения см. в разделе [Редактор источника "CDC" (страница "Вывод ошибок")](../cdc-source-editor-error-output-page.md).  
  
## <a name="data-type-support"></a>Поддержка типов данных  
 Компонент источника CDC для Microsoft поддерживает все типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые сопоставлены с верными типами данных SSIS.  
  
## <a name="troubleshooting-the-cdc-source"></a>Устранение нарушений в работе с источником CDC  
 Ниже приведена информация об устранении нарушений в работе с источником CDC.  
  
### <a name="use-this-script-to-isolate-problems-and-reproduce-them-in-sql-server-management-studio"></a>Этот скрипт используется для выявления проблем и воспроизведения их в среде SQL Server Management Studio  
 Операцией источника CDC управляет операция задачи «Управление CDC», выполняемая перед вызовом источника CDC. Задача «Управление CDC» подготавливает значение переменной пакета состояния CDC для включения начального и конечного номеров LSN. Задача выполняет функции, эквивалентные следующему скрипту:  
  
```  
use <cdc-enabled-database-name>  
               declare @start_lsn binary(10), @end_lsn binary(10)  
               set @start_lsn = sys.fn_cdc_increment_lsn(  
                       convert(binary(10),'0x' + '<value-from-state-cs>', 1))  
               set @end_lsn =   
                       convert(binary(10),'0x' + '<value-from-state-ce>', 1)  
               select * from cdc.fn_cdc_get_net_changes_dbo_Table1(@start_lsn,  
@end_lsn, '<mode>')  
```  
  
 где:  
  
-   \<cdc-enabled-database-name> — это имя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], содержащей таблицы изменений.  
  
-   \<value-from-state-cs> — это значение, которое появляется в переменной состояния CDC в виде CS/\<value-from-state-cs>/ (CS означает Current-processing-range-Start — начало текущего диапазона обработки).  
  
-   \<value-from-state-ce> — это значение, которое появляется в переменной состояния CDC в виде CE/\<value-from-state-cs>/ (CE означает Current-processing-range-End — конец текущего диапазона обработки).  
  
-   \<mode> — это режимы обработки CDC. Режимы обработки могут иметь одно из следующих значений: **Все**, **Все со старыми значениями**, **Суммарные**, **Суммарные с маской обновления**, **Суммарные со слиянием**.  
  
 Этот скрипт позволяет выявлять проблемы путем воспроизведения их в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], где можно легко воспроизводить и идентифицировать ошибки.  
  
#### <a name="sql-server-error-message"></a>Сообщение об ошибке SQL Server  
 Следующее сообщение может быть возвращено [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 **Для функции или процедуры cdc.fn_cdc_get_net_changes_\<..> задано недостаточное количество аргументов.**  
  
 Эта ошибка не указывает, что отсутствует какой-то аргумент. Она означает, что начало или конец диапазона значений номеров LSN в переменной состояния CDC является недопустимым.  
  
## <a name="configuring-the-cdc-source"></a>Настройка CDC-источника  
 Источник CDC можно настраивать программным путем или с помощью конструктора служб SSIS.  
  
 Дополнительные сведения см. в одном из следующих разделов:  
  
-   [Редактор источника "CDC" (страница "Диспетчер соединений")](../cdc-source-editor-connection-manager-page.md)  
  
-   [Редактор источника "CDC" (страница "Столбцы")](../cdc-source-editor-columns-page.md)  
  
-   [Редактор источника "CDC" (страница "Вывод ошибок")](../cdc-source-editor-error-output-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые могут быть заданы программным путем.  
  
 Открытие диалогового окна **Расширенный редактор** .  
  
-   На экране **Поток данных** вашего проекта [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] щелкните правой кнопкой мыши источник CDC и выберите элемент **Показать расширенный редактор**.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Расширенный редактор** , см. в разделе [CDC Source Custom Properties](cdc-source-custom-properties.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Редактор источника "CDC" (страница "Диспетчер соединений")](../cdc-source-editor-connection-manager-page.md)  
  
-   [Редактор источника "CDC" (страница "Столбцы")](../cdc-source-editor-columns-page.md)  
  
-   [Редактор источника "CDC" (страница "Вывод ошибок")](../cdc-source-editor-error-output-page.md)  
  
-   [Пользовательские свойства источника «CDC»](cdc-source-custom-properties.md)  
  
-   [Извлечение информации об изменениях данных с помощью источника «CDC»](cdc-source.md)  
  
## <a name="related-content"></a>См. также  
  
-   Запись в блоге [Режимы обработки для источника CDC](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/)на сайте mattmasson.com.  
  
  
