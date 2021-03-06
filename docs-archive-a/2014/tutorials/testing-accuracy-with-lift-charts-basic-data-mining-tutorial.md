---
title: Проверка точности с помощью диаграмм точности прогнозов (учебник по интеллектуальному анализу данных — базовый) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a3dcdd1d1b78911f5ffd37a383532abdd4814c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734637"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a>Проверка точности при помощи диаграмм точности прогнозов (учебник интеллектуального анализа данных — начальный уровень)
  На вкладке **Диаграмма точности интеллектуального анализа** конструктора интеллектуального анализа данных можно вычислить, насколько хорошо каждая из моделей выполняет прогнозы, и сравнивать результаты каждой модели непосредственно с результатами других моделей. Этот метод сравнения называется *диаграммой точности прогнозов*. Обычно точность прогнозирования модели интеллектуального анализа данных определяется либо точностью предсказания, либо точностью классификации. В данном учебнике используются только диаграммы точности прогнозов.  
  
 В этом разделе будут выполнены следующие задачи:  
  
-   [Выбор входных данных](#BKMK_InputData)  
  
-   [Настройка параметров диаграммы точности](#BKMK_Selecting)  
  
##  <a name="choosing-the-input-data"></a><a name="BKMK_InputData"></a>Выбор входных данных  
 Первым шагом в проверке точности моделей интеллектуального анализа данных является выбор источника данных, который будет использоваться для проверки. Будет проверено, насколько хорошо работают модели на проверочных данных, а затем эти модели будут использованы с внешними данными.  
  
#### <a name="to-select-the-data-set"></a>Выбор набора данных  
  
1.  Перейдите на вкладку **Диаграмма точности интеллектуального анализа** в конструкторе интеллектуального анализа данных в [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и выберите вкладку **Выбор входа** .  
  
2.  В поле **выберите набор данных для использования в группе диаграмм точности** выберите **использовать проверочные варианты структуры интеллектуального анализа**. Это проверочные данные, которые задаются при создании структуры интеллектуального анализа данных.  
  
     Дополнительные сведения о других параметрах см. в разделе [Выбор типа диаграммы точности и установка параметров диаграммы](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).  
  
##  <a name="setting-accuracy-chart-parameters"></a><a name="BKMK_Selecting"></a>Настройка параметров диаграммы точности  
 Чтобы создать диаграмму точности, необходимо определить три вещи:  
  
-   Какие модели следует включить в диаграмму точности?  
  
-   Какой прогнозируемый атрибут требуется измерить? Некоторые модели могут иметь несколько целевых объектов, но каждая диаграмма может измерять только один результат за раз.  
  
     Для использования столбца в качестве **прогнозируемого имени столбца** в диаграмме точности столбцы должны иметь тип использования `Predict` или `Predict Only` . Кроме того, тип содержимого целевого столбца должен быть либо `Discrete` или `Discretized` . Иными словами, нельзя измерять точность для непрерывных числовых выходов с помощью диаграммы точности прогнозов.  
  
-   Вы хотите измерить общую точность модели или ее точность при прогнозировании определенного значения (например, [Покупатель велосипеда] = ' Да ')  
  
#### <a name="to-generate-the-lift-chart"></a>Создание диаграммы точности прогнозов  
  
1.  На вкладке **Выбор входа** конструктора интеллектуального анализа данных в разделе **Выбор прогнозируемых столбцов модели интеллектуального анализа для отображения на диаграмме точности**прогнозов установите флажок **синхронизировать прогнозируемые столбцы и значения**.  
  
2.  Убедитесь, что в столбце **имя прогнозируемого столбца** выбрано значение **Покупатель велосипеда** для каждой модели.  
  
3.  В столбце **Показывать** выберите каждую из моделей.  
  
     По умолчанию выбраны все модели в структуре интеллектуального анализа данных. Можно выбрать любую из моделей, однако в данном учебнике следует оставить выбранными все модели.  
  
4.  В столбце **значение прогноза** выберите **1**. То же значение автоматически вводится для каждой модели, имеющей такой же прогнозируемый столбец.  
  
5.  Перейдите на вкладку **Диаграмма точности прогнозов** .  
  
     При нажатии на вкладку выполняется прогнозирующий запрос для получения прогнозов для тестовых данных, а результаты сравниваются с известными значениями. Результаты выводятся в виде диаграммы.  
  
     Если вы указали конкретный целевой результат с помощью параметра **Прогноз значения** , на диаграмме точности прогнозов отображаются результаты случайных прогнозов и результаты идеальной модели.  
  
    -   В строке случайного предположения показано, насколько точна модель без использования каких-либо данных для информирования своих прогнозов: то есть 50-50 разбивается между двумя результатами. Диаграмма точности прогнозов позволяет визуализировать, насколько эффективнее работает модель в сравнении с произвольным предположением.  
  
    -   Идеальная линия модели представляет верхнюю границу точности. Он показывает максимально возможное преимущество, которое можно достигнуть, если модель всегда прогнозируется точно.  
  
     Созданные модели интеллектуального анализа данных, как правило, находятся между этими двумя крайними значениями. Любое улучшение от случайного предположения считается *приподнятым*.  
  
6.  Для нахождения линий, представляющих идеальную модель и модель случайного выбора, используйте условные обозначения.  
  
     Вы заметите, что `TM_Decision_Tree` модель обеспечивает наибольший прогноз, использующий модели упрощенного алгоритма кластеризации и Байеса.  
  
 Подробное описание диаграммы точности прогнозов, подобной созданной на этом занятии, см. в разделе [Диаграмма точности прогнозов &#40;Analysis Services-&#41;интеллектуального анализа данных ](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Тестирование фильтрованной модели &#40;учебник по интеллектуальному анализу данных (Basic)&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также:  
 [Диаграмма точности прогнозов &#40;Analysis Services&#41;интеллектуального анализа данных](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Вкладка диаграммы точности прогнозов &#40;представление диаграммы точности интеллектуального анализа данных&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  
