---
title: Предоставление настраиваемого доступа к данным измерения (Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.dimensiondata.f1
helpviewer_keywords:
- dimensions [Analysis Services], security
- AllowedSet property
- IsAllowed property
- DeniedSet property
- user access rights [Analysis Services], dimensions
- custom dimension data access [Analysis Services]
- permissions [Analysis Services], dimensions
- DefaultMember property
- VisualTotals property
- ApplyDenied property
ms.assetid: b028720d-3785-4381-9572-157d13ec4291
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d3f91fef6410e05bfd9014f3f2db67530e83e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727409"
---
# <a name="grant-custom-access-to-dimension-data-analysis-services"></a>Предоставление настраиваемого доступа к данным измерений (Analysis Services)
  После включения доступа на чтение для куба можно задать дополнительные разрешения, которые явно разрешают или отклоняют доступ к элементам измерений (включая меры, содержащиеся в разделе "Измерение мер" со всеми мерами, использующимися в кубе). Например, для нескольких категорий торговых посредников может понадобиться задать разрешения, чтобы исключить данные для определенного бизнес-типа. На следующей иллюстрации показан эффект до и после отклонения доступа к бизнес-типу "Хранилище" в измерении "Торговый посредник".  
  
 ![Сводные таблицы с и без элементов измерения](../media/ssas-permsdimdenied.png "Сводные таблицы с и без элементов измерения")  
  
 По умолчанию наличие возможности чтения данных из куба [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] автоматически означает присутствие разрешений на чтение во всех мерах и элементах измерения, связанных с этим кубом. Хотя это поведение может быть достаточным для многих сценариев, иногда требования к безопасности вызывают более сегментированную стратегию авторизации с несколькими уровнями доступа для разных пользователей в одном измерении.  
  
 Можно ограничить доступ, выбрав, каким элементам разрешить (AllowedSet) или отклонить (DeniedSet) доступ. Это можно сделать, выделив элементы измерений или отменив их выделение, чтобы включить их в роль или исключить из нее.  
  
 Базовая безопасность измерения — самый простой способ. Нужно просто выбрать, какие атрибуты измерений и иерархии атрибутов следует включить в роль или исключить из нее. Расширенная безопасность является более сложной и требует экспертизы в многомерных скриптах. Оба подхода описываются ниже.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Не все меры или элементы измерения можно использовать в сценариях настраиваемого доступа. Если роль ограничивает доступ либо к мере или элементу по умолчанию, либо к мерам, являющимся частью выражений меры, то произойдет сбой подключения.  
  
 **Проверка наличия помех безопасности измерений: меры по умолчанию, элементы по умолчанию и меры, используемые в выражениях меры**  
  
1.  В SQL Server Management Studio щелкните правой кнопкой мыши куб и выберите команду **создать скрипт для Куба как**  |  **изменить на**  |  **новое окно редактора запросов**.  
  
2.  Найдите `DefaultMeasure`. Следует найти одну строку для куба и по одной строке для каждой перспективы. При определении безопасности измерений избегайте ограничения доступа к мерам по умолчанию.  
  
3.  Теперь выполните поиск строки `MeasureExpression`. Выражение меры — это мера на основе вычисления, где вычисление часто включает другие меры. Убедитесь, что мера, которую планируется ограничить, не используется в выражении. Можно также пойти вперед и ограничить доступ, только необходимо убедиться, что все ссылки на эту меру исключены во всем кубе.  
  
4.  Наконец, выполните поиск строки `DefaultMember`. Запишите все атрибуты, которые служат в качестве элемента атрибута по умолчанию. Не устанавливайте ограничения на эти атрибуты при настройке безопасности измерений.  
  
## <a name="basic-dimension-security"></a>Базовая безопасность измерения  
  
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , разверните узел **роли** для соответствующей базы данных в обозревателе объектов, а затем щелкните роль базы данных (или создайте новую роль базы данных).  
  
     Роль должна уже иметь доступ на чтение к кубу. Дополнительные сведения см. в разделе [Предоставление разрешений кубу или модели (службы Analysis Services)](grant-cube-or-model-permissions-analysis-services.md) .  
  
2.  В поле **данные измерения**  |  **Basic**выберите измерение, для которого настраиваются разрешения.  
  
3.  Выберите иерархию атрибутов. Могут быть доступны не все атрибуты. В списке **Иерархия атрибутов** появятся только атрибуты с параметром **AttributeHierarchyEnabled** .  
  
4.  Выберите элементы, которым следует разрешить или отклонить доступ. По умолчанию доступ разрешен (параметр **Выбрать все элементы** ). Рекомендуется сохранить значение по умолчанию, а затем очистить индивидуальные элементы, которые не должны отображаться в учетных записях пользователя и группы Windows на панели **Членства** в этой роли. Преимущество состоит в том, что новые элементы, добавляемые в будущие операции обработки автоматически доступны для пользователей, подключающихся с помощью этой роли.  
  
     Кроме того, можно **Отменить выделение всех элементов** , чтобы отозвать общий доступ, а затем выбрать, каким пользователям следует разрешить его. В будущих операциях обработки новые элементы не видны, пока вы вручную не измените безопасность, разрешив доступ к данным измерения.  
  
5.  При необходимости нажмите кнопку **Дополнительно** , чтобы включить `Visual Totals` для этой иерархии атрибута. Этот параметр повторно вычисляет статистические выражения на базе элементов, доступных в этой роли.  
  
    > [!NOTE]  
    >  При применении разрешений, которые усекают элементы измерения, автоматическое повторное вычисление суммарных итогов не выполняется. Предположим, что `All` элемент иерархии атрибута возвращает число 200 до применения разрешений. После применения разрешений, запрещающих доступ к некоторым элементам, `All` по-прежнему возвращает 200, даже несмотря на то, что значения элементов, видимые для пользователя, гораздо меньше. Чтобы избежать путаницы с потребителями Куба, можно настроить элемент как `All` совокупность только тех элементов, к которым принадлежат члены роли, а не совокупность всех элементов иерархии атрибута. Чтобы вызвать это поведение, можно включить `Visual Totals` на вкладке **Дополнительно** при настройке безопасности измерения. После включения во время выполнения запроса вместо получения заранее вычисленного значения статистическое выражение будет вычисляться. Это может заметно повлиять на производительность запроса, поэтому функцию следует использовать только при необходимости.  
  
## <a name="hiding-measures"></a>Скрытие мер  
 В среде [Предоставление настраиваемого доступа к данным ячейки (службы Analysis Services)](grant-custom-access-to-cell-data-analysis-services.md)объяснялось, что для полного скрытия всех визуальных аспектов меры, а не только данных ячейки, необходимы разрешения в элементах измерения. В этом разделе описывается, как отклонить доступ к метаданным объекта меры.  
  
1.  Прокрутите список измерений **на**  |  **базовом**измерении измерение до тех пор, пока не будут доступны измерения куба, а затем выберите **измерение мер**.  
  
2.  В списке мер снимите флажок для мер, которые не должны отображаться пользователям, подключающимся через эту роль.  
  
> [!NOTE]  
>  Сведения о том, как обнаружить меры, способные нарушить безопасность ролей, см. в разделе "Предварительные требования".  
  
## <a name="advanced-dimension-security"></a>Дополнительная безопасность измерений  
 При наличии многомерной экспертизы другим подходом является запись многомерных выражений, которые задают критерии разрешения или отклонения доступа для элементов. Щелкните **создать роль**  |  **данные измерения**  |  **Дополнительно** , чтобы предоставить скрипт.  
  
 Можно изменить конструктор многомерных выражений для записи многомерного выражения. Дополнительные сведения см. в разделе [Конструктор многомерных выражений (службы Analysis Services — многомерные данные)](../mdx-builder-analysis-services-multidimensional-data.md). На вкладке **Дополнительно** доступны следующие параметры.  
  
 **Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))  
 Выберите атрибут, безопасность которого необходимо настроить.  
  
 **Разрешенный набор элементов**  
 Свойство AllowedSet можно разрешить в набор без элементов (по умолчанию), с некоторыми или всеми элементами. Если при предоставлении доступа к атрибуту не определяются никакие элементы допустимого набора, то будет разрешен доступ ко всем элементам. Если при предоставлении доступа к атрибуту определяется конкретный набор элементов атрибута, то отображаться будут только явно разрешенные элементы.  
  
 Создание AllowedSet окажет влияние, если атрибут участвует в многоуровневой иерархии. Предположим, роль разрешает доступ к штату Вашингтон (рассмотрим сценарий, где роль предоставляет разрешения отделу продаж в штате Вашингтон компании). Пользователи, подключающиеся через эту роль, увидят только элементы в цепи запросов с предками (США) или потомками (Сиэтл и Редмонд), включающие штат Вашингтон. Поскольку другие штаты не разрешены явно, эффект будет такой, как если бы они были отклонены.  
  
