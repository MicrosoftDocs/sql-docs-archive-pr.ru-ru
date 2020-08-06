---
title: Определение связи фактов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4b49a078-6848-4286-bc71-cf4862d29064
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26f8068301c424d5aea9f54e882ceb8a4dc72806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668478"
---
# <a name="defining-a-fact-relationship"></a>Определение связи фактов
  Иногда пользователи хотят иметь возможность вводить для мер измерения, которые образуются из элементов данных таблицы фактов, или создавать запросы к таблице фактов для получения специальных дополнительных сведений, таких как номера счетов или номера заказов на покупку, относящихся к конкретным фактам продаж. При определении измерения, основанного на подобных элементах таблиц фактов, оно называется *измерением фактов*. Измерения фактов также называют вырожденными измерениями. Измерения фактов полезны для группирования строк таблицы фактов, например для выбора всех строк, относящихся к определенному номеру счета. Хотя можно поместить эти сведения в отдельную таблицу измерения в реляционной базе данных, создание такой таблицы измерения не принесет пользы, потому что таблица измерения станет расти так же быстро, как и таблица фактов, что будет лишь порождать дублирование и приведет к необоснованной сложности таблицы.

 Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]позволяют указать, следует данные измерения фактов повторить в MOLAP-структуре измерения (это повышает производительность обработки запросов) или же определить измерение фактов как измерение ROLAP, чтобы сохранить место в хранилище за счет снижения производительности обработки запросов. При хранении измерения в режиме хранения MOLAP все элементы измерения, помимо хранения в секциях группы мер, хранятся в экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в крайне сжатой структуре MOLAP. При хранении измерения в режиме хранения ROLAP в структуре MOLAP сохраняется только определение измерения — сами элементы измерения запрашиваются из базовой реляционной таблицы фактов во время запроса. Выбор подходящего режима хранения зависит от того, как часто обращаются с запросами к измерению фактов, сколько строк возвращает типичный запрос, каковы производительность обработки запроса и стоимость обработки. Определение измерения как ROLAP не требует, чтобы все кубы, использующие это измерение, также хранились в режиме ROLAP. Режимы хранения для каждого измерения можно настраивать независимо.

 При определении измерения фактов можно задать связь между этим измерением и группой мер как связь фактов. К связям фактов применяются следующие ограничения:

-   Атрибут гранулярности должен быть ключевым столбцом для измерения, что образует связь «один к одному» между измерением и фактами в таблице фактов.

-   Измерение может иметь связь фактов только с одной группой мер.

> [!NOTE]
>  В измерения фактов необходимо вносить частичные обновления после каждого обновления в группе мер, на которую ссылается связь фактов.

 Дополнительные сведения см. в разделах [Связи измерений](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)и [Определение связей фактов и свойств связей фактов](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).

 В задачах этого раздела нужно добавить новое измерение куба, основанное на столбце **CustomerPONumber** таблицы фактов **FactInternetSales** . Затем предстоит указать связь фактов между этим новым измерением куба и группой мер **Продажи через Интернет** .

## <a name="defining-the-internet-sales-orders-fact-dimension"></a>Определение измерения фактов «Заказы через Интернет»

1.  В обозреватель решений щелкните правой кнопкой мыши элемент **измерения**и выберите пункт **создать измерение**.

2.  На странице **Вас приветствует мастер измерений** нажмите кнопку **Далее**.

3.  На странице **Выбор метода создания** выберите параметр **Использовать существующую таблицу** и нажмите кнопку **Далее**.

4.  Убедитесь в том, что на странице **Определение исходных сведений** выбрано представление источника данных **Adventure Works DW 2012** .

5.  В списке **Основная таблица** выберите таблицу **InternetSales**.

6.  Убедитесь в том, что в списке **Ключевые столбцы** присутствуют столбцы **SalesOrderNumber** и **SalesOrderLineNumber** .

7.  В списке **Столбец имени** выберите столбец **SalesOrderLineNumber**.

8.  Щелкните **Далее**.

9. На странице **Выбор связанных таблиц** снимите флажки для всех таблиц и нажмите кнопку **Далее**.

10. На странице **Выбор атрибутов измерения** дважды щелкните флажок в заголовке, чтобы снять все флажки. Атрибут **Номер заказа** останется выбранным, так как он является ключевым атрибутом.

11. Выберите атрибут **Номер почтового отделения заказчика** и нажмите кнопку **Далее**.

12. На странице **Завершение работы мастера** измените имя на **Подробности заказа через Интернет** и нажмите кнопку **Готово** .

13. В меню **File** (Файл) выберите команду **Save All** (Сохранить все).

