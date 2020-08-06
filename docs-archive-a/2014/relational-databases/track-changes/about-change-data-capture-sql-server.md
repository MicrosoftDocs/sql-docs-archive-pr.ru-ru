---
title: Об отслеживании измененных данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], about
- change data capture [SQL Server]
- 22832 (Database Engine error)
ms.assetid: 7d8c4684-9eb1-4791-8c3b-0f0bb15d9634
author: rothja
ms.author: jroth
ms.openlocfilehash: cf8045ff45e7467a626bee85857ae8319f5d2649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665914"
---
# <a name="about-change-data-capture-sql-server"></a>Об отслеживании измененных данных (SQL Server)
  Система отслеживания измененных данных регистрирует операции вставки, обновления и удаления, которые применяются к таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Тем самым обеспечивается доступ к подробностям этих изменений в легко обрабатываемом реляционном формате. Сведения о столбцах и метаданных, которые требуются для применения изменений к целевой среде, отслеживаются в измененных строках и хранятся в таблицах изменений, отражающих структуру столбцов исходных таблиц. Чтобы потребители данных могли систематически получать доступ к информации об изменениях, предоставляются функции с табличным значением.  
  
 Хорошим примером потребителя данных, для которого предназначена эта технология, является приложение для извлечения, преобразования и загрузки данных (ETL). ETL-приложение постепенно загружает информацию об изменениях из исходных таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в хранилище или витрину данных. Хотя представление исходных таблиц в хранилище данных должно отражать изменения в этих таблицах, использование технологии, которая обновляла бы реплики исходной таблицы, в данном случае не подходит. Вместо этого необходим надежный поток информации об изменениях, структурированный таким образом, чтобы клиенты могли применить его к другим целевым предоставлениям данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="change-data-capture-data-flow"></a>Поток данных системы отслеживания измененных данных  
 На следующем рисунке показан основной поток данных для системы отслеживания измененных данных.  
  
 ![Поток данных системы отслеживания измененных данных](../../database-engine/media/cdcdataflow.gif "Поток данных системы отслеживания измененных данных")  
  
 Источником измененных данных для системы отслеживания является журнал транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . По мере того, как в исходных отслеживаемых таблицах выполняются операции вставки, обновления и удаления, в журнал добавляются записи, описывающие эти изменения. Журнал служит входом для процесса отслеживания. Процесс считывает журнал и добавляет данные изменений в таблицу изменений, связанную с отслеживаемой таблицей. Предусмотрены функции для перечисления изменений, появляющихся в таблицах изменений в заданном диапазоне, а также для возврата данных в виде отфильтрованного результирующего набора. Отфильтрованный результирующий набор обычно используется процессом приложения для обновления представления источника во внешней среде.  
  
## <a name="understanding-change-data-capture-and-the-capture-instance"></a>Основные сведения о системе отслеживания измененных данных и экземпляре системы отслеживания  
 Прежде чем можно будет отслеживать изменения в отдельных таблицах базы данных, необходимо явно активировать систему отслеживания измененных данных в этой базе данных. Это делается с помощью хранимой процедуры [sys.sp_cdc_enable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql). После того как база данных будет активирована, с помощью хранимой процедуры [sys.sp_cdc_enable_table](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql)исходные таблицы можно определить как отслеживаемые. Если для таблицы активирована система отслеживания измененных данных, создается связанный экземпляр системы отслеживания изменений для распространения данных об изменениях в исходной таблице. Экземпляр системы отслеживания состоит из таблицы изменений и одной-двух функций запроса. Метаданные, подробно описывающие подробности конфигурации экземпляра системы отслеживания, сохраняются в таблицах отслеживания измененных метаданных `cdc.change_tables`, `cdc.index_columns` и `cdc.captured_columns`. Эти сведения можно получить с помощью хранимой процедуры [sys.sp_cdc_help_change_data_capture](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql).  
  
 Все объекты, связанные с экземпляром системы отслеживания, создаются в схеме системы отслеживания измененных данных для активированной базы данных. Именем экземпляра системы отслеживания должно быть допустимое имя объекта, уникальное для всех экземпляров системы отслеживания этой базы данных. Имя по умолчанию — \<*schema name*_*table name*> для таблицы-источника. Связанная с ним таблица изменений именуется путем добавления ключевого слова `_CT` к имени экземпляра системы отслеживания. Функция, которая используется для запроса всех изменений, именуется путем добавления к началу имени экземпляра системы отслеживания префикса `fn_cdc_get_all_changes_`. Если экземпляр отслеживания настроен для поддержки `net changes` , то `net_changes` также создается функция запроса с именем, добавляемым в **fn_cdc_get_net_changes \_ ** в качестве имени экземпляра отслеживания.  
  