> [!NOTE]  
>  При определении пустого набора ( {} ) элементов атрибута ни один из элементов атрибута не будет виден роли базы данных. Отсутствие допустимого набора не трактуется как пустой набор.  
  
 **Запрещенный набор элементов**  
 Свойство DeniedSet можно разрешить в набор без элементов, с некоторыми или со всеми элементами атрибута (по умолчанию). Если отклоненный набор содержит только определенный набор элементов атрибутов, доступ к роли базы данных отклоняется только для этих конкретных элементов, а также для потомков, если атрибут находится в многоуровневой иерархии. Рассмотрим пример отдела продаж в штате Вашингтон. Если Вашингтон находится в DeniedSet, пользователи, подключающиеся через эту роль, увидят все остальные штаты, за исключением Вашингтона и атрибутов его потомков.  
  
 Вспомните из предыдущего раздела, что отклоненный набор является исправленной коллекцией. Если в дальнейшем обработка представляет новые элементы, доступ к которым также должен быть отклонен, необходимо изменить эту роль, чтобы добавить элементы в список.  
  
 **Элемент по умолчанию**  
 Свойство DefaultMember определяет набор данных, возвращаемый клиенту в том случае, если атрибут не включается явным образом в запрос. Если атрибут не включается явным образом, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют для атрибута один из следующих элементов по умолчанию.  
  
