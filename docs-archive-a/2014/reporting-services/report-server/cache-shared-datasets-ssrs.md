---
title: Общие наборы данных в кэше (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4acb1bbe-1c04-4979-b893-dc1b1c5039b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b08149b075ae3fd267baf2dad0ca342457958c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665832"
---
# <a name="cache-shared-datasets-ssrs"></a>Общий набор данных в кэше (служба SSRS)
  Результаты запроса для общего набора данных могут быть скопированы в кэш, чтобы предоставить согласованные данные для нескольких отчетов и улучшить время ответа для запроса к набору данных. Как и отчеты, общие наборы данных можно настраивать как подлежащие кэшированию при первом использовании или согласно расписанию.  
  
 Общий набор данных может быть включен в несколько отчетов или задан как часть определений компонентов. Кэширование общего набора данных позволяет предоставить согласованный набор данных для всех использующих его отчетов, а также уменьшить количество запросов к внешнему источнику набору данных.  
  
 В следующем списке приведены примеры, когда следует кэшировать общий набор данных.  
  
-   Выполнение запроса требует значительного времени.  
  
-   Запрос принимает параметры, но чаще всего количество сочетаний параметров невелико. Для каждого сочетания параметров создаются кэшированные результаты запроса.  
  
-   Запрос запускается в прогнозируемое время дня, недели или месяца.  
  
-   Запрос запускается в результате ссылки на общий набор данных в отчете, который доставляется по электронной почте, и велика вероятность того, что за короткий промежуток времени эту ссылку щелкнут многие пользователи.  
  
-   В следующем списке приведены примеры, когда не следует кэшировать общий набор данных.  
  
-   Результаты запроса должны всегда содержать самые последние данные.  
  
-   Запрос выполняется быстро.  
  
-   Запрос выполняется редко.  
  
-   Запрос принимает параметры, количество сочетаний параметров велико, и ни одно сочетание не является более вероятным, чем другие.  
  
-   Источник данных, на котором основан общий набор данных, имеет учетные данные, предоставляемые с помощью приглашения или встроенной безопасности Windows.  
  
-   Фильтр общего набора данных или запрос содержит выражение со ссылкой на пользователя глобальной коллекции.  
  
 Если пользователь выбирает значения параметров отчета, которые отличаются от значений по умолчанию, указанных для кэшированного результирующего набора, то запрос к набору данных выполняется активно и для этого запроса не используются кэшированные результаты.  
  
## <a name="caching-shared-datasets"></a>Кэширование общих наборов данных  
 Чтобы включить кэширование для общего набора данных, необходимо выбрать параметр кэширования для этого общего набора данных. После включения кэширования результаты запроса для общего набора данных копируются в кэш при первом использовании. Если общий набор данных имеет параметры, то каждое сочетание параметров создает новую запись в кэше.  
  
 До тех пор пока результаты запроса для конкретного сочетания параметров находятся в кэше, каждый отчет, запускаемый на обработку и включающий ссылку на общий набор данных с теми же значениями параметров, будет использовать кэшированные данные.  
  
 Можно указать, как долго данные должны храниться в кэше до истечения срока их действия. Дополнительные сведения см. в разделе [Страница "Кэширование", "Общие наборы данных" (диспетчер отчетов)](../caching-page-shared-datasets-report-manager.md).  
  
## <a name="preloading-the-cache"></a>Предварительная загрузка кэша  
 Можно произвести предварительную загрузку кэша путем создания плана обновления кэша. План обновления позволяет указать, как часто следует обновлять кэш с помощью расписания элемента или общего расписания. Чтобы избежать появления нескольких записей кэша для одного и того же элемента, заданное расписание должно предусматривать достаточное количество времени для обработки запроса по отношению к внешнему источнику данных. Например, если для выполнения запроса требуется 20 минут, то расписание обновления должно предусматривать интервал больше 20 минут. Дополнительные сведения см. в разделе [Schedules](../subscriptions/schedules.md).  
  
 При создании плана обновления кэша для общего набора данных применяются следующие условия.  
  
-   Для общего набора данных должно быть включено кэширование.  
  
-   В общем источнике данных, от которого зависит общий набор данных, не могут использоваться учетные данные, предоставляемые с помощью приглашения или встроенной безопасности Windows.  
  
-   Если общий набор данных имеет параметры, следует указать статические значения по умолчанию для каждого параметра, который не отмечен как предназначенный только для чтения. Для параметров, допускающих только чтение, всегда используются значения по умолчанию. Чтобы кэшировать общий набор данных для нескольких сочетаний параметров, необходимо создать отдельный план обновления кэша для каждого сочетания значений. Параметры не могут содержать ссылки на другие наборы данных.  
  
-   Каждый план обновления кэша связан только с одним общим набором данных или отчетом.  
  
-   Необходимо иметь разрешения ReadPolicy и UpdatePolicy на общий набор данных.  
  
 Планы обновления кэша применяются и к общим наборам данных, и к отчетам. Дополнительные сведения см. в разделе [Параметры обновления кэша (диспетчер отчетов)](../cache-refresh-options-report-manager.md).  
  
## <a name="conditions-that-cause-cache-expiration"></a>Условия, приводящие к истечению срока кэша  
 Кэш общего набора данных может стать недействительным при следующих условиях.  
  
-   Истек срок действия одного из условий расписания. Происходит очистка кэша по времени ожидания, или истекает срок хранения.  
  
-   Удаляется общее расписание.  
  
-   В общее расписание вносятся изменения. Общие расписания могут быть приостановлены, что также влияет на истечение срока действия кэша.  
  
-   Изменяется определение запроса для общего набора данных.  
  
-   Изменяются учетные данные для общего источника данных, от которого зависит общий набор данных.  
  
-   Изменяются параметры кэша для общего набора данных.  
  
-   Изменяются значения по умолчанию для допускающих только чтение параметров общего набора данных.  
  
-   Изменяются фильтры, которые являются частью определения общего набора данных.  
  
-   Общий набор данных удаляется с сервера отчетов. При удалении общего набора данных удаляются также связанные с ним кэшированные копии и планы обновления кэша.  
  
 Внесение изменений в планы обновления кэша для общих наборов данных не затрагивает отчеты, которые уже обрабатываются. Изменение плана обновления кэша затрагивает только будущие запуски отчетов, которые ссылаются на рассматриваемый общий набор данных.  
  
## <a name="see-also"></a>См. также:  
 [Управление общими наборами данных](../report-data/manage-shared-datasets.md)  
  
  
