---
title: Занятие 4. Создание прогнозов временных рядов с помощью расширений интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 772e5f5f71ca82dd18fec48730522c80e907414f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727497"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a>Занятие 4: Создание прогнозов на основе временных рядов с помощью расширений интеллектуального анализа данных
  На этом занятии и на следующем занятии будут использоваться расширения интеллектуального анализа данных для создания различных типов прогнозов на основе моделей временных рядов, созданных на [занятии 1. Создание модели и структуры интеллектуального анализа данных временных рядов](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md) , а также [занятие 2. Добавление моделей интеллектуального анализа данных в структуру интеллектуального анализа временных рядов](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md).  
  
 Использование модели временных рядов дает много возможностей для выполнения прогнозирования.  
  
-   Использование в модели интеллектуального анализа данных существующих закономерностей и данных.  
  
-   Использование в модели интеллектуального анализа данных существующих закономерностей, но предоставление новых данных.  
  
-   Добавление в модель новых данных или обновление модели.  
  
 Далее приведен синтаксис выполнения этих типов прогнозов.  
  
 Используемый по умолчанию прогноз временных рядов.  
 Используйте [PredictTimeSeries &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/predicttimeseries-dmx) , чтобы получить указанное количество прогнозов из обученной модели интеллектуального анализа данных.  
  
 Например, см. раздел [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) или [примеры запросов модели временных рядов](../../2014/analysis-services/data-mining/time-series-model-query-examples.md).  
  
 EXTEND_MODEL_CASES  
 Используйте [PredictTimeSeries &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/predicttimeseries-dmx) с аргументом EXTEND_MODEL_CASES, чтобы добавить новые данные, расширить ряд и создать прогнозы на основе обновленной модели интеллектуального анализа данных.  
  
 Этот учебник содержит пример использования аргумента EXTEND_MODEL_CASES.  
  
 REPLACE_MODEL_CASES  
 Используйте [PredictTimeSeries &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/predicttimeseries-dmx) с аргументом REPLACE_MODEL_CASES, чтобы заменить исходные данные на новый ряд данных, а затем создайте прогнозы на основе применения шаблонов в модели интеллектуального анализа данных к новым рядам.  
  
 Пример использования REPLACE_MODEL_CASES см. в разделе [занятие 2. Создание сценария прогнозирования &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии будут выполнены следующие задачи.  
  
-   Создание запроса для получения используемых по умолчанию прогнозов, основанных на существующих данных.  
  
 На следующем занятии будут выполнены следующие связанные задачи.  
  
-   Создание запроса для предоставления новых данных и получения обновленных прогнозов.  
  
 Наряду с созданием запросов вручную, при помощи расширений интеллектуального анализа данных, можно также создавать прогнозы в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], с помощью построителя прогнозирующих запросов.  
  
## <a name="simple-time-series-prediction-query"></a>Простой прогнозирующий запрос временных рядов  
 На первом шаге используется инструкция `SELECT FROM` совместно с функцией `PredictTimeSeries` для создания прогноза временных рядов. Модели временных рядов поддерживают упрощенный синтаксис создания прогнозов: нет необходимости предоставлять входные данные, нужно только задать количество создаваемых прогнозов. В следующем фрагменте показан общий пример инструкции, которая будет использоваться в дальнейшем.  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 Список выбора может содержать столбцы из модели, например имя линии продукта, для которой создаются прогнозы, или прогнозирующие функции, такие как [запаздывание &#40;dmx&#41;](/sql/dmx/lag-dmx) или [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx), которые предназначены специально для моделей интеллектуального анализа данных временных рядов.  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a>Создание простого запроса прогнозирования временного ряда  
  
1.  В окне **Обозреватель объектов**щелкните правой кнопкой мыши экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], укажите **Создать запрос**, а затем выберите пункт **Расширения интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
2.  Скопируйте общий пример инструкции в пустой запрос.  
  
3.  Вместо  
  
    ```  
    <select list>   
    ```  
  
     на:  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     В первой строке извлекается значение из модели интеллектуального анализа данных, которая идентифицирует ряд.  
  
     Во второй и третьей строке используется функция `PredictTimeSeries`. В каждой строке предсказание выполняется для разных атрибутов, для `[Quantity]` или `[Amount]`. Числа после имен прогнозируемых атрибутов указывают количество временных шагов, необходимых для прогнозирования.  
  
     Предложение `AS` используется для предоставления имени столбца, возвращаемого каждой прогнозирующей функцией. Если псевдоним не указывается, по умолчанию возвращаются оба столбца с меткой `Expression`.  
  
4.  Вместо  
  
    ```  
    [<mining model>]   
    ```  
  
     на:  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  Вместо  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     на:  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     Полная инструкция теперь должна выглядеть следующим образом.  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
7.  В диалоговом окне **Сохранить как** перейдите в соответствующую папку и присвойте файлу имя `SimpleTimeSeriesPrediction.dmx` .  
  
8.  На панели инструментов нажмите кнопку **Выполнить** .  
  
     Запрос возвращает 6 прогнозов для каждого из двух сочетаний продукта и региона, указанных в предложении `WHERE`.  
  
 На следующем занятии будет создан запрос, предоставляющий модели новые данные, и будет выполнено сравнение результатов этого прогноза с результатами только что созданного прогноза.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Занятие 5.: Расширение модели временных рядов](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a>См. также:  
 [PredictTimeSeries &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/predicttimeseries-dmx)   
 [Запаздывание &#40;&#41;расширений интеллектуального анализа данных](/sql/dmx/lag-dmx)   
 [Примеры запросов модели временных рядов](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Занятие 2. Создание сценария прогнозирования &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  