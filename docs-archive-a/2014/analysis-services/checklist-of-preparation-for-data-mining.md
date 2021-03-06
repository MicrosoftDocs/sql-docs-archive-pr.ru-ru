---
title: Контрольный список подготовки к интеллектуальному анализу данных | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e056c95-ba06-413e-8dc1-4d411a447c3b
author: minewiskan
ms.author: owend
ms.openlocfilehash: e37b1adb6aebe5d5f8fd23f5289f52425f752a6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657419"
---
# <a name="checklist-of-preparation-for-data-mining"></a>Контрольный список для подготовки к интеллектуальному анализу данных
  Хотя надстройки интеллектуального анализа данных упрощают создание и эксперименты с моделями, когда требуется получить повторяемые результаты, на основании которых можно действовать, необходимо выделить достаточный срок для формулировки базовых требований бизнеса и получения и подготовки данных. В этом разделе представлен контрольный список, который поможет вам спланировать исследование, а также приводится описание распространенных проблем.  
  
## <a name="checklist-of-data-preparation"></a>Контрольный список подготовки данных  
 **Я указал точно заданные выходные данные.**  
 Создать план использования результатов. У различных типов моделей различные выходы. Модель временных рядов формирует значения для рядов в будущем, которые легко понять и применить. Другие модели создают комплексные наборы, которые для получения наибольшей пользы должны быть проанализированы специалистами в соответствующей предметной области.  
  
-   Какие выходные данные нужны?  
  
-   Можно ли определить выходные данные как один столбец, одно значение или другой тип результата?  
  
-   Каковы критерии того, что созданная модель была полезной?  
  
-   Как эти результаты будут использоваться и интерпретироваться?  
  
-   Можно ли сопоставить новые входные данные с ожидаемым результатами?  
  
 **Я знаю значение, типы данных и распределение входных данных.**  
 Уделите время изучению и анализу исходных данных. Важно, чтобы пользователи, которые будут просматривать модель, понимали, какие вводные данные использовались и как интерпретировать типы и разброс данных, а также баланс и качество.  
  
-   Каков объем имеющихся данных? Достаточно ли данных для моделирования?  
  
     Это не должно быть огромным размером и сбалансированным.  
  
-   Данные получены из нескольких источников или одного источника?  
  
-   Данные уже обработаны и очищены? Доступно ли большее количество входных данных?  
  
-   Вам известно, как он был обработан перед получением, — каким способом данные могут быть усечены, суммироваться или преобразованы?  
  
-   Содержат ли входные данные результаты, которые можно использовать для обучения?  
  
 **Я понимаю уровень целостности данных в нашей системе и уровень, которого нам необходимо достигнуть.**  
 Неверные данные могут повлиять на качество модели или даже не позволить создать модель. Необходимо хорошо понимать распределение и значение данных, а также как они пришли к этому состоянию. Необходимо понимать, можно ли упростить данные путем добавления меток, усечения числовых типов данных или обобщением.  
  
-   Метки данных: они понятны и исправлены?  
  
-   Типы данных: нужны ли они и были ли они изменены?  
  
-   Выполнили ли вы сортировку, очистку или отклонение неверных данных?  
  
     Проверены ли данные на наличие повторов?  
  
-   Как будут обрабатываться отсутствующие значения? Есть ли смысл у отсутствующих значений?  
  
-   Проверены ли источники данных, чтобы убедиться в целостности импортируемых данных?  
  
     Где хранятся входные данные? Насколько долго данные будут оставаться доступными?  
  
     Существует ли словарь данных? Можно ли создать словарь?  
  
-   Если наборы данных были объединены, проводилась ли проверка столбцов, дублирующих одни и те же данные?  
  
 **Я могу узнать, где хранятся исходные данные, откуда они поступили и как они обрабатываются. При необходимости процесс можно легко повторить.**  
 Односторонние наборы данных прекрасно подойдут для экспериментов, но если вам когда-либо нужно переместить модель в рабочую среду, необходимо заранее подумать о том, как процесс очистки можно применить к рабочим данным. Кроме того, если у вас есть операционные данные, необходимо знать, как она могла быть изменена до того, как она была получена. вам нужно знать, как она была округлена или обобщена, безусловно.  
  
-   Нужна ли возможность повторять эксперимент?  
  
-   Какие инструменты будут использоваться для подготовки данных в формате, который поддерживает анализ данных? Можно ли автоматизировать процесс или необходим кто-то для просмотра и очистки данных в Excel?  
  
-   Если данные подкачиваются из другой системы, будет ли возможность отслеживать использование фильтров?  
  
-   Может ли ваша среда обработки данных также применить машинные алгоритмы обучения, выполнять тесты и визуализировать ресурсы?  
  
 **Мы достигли соглашения по уровню гранулярности прогнозов, и наши данные были изменены для вывода такими блоками.**  
 Примите решение по нужной гранулярности результатов до момента подготовки данных. Например, определите, хотите ли вы получать предсказания по уровням продаж ежедневно или ежеквартально? Рассмотрите возможность создания различных структур данных для одних и тех же данных, чтобы обрабатывать различные уровни сводки.  
  
-   Какова текущая единица измерения или единица времени?  
  
     Какую единицу измерения нужно использовать в результатах?  
  
-   Можно ли определить базовую единицу (например, день, час, минуту или вызов инструкции) для всех входных данных?  
  
     Требуется ли свертка до больших единиц измерения?  
  
-   Категории обозначены последовательно? Прост ли процесс добавления или удаления категорий?  
  
 **Наша опытная конструкция воспроизводима во всех отношениях.**  
 Рассмотрите стратегии для анализа и проверки результатов и запланируйте получение моментального снимка данных, чтобы получить возможности связать последствия с данными. При использовании случайного начального значения результаты могут слегка различаться. Это может затруднить сравнение и проверку моделей.  
  
-   При внесении большого количества изменений в данные что происходит при следующем построении модели?  
  
-   Определены ли ручная процедура или процесс, которые необходимо использовать для обработки входных данных и получения нужных выходных данных?  
  
-   Будет ли использоваться начальное значение в модели?  
  
 **Мы имеем набор знаний домена для проверки результатов или доступ к специалистам, которые могут дать рекомендации.**  
 Уделите время, чтобы проверить переменные, модель и результаты. Попросите помощи у специалистов для оценки взаимодействия и результатов. Тем не менее, не следует предполагать, что свидетельство переносится. Будьте открыты для новых и непредвиденных заключений.  
  
-   Доступны ли знания предметной области для помощи с фильтрацией данных и уменьшением шума входных данных?  
  
-   Могут ли эксперты в предметной области понять и интерпретировать результаты, а также предложить улучшения?  
  
## <a name="see-also"></a>См. также:  
 [Выбор данных для интеллектуального анализа данных](choosing-data-for-data-mining.md)  
  
  
