---
title: Представление конструктора отчетов (построитель отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10440"
- "10426"
- "10439"
- "10434"
- "10438"
- "10436"
helpviewer_keywords:
- reports, creating
- user interface
- overview of Report Builder
ms.assetid: 1544472c-2803-448d-af52-e901cb457a00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0aef92d69539ffc74900c069630cb2dc546d28c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656198"
---
# <a name="report-design-view-report-builder"></a>Представление конструктора отчетов (построитель отчетов)
  Окно построителя отчетов предназначено для упрощения организации ресурсов отчета и быстрого построения нужных отчетов. В центре окна расположена область конструктора, в верхней части — лента, а слева, внизу и справа находятся панели «Данные отчета», «Группирование» и «Свойства», а также галерея элементов отчетов. В области конструктора добавляются и организовываются элементы отчета. Лента распределяет традиционные элементы меню по категории, что упрощает их поиск и использование. Панели позволяют добавлять, выбирать и организовать ресурсы отчета и изменить свойства элементов отчета.  
  
 ![ReportDesignView](../media/reportdesignview.gif "ReportDesignView")  
  
##  <a name="the-ribbon"></a><a name="Ribbon"></a>Лента  
 Лента предназначена для быстрого поиска команд, необходимых для выполнения задачи. Команды организованы в логические группы, которые собраны вместе на вкладках. Каждая вкладка связана с типом активности, таким как вставка элементов отчета или форматирование текста.  
  
 В представлении конструктора отчетов лента разделена на следующие вкладки: "Главная", "Вставка" и "Вид". Если невозможно найти задачу на ленте, некоторые группы ленты имеют связанное диалоговое окно, которое открывается, если щелкнуть стрелку внизу слева от группы. Невозможно свернуть и удалить ленту или заменить ее панелями инструментов и меню.  
  
 В режиме выполнения на ленте имеется только одна вкладка, **выполните**.  
  
### <a name="home-tab"></a>Вкладка «Главная»  
 Вкладка «Главная» — это коллекция часто применяемых команд, связанных с внешним видом элементов отчета. На вкладке «Корневая папка» можно получить доступ к командам, связанным с выполнением, шрифтом, параграфом, границами, числами и макетом. Если щелкнуть элемент на этой вкладке, то в области конструктора выбранный элемент изменится. При нажатии кнопки **выполнить**отчет готовится к просмотру в формате HTML, что позволит увидеть, как содержимое отчета будет отображаться при публикации, а вместо вкладки Главная появится вкладка выполнить. Вкладка Главная — это вкладка по умолчанию, отображаемая при первом создании отчета.  
  
### <a name="insert-tab"></a>Вкладка «Вставить»  
 Вкладка «Вставить» — это коллекция команд, часто используемых для добавления элементов в отчет. На вкладке «Вставить» можно использовать мастера для добавления таблицы, матрицы, диаграммы или карты. Можно также добавить эти элементы без использования мастера и добавить другие элементы отчета, например sparkline-графики, индикаторы, текстовые поля, изображения, линии, прямоугольники, вложенные отчеты и колонтитулы.  
  
 При выборе **элементов отчета** на вкладке Вставка открывается Галерея элементов отчетов. Можно выполнить поиск элементов отчетов, сохраненных на сервере отчетов. Дополнительные сведения см. в разделе [Элементы отчета (построитель отчетов и службы SSRS)](../report-parts-report-builder-and-ssrs.md).  
  
 После добавления элемента построитель отчетов автоматически переключается назад на вкладку «Корневая папка».  
  
### <a name="view-tab"></a>Вкладка «Вид»  
 Вкладка «Вид» — это коллекция команд, управляющих содержимым окна построителя отчетов. Можно изменить параметры отображения для линейки и панелей «Группирование», «Данные отчета» и «Свойства».  
  
### <a name="run-tab"></a>Вкладка запуска  
 При нажатии кнопки **выполнить** на вкладке Главная в средстве просмотра HTML-страниц запускается предварительный просмотр отчета, а вместо вкладки Главная отображается вкладка выполнить.  
  
 Вкладка «Выполнить» содержит коллекцию команд, которые можно использовать после того, как отчет будет подготовлен к просмотру. Можно распечатать отчет, перейти между страницами отчета, экспортировать отчет в другой формат, просмотреть схему документа, просмотреть параметры (при наличии таковых в отчете) и найти элементы внутри отчета. Дополнительные сведения см. [в разделе Предварительный просмотр отчета в режиме выполнения](#RunMode).  
  
 Чтобы вернуться в представление конструктора отчетов, на вкладке **выполнение** нажмите кнопку **конструктор**.  
  
  
##  <a name="the-report-design-surface"></a><a name="RptDesignSurface"></a> Область конструктора отчетов  
 Область конструктора отчетов в построителе отчетов — это основная область работы для конструирования отчетов. Для размещения в отчете таких элементов, как области данных, вложенные отчеты, текстовые поля, изображения, прямоугольники и линии, их следует добавить с ленты или из галереи элементов отчетов в область конструктора. Там можно добавлять в элементы отчета группы, выражения, параметры, фильтры, действия, видимость и форматирование.  
  
 Также можно изменять:  
  
-   свойства текста отчета, такие как цвет границ и заливки, щелкнув правой кнопкой мыши белую область в области конструктора за пределами элементов отчета и выбрав пункт **Свойства тела**;  
  
-   свойства верхнего и нижнего колонтитулов, например цвет границ и заливки, щелкнув правой кнопкой мыши белую область в области конструктора в области верхнего и нижнего колонтитула за пределами элементов отчета и выбрав пункт **Свойства верхнего колонтитула** или **Свойства нижнего колонтитула**;  
  
-   Свойства самого отчета, например параметры страницы, щелкнув правой кнопкой мыши синюю область вокруг области конструктора и выбрав пункт **Свойства отчета**.  
  
-   свойства элементов отчета, щелкнув их правой кнопкой мыши и выбрав пункт **Свойства**.  
  
> [!NOTE]  
>  Если перетащить поле из области данных отчета непосредственно в область конструктора отчета вместо помещения в область данных, такую как таблица или диаграмма, то при выполнении отчета будет отображаться только первое значение из данных этого поля.  
  
 Дополнительные сведения об использовании клавиатуры для работы с элементами в области конструктора см. в разделе [Сочетания клавиш (построитель отчетов)](keyboard-shortcuts-report-builder.md).  
  
### <a name="design-surface-size-and-print-area"></a>Размер области конструктора и область печати  
 Размер области конструктора может отличаться от области печати страницы, указанной для печати отчета. Изменение размера области конструктора не ведет к изменению области печати отчета. Вне зависимости от размера, заданного для области печати отчета, полный размер области конструирования не изменится. Дополнительные сведения см. в разделе [Поведение при подготовке к просмотру (построитель отчетов и службы SSRS)](../report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Чтобы отобразить линейку, установите на вкладке **Вид** флажок **Линейка**.  
  
  
##  <a name="the-report-data-pane"></a><a name="ReptDataPane"></a> The Report Data Pane  
 До начала разработки макета отчета в области данных отчета можно определить данные отчета и ресурсы отчета, необходимые для отчета. Например, на панель данных отчета можно добавить источники данных, наборы данных, вычисляемые поля, параметры отчета и изображения.  
  
 После добавления элементов к области данных отчета просто перетащите поля в элементы отчета в области конструктора для управления положением отображения данных в отчете.  
  
 Можно также перетаскивать встроенные поля из области данных отчета в область конструктора отчетов. При подготовке к просмотру эти поля содержат такие полезные сведения об отчете, как имя отчета, общее число страниц в отчете и номер текущей страницы.  
  
 При добавлении элементов в область конструктора отчетов эти элементы автоматически добавляются в область данных отчета. Например, если добавить элемент отчета из галереи элементов отчетов и данный элемент отчета является областью данных, набор данных автоматически добавляется в панель данных отчета. Дополнительные сведения см. в разделе [Элементы отчета и наборы данных в построителе отчетов](../report-data/report-parts-and-datasets-in-report-builder.md). Кроме того, при внедрении изображения в отчет оно будет добавлено в папку «Изображения» на панели данных отчета.  
  
> [!NOTE]  
>  С помощью кнопки **Создать** в область данных отчета можно добавить новый элемент. В отчет можно добавить несколько наборов данных из одного и того же или из нескольких источников данных. Можно добавить общие наборы данных с сервера отчетов. Чтобы добавить новый набор данных из одного и того же источника данных, щелкните правой кнопкой мыши источник данных и выберите команду **Добавить набор данных**.  
  
 Дополнительные сведения об элементах области данных отчета см. в следующих разделах:  
  
-   [Встроенные глобальные значения и ссылки на пользовательские поля (построитель отчетов и службы SSRS)](../report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md)  
  
-   [Параметры отчета (построитель отчетов и конструктор отчетов)](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
-   [Изображения (построитель отчетов и службы SSRS)](../report-design/images-report-builder-and-ssrs.md)  
  
-   [Подключения к данным, источники данных и строки подключения в построителе отчетов](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
-   [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
-   [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
##  <a name="the-report-part-gallery"></a><a name="ReptPartGallery"></a>Коллекция элементов отчетов  
 Самым простым способом создания отчета является нахождение имеющихся элементов отчета, например таблиц или диаграмм, на сервере отчетов или сервере отчетов, интегрированном с сайтом SharePoint. Поиск элементов отчетов, предназначенных для добавления к конкретному отчету, осуществляется в галерее элементов отчетов. Можно фильтровать элементы отчетов, указывая полностью или частично имя элемента отчета, кем он создан, кто внес в него последнее изменение, когда произошло последнее изменение, где он хранится или к какому типу относится. Например, можно выполнить поиск всех диаграмм, созданных на прошлой неделе одним из сотрудников.  
  
> [!NOTE]  
>  Для просмотра галереи элементов отчетов необходимо подключение к серверу отчетов.  
  
 Результаты поиска можно просматривать в виде миниатюр или списка, а также сортировать результаты поиска по именам, датам создания и изменения или именам пользователей, создавших части отчетов. Дополнительные сведения см. в разделе [Элементы отчета (построитель отчетов и службы SSRS)](../report-parts-report-builder-and-ssrs.md).  
  
  
##  <a name="the-properties-pane-report-builder"></a><a name="PropertiesPane"></a> Панель свойств (построитель отчетов)  
 С каждым элементом отчета, включая текст отчета, области данных, изображения и текстовые поля, сопоставлен набор свойств. Например, свойство BorderColor для текстового поля показывает значение цвета границы текстового поля, а свойство PageSize для отчета показывает размер страницы отчета.  
  
 Эти свойства отображаются на панели свойств. Свойства этой панели меняются в зависимости от выбранного элемента отчета.  
  
 Чтобы вывести панель свойств, выберите пункт «Свойства» в группе «Показать/скрыть» на вкладке «Вид».  
  
### <a name="changing-property-values"></a>Изменение значений свойств  
 В построителе отчетов можно изменять свойства элементов отчета несколькими способами:  
  
-   нажимая кнопки и выбирая списки на ленте;  
  
-   изменяя параметры в диалоговых окнах;  
  
-   изменяя значения свойств в панели свойств.  
  
 Наиболее часто используемые свойства доступны в диалоговых окнах и на ленте.  
  
 В зависимости от свойства можно выбрать его значение из раскрывающегося списка, ввести значение с клавиатуры или нажать кнопку `<Expression>` , чтобы создать выражение.  
  
### <a name="changing-the-properties-pane-view"></a>Изменение вида панели свойств  
 По умолчанию свойства, отображаемые в панели свойств, упорядочены по основным категориям — «Действие», «Граница», «Заливка», «Шрифт», «Общие» и др. С каждой категорией сопоставлен набор свойств. Например, в категории "Шрифт" перечислены следующие свойства: Color, FontFamily, FontSize, FontStyle, FontWeight, LineHeight и TextDecoration. В случае необходимости можно отсортировать по алфавиту все свойства, выведенные в панели. В результате категории не будут отображаться, а все свойства будут выведены в алфавитном порядке независимо от категории.  
  
 В верхней части панели свойств есть три кнопки: "По категориям", "По алфавиту" и "Страницы свойств". Кнопки «По категориям» и «По алфавиту» позволяют переключаться между режимами отображения панели свойств. Нажмите кнопку **Страницы свойств** , чтобы открыть диалоговое окно свойств для выбранного элемента отчета.  
  
  
##  <a name="the-grouping-pane-report-builder"></a><a name="GroupPane"></a> Панель «Группирования» (построитель отчетов)  
 Группы используются для организации данных отчета в визуальной иерархии и для вычисления итогов. Группы строк и столбцов можно просматривать в области данных, размещаемой в области конструктора, а также в панели группирования. Панель группирования делится на две области: "Группы строк" и "Группы столбцов". Если выбрать область данных, панель группирования отображает в виде иерархического списка все группы, входящие в эту область данных: дочерние элементы отображаются с отступом под родительскими.  
  
 ![Панель группирования для вложенных групп строк и столбцов](../media/rs-basictablixdesigngroupingpanedefaultview.gif "Панель группирования для вложенных групп строк и столбцов")  
  
 Группы можно создавать путем перетаскивания полей из панели данных отчета на панель конструктора или на панель группирования. В панели группирования можно добавлять родительские, соседние и дочерние группы, изменять свойства групп и удалять группы.  
  
 Панель группирования отображается по умолчанию, но эту панель можно закрыть, сняв флажок Панель группирования на вкладке Вид. Панель группирования недоступна для областей данных диаграммы или датчика.  
  
 Дополнительные сведения см. в разделах [Панель группировки (построитель отчетов)](../report-design/grouping-pane-report-builder.md) и [Основные сведения о группах (построитель отчетов и службы SSRS)](../report-design/understanding-groups-report-builder-and-ssrs.md).  
  
  
##  <a name="previewing-your-report-in-run-mode"></a><a name="RunMode"></a> Предварительный просмотр отчета в режиме выполнения  
 В представлении конструктора отчетов работа ведется не с фактическими данными, а с их представлением, которое указывается именем поля или выражением. Если нужно просмотреть фактические данные, отображаемые в контексте сконструированного отчета, можно запустить отчет для предварительного просмотра данных из основной базы данных, отображаемых в макете отчета. Переключение между конструированием и выполнением отчета позволяет корректировать его структуру с немедленным отображением результатов. Чтобы просмотреть отчет, нажмите кнопку **выполнить** в группе **представления** на ленте.  
  
 При нажатии кнопки **Выполнить**построитель отчетов подключается к источникам данных отчета, кэширует данные на компьютере, комбинирует эти данные с макетом и выводит отчет в средстве просмотра HTML-страниц. Можно запускать отчет во время создания столько раз, сколько пожелаете. Когда отчет полностью удовлетворяет вашим требованиям, его можно сохранить на сервере отчетов, где его смогут просмотреть другие лица, обладающие соответствующими разрешениями.  
  
### <a name="running-a-report-with-parameters"></a>Запуск отчета с параметрами  
 При запуске отчета он обрабатывается автоматически. Если отчет содержит параметры, все они должны иметь значения по умолчанию, прежде чем отчет можно будет автоматически запустить. Если параметр не имеет значения по умолчанию, то при запуске отчета необходимо выбрать значение параметра, а затем нажать кнопку **Просмотреть отчет** на вкладке выполнить. Дополнительные сведения см. в разделе [Параметры отчета &#40;построитель отчетов и конструктор отчетов&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
### <a name="print-preview"></a>Предварительный просмотр  
 При предварительном просмотре отчета в режиме выполнения он напоминает отчет, выданный в формате HTML. Отчет не является HTML-страницей, но его макет и разбиение на страницы подобны выходному формату HTML. Вместо этого отчет можно просмотреть в таком виде, как если бы он был напечатан, путем переключения в режим просмотра печати. Нажмите кнопку **Предварительный просмотр** на вкладке **выполнить** . Отчет будет отображаться так, как будто он находился на физической странице. Этот режим просмотра похож на результат работы модуля подготовки отчетов в формате PDF и формате изображения. Предварительный просмотр не является изображением или PDF-файлом, но макет отчета и его разбиение на страницы подобны выходному результату в этих форматах.  
  
  
## <a name="see-also"></a>См. также  
 [Поиск, просмотр отчетов и управление ими &#40;построитель отчетов и SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Построитель отчетов в SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  