## <a name="change-table"></a>Таблица изменений  
 Первые пять столбцов таблицы изменений для системы отслеживания измененных данных являются столбцами метаданных. Они предоставляют дополнительные сведения, относящиеся к регистрируемому изменению. Остальные столбцы отражают опознанные отслеживаемые столбцы исходной таблицы по имени и типу. В этих столбцах хранятся данные отслеживаемых столбцов из исходной таблицы.  
  
 Каждая операция вставки или удаления, которая была выполнена в исходной таблице, отражается как одна строка в таблице изменений. Столбцы данных в строке, отражающей результаты операции вставки, содержат значения столбов после вставки. Столбцы данных в строке, отражающей результаты операции удаления, содержат значения столбов перед удалением. Операции обновления требуется одна строка для определения значений столбца перед обновлением, и еще одна строка — для значений столбца после обновления.  
  
 Каждая строка в таблице изменений содержит также дополнительные метаданные, позволяющие интерпретировать операции изменения. Столбец __$start_lsn определяет номер LSN фиксации, который был присвоен изменению. Зафиксированный номер LSN определяет как операции изменения, которые были проведены в рамках одной транзакции, так и порядок транзакций. Столбец \_\_$seqval можно использовать для упорядочивания дополнительных изменений в этой транзакции. Столбец \_\_$operation регистрирует операцию, связанную с изменением: 1 = удаление, 2 = вставка, 3 = обновление (исходный образ), 4 = обновление (образ после операции). Столбец \_\_$update_mask — это переменная в виде битовой маски, в которой каждому отслеживаемому столбцу соответствует один бит. Для записей операций вставки и удаления все биты в маске обновления всегда будут установленными. У строк операций обновления будут установлены только биты, соответствующие измененным столбцам.  
  
## <a name="change-data-capture-validity-interval-for-a-database"></a>Период действия системы отслеживания измененных данных в базе данных  
 Период действия системы отслеживания измененных данных для базы данных — это время, в течение которого данные изменений доступны для экземпляров отслеживания. Период действия начинается с создания первого экземпляра отслеживания для таблицы базы данных и продолжается до настоящего времени.  
  
 Данные, хранящиеся в таблицах изменений, будут неуправляемо расти, если периодически и систематически не усекать эти данные. Процесс очистки системы отслеживания измененных данных отвечает за политику принудительной очистки данных по истечении срока их хранения. Прежде всего он перемещает нижнюю конечную точку периода действия в соответствии с ограничениями по времени. Затем записи таблицы изменений, у которых истек срок действия, удаляются. По умолчанию эти данные сохраняются три дня.  
  
 В верхней конечной точке по мере того, как процесс отслеживания фиксирует каждый новый пакет информации об изменениях, новые записи добавляются к `cdc.lsn_time_mapping` для каждой транзакции, для которой имеются записи в таблице изменений. В таблице сопоставлений сохраняются регистрационный номер транзакции в журнале и время фиксации транзакции (столбцы start_lsn и tran_end_time соответственно). Максимальное значение номера LSN, обнаруженное в `cdc.lsn_time_mapping`, представляет верхнюю конечную точку диапазона периода действия. Соответствующее ей время фиксации используется как базовое значение, из которого очистка данных по истечении срока хранения вычисляет новое значение нижней конечной точки.  
  
 Поскольку процесс отслеживания извлекает информацию об изменениях из журнала транзакций, имеется естественная задержка между временем, когда изменение фиксируется в исходной таблице, и временем, когда это изменение записывается в связанную таблицу изменений. Хотя эта задержка обычно мала, важно помнить, что информация об изменениях недоступна, пока процесс отслеживания не обработает соответствующие записи журнала.  
  
