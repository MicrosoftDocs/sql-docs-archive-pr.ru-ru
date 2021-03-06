---
title: Выделение исключений (средства анализа таблиц для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97e8197fc76f431cf9740c5c6fbd7ac44d8204a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740592"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a>Выделение исключений (средства анализа таблиц для Excel)
  ![Кнопка «Выделение исключений» на ленте](media/tat-highlightex.gif "Кнопка «Выделение исключений» на ленте")  
  
 Иногда данные могут содержать значения довольно необычная. Например, возраст владельца дома может быть равен 5 годам. Эти значения, часто называемые *выбросами*, могут быть неправильными из-за ошибки ввода данных или могут указывать на необычные тенденции. Как бы то ни было, исключения могут снизить качество анализа. Средство **выделение исключений** помогает найти эти значения и просмотреть их для дальнейших действий.  
  
 Средство **выделение исключений** может работать с целым диапазоном данных в таблице данных Excel или можно выбрать только несколько столбцов. Можно также настроить порог, управляющий изменчивостью данных, чтобы обнаруживать больше или меньше исключений.  
  
 По завершении анализа это средство создает лист, содержащий сводный отчет о количестве выбросов, найденных в каждом проанализированном столбце. Кроме того, это средство выделяет исключения в исходной таблице данных. Поскольку это средство анализирует общие тренды, оно может обнаружить, что большая часть значений в строке отвечает условиям, и выделить только одну ячейку в этой строке. В приведенном выше примере хомеовнер может быть выделен только столбец **Age** .  
  
 Также можно изменить **пороговое значение исключения** в **сводном отчете**. Это значение указывает вероятность того, что конкретная ячейка содержит ненормальное значение. Таким образом, если увеличить значение, то в качестве выбросов будет выделено меньшее число значений. И наоборот, при понижении порога появляется больше выделенных ячеек.  
  
## <a name="using-the-highlight-exceptions-tool"></a>Использование средства «Выделение исключений»  
  
1.  Откройте таблицу Excel и выберите **выделить исключения**.  
  
2.  Укажите столбцы для анализа.  
  
3.  Нажмите кнопку **Запустить**.  
  
4.  Откройте лист с названием \<table name> выбросы, чтобы просмотреть сводку обнаруженных выбросов.  
  
5.  Чтобы изменить число выделений, щелкните стрелки вверх и вниз в строке **порог исключения** в **отчете выделение исключений**.  
  
### <a name="requirements"></a>Требования  
 Если какие-либо столбцы содержат правильные значения, которые будут полезными при прогнозировании других строк, можно включить их в анализ. Тем не менее необходимо снять выбор столбцов, имеющих отсутствующие или нулевые значения.  
  
 Так как все выделенные столбцы используются для создания общего шаблона, не следует выбирать входные столбцы, в которых заведомо содержится некачественная информация, например:  
  
-   столбцы, содержащие уникальные значения, такие как идентификаторы;  
  
-   столбцы с высоким содержанием неверных значений;  
  
-   столбцы со многими отсутствующими значениями;  
  
     Обратите внимание, что в некоторых случаях целесообразно включить входные столбцы с большим количеством отсутствующих значений. Например, если значение поля адреса всегда отсутствует, когда клиент покупает розничный продавец, алгоритм интеллектуального анализа данных может использовать эти сведения для распознавания других аналогичных клиентов. Необходимо определить по отдельности, нет ли данных, пропуская или потому, что состояние Missing является осмысленным.  
  
-   столбцы, которые вряд ли полезны для создания закономерности. Например, столбцы, имеющие одинаковые значения в каждой строке, не добавляют информации, которая могла бы быть полезной в построении закономерностей.  
  
## <a name="understanding-the-highlight-exceptions-report"></a>Основные сведения об отчете средства выделения исключений  
 При нажатии кнопки **запустить**средство выполняет три действия:  
  
-   создает структуру интеллектуального анализа на основе текущих данных в таблице;  
  
-   создает новую модель интеллектуального анализа данных, используя алгоритм кластеризации [!INCLUDE[msCoName](../includes/msconame-md.md)];  
  
-   создает прогнозирующий запрос на основе закономерностей для поиска невозможных значений в листе.  
  
 Начальное значение для порогового значения исключения всегда равно 75 и означает, что в вычисляемом здесь алгоритме имеется 75%-я вероятность, что выделенные данные неправильны. Это средство автоматически задает указанное пороговое значение для начального прохода анализа, но это значение можно изменить в отчете.  
  
 Средство **выделение исключений** выделяет ячейки в исходной таблице данных, которые являются подозрительными. Темная подсветка означает, что строка требует внимания. Светлая подсветка означает, что значение в этой конкретной ячейке рассматривается как подозрительное. Если пороговое значение изменяется для исключений, то соответствующим образом изменяются выделенные значения.  
  
 На сводной диаграмме показано число ячеек в каждом столбце, значения в которых превышают порог исключений.  
  
## <a name="related-tools"></a>Дополнительные средства  
 При очистке или просмотре данных в процессе подготовки к интеллектуальному анализу можно также использовать функции просмотра данных клиента интеллектуального анализа данных для Excel. Эта надстройка предоставляет дополнительные средства для поиска выбросов, переразметки данных и просмотра их распределения. Дополнительные сведения о средствах просмотра данных в клиенте интеллектуального анализа данных для Excel см. в разделе [Просмотр и очистка данных](exploring-and-cleaning-data.md).  
  
 Средство **выделение исключений** использует [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм кластеризации. Модель кластеризации определяет группы строк со сходными характеристиками. Клиент интеллектуального анализа данных для Excel предоставляет окно **обзора** , которое использует графы и профили характеристик для просмотра моделей интеллектуального анализа данных, созданных кластеризацией. Сведения о том, как просмотреть модель кластеризации, созданную с помощью средства " **выделение исключений** ", см. в разделе [Обзор моделей (клиент интеллектуального анализа данных для Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).  
  
 Дополнительные сведения об алгоритме кластеризации [!INCLUDE[msCoName](../includes/msconame-md.md)] см. в разделе «Алгоритм кластеризации (Майкрософт)» в электронной документации к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Средства анализа таблиц для Excel](table-analysis-tools-for-excel.md)  
  
  