-   Если роль базы данных определяет для атрибута элемент по умолчанию, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют данный элемент по умолчанию.  
  
-   Если роль базы данных не определяет для атрибута элемент по умолчанию, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют элемент по умолчанию, заданный для самого атрибута. Элемент по умолчанию для атрибута, если не указывается иное, является элементом `All` (если только атрибут не определяется как не включаемый в статистическое вычисление).  
  
 Предположим, роль базы данных указывает `Male` в качестве элемента по умолчанию для атрибута `Gender`. Если только в запросе явно не включен атрибут `Gender` и не указан другой элемент для такого атрибута, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] вернут набор данных, включающий в себя только клиентов мужского пола. Дополнительные сведения о настройке элементов по умолчанию см. в разделе [Определение элемента по умолчанию](attribute-properties-define-a-default-member.md).  
  
 **Активировать визуальные итоги**  
 Свойство VisualTotals указывает на то, вычисляются ли отображаемые статистические значения ячеек в соответствии со всеми значениями ячеек или только в соответствии со значениями ячеек, видимых роли базы данных.  
  
 По умолчанию свойство VisualTotals отключено (имеет значение `False` ). Указанный параметр по умолчанию позволяет добиться максимальной производительности, потому что службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] могут быстро вычислить сумму всех значений ячеек, не тратя время на выбор значений ячеек для включения в вычисление.  
  
 Однако отключение свойства VisualTotals может оказать отрицательное влияние на безопасность, если пользователь может воспользоваться статистическими значениями ячеек для вывода значений элементов атрибута, к которым роль базы данных пользователя не имеет доступа. Например, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют значения трех элементов атрибута для вычисления статистического значения ячейки. У роли базы данных есть доступ к просмотру двух из указанных трех элементов атрибута. Используя статистическое значение ячейки, член данной роли базы данных сможет вывести значение третьего элемента атрибута.  
  
 Установка для свойства VisualTotals значения `True` может устранить этот риск. Если свойство VisualTotals включено, то роль базы данных может просматривать только суммарные итоги по элементам измерения, для работы с которыми роли предоставлено разрешение.  
  
 **Проверка**  
 Щелкните, чтобы проверить синтаксис многомерных выражений, заданный на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Предоставление разрешений куба или модели &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)   
 [Предоставление настраиваемого доступа к данным ячейки &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)   
 [Предоставление разрешений на структуры и модели интеллектуального анализа данных &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)   
 [Предоставление разрешений объекту источника данных (службы Analysis Services)](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
  