## <a name="change-data-capture-validity-interval-for-a-capture-instance"></a>Период действия системы отслеживания измененных данных для экземпляра отслеживания  
 Хотя обычно периоды действия для базы данных и отдельного экземпляра отслеживания совпадают, иногда это бывает не так. Период действия экземпляра отслеживания начинается, когда процесс отслеживания распознает экземпляр отслеживания и начинает записывать связанные с ним изменения в таблицу изменений. В результате, если экземпляры отслеживания создаются в разное время, каждый будет иметь свою нижнюю конечную точку. Столбец start_lsn результирующего набора, который возвращается функцией [sys.sp_cdc_help_change_data_capture](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql) , показывает текущую нижнюю конечную точку для каждого определенного экземпляра отслеживания. Когда процесс очистки очищает записи таблицы изменений, он корректирует значения start_lsn для всех экземпляров отслеживания, чтобы отразить новую нижнюю конечную точку для каждого доступного набора информации об изменениях. Корректируются только те экземпляры отслеживания, текущие значения start_lsn которых меньше, чем новая нижняя конечная точка. Со временем, если не создаются новые экземпляры отслеживания, периоды действия для всех отдельных экземпляров постепенно совпадают с периодом действия для базы данных.  
  
 Период действия важен для потребителей данных об изменениях, поскольку интервал извлечения для запроса должен полностью покрываться периодом действия системы отслеживания измененных данных для экземпляра отслеживания. Если нижняя конечная точка интервала извлечения перекрывает нижнюю конечную точку периода действия, возможна потеря информации об изменениях вследствие слишком агрессивной очистки. Если верхняя конечная точка интервала извлечения перекрывает верхнюю конечную точку периода действия, процесс отслеживания не успеет обработать данные за время, представленное интервалом извлечения, поэтому также возможна потеря информации об изменениях.  
  
 Функция [sys.fn_cdc_get_min_lsn](/sql/relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql) используется для получения текущего минимального номера LSN для экземпляра отслеживания, а функция [sys.fn_cdc_get_max_lsn](/sql/relational-databases/system-functions/sys-fn-cdc-get-max-lsn-transact-sql) — для извлечения текущего максимального номера LSN. Функции запроса системы отслеживания измененных данных завершатся ошибкой при запросе данных об изменениях, если заданный диапазон номеров LSN выйдет за пределы этих двух значений номеров LSN.  
  
## <a name="handling-changes-to-source-tables"></a>Обработка изменений исходных таблиц  
 Обработка изменений столбцов в отслеживаемых исходных таблицах — достаточно трудный вопрос для потребителей потока данных. Хотя включение системы отслеживания измененных данных в исходной таблице не препятствует такого рода DDL-изменениям, система отслеживания помогает снизить их влияние на потребителей за счет неизменности результирующих наборов, которые возвращаются через API-интерфейс, даже при изменениях структуры базовой исходной таблицы. Структура с фиксированными столбцами также отражается в базовых таблицах изменений, к которым получают доступ функции запроса.  
  
 Для поддержки работы с таблицей изменений, имеющей фиксированную структуру столбцов, процесс отслеживания, отвечающий за заполнение таблицы изменений, не учитывает новые, не определенные для отслеживания столбцы, если в исходной таблице активирована система отслеживания измененных данных. Если отслеживаемый столбец удаляется, в соответствующих записях изменений указываются значения null. Но если у существующего столбца меняется тип данных, это изменение отражается в таблице изменений, чтобы не допустить потерю данных в отслеживаемых столбцах. Процесс отслеживания также отправляет все изменения в структуре столбцов отслеживаемой таблицы в таблицу cdc.ddl_history. Потребители, желающие получить предупреждение о корректировке, которую, возможно, придется внести в нисходящие приложения, используют хранимую процедуру [sys.sp_cdc_get_ddl_history](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql).  
  
 Как правило, текущий экземпляр отслеживания продолжает сохранять свой формат, когда DDL-изменения применяются к соответствующей исходной таблице. Однако для таблицы, отражающей новую структуру столбцов, можно создать второй экземпляр отслеживания. Это позволит процессу отслеживания воспроизвести изменения одной исходной таблицы в двух таблицах изменений, имеющих разную структуру столбцов. Таким образом, в то время как одна таблица изменений будет поставлять данные в текущие рабочие приложения, вторая будет служить источником данных для среды разработки, принимающей данные нового столбца. Позволив средству отслеживания одновременно заполнять обе таблицы изменений, можно добиться перехода от одного формата к другому без потери информации. Это может случиться, когда произойдет перекрытие временных шкал двух систем отслеживания измененных данных. После завершения перехода устаревший экземпляр отслеживания можно удалить.  
  
