---
title: Учебник. Добавление гистограммы к отчету (построитель отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ef3b3f2872c2f8181296bb05337ca18975ac2f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737862"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a>Учебник. Добавление гистограммы к отчету (построитель отчетов)
  Гистограмма отображает ряды в виде набора вертикальных прямоугольников, сгруппированных по категориям. Гистограмма может быть полезна в следующих случаях:  
  
-   отображение изменений данных в течение периода времени;  
  
-   сравнение относительных значений нескольких рядов.  
  
-   отображение скользящего среднего для показа трендов.  
  
 На следующем рисунке показывается создаваемая столбцовая диаграмма со скользящим средним.  
  
 ![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Что вы узнаете  
 В этом учебнике рассматриваются следующие темы:  
  
1.  [Создание диаграммы с помощью мастера диаграмм](#Chart)  
  
2.  [Выбор типа диаграммы](#ChartType)  
  
3.  [Форматирование и задание меток для горизонтальной оси](#Horizontal)  
  
4.  [Перемещение условных обозначений](#Legend)  
  
5.  [Задание заголовка для диаграммы](#ChartTitle)  
  
6.  [Форматирование и задание меток для вертикальной оси](#Vertical)  
  
7.  [Добавление скользящего среднего](#Average)  
  
8.  [Добавление заголовка отчета](#Title)  
  
9. [Сохранение отчета](#Save)  
  
> [!NOTE]  
>  В этом учебнике шаги работы с мастером объединены в одну процедуру. Пошаговые инструкции по переходу к серверу отчетов, выбору источника данных и созданию набора данных см. в первом учебнике этой серии: [Учебник. Создание простого табличного отчета &#40;построитель отчетов&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Предполагаемое время для выполнения заданий этого учебника: 15 минут.  
  
## <a name="requirements"></a>Требования  
 Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a>1. Создание отчета с диаграммой с помощью мастера диаграмм  
 В диалоговом окне **Начало работы** с помощью мастера диаграмм создайте внедренный набор данных, выберите общий источник и Создайте гистограмму.  
  
> [!NOTE]  
>  В этом учебнике запрос уже содержит значения данных, поэтому внешний источник данных не требуется. В связи с этим запрос получается весьма длинным. В рабочей среде запрос не будет содержать данные. Этот запрос содержит данные только в учебных целях.  
  
#### <a name="to-create-a-new-chart-report"></a>Создание нового отчета с диаграммой  
  
1.  Нажмите кнопку **Пуск**, наведите курсор на пункты **Все программы**, **Построитель отчетов Microsoft SQL Server 2012**и выберите пункт **Построитель отчетов**.  
  
     Откроется диалоговое окно **Начало работы** .  
  
    > [!NOTE]  
    >  Если диалоговое окно **Начало работы** не отображается, на кнопке **Построитель отчетов** нажмите кнопку **создать**.  
  
2.  Убедитесь, что на левой панели выбран **Новый отчет** .  
  
3.  На правой панели выберите **Мастер диаграмм**.  
  
4.  На **странице Выбор набора данных**щелкните **создать набор данных**, а затем нажмите кнопку **Далее**.  
  
5.  На странице **Выбор соединения с источником данных** выберите существующий источник данных или перейдите к серверу отчетов и выберите источник данных, а затем нажмите кнопку **Далее**. Может потребоваться указать имя пользователя и пароль.  
  
    > [!NOTE]  
    >  При наличии необходимых разрешений выбор источника данных не имеет существенного значения. Этот источник данных не будет использоваться для получения данных. Дополнительные сведения см. в разделе [Альтернативные способы создания подключения к данным &#40;построитель отчетов&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  На странице **Проектирование запроса** нажмите кнопку **Изменить как текст**.  
  
7.  На панель запроса вставьте следующий запрос:  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  Нажмите кнопку Выполнить (**!**), чтобы просмотреть данные, на основе которых будет создана диаграмма (необязательно).  
  
9. Щелкните **Далее**.  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a>2. Выбор типа диаграммы  
 Можно выбрать один из различных стандартных типов диаграмм.  
  
#### <a name="to-add-a-column-chart"></a>Добавление гистограммы  
  
1.  На странице **Выбор типа диаграммы** в качестве типа диаграммы по умолчанию задана гистограмма. Щелкните **Далее**.  
  
2.  На странице **Расположение полей диаграммы** перетащите поле "ДатаПродаж" в **Категории**. Категории отображаются по горизонтальной оси.  
  
3.  Перетащите поле "Продажи" в область **Значения**. В поле **Значения** отображается выражение Sum(Продажи), так как общее значение строки суммируется для каждой даты заказа на продажу. Значения отображаются по вертикальной оси.  
  
4.  Щелкните **Далее**.  
  
5.  На странице **Выбор стиля** в поле Стили выберите стиль.  
  
     Стиль задает стиль шрифта, набор цветов и стиль границы. При выборе стиля на панели просмотра отобразится образец диаграммы с этим стилем.  
  
6.  Нажмите кнопку **Готово**.  
  
     Диаграмма добавляется в область конструктора.  
  
7.  Щелкните диаграмму, чтобы отобразить ее маркеры. Перетащите правый нижний угол диаграммы вниз, чтобы увеличить ее размер. Обратите внимание, что область конструктора отчета увеличивается для соответствия размеру диаграммы.  
  
8.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a>3. форматирование и пометка горизонтальной оси  
 По умолчанию по горизонтальной оси отображаются значения в общем формате, который автоматически масштабируется в соответствии с размером диаграммы.  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a>Форматирование даты по горизонтальной оси  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Щелкните правой кнопкой мыши горизонтальную ось и выберите пункт **Свойства горизонтальной оси**.  
  
3.  Выберите **Число**.  
  
4.  В списке **Категория**выберите **Дата**.  
  
5.  В поле **Тип** выберите **31 января 2000 года**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  На вкладке Главная нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Дата отображается в выбранном формате дат. Обратите внимание, что на горизонтальной оси диаграммы имеются метки не для всех категорий. По умолчанию включаются только метки, расположенные рядом с осью.  
  
 Можно настроить отображение меток, повернув их и указав интервал.  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a>Поворот меток осей и изменение интервала отображения по горизонтальной оси  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Щелкните правой кнопкой мыши заголовок горизонтальной оси и выберите команду **отобразить заголовок оси** , чтобы удалить заголовок. Так как на горизонтальной оси отображаются даты, заголовок не нужен.  
  
3.  Щелкните правой кнопкой мыши горизонтальную ось и выберите пункт **Свойства горизонтальной оси**.  
  
4.  На странице **Параметры оси** в разделе **Диапазон оси и интервал**введите **3** для параметра **интервал**. На диаграмме отобразится каждая третья дата.  
  
5.  Щелкните **Метки**.  
  
6.  В окне **изменение параметров автоподбора метки оси**установите флажок Отключить автоподбор **размера**.  
  
7.  В поле **Угол поворота метки**выберите значение **-90**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Образец текста для горизонтальной оси поворачивается на 90 градусов.  
  
9. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 На диаграмме метки поворачиваются, причем отображаются метки для каждой третьей даты.  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a>4. Перемещение условных обозначений  
 Условные обозначения автоматически создаются на основе данных категорий и рядов.  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a>Перемещение условных обозначений под область гистограммы  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Щелкните правой кнопкой мыши условные обозначения на диаграмме и выберите пункт **Свойства условных обозначений**.  
  
3.  Выберите другую положение для **макета и расположения**. Например, можно выбрать параметр, соответствующий расположению посередине в нижней части.  
  
     Если условные обозначения перемесить в верхнюю или нижнюю часть диаграммы, их макет изменится с вертикального на горизонтальный. Можно выбрать другой макет в раскрывающемся списке **Макет** .  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  (Необязательно) Так как в данном учебнике имеется только одна категория, условные обозначения не требуются. Чтобы удалить условные обозначения, щелкните условные обозначения правой кнопкой мыши и выберите пункт **удалить условные обозначения**.  
  
6.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a>5. заголовком диаграммы  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a>Изменение заголовка диаграммы над областью диаграммы  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Выберите **заголовок диаграммы** "слова" в верхней части диаграммы, а затем введите следующий текст: " **Хранение итогов заказов на продажу**".  
  
3.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a>6. форматирование и пометка вертикальной оси  
 По умолчанию по вертикальной оси отображаются значения в общем формате, который автоматически масштабируется в соответствии с размером диаграммы.  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a>Форматирование чисел по вертикальной оси для представления валюты  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Чтобы выбрать метки, дважды щелкните метки на вертикальной оси сбоку от диаграммы.  
  
3.  На ленте на вкладке **Главная** в группе **число** нажмите кнопку **Валюта** . Метки оси изменятся, отображая формат валюты.  
  
4.  На ленте на вкладке **Главная** в группе **число** нажмите кнопку **уменьшить десятичную дробь** два раза, чтобы отобразить число, округленное до ближайшего доллара.  
  
5.  Щелкните правой кнопкой мыши вертикальную ось и выберите пункт **Свойства вертикальной оси**.  
  
6.  Выберите **Число**. Обратите внимание, что **Валюта** уже выбрана в поле **Категория** , а **десятичные разряды** уже **равны 0** (нулю).  
  
7.  В поле **Показывать значения в** выберите **тысячи**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Щелкните правой кнопкой мыши заголовок вертикальной оси вдоль стороны диаграммы и выберите пункт **Свойства заголовка оси**.  
  
10. Замените текст в поле " **текст заголовка** " следующим текстом: **объем продаж (в тысячах)**. Можно также указать несколько параметров, связанных с форматом заголовка.  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a>7. Добавление скользящего среднего  
  
#### <a name="to-add-a-moving-average"></a>Добавление скользящего среднего  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Дважды щелкните диаграмму, чтобы отобразить панель **Данные диаграммы** .  
  
3.  Щелкните правой кнопкой мыши поле **[Sum (Sales)]** , которое находится в области **значения** , и выберите команду **Добавить вычисляемый ряд**.  
  
4.  Убедитесь в том, что в поле **Формула**выбрано **Скользящее среднее** .  
  
5.  В разделе **Задание параметров формулы**для параметра **Период**задайте значение **4**.  
  
6.  Нажмите кнопку **граница**.  
  
7.  В окне **толщина линии**выберите **3 пунктов**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 На диаграмме отображается линия, показывающая скользящее среднее для общих продаж по дате, усредненное по каждым четырем дням.  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a>8. Добавление заголовка отчета  
  
#### <a name="to-add-a-report-title"></a>Добавление заголовка отчета  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  В области конструктора щелкните ссылку **Щелкните, чтобы добавить заголовок**.  
  
3.  Введите **Диаграмма продаж**, нажмите клавишу ВВОД, а затем введите **Январь 2009 декабря**, чтобы он выглядел следующим образом:  
  
     **Диаграмма продаж**  
  
     **Январь — декабрь 2009 г.**  
  
4.  Выберите **Диаграмма продаж**и нажмите кнопку **полужирный** в разделе **Шрифт** на вкладке **Главная** ленты.  
  
5.  Выберите **Январь до декабря 2009**, а в разделе **Шрифт** на вкладке **Главная** установите размер шрифта равным **10**.  
  
6.  Используемых Может потребоваться увеличить высоту текстового поля **заголовка** , чтобы разместить две строки текста, выжимая стрелки двойных стрелок при щелчке по середине нижнего края.  
  
     Данный заголовок появится в верхней части отчета. При отсутствии верхнего колонтитула страницы элементы в верхней части текста отчета выполняют роль заголовка отчета.  
  
7.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="9-save-the-report"></a><a name="Save"></a>9. Сохранение отчета  
  
#### <a name="to-save-the-report"></a>Сохранение отчета  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Нажмите кнопку «Построитель отчетов» и выберите **Сохранить как**.  
  
3.  В поле **Имя**введите **Гистограмма заказов на продажу**.  
  
4.  Выберите команду **Сохранить**.  
  
## <a name="next-steps"></a>Next Steps  
 Учебник «Добавление гистограммы к отчету» завершен. Дополнительные сведения о диаграммах см. в разделах [Диаграммы (построитель отчетов и службы SSRS)](report-design/charts-report-builder-and-ssrs.md) и [Спарклайны и гистограммы (построитель отчетов и службы SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Учебники &#40;построитель отчетов&#41;](report-builder-tutorials.md)   
 [Построитель отчетов в SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  