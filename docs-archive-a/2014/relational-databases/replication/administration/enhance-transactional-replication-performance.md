---
title: Повышение производительности репликации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe802796b129ff9bdb50e5dea13e1fe98beee269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750771"
---
# <a name="enhance-transactional-replication-performance"></a>Повышение производительности репликации транзакций
  После рассмотрения общих рекомендаций в отношении производительности, описываемых в разделе [Повышение общей производительности репликации](enhance-general-replication-performance.md), необходимо проанализировать следующие дополнительные области, относящиеся к репликации транзакций.  
  
## <a name="database-design"></a>Структура базы данных  
  
-   Минимизируйте размер транзакций в структуре приложения.  
  
     По умолчанию репликация транзакций распространяет изменения в соответствии с границами транзакций. Если транзакции имеют небольшой размер, то маловероятно, что агенту распространителя придется повторно пересылать транзакцию вследствие перебоев в сети. Если агенту потребуется переслать транзакцию, то количество отсылаемых данных будет меньшим.  
  
## <a name="distributor-configuration"></a>Настройка распространителя  
  
-   Настройте распространитель на выделенном сервере.  
  
     Нагрузку, связанную с обработкой на издателе, можно снизить, настроив удаленный распространитель. Дополнительные сведения см. в разделе [Configure Distribution](../configure-distribution.md).  
  
-   Установите надлежащий размер для базы данных распространителя.  
  
     Проверьте репликацию с типовой нагрузкой системы, чтобы определить пространство, необходимое для хранения команд. Убедитесь в том, что база данных имеет достаточный размер для хранения команд без частого автоматического увеличения размера. Дополнительные сведения об изменении размера базы данных см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="publication-design"></a>Разработка публикации  
  
-   Реплицируйте выполнение хранимых процедур при выполнении пакетных обновлений опубликованных таблиц.  
  
     При наличии пакетов обновлений, которые эпизодически воздействуют на большое количество строк на подписчике, следует рассмотреть возможность обновления опубликованной таблицы с использованием хранимой процедуры и опубликовать результаты выполнения этой хранимой процедуры. Вместо отправки обновления или удаления для каждой изменяемой строки агент распространителя выполняет эту процедуру на подписчике с теми же значениями параметров. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Распределение статей по нескольким публикациям.  
  
     Если невозможно использовать параметр **-SubscriptionStreams** (описываемый далее в данном разделе), необходимо рассмотреть возможность создания нескольких публикаций. Распределение статей между этими публикациями позволяет репликации параллельно применять изменения на подписчиках.  
  
## <a name="subscription-considerations"></a>Вопросы использования подписок  
  
-   Если на одном и том же издателе имеется несколько публикаций, используйте независимые агенты вместо общих агентов (эта конфигурация устанавливается по умолчанию в мастере создания публикаций).  
  
-   Выполняйте агенты в непрерывном режиме вместо запуска по часто повторяющимся расписаниям.  
  
     Настройка агентов на непрерывное выполнение вместо создания часто выполняемых расписаний (например, ежеминутных) позволяет повысить производительность репликации за счет экономии времени на запусках и остановках агента. Если агент распространителя настроен на непрерывную работу, изменения пересылаются на другие серверы, соединенные в топологии, с малой задержкой. Дополнительные сведения см. в разделе:  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]: [Указание расписаний синхронизации](../specify-synchronization-schedules.md)  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a>Параметры агента распространителя и агента чтения журнала  
  
