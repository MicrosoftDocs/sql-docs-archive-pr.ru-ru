---
title: Задачи и инструкции по запросам интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], how-to topics
ms.assetid: 1bc2a775-6e62-4c66-a53c-201f2ea66295
author: minewiskan
ms.author: owend
ms.openlocfilehash: 454a3af33d0c18232bb36771235b328a17da6b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668530"
---
# <a name="data-mining-query-tasks-and-how-tos"></a>Задачи и инструкции по запросам интеллектуального анализа данных
  Чтобы воспользоваться моделями интеллектуального анализа данных, чрезвычайно важно грамотно составлять запросы. В этом разделе приведены ссылки на примеры создания запросов к модели интеллектуального анализа данных с помощью средств, предоставляемых в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения о том, что представляет собой запрос к модели интеллектуального анализа данных, а также о типах создаваемых запросов см. в разделе [Запрос интеллектуального анализа данных](data-mining-queries.md).  
  
## <a name="creating-queries-with-prediction-query-builder"></a>Создание запросов с помощью построителя прогнозирующих запросов  
 Построитель прогнозирующих запросов имеется как в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , так и в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Он служит для графического построения запросов к моделям интеллектуального анализа. В следующих разделах описано, как можно выбрать модель, указать источник данных, настроить прогнозы и сохранить полученные данные.  
  
-   [Создание прогнозирующего запроса с помощью построителя прогнозирующих запросов](create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [Создание одноэлементного запроса в конструкторе интеллектуального анализа данных](create-a-singleton-query-in-the-data-mining-designer.md)  
  
-   [Создание прогнозирующего запроса с помощью построителя прогнозирующих запросов](create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [Просмотр и сохранение результатов прогнозирующего запроса](view-and-save-the-results-of-a-prediction-query.md)  
  
-   [Изменение прогнозирующего запроса вручную](manually-edit-a-prediction-query.md)  
  
-   [Применение функций прогнозирования к модели](apply-prediction-functions-to-a-model.md)  
  
-   [Выбор и сопоставление входных данных для прогнозирующего запроса](choose-and-map-input-data-for-a-prediction-query.md)  
  
## <a name="using-other-data-mining-query-tools"></a>Использование других средств построения запросов интеллектуального анализа данных  
 Кроме построителя прогнозирующих запросов, можно воспользоваться расширениями интеллектуального анализа данных или XMLA, введя запрос непосредственно в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Вы также можете программно создавать прогнозирующие запросы и направлять их на сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . В следующих разделах приведены дополнительные сведения о создании и использовании прогнозирующих запросов вне построителя прогнозирующих запросов.  
  
 [создать одноэлементный прогнозирующий запрос из шаблона](create-a-singleton-prediction-query-from-a-template.md)  
 Описывает использование средств в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для построения и выполнения прогнозирующего запроса.  
  
 [создать одноэлементный прогнозирующий запрос из шаблона](create-a-singleton-prediction-query-from-a-template.md)  
 Описывает использование шаблонов, предоставляемых в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , для добавления параметров прогнозирующего запроса.  
  
 [изменить значение времени ожидания для запросов интеллектуального анализа данных](change-the-time-out-value-for-data-mining-queries.md)  
 Описывает задание на сервере свойств, управляющих поведением запросов, связанных с интеллектуальным анализом данных.  
  
 [Создание запроса содержимого к модели интеллектуального анализа данных](create-a-content-query-on-a-mining-model.md)  
 Описывает создание запросов, возвращающих детализированные данные, хранящиеся в модели интеллектуального анализа данных, на основе наборов рядов схемы интеллектуального анализа.  
  
 [Создание запроса интеллектуального анализа данных с помощью XMLA](create-a-data-mining-query-by-using-xmla.md)  
 Описывает создание запросов содержимого модели интеллектуального анализа данных с помощью XMLA-шаблонов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку запросов и выражений &#40;Analysis Services&#41;](https://msdn.microsoft.com/library/gg492188(SQL.130).aspx)   
 [Хранимые процедуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