> [!NOTE]  
>  С одной исходной таблицей одновременно можно связать не более двух экземпляров отслеживания.  
  
## <a name="relationship-between-the-capture-job-and-the-transactional-replication-logreader"></a>Связь между заданием отслеживания и агентом чтения журнала репликации транзакций  
 Логика процесса отслеживания измененных данных внедрена в расширенную хранимую процедуру [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql), во внутреннюю серверную функцию, являющуюся частью программы sqlservr.exe, а также используемую репликацией транзакций, которая считывает изменения из журнала транзакций. Если в базе данных активирована только система отслеживания измененных данных, создается задание отслеживания агента SQL Server как средство вызова хранимой процедуры sp_replcmds. Если включена также репликация, для поставки информации об изменениях обоим потребителям используется только агент чтения журнала транзакций. Такой метод значительно снижает возможность состязания, если в одной базе данных активирована как система отслеживания измененных данных, так и репликация.  
  
 Переключение между этими рабочими моделями происходит автоматически каждый раз, когда меняется состояние репликации в базе данных с активированной системой отслеживания измененных данных.  
  
> [!IMPORTANT]  
>  Оба экземпляра логики отслеживания измененных данных требуют запуска агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Основная задача процесса отслеживания заключается в просмотре журнала и записи данных столбцов и связанных с ними сведений о транзакциях в таблицы изменений системы отслеживания измененных данных. Чтобы обеспечить транзакционно согласованную границу между всеми таблицами изменений, процесс отслеживания измененных данных открывает и фиксирует собственные транзакции по каждому циклу считывания. Он обнаруживает вновь активированные таблицы системы отслеживания измененных данных и автоматически включает их в набор таблиц, в которых отслеживается изменение данных. Точно так же обнаруживается отключение системы отслеживания измененных данных, что приводит к удалению исходной таблицы из набора таблиц, в которых проводится наблюдение за изменением данных. Когда завершается обработка раздела журнала, процесс отслеживания вызывает серверную логику усечения журнала, которая использует данные процесса для определения записей журнала, подлежащих усечению.  
  
> [!NOTE]  
>  Если в базе данных было включено отслеживание измененных данных, то даже в том случае, если в качестве модели восстановления базы данных было выбрано простое восстановление, то точка усечения журнала не будет передвинута далее, пока все отслеживаемые изменения не будут собраны процессом отслеживания. Если процесс отслеживания не выполняется и присутствуют изменения, которые следует собрать, то при выполнении инструкции CHECKPOINT журнал усечен не будет.  
  
 Кроме того, процесс отслеживания используется также для ведения журнала DDL-изменений в отслеживаемых таблицах. Инструкции DDL, связанные с системой отслеживания измененных данных, создают записи в журнале транзакций базы данных каждый раз, когда удаляется база данных или таблица с активированной системой отслеживания измененных данных или добавляются, изменяются или удаляются столбцы такой таблицы. Эти записи журнала обрабатываются процессом отслеживания, который затем отправляет соответствующие DDL-события в таблицу cdc.ddl_history. Сведения о событиях DDL, влияющих на отслеживаемые таблицы, можно получить с помощью хранимой процедуры [sys.sp_cdc_get_ddl_history](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql).  
  