14. На панели **атрибуты** конструктора измерений для измерения **Подробности заказа через Интернет** выберите **номер заказа на продажу**, а затем измените свойство **Name** в окно свойств на`Item Description.`

15. В ячейке свойства **NameColumn** нажмите кнопку обзора **(...)**. В диалоговом окне **Столбец имени** выберите **продукт** из списка **Исходная таблица** , в поле **Исходный столбец**выберите **EnglishProductName** , а затем нажмите кнопку **ОК**.

16. Добавьте атрибут **Номер заказа на покупку** к этому измерению, перетащив столбец **SalesOrderNumber** из таблицы **InternetSales** панели **Представление источника данных** на панели **Атрибуты** .

17. Измените свойство **имя** нового атрибута **номер заказа на продажу** на и `Order Number` измените свойство **OrderBy** на **Key**.

18. На панели **иерархии** создайте пользовательскую иерархию **заказы через Интернет** , содержащую `Order Number` уровни **описания элементов** и в указанном порядке.

19. На панели **Атрибуты** выберите **Подробности заказа через Интернет**, а затем просмотрите значение свойства **StorageMode** в окне свойств.

     Обратите внимание, что данное измерение хранится как измерение MOLAP. Хотя изменение режима хранения на ROLAP позволит сократить время обработки и пространство для хранения, это произойдет за счет уменьшения скорости обработки запросов. При выполнении упражнений данного учебника в качестве режима хранения будет использован MOLAP.

20. Чтобы добавить созданное измерение в куб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial, переключитесь в **Конструктор кубов**. На вкладке **Структура куба** щелкните правой кнопкой мыши панель **Измерения** и выберите команду **Добавить измерение куба**.

21. В диалоговом окне **Добавление измерения куба**выберите измерение **Подробности заказа через Интернет** и нажмите кнопку **ОК**.

## <a name="defining-a-fact-relationship-for-the-fact-dimension"></a>Определение связи фактов для измерений фактов

1.  В конструкторе кубов для куба по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial перейдите на вкладку **Использование измерений** .

     Обратите внимание, что измерение куба **Подробности заказа через Интернет** автоматически настроено как измерение, имеющее связь фактов, что отражает его уникальный значок.

2.  Нажмите кнопку обзора (**...**) в ячейке **Описание элемента** на пересечении группы мер Интернет- **продажи** и измерения **Подробности заказа через Интернет** , чтобы просмотреть свойства связи фактов.

     Будет открыто диалоговое окно **Задание связи** . Обратите внимание, что настройка свойств невозможна.

     На рисунке ниже показаны свойства связи фактов в диалоговом окне **Задание связи** .

     ![Диалоговое окно «Задание связи»](../../2014/tutorials/media/l5-factrelationship-2.gif "Диалоговое окно «Задание связи»")

3.  Щелкните **Отмена**.

## <a name="browsing-the-cube-by-using-the-fact-dimension"></a>Просмотр куба с использованием измерения фактов

1.  В меню **Сборка** выберите команду **Развернуть Analysis Services Tutorial** , чтобы внести изменения в экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и обработать базу данных.

2.  После успешного завершения развертывания перейдите в конструкторе кубов на вкладку **Браузер** , выберите куб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial и нажмите кнопку **Повторное соединение** .

3.  Очистите все меры и иерархии на панели данных, а затем добавьте измерение **Продажи через Интернет — сумма продаж** в раздел строк области данных.

4.  На панели метаданных разверните узлы **Заказчик**, **Расположение**, **География заказчика**, **Элементы**, **Все заказчики**, **Австралия**, **Квинсленд**, **Брисбейн**, **4000**, щелкните правой кнопкой мыши **Адам Пауэлл**и выберите пункт **Добавить в фильтр**.

     Фильтр, согласно которому ограничивается число заказов, возвращаемых одному клиенту, позволяет пользователю выполнить детализацию по огромной таблице фактов, не ощущая заметного падения скорости обработки запросов.

5.  Добавьте определяемую пользователем иерархию **Заказы через Интернет** из измерения **Подробности заказа через Интернет** в разделе строк панели данных.

     Обратите внимание, что соответствующие номера заказов и объемы закупок Адама Пауэла теперь отображаются на панели данных.

     На следующем рисунке показано, как выглядят измерения после выполнения ранее описанных шагов.

     ![Создание измерения Internet Sales-Sales Amount](../../2014/tutorials/media/l5-factrelationship-3.gif "Создание измерения Internet Sales-Sales Amount")

## <a name="next-task-in-lesson"></a>Следующая задача занятия
 [Определение связи «многие ко многим»](lesson-5-3-defining-a-many-to-many-relationship.md)

## <a name="see-also"></a>См. также:
 [Связи измерений](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [определяют связи фактов и свойства связей фактов](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)