-   Чтобы устранить случайную неоднократную узкие места, используйте параметр **-MaxCmdsInTran** для агент чтения журнала.  
  
     Параметр **-MaxCmdsInTran** указывает максимальное количество инструкций, сгруппированных в транзакцию, когда читатель журнала записывает команды в базу данных распространителя. Использование этого параметра позволяет агенту чтения журнала и агенту распространителя разделять большие транзакции (состоящие из множества команд) на издателе на несколько меньших транзакций при применении команд на подписчике. Задание этого параметра может снизить вероятность состязаний на распространителе и уменьшить задержку при передаче данных между издателем и подписчиком. Поскольку исходная транзакция применяется меньшими по размеру блоками, подписчик может получить доступ к строкам большой логической транзакции издателя до завершения исходной транзакции, разбивая строгую атомарность транзакции. По умолчанию установлено значение **0**, сохраняющее границы транзакции издателя. Этот параметр не применим для издателей Oracle.  
  
    > [!WARNING]  
    >  Параметр `MaxCmdsInTran` не предназначен для постоянного использования. Он существует для разрешения ситуаций, в которых случайно было запущено большое количество операций DML в рамках одной транзакции (из-за чего возникают задержки при распределении команд до тех пор, пока вся транзакция не будет находиться в базе данных распространителя, поскольку удерживаются блокировки и т. д.). Если такая ситуация возникает регулярно, следует проанализировать приложения и найти пути уменьшения размера транзакции.  
  
-   Используйте параметр **-SubscriptionStreams** для агент распространения.  
  
     Параметр **-SubscriptionStreams** может значительно увеличить общую пропускную способность репликации. Он позволяет нескольким соединениям с подписчиком параллельно применять пакеты изменений, при этом сохраняя многие свойства транзакций, характерные для использования одиночного потока. Если одному из соединений не удается осуществить выполнение или фиксацию, все подключения прекратят выполнение текущего пакета, и агент будет использовать одиночный поток для повторных попыток выполнения поврежденных пакетов. Перед завершением фазы выполнения повторной попытки могут существовать временные несоответствия транзакций на подписчике. После успешной фиксации всех поврежденных пакетов подписчик возвращается в состояние согласованности транзакций.  
  
     Значение для этого параметра агента можно указать с помощью ** \@ subscriptionstreams** [SP_ADDSUBSCRIPTION &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).  
  
-   Увеличьте значение параметра **-ReadBatchSize** для агента чтения журнала.  
  
     Агент чтения журнала и агент распространителя поддерживают разные размеры пакетов для операций чтения и фиксации транзакций. По умолчанию размер пакетов составляет 500 транзакций. Агент чтения журнала считывает заданное количество транзакций из журнала независимо от того, отмечены они для репликации или нет. Когда в базу данных публикации записано большое количество транзакций и только небольшое подмножество этих транзакций помечено для репликации, следует использовать параметр **-ReadBatchSize** для увеличения размера пакета, считываемого агентом чтения журнала. Этот параметр не применим для издателей Oracle.  
  
-   Увеличьте значение параметра **-CommitBatchSize** для агента распространителя.  
  
     Фиксация набора транзакций требует постоянного объема служебных операций. При выполнении менее частых фиксаций большего количества транзакций постоянный объем служебных операций приходится на больший объем данных. Однако выгода от увеличения значения этого параметра невелика, поскольку затраты на применение изменений управляются другими факторами, например максимальной пропускной способностью системы ввода-вывода диска, на котором хранится журнал. Кроме того, необходимо найти баланс между преимуществами и недостатками: в случае любого сбоя, приводящего к перезапуску агента распространителя, необходимо выполнить откат и повторное применение большого количества транзакций. В сетях с низкой надежностью более низкое значение параметра может уменьшить количество сбоев и число транзакций, для которых необходимо выполнить откат и повторное применение в случае сбоя.  
  
-   Уменьшите значение параметра **-PollingInterval** для агента чтения журнала.  
  
     Параметр **-PollingInterval** задает частоту опроса журнала транзакций опубликованной базы данных для определения транзакций, подлежащих репликации. Значение по умолчанию — 5 секунд. При уменьшении этого значения журнал опрашивается чаще, что может привести к меньшей задержке доставки транзакций из базы данных публикации в базу данных распространителя. Однако необходимо найти баланс между уменьшением задержки и ростом нагрузки на сервер с увеличением частоты опросов.  
  
 Параметры агента могут задаваться в профилях агента или в командной строке. Дополнительные сведения см. в разделе:  
  
-   [Работа с профилями агента репликации](../agents/replication-agent-profiles.md)  
  
-   [Просмотр и изменение параметров командной строки агента репликации (среда SQL Server Management Studio)](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)  
  
  