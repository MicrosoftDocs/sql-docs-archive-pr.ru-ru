---
title: Учебник. Отчет-карта (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8d831356-7efa-40cc-ae95-383b3eecf833
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b737bb3fe74eb3524f2944a7458cb4837b1aeedf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737787"
---
# <a name="tutorial-map-report-report-builder"></a>Учебник. Отчет-карта (построитель отчетов)
  Этот учебник позволяет изучить функции карты, которые можно использовать для отображения данных отчета в географическом контексте.  
  
 Карты строятся по пространственным данным, которые обычно представляют собой набор точек, линий и многоугольников. Например, многоугольник может представлять очертания страны, линия — дорогу, а точка может обозначать местоположение города. Все типы пространственных данных отображаются на отдельном слое карты в виде набора элементов карты.  
  
 Чтобы изменить внешний вид элементов карты, необходимо указать поле со значениями, сопоставляющими элементы карты с аналитическими данными из набора данных. Также можно определять на основе диапазонов данных правила, с помощью которых задается цвет, размер и другие свойства.  
  
 В этом учебнике выполняется создание отчета-карты, где отображается местоположение магазинов в округах штата Нью-Йорк.  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Что вы узнаете  
 В этом учебнике рассматриваются следующие темы:  
  
1.  [Создание карты со слоем многоугольника с помощью мастера карт](#Map)  
  
2.  [Добавление слоя точек карты для отображения местоположения магазинов](#PointLayer)  
  
3.  [Добавление слоя линий карты для отображения маршрута](#LineLayer)  
  
4.  [Добавление мозаичного фона Bing Maps](#TileLayer)  
  
5.  [Преобразование слоя в прозрачный](#Transparent)  
  
6.  [Задание различных цветов для округов в зависимости от уровня продаж](#Vary)  
  
    1.  [Построение связей между пространственными и аналитическими данными](#Relationship)  
  
    2.  [Указание правил цвета для многоугольников](#ColorRules)  
  
    3.  [Форматирование данных в цветовой шкале как различных валют](#ColorScale)  
  
    4.  [Создание новых условных обозначений](#NewLegend)  
  
    5.  [Связывание условных обозначений и правил цветов](#Associate)  
  
    6.  [Очистка цветов округов, не содержащих данных](#NoData)  
  
7.  [Добавление пользовательской точки](#CustomPoint)  
  
8.  [Центрирование представления карты](#CenterView)  
  
9. [Добавление заголовка отчета](#Title)  
  
10. [Сохранение отчета](#Save)  
  
> [!NOTE]  
>  В данном учебнике стадии работы мастера объединены в две процедуры: для создания набора данных и для создания таблиц. Пошаговые инструкции по переходу к серверу отчетов, выбору источника данных, созданию набора данных и запуску мастера см. в первом учебнике этой серии: [Учебник. Создание простого табличного отчета &#40;построитель отчетов&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Предполагаемое время для выполнения заданий данного учебника: 30 минут.  
  
## <a name="requirements"></a>Требования  
 Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-map-with-a-polygon-layer-from-the-map-wizard"></a><a name="Map"></a>1. Создание схемы с слоем многоугольников с помощью мастера карт  
 Добавление карты к отчету из галереи отчетов. На карте имеется один слой, на котором отображаются округи штата Нью-Йорк. Все округи имеют одну форму — форму многоугольника, заданную на основе пространственных данных, внедряемых в карту из галереи карт.  
  
#### <a name="to-add-a-map-with-the-map-wizard-in-a-new-report"></a>Добавление в новый отчет карты с помощью мастера карт  
  
1.  Нажмите кнопку **Пуск**, укажите пункт **программы**, выберите пункт [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Построитель отчетов**, а затем щелкните **Построитель отчетов**.  
  
     Откроется диалоговое окно Приступая к работе.  
  
    > [!NOTE]  
    >   Если диалоговое окно «Приступая к работе» не откроется, выберите команду **Создать**в меню кнопки «Построитель отчетов».  
  
2.  Убедитесь, что на панели слева выбран пункт **Отчет** .  
  
3.  На правой панели щелкните **Мастер карт**.  
  
4.  Нажмите кнопку **Создать**.  
  
5.  На странице**Выбор источника пространственных данных** убедитесь, что выбран параметр **Галерея карт** .  
  
6.  На панели «Галерея карт» разверните узел **Штаты по округам** в узле **США**и выберите **Нью-Йорк**.  
  
     На панели «Предварительный просмотр карты» отобразится карта округов штата Нью-Йорк.  
  
7.  Щелкните **Далее**.  
  
8.  На странице **Выбор пространственных данных и параметров просмотра карты** примите значения по умолчанию. По умолчанию все элементы карты из галереи карт автоматически внедряются в определение отчета.  
  
9. Щелкните **Далее**.  
  
10. На странице **Выбор визуализации карты** выберите параметр **Простая карта** и нажмите кнопку **Далее**.  
  
11. На странице **Выбор цветовой схемы и визуализации данных** выберите параметр **Отображать метки** .  
  
12. Если флажок **Одноцветная карта** установлен, снимите его.  
  
13. В раскрывающемся списке **поле данных** выберите #COUNTYNAME. На панели «Предварительный просмотр карты» в мастере отображаются следующие элементы:  
  
    -   Заголовок с текстом **Заголовок карты**.  
  
    -   На карте отображаются округи, входящие в штат Нью-Йорк, причем каждый из округов окрашен в собственный цвет, а его название выведено в наиболее подходящем месте площади этого округа.  
  
    -   Условные обозначения, содержащие заголовок и перечень элементов от 1 до 5.  
  
    -   Цветовая шкала, содержащая значения от 0 до 160 и отсутствие цвета.  
  
    -   Шкала расстояний, отображающая расстояния в километрах и милях.  
  
14. Нажмите кнопку **Готово**.  
  
     Карта добавляется в область конструктора.  
  
15. Щелкните карту, чтобы выбрать ее и отобразить панель **Слои карты**. Панель **Слои карты** показывает один слой многоугольников типа **Внедренный**. Каждый округ представляет собой элемент карты, внедренный в этот слой.  
  
    > [!NOTE]  
    >  Если панель **Слои карты** не видна, она может отображаться за пределами текущего представления. Используйте полосу прокрутки в нижней части окна в режиме конструктора для перемещения представления. Также можно снять флажок параметра **Свойства** или **Данные отчета** на вкладке **Вид** , чтобы освободить дополнительную область конструктора.  
  
16. Щелкните правой кнопкой мыши заголовок карты и выберите пункт **Свойства заголовка**.  
  
17. Замените текст заголовка текстом **Продажи по магазинам**.  
  
18. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
19. Просмотрите отчет.  
  
 В готовом к просмотру отчете отображается заголовок карты, карта и шкала расстояний. Округи находятся на слое многоугольников карты. Каждый округ представляет собой многоугольник, окрашенный в определенный цвет цветовой палитры, однако цвета не связаны с данными. Шкала расстояний отображает расстояния в километрах и в милях.  
  
 Условные обозначения и цветовая шкала не отображаются на этом этапе, поскольку отсутствуют аналитические данные, связанные с каждым из округов. Добавление аналитических данных описано в этом учебнике ниже.  
  
##  <a name="2-add-a-map-point-layer-to-display-store-locations"></a><a name="PointLayer"></a>2. Добавление слоя точек на карте для отображения расположений магазинов  
 Чтобы добавить слой точек, в котором отображается местоположение магазинов, воспользуйтесь мастером слоев карты.  
  
> [!NOTE]  
>  В этом учебнике запрос уже содержит значения данных, поэтому внешний источник данных не требуется. В связи с этим запрос получается весьма длинным. В рабочей среде запрос не будет содержать данные. Этот запрос содержит данные только в учебных целях.  
  
#### <a name="to-add-a-point-layer-based-on-a-sql-server-spatial-query"></a>Добавление слоя точек на основе пространственного запроса SQL Server  
  
1.  Переключитесь в режим конструктора.  
  
2.  Дважды щелкните карту, чтобы отобразить панель **Слой карты** . На панели инструментов нажмите кнопку **Мастер создания слоя**![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard").  
  
3.  На странице **Выбор источника пространственных данных** выберите параметр **Пространственный запрос SQL Server**и нажмите кнопку **Далее**.  
  
4.  На странице **Выбор набора данных с пространственными данными SQL Server** нажмите **Добавить новый набор данных с пространственными данными SQL Server**, затем нажмите кнопку **Далее**.  
  
5.  На странице **Выбор соединения с источником пространственных данных SQL Server** выберите существующий источник данных или перейдите к серверу отчетов и выберите источник данных.  
  
6.  Щелкните **Далее**.  
  
7.  На странице Конструирование запроса нажмите кнопку **изменить как текст**.  
  
8.  Вставьте на панель запроса следующий текст:  
  
    ```  
    Select 114 as StoreKey, 'Contoso Albany Store' as StoreName, 1125 as SellingArea, 'Albany' as City, 'Albany' as County,   
     CAST(1000000 as money) as Sales, CAST('POINT(-73.7472924218681 42.6564617079878)' as geography) AS SpatialLocation  
    UNION ALL SELECT 115 AS StoreKey, 'Contoso New York No.1 Store' AS  StoreName, 500 as SellingArea, 'New York' AS City, 'New York City' as County,  
     CAST('2000000' as money) as Sales, CAST('POINT(-73.9922069374483 40.7549638237402)' as geography) AS SpatialLocation  
    UNION ALL Select 116 as StoreKey, 'Contoso Rochester No.1 Store' as StoreName, 462 as SellingArea, 'Rochester' as City,  'Monroe' as County,    
     CAST(3000000 as money) as Sales, CAST('POINT(-77.624041566786 43.1547066024338)' as geography)  AS SpatialLocation  
    UNION ALL Select 117 as StoreKey, 'Contoso New York No.2 Store' as StoreName, 700 as SellingArea, 'New York' as City,'New York City' as County,    
      CAST(4000000 as money) as Sales, CAST('POINT(-73.9712488 40.7830603)' as geography) AS SpatialLocation  
    UNION ALL Select 118 as StoreKey, 'Contoso Syracuse Store' as StoreName, 680 as SellingArea, 'Syracuse' as City, 'Onondaga' as County,  
     CAST(5000000 as money) as Sales, CAST('POINT(-76.1349120532546 43.0610223535974)' as geography) AS SpatialLocation  
    UNION ALL Select 120 as StoreKey, 'Contoso Plattsburgh Store' as StoreName, 560 as SellingArea, 'Plattsburgh' as City,  'Clinton' as County,  
     CAST(6000000 as money) as Sales, CAST('POINT(-73.4728622833178 44.7028831413324)' as geography) AS SpatialLocation  
    UNION ALL Select 121 as StoreKey, 'Contoso Brooklyn Store' as StoreName, 1125 as SellingArea, 'Brooklyn' as City, 'New York City' as County,  
     CAST(7000000 as money) as Sales, CAST('POINT (-73.9638533447143 40.6785123489351)' as geography) AS SpatialLocation  
    UNION ALL Select 122 as StoreKey, 'Contoso Oswego Store' as StoreName, 500 as SellingArea, 'Oswego' as City, 'Oswego' as County,    
     CAST(8000000 as money) as Sales, CAST('POINT(-76.4602850815536 43.4353224527794)' as geography) AS SpatialLocation  
    UNION ALL Select 123 as StoreKey, 'Contoso Ithaca Store' as StoreName, 460 as SellingArea, 'Ithaca' as City, 'Tompkins' as County,  
     CAST(9000000 as money) as Sales, CAST('POINT(-76.5001866085881 42.4310489934743)' as geography) AS SpatialLocation  
    UNION ALL Select 124 as StoreKey, 'Contoso Rochester No.2 Store' as StoreName, 700 as SellingArea, 'Rochester' as City, 'Monroe' as County,    
     CAST(100000 as money) as Sales, CAST('POINT(-77.6240415667866 43.1547066024338)' as geography) AS SpatialLocation  
    UNION ALL Select 125 as StoreKey, 'Contoso Queens Store' as StoreName, 700 as SellingArea,'Queens' as City, 'New York City' as County,  
     CAST(500000 as money) as Sales, CAST('POINT(-73.7930979029883 40.7152781765927)' as geography) AS SpatialLocation  
    UNION ALL Select 126 as StoreKey, 'Contoso Elmira Store' as StoreName, 680 as SellingArea, 'Elmira' as City, 'Chemung' as County,  
     CAST(800000 as money) as Sales, CAST('POINT(-76.7397414783301 42.0736492742663)' as geography) AS SpatialLocation  
    UNION ALL Select 127 as StoreKey, 'Contoso Poestenkill Store' as StoreName, 455 as SellingArea, 'Poestenkill' as City, 'Rensselaer' as County,    
    CAST(1500000 as money) as Sales, CAST('POINT(-73.5626737425063 42.6940551238618)' as geography) AS SpatialLocation  
    ```  
  
9. На панели инструментов конструктора запросов нажмите кнопку **выполнить** (**!**).  
  
     Результирующий набор отображает семь столбцов: StoreKey, StoreName, SellingArea, City, округ, Sales и SpatialLocation. Эти данные представляют определенную совокупность магазинов в штате Нью-Йорк, торгующих потребительскими товарами. Каждая строка в результирующем наборе содержит идентификатор магазина, его название, торговую площадь, используемую для демонстрации товаров, город и округ расположения, общий объем продаж и пространственное положение (широту и долготу). Торговая площадь лежит в диапазоне от 455 кв. ф. до 1125 кв. ф.  
  
10. Щелкните **Далее**.  
  
     Будет создан набор данных отчета с именем DataSet1. После завершения работы с мастером можно просмотреть коллекцию полей отчета в области «Данные отчета».  
  
11. На странице **Выбор пространственных данных и параметров представления карт** убедитесь, что **пространственное поле** имеет значение, `SpatialLocation` а **тип слоя** — **Point**. Примите другие значения по умолчанию на этой странице.  
  
     На представлении карты будут отображены окружности, отмечающие местоположения магазинов.  
  
12. Щелкните **Далее**.  
  
13. Укажите тип карты, для которого отображение маркеров зависит от аналитических данных. На странице «Выбор параметров визуализации карты» выберите **Аналитическая карта с отметками**, затем нажмите **Далее**.  
  
14. На странице **Выбор набора аналитических данных** щелкните DataSet1. На новом слое точек будет отображен набор данных, содержащий аналитические и пространственные данные.  
  
15. Щелкните **Далее**.  
  
16. На странице **Выбор цветовой темы и визуализации данных** снимите флажок **Использовать цвета маркеров для визуализации данных** и установите флажок **Использовать типы маркеров для визуализации данных**.  
  
17. В **Поле данных**выберите `[Sum(SellingArea)]` , чтобы задать разные типы маркеров в зависимости от размера площади, используемой для демонстрации продуктов.  
  
18. Нажмите кнопку **Готово**.  
  
     В отчет будет добавлен слой карты. В условном обозначении будут отображены типы маркеров, зависящих от значения SellingArea.  
  
     Дважды щелкните карту, чтобы отобразить панель **Слой карты** . На панели **Слой карты** отображается новый слой PointLayer1 с источником пространственных данных типа **DataRegion**.  
  
19. Добавьте заголовок условных обозначений. Щелкните правой кнопкой мыши заголовок условных обозначений и выберите пункт **Свойства заголовка условных обозначений**.  
  
20. Удалите название и введите **Торговая площадь (в кв.ф.)**.  
  
21. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
22. Просмотрите значения по умолчанию, заданные мастером. На панели **Слои карты**щелкните правой кнопкой мыши слой точек, а затем щелкните **Правило типа маркера**.  
  
     На вкладке **Общие** маркеры указаны в порядке, в котором они отображаются в условном обозначении. На вкладке **Распространение** количество поддиапазонов равно 5. На вкладке **Условные обозначения** текст условного обозначения настроен на отображение начального и конечного значений в каждом из диапазонов.  
  
23. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
24. Просмотрите отчет.  
  
 На карте отображаются местоположения магазинов в штате Нью-Йорк. Тип маркера для каждого магазина зависит от торговой площади. Пять диапазонов площади рассчитаны автоматически.  
  
##  <a name="3-add-a-map-line-layer-to-display-a-route"></a><a name="LineLayer"></a>3. Добавление слоя линий на карте для отображения маршрута  
 С помощью мастера слоя карты добавьте слой карты, который будет показывать маршрут между двумя магазинами. В этом учебнике создается путь от трех местоположений магазинов. В бизнес-приложениях путь может представлять оптимальный маршрут между магазинами.  
  
#### <a name="to-add-a-line-layer-to-map"></a>Добавление на карту слоя линий  
  
1.  Переключитесь в режим конструктора.  
  
2.  Дважды щелкните карту, чтобы отобразить панель **Слой карты** . На панели инструментов нажмите кнопку **Мастер создания слоя**.  
  
3.  На странице **Выбор источника пространственных данных** выберите **SQL Server пространственный запрос** и нажмите кнопку **Далее**.  
  
4.  На странице **Выбор набора данных с пространственными данными SQL Server** нажмите **Добавить новый набор данных с пространственными данными SQL Server** , затем нажмите кнопку **Далее**.  
  
5.  На странице **Выбор соединения с источником пространственных данных SQL Server**выберите DataSource1 — источник данных, созданный в первой процедуре.  
  
6.  Щелкните **Далее**.  
  
7.  На странице **Конструирование запроса** нажмите кнопку **изменить как текст**. Конструктор запросов переключается в текстовый режим.  
  
8.  Вставьте на панель запроса следующий текст:  
  
    ```  
    SELECT N'Path' AS Name, CAST('LINESTRING(  
       -76.5001866085881 42.4310489934743,  
       -76.4602850815536 43.4353224527794,  
       -73.4728622833178 44.7028831413324)' AS geography) as Route  
    ```  
  
9. Щелкните **Далее**.  
  
     На карте отображается путь, соединяющий три магазина.  
  
10. На странице **Выбор пространственных данных и параметров просмотра карты** установите для параметра **Пространственное поле** значение **Маршрут** , а для параметра **Тип слоя** — значение **Линейный**. Остальные значения примите по умолчанию.  
  
     На карте отображается путь от магазина в северной части штата Нью-Йорк к магазину в южной части штата Нью-Йорк.  
  
11. Щелкните **Далее**.  
  
12. На странице **Выбор визуализации карты** нажмите **Базовая карта линий**и нажмите кнопку **Далее**.  
  
13. На странице **Выбор цветовой схемы и визуализации данных**выберите параметр **Одноцветная карта**. Путь отображается одним цветом, в соответствии с выбранной темой.  
  
14. Нажмите кнопку **Готово**.  
  
 На карте отображается новый слой линий с источником пространственных данных типа **DataSet**. В этом примере пространственные данные поступают из набора данных, но нет никаких аналитических данных, связанных с этой линией.  
  
##  <a name="4-add-a-bing-maps-tile-background"></a><a name="TileLayer"></a>4. Добавление мозаичного фона Bing Maps  
 Добавление слоя карты, который используется для отображения мозаичного фона Bing Maps.  
  
#### <a name="to-add-a-virtual-earth-tile-background"></a>Добавление мозаичного фона Virtual Earth  
  
1.  Переключитесь в режим конструктора.  
  
2.  Дважды щелкните карту, чтобы отобразить панель **Слой карты** . На панели инструментов нажмите кнопку **Добавить слой**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer").  
  
3.  Из раскрывающегося списка выберите пункт **Слой мозаики**.  
  
     Последним слоем на панели **Слой карты** является слой TileLayer1. По умолчанию мозаичный слой отображается в стиле дорожной карты.  
  
    > [!NOTE]  
    >  В мастере также можно добавить мозаичный слой на странице **Выбор пространственных данных и параметров отображения карты** . Для этого выберите **Добавить фон Bing Maps для данного представления карты**. В подготовленном к просмотру отчете мозаичный фон Bing Maps отображается в соответствии с текущими параметрами центрирования и масштабирования карты.  
  
4.  Щелкните на TileLayer1 стрелку вниз, а затем выберите **Свойства мозаичных элементов**.  
  
5.  В поле **Тип**выберите **Воздушный**. Воздушное представление не содержит текста.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="5-make-a-layer-transparent"></a><a name="Transparent"></a>5. сделать слой прозрачным  
 Чтобы настроить отображение элементов на одном слое сквозь другой слой, можно изменять порядок слоев и прозрачность каждого из слоев, пока не будет достигнут необходимый эффект.  
  
#### <a name="to-set-the-transparency-of-a-layer"></a>Изменение прозрачности слоя  
  
1.  Переключитесь в режим конструктора.  
  
2.  Дважды щелкните карту, чтобы отобразить панель **Слой карты** .  
  
3.  Щелкните на PolygonLayer1 стрелку вниз и выберите **Данные слоя**. Открывается диалоговое окно **Свойства слоя многоугольников карты** .  
  
4.  Щелкните **Видимость**.  
  
5.  В поле **Прозрачность (%)** введите значение **30**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 В области конструктора округа отображаются полупрозрачными.  
  
##  <a name="6-vary-county-color-based-on-sales"></a><a name="Vary"></a>6. Изменяйте цвет района на основе продаж  
 Все округа на слое многоугольников имеют разные цвета, поскольку обработчик отчетов автоматически назначает им значения цветов из цветовой палитры темы, которую можно выбрать на последней странице шаге мастера создания карты.  
  
 В последующих шагах укажите правило выбора цвета для связывания цветов с диапазонами значений продаж магазинов по каждому из округов. Красный, желтый и зеленый цвета обозначают относительные значения уровня продаж. Отформатируйте цветовую шкалу для отображения валюты. Отобразите диапазоны значений годовых продаж в новых условных обозначениях. Округа, в которых нет магазинов, не будут выделены цветом, чтобы показать, что для них нет связанных данных.  
  
###  <a name="6a-build-a-relationship-between-spatial-and-analytical-data"></a><a name="Relationship"></a>SP6a. Построение связей между пространственными и аналитическими данными  
 Чтобы при окраске фигур округов в соответствии с аналитическими данными границы между ними были различимы, необходимо сначала связать аналитические данные с пространственными. В этом учебнике для сопоставления используются имена округов.  
  
##### <a name="to-build-a-relationship-between-spatial-data-and-analytical-data"></a>Построение связи между пространственными и аналитическими данными  
  
1.  Переключитесь в режим конструктора.  
  
2.  Дважды щелкните карту, чтобы отобразить панель **Слой карты** .  
  
3.  Щелкните на PolygonLayer1 стрелку вниз и выберите **Данные слоя**. Открывается диалоговое окно **Свойства слоя многоугольников карты** .  
  
4.  Выберите **Аналитические данные**.  
  
5.  В раскрывающемся списке выберите DataSet1. Этот набор данных был создан мастером, когда был выбран запрос пространственных данных для округов.  
  
6.  В списке **Поля для соответствия**нажмите кнопку **Добавить**. Добавляется новая строка.  
  
7.  В поле **Из пространственного набора данных**выберите из раскрывающегося списка COUNTYNAME.  
  
8.  В поле **Из аналитического набора данных**из раскрывающегося списка выберите [County].  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Просмотрите отчет.  
  
 После выбора поля соответствия в источнике пространственных данных и аналитическом наборе данных обработчик отчета получает возможность группировать аналитические данные на основе элементов карты. У элемента карты, привязанного к данным, имеется совпадение с указанными значениями.  
  
 У всех округов, в которых имеются магазины, имеется цвет, определяемый на основе цветовой палитры стиля, выбранного в мастере.  
  
###  <a name="6b-specify-color-rules-for-polygons"></a><a name="ColorRules"></a>6B. Указание правил цвета для многоугольников  
 Чтобы создать правило, управляющее выбором различных цветов для округов в зависимости от объема продаж магазина в этом округе, необходимо указать значения диапазона, количество интервалов в отображаемом диапазоне, а также используемые цвета.  
  
##### <a name="to-specify-color-rules-for-all-polygons-that-have-associated-data"></a>Указание цветовых правил для всех многоугольников, с которыми связаны данные  
  
1.  Переключитесь в режим конструктора.  
  
2.  Щелкните на PolygonLayer1 стрелку вниз и выберите **Правило цвета многоугольника**. Открывается диалоговое окно **Свойства цветовых правил карты** . Обратите внимание, что выбран параметр цветового правила **Визуализировать данные с помощью цветовой палитры** . Этот параметр был установлен мастером.  
  
3.  Выберите **Визуализировать данные с помощью цветовых диапазонов**. Вместо палитры появляются параметры выбора начального, среднего и конечного цветов.  
  
4.  Определите значения диапазонов для продаж в округах. Из раскрывающегося списка **Поле данных**выберите элемент `[Sum(Sales)]`.  
  
5.  Чтобы валюта отображалась в тысячах, измените выражение на следующее: `=Sum(Fields!Sales.Value)/1000`  
  
6.  Измените **Начальный цвет** на **Красный**.  
  
7.  Измените **Конечный цвет** на **Зеленый**.  
  
     **Красный** представляет значения низкого уровня продаж, **Желтый** — средние, а **Зеленый** — значения высокого уровня продаж. Обработчик отчета вычисляет цветовой диапазон исходя из этих значений и параметров, выбранных на странице **Распределение** .  
  
8.  Щелкните **Распределение**.  
  
9. Выберите тип распределения **Оптимальный**. Для выражения, заданного на шаге 5, оптимальное распределение сортирует значения по поддиапазонам, обеспечивая равномерность распределения элементов по диапазонам и длин диапазонов.  
  
10. Для остальных параметров на этой странице примите значения по умолчанию. В случае выбора оптимального типа распределения, число поддиапазонов рассчитывается при выполнении отчета.  
  
11. Выберите **Условные обозначения**.  
  
12. В разделе **Параметры цветовой шкалы**выберите параметр **Показать на цветовой шкале** .  
  
13. В раскрывающемся списке **Показать в этих условных обозначениях**выберите пустую строку. Пока цветовые диапазоны будут показаны только на цветовой шкале.  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 Цветовая шкала содержит пять цветов: красный, оранжевый, желтый, желто-зеленый и зеленый. Каждый цвет представляет диапазон объемов продаж, рассчитанный автоматически на основе объемов продаж по округам.  
  
###  <a name="6c-format-the-data-in-the-color-scale-as-currency"></a><a name="ColorScale"></a>6c. Форматирование данных в цветовой шкале как различных валют  
 По умолчанию для данных задается общий формат. Для них можно применять пользовательские форматы.  
  
##### <a name="to-set-the-format-for-the-color-scale"></a>Задание формата цветовой шкалы  
  
1.  Щелкните правой кнопкой мыши цветовую шкалу и выберите пункт **Свойства цветовой шкалы**.  
  
2.  Выберите **Число**.  
  
3.  В пункте **Категория**выберите **Валюта**.  
  
4.  В поле **Десятичные разряды**введите **0**. Этот формат указывает на отсутствие десятичных разрядов для валюты.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Просмотрите отчет.  
  
 Цветовая шкала отображает годовой объем продаж в формате денежной суммы для каждого из диапазонов.  
  
###  <a name="6d-create-a-new-legend"></a><a name="NewLegend"></a>6d. Создание новых условных обозначений  
 По умолчанию все правила отображаются в первых условных обозначениях. Чтобы улучшить отображение карты, можно добавить дополнительные условные обозначения.  
  
 Чтобы изменить параметры отображения по умолчанию, выполните два следующих действия: создайте новое условное обозначение и свяжите результаты правила для слоя карты с новым условным обозначением.  
  
##### <a name="to-create-a-new-legend"></a>Создание новых условных обозначений  
  
1.  Переключитесь в режим конструктора.  
  
2.  Щелкните правой кнопкой мыши карту за пределами окна просмотра, а затем выберите пункт **Добавить условные обозначения**. Новые условные обозначения добавляются на карту в месте по умолчанию.  
  
3.  Щелкните правой кнопкой мыши условные обозначения и выберите пункт **Свойства условных обозначений**.  
  
4.  В разделе **Параметры позиции**щелкните место, где должны находиться условные обозначения относительно окна просмотра. Карта в области конструктора изменяется, показывая эффект от изменения параметров.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Щелкните **Заголовок** на условных обозначениях, чтобы выбрать их заголовок.  
  
7.  Еще раз щелкните **Заголовок** , чтобы войти в режим ввода текста. Замените текст **Заголовок** на **Продажи (в тыс.)**, а затем щелкните за пределами текста.  
  
 Условные обозначения расширяются, отображая заголовок.  
  
###  <a name="6e-associate-legend-and-color-rules"></a><a name="Associate"></a>6e. Связывание условных обозначений и правил цветов  
 Во всех условных обозначениях могут отображаться один или несколько наборов результатов правил.  
  
##### <a name="to-associate-a-legend-with-color-rules"></a>Связывание условных обозначений с цветовыми правилами  
  
1.  Дважды щелкните карту, чтобы отобразить панель **Слой карты** .  
  
2.  Щелкните на PolygonLayer1 стрелку вниз и выберите **Правило цвета многоугольника**. Открывается диалоговое окно **Свойства цветовых правил карты** .  
  
3.  Выберите **Условные обозначения**.  
  
4.  В области **Параметры цветовой шкалы**снимите флажок **Показать на цветовой шкале**.  
  
5.  В области **Параметры условных обозначений**выберите из раскрывающегося списка Legend2. Отображаются параметры текста условных обозначений. По умолчанию текст условного обозначения форматируется с помощью общей строки формата [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Число 0 в «N0» указывает на отсутствие десятичных знаков.  
  
6.  В **тексте условных обозначений**используйте следующий формат, чтобы указать валюту без десятичных знаков:`#FROMVALUE {C0} - #TOVALUE {C0}`  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     В области конструктора условные обозначения отображают цветовые диапазоны с образцами данных, отформатированных в качестве валюты.  
  
8.  Просмотрите отчет.  
  
 Округи, в которых имеются связанные магазины и данные о продажах, отображаются в соответствии с правилами цвета. Округи, в которых отсутствуют продажи, отображаются без цвета.  
  
###  <a name="6f-change-color-for-counties-with-no-data"></a><a name="NoData"></a>6f. Изменение цветов округов, не содержащих данных  
 Можно настроить параметры отображения по умолчанию для всех элементов карты на слое. Правила цвета имеют больший приоритет, чем эти параметры отображения.  
  
##### <a name="to-set-the-display-properties-for-all-elements-on-a-layer"></a>Задание свойств отображения для всех элементов слоя  
  
1.  Переключитесь в режим конструктора.  
  
2.  Дважды щелкните карту, чтобы отобразить панель **Слой карты** .  
  
3.  Щелкните на PolygonLayer1 стрелку вниз и выберите **Свойства многоугольника**. Открывается диалоговое окно **Свойства многоугольников карты** . Параметры отображения, заданные в этом диалоговом окне, применяются ко всем многоугольникам на слое до применения параметров отображения, заданных на основе правил.  
  
4.  Нажмите кнопку **Заливка**.  
  
5.  Убедитесь, что выбран стиль заливки **Сплошная.** Градиенты и узоры применяются ко всем цветам.  
  
6.  В поле **Цвет**нажмите стрелку вниз и выберите **Светло-синий металлик**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Просмотрите отчет.  
  
 Округи, не имеющие связанных данных, отображаются синим цветом. Цвета в диапазоне от **Красного** по **Зеленый** в соответствии с заданными правилами цвета используются для отображения только тех округов, для которых имеются связанные аналитические данные.  
  
##  <a name="7-add-a-custom-point"></a><a name="CustomPoint"></a>7. Добавление пользовательской точки  
 Чтобы создать представление нового магазина, который еще не построен, укажите точку и воспользуйтесь типом маркера **Вешка** .  
  
#### <a name="to-add-a-custom-point"></a>Добавление пользовательской точки  
  
1.  Переключитесь в режим конструктора.  
  
2.  Дважды щелкните карту, чтобы отобразить панель **Слой карты** . На панели инструментов нажмите кнопку **Добавить слой**, а затем выберите **Слой точек**.  
  
     На карту добавляется новый слой точек. По умолчанию он имеет тип пространственных данных **Внедренный**.  
  
3.  Щелкните стрелку рядом с PointLayer2 и выберите **Добавить точку**.  
  
4.  Переместите указатель над окном просмотра карты. Курсор превращается в перекрестье.  
  
5.  Щелкните место на карте, где нужно добавить точку. В этом учебнике щелкните расположение в округе рядом с началом маршрута. Точка, помеченная окружностью, добавляется на слой в месте щелчка. По умолчанию точка будет выбрана.  
  
6.  Щелкните правой кнопкой мыши добавленную точку и выберите пункт **Свойства внедренной точки**.  
  
7.  Выберите параметр **Переопределить свойства точки для этого слоя**. В диалоговом окне появляются дополнительные страницы. Значения, заданные на этих страницах, имеют более высокий приоритет, чем параметры отображения, заданные для слоя или цветовых правил.  
  
8.  Нажмите кнопку **Маркер**.  
  
9. В поле **Тип маркера**выберите **Звезда**.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Просмотрите отчет.  
  
 Новая добавленная точка отображается, как **Звезда**.  
  
#### <a name="to-add-a-label-for-the-custom-point"></a>Добавление метки для пользовательской точки  
  
1.  Переключитесь в режим конструктора.  
  
2.  Щелкните правой кнопкой мыши добавленную точку и выберите параметр **Свойства внедренной точки**.  
  
3.  Щелкните **Метки**.  
  
4.  В поле **Текст метки**введите **Новый магазин**.  
  
5.  В поле **Размещение**выберите **Сверху**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Просмотрите отчет.  
  
 Метка помещается над местоположением магазина.  
  
##  <a name="center-the-map-view"></a><a name="CenterView"></a>Центрирование представления карт  
 Измените параметры центрирования и масштабирования окна просмотра карты.  
  
#### <a name="to-change-the-viewport"></a>Изменение области просмотра  
  
1.  Щелкните правой кнопкой мыши область просмотра и выберите пункт **Свойства окна просмотра карты**.  
  
2.  Нажмите кнопку **Центрирование и масштабирование**.  
  
3.  Убедитесь, что установлен флажок **Задать центр представления и масштаб** .  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Щелкните окно просмотра карты и перетащите центр области просмотра в необходимое местоположение.  
  
6.  Используйте колесо прокрутки на мыши, чтобы изменить масштаб области просмотра.  
  
7.  Просмотрите отчет.  
  
 В режиме конструктора при отображении карты в отображаемой области и в представлении будут использоваться образцы данных. В подготовленном для просмотру отчете представление карты будет центрировано по выбранному представлению.  
  
##  <a name="add-a-report-title"></a><a name="Title"></a>Добавление заголовка отчета  
  
#### <a name="to-add-a-report-title"></a>Добавление заголовка отчета  
  
1.  В области конструктора щелкните ссылку **Щелкните, чтобы добавить заголовок**.  
  
2.  Введите фразу **Продажи в магазинах Нью-Йорка** и щелкните вне текстового поля.  
  
 Данный заголовок появится в верхней части отчета. Элементы, расположенные в верхней части текста отчета, при отсутствии определенного верхнего колонтитула страницы служат заголовком отчета.  
  
##  <a name="save-the-report"></a><a name="Save"></a>Сохранение отчета  
  
#### <a name="to-save-the-report"></a>Сохранение отчета  
  
1.  Переключитесь в режим конструктора.  
  
2.  Нажмите кнопку «Построитель отчетов» и выберите **Сохранить как**.  
  
3.  В поле **Имя**введите **Продажи магазинов в Нью-Йорке**.  
  
 Выберите команду **Сохранить**.  
  
## <a name="next-steps"></a>Next Steps  
 На этом пошаговое руководство по добавлению карты в отчет завершается.  
  
 Дополнительные сведения см. в статьях [Maps &#40;построитель отчетов и SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) и запись блога [картографическую корректировка пространственных данных для SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=152771) на blogs.MSDN.com.  
  
 Дополнительные руководства см. в [учебниках &#40;построитель отчетов&#41;](report-builder-tutorials.md).  
  
## <a name="see-also"></a>См. также:  
 [Учебники &#40;построитель отчетов&#41;](report-builder-tutorials.md)   
 [построитель отчетов в SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)   
 [Мастера карт и мастер слоев карт &#40;построитель отчетов и SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)   
 [Изменение параметров отображения многоугольников, линий и точек с помощью правил и аналитических данных (построитель отчетов и службы SSRS)](report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  