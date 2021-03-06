---
title: Учебник по интеллектуальному анализу данных (Analysis Services — интеллектуальный анализ данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 404b31d5-27f4-4875-bd60-7b2b8613eb1b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 090bcd8cc987da57a5c4bdf27e6782ae07b85719
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656119"
---
# <a name="intermediate-data-mining-tutorial-analysis-services---data-mining"></a>Учебник по интеллектуальному анализу данных — средний уровень (службы Analysis Services — интеллектуальный анализ данных)
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]предоставляет интегрированную среду для создания моделей интеллектуального анализа данных и работы с ними. В ней удобно создавать привязки к источникам данных, создавать и тестировать несколько моделей на одних и тех же данных, а также развертывать модели, используемые в анализе для прогнозирования.  
  
 В учебнике по интеллектуальному анализу данных (начальный уровень) было описано создание решения интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], даны инструкции по построению трех моделей, обеспечивающих поддержку кампании целевой рассылки для анализа поведения клиента в процессе покупки и выявления потенциальных групп покупателей.  
  
 В учебнике среднего уровня подразумевается наличие опыта работы с этими средствами и представлено несколько новых сценариев, в том числе общие бизнес-требования, например прогнозирование и анализ покупательского поведения. В учебнике рассматривается создание модели временных рядов, модели взаимосвязей и модели кластеризации последовательностей. И наконец, рассматривается использование нейронных сетей для исследования корреляций в данных и использование логистической регрессии для создания прогнозов.  
  
 Занятия не зависят друг от друга и могут выполняться по отдельности.  
  
 Для прохождения этих учебников обучаемый должен быть знаком со средствами интеллектуального анализа данных, а также со средствами просмотра моделей интеллектуального анализа данных, описанными в учебнике по интеллектуальному анализу данных (начальный уровень).  
  
 Во всех сценариях используется источник данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], при этом для разных сценариев будут создаваться разные представления источников данных. Если вначале был создан источник данных, то занятия можно проходить в любом порядке.  
  
## <a name="lesson-scenarios"></a>Сценарий занятия  
 После успешного проведения кампании целевой рассылки предлагается, используя знания интеллектуального анализа данных, разработать несколько новых моделей, применяемых в бизнес-планировании. В том числе следующие задачи:  
  
-   **Прогнозирование:** Вы создадите модель *временных рядов* , чтобы прогнозировать продажи продуктов в разных регионах по всему миру. Вы разрабатываете отдельные модели для каждого региона и узнаете, как использовать *перекрестное прогнозирование*.  
  
-   **Анализ потребительской корзины:** Вы создадите *Модель взаимосвязей*, чтобы анализировать группы продуктов, приобретенных во время посещения [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] сайта электронной коммерции. На основании этой модели потребительской корзины можно рекомендовать продукты клиентам.  
  
-   **Анализ последовательности:** Вы создаете *модель кластеризации последовательностей*для анализа порядка, в котором клиенты покупают продукты. На основании этой модели можно планировать изменения дизайна веб-сайта или предложений новых продуктов.  
  
-   **Анализ коэффициента:** Модель *нейронной сети* используется для изучения возможных причин плохого качества обслуживания в данных центра обработки вызовов. Основываясь на аналитических данных из предварительной модели, вы создадите *модель логистической регрессии* для прогнозирования стратегий улучшения качества взаимодействия с клиентами.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 Этот учебник поможет научиться создавать несколько разных типов алгоритмов интеллектуального анализа данных и работать с ними. Учебник содержит следующие занятия:  
  
 [Занятие 1. Создание промежуточного решения интеллектуального анализа данных &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
 На этом занятии будет создан новый проект на основе базы данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], поддерживающий несколько новых представлений источников данных и несколько дополнительных моделей интеллектуального анализа данных.  
  
 [Занятие 2. Создание сценария прогнозирования &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
 На этом занятии рассматривается создание моделей интеллектуального анализа данных, которые можно использовать в сценарии прогнозирования. Также будут рассмотрены модели интеллектуального анализа данных, построенные с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритма временных рядов.  
  
 Предстоит разработать отдельные модели для каждого региона, а также общую модель, которую можно использовать для перекрестного прогнозирования.  
  
 [Урок 3. Построение сценария покупательского поведения (учебник по интеллектуальному анализу данных — средний уровень)](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
 Цель этого занятия — добавить новое представление источника данных и научиться работать со вложенными таблицами и ключами. На этих данных рассматривается создание моделей интеллектуального анализа данных, которые могут использоваться в сценарии потребительской корзины. Также будут рассмотрены модели интеллектуального анализа данных, построенные с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритма взаимосвязей.  
  
 [Занятие 4. Создание сценария кластеризации последовательностей &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
 На этом занятии рассматривается создание моделей интеллектуального анализа данных, которые могут использоваться в сценарии кластеризации последовательностей. Кроме того, вы узнаете, как исследовать модели интеллектуального анализа данных, построенные с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритма кластеризации последовательностей.  
  
 [Занятие 5. Построение моделей нейронной сети и логистической регрессии (учебник по интеллектуальному анализу данных — средний уровень)](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
 На этом занятии с помощью алгоритмов нейронной сети и логистической регрессии (Майкрософт) нужно создать несколько связанных моделей интеллектуального анализа данных. Также вы узнаете, как с помощью представлений источников данных можно исследовать базовые данные моделей.  
  
## <a name="requirements"></a>Требования  
 Убедитесь, что установлены следующие компоненты:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с базой данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] .  
  
 В целях повышения безопасности образцы баз данных по умолчанию не установлены. Чтобы установить официальные базы данных для [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , посетите страницу [образцов баз данных SQL Microsoft](https://go.microsoft.com/fwlink/?LinkId=88417) и выберите соответствующую версию образца базы данных.  
  
## <a name="see-also"></a>См. также  
 [Учебник по основам интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Учебник по DMX-покупателям велосипедов](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [Учебник по расширениям интеллектуального анализа данных потребительской корзины](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
  