## <a name="change-data-capture-agent-jobs"></a>Задания агента системы отслеживания измененных данных  
 С базой данных, в которой активирована система отслеживания измененных данных, обычно связаны два задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : одно заполняет таблицы изменений, а второе отвечает за их очистку. Оба задания состоят из одного шага, который выполняет команду [!INCLUDE[tsql](../../includes/tsql-md.md)] . Вызываемая команда [!INCLUDE[tsql](../../includes/tsql-md.md)] представляет собой хранимую процедуру, определенную системой отслеживания измененных данных, которая реализует логику задания. Оба задания создаются, когда система отслеживания измененных данных активируется в первой таблице базы данных. Задание очистки создается всегда. Задание отслеживания создается, только если для базы данных не определена публикация транзакций. Задание отслеживания также создается, когда в базе данных активируется как система отслеживания измененных данных, так и репликация транзакций, а задание агента чтения журнала транзакций удаляется, поскольку в базе данных теперь отсутствуют заданные публикации.  
  
 Как задание отслеживания, так и задание очистки создаются с помощью параметров по умолчанию. Задание отслеживания запускается немедленно. Оно выполняется постоянно, обрабатывая до 1 000 транзакций за цикл просмотра с 5-секундной задержкой между циклами. Задание очистки запускается ежедневно в 02.00. Оно сохраняет записи таблицы изменений в течение 4320 минут или 3 суток, удаляя до 5000 записей в одной инструкции удаления.  
  
 Задания агента системы отслеживания измененных данных удаляются, когда система отключается в базе данных. Задание отслеживания можно также удалить, когда к базе данных добавляется первая публикация и включаются как система отслеживания измененных данных, так и репликация транзакций.  
  
 На внутреннем уровне задания системы отслеживания измененных данных создаются и удаляются хранимыми процедурами [sys.sp_cdc_add_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql) и [sys.sp_cdc_drop_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql)соответственно. Эти хранимые процедуры открыты для доступа, чтобы администратор мог управлять созданием и удалением этих заданий.  
  
 Администратор не может явно управлять применяемой по умолчанию конфигурацией заданий агента для системы отслеживания измененных данных. Для изменения параметров конфигурации по умолчанию используется хранимая процедура [sys.sp_cdc_change_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql) . Кроме того, хранимая процедура [sys.sp_cdc_help_jobs](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql) позволяет просматривать текущие параметры конфигурации. Задание отслеживания и задание очистки при запуске извлекают параметры конфигурации из таблицы msdb.dbo.cdc_jobs. Изменения значений этих параметров, выполненные с помощью хранимой процедуры [sys.sp_cdc_change_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql) , вступают в силу только после остановки и перезапуска задания.  
  
 Для остановки и запуска заданий агента системы отслеживания измененных данных используются две дополнительные хранимые процедуры: [sys.sp_cdc_start_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql) и [sys.sp_cdc_stop_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql).  
  
> [!NOTE]  
>  Запуск и остановка задания отслеживания не приводят к потере информации об изменениях. Это лишь препятствует процессу отслеживания активно просматривать журнал в поисках записей изменения и помещать их в таблицы изменений. Чтобы избежать дополнительной рабочей нагрузки в результате просмотра журнала, в период пиковой нагрузки рекомендуется остановить задание отслеживания и вновь запустить его, когда нагрузка уменьшится.  
  
 Оба задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] достаточно гибкие и настраиваемые, чтобы удовлетворить основные потребности среды системы отслеживания измененных данных. Однако в обоих случаях базовые хранимые процедуры, обеспечивающие основные функциональные возможности, открыты для доступа, чтобы сделать возможной дополнительную настройку.  
  
 Система отслеживания измененных данных не может работать правильно, когда служба ядра СУБД или служба агента SQL Server работает под учетной записью NETWORK SERVICE. В этом случае может возникать ошибка 22832.  
  
## <a name="see-also"></a>См. также:  
 [Отслеживание измененных данных (SQL Server)](../track-changes/track-data-changes-sql-server.md)   
 [Включение и отключение отслеживания измененных данных (SQL Server)](../track-changes/enable-and-disable-change-data-capture-sql-server.md)   
 [Работа с информацией об изменениях (SQL Server)](../track-changes/work-with-change-data-sql-server.md)   
 [Администрирование и наблюдение за отслеживанием измененных данных (SQL Server)](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  