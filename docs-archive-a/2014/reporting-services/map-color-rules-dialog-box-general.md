---
title: Диалоговое окно «Правила цвета карт», «общие» | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10541"
- sql12.rtp.rptdesigner.shared.mapcolorrulesgeneral.f1
ms.assetid: 14ff5fc1-4cf8-4a45-9d98-47a1bf1c52c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0dffc6c0b31400cb4eb9cecbbada1a52f8f41443
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668086"
---
# <a name="map-color-rules-dialog-box-general"></a>Диалоговое окно «Правила цвета карты» — «Общие»
  Перейдите на страницу **Общие** в диалоговом окне **Свойства правил цвета** , чтобы определить параметры цвета для элементов карты на данном слое. Элементы карты включают многоугольники, линии и точки. Правила цвета можно применить, если создана связь между элементами карты на основе пространственных и аналитических данных из поля набора данных либо из поля источника пространственных данных.  
  
 Чтобы отобразить все элементы карты на слое при помощи цветного градиента с разными первичными и вторичными цветами, используйте страницу **Заливка** диалогового окна «Свойства многоугольников карты». Правила цвета имеют приоритет над свойствами отображения для слоя. Дополнительные сведения см. в разделе [Настройка данных и отображения карты или слоя карты (построитель отчетов и службы SSRS)](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Варианты  
 **Применить стиль шаблона**  
 Выберите этот параметр, чтобы использовать цвета на основе темы, выбранной в мастере или заданной в свойствах слоя «Многоугольник», «Линия» или «Точка». Тема задает параметры по умолчанию для цвета, шрифта и границ для карты. Для данного параметра правила назначения цветов каждому элементу карты не используются.  
  
 **Отобразить данные при помощи палитры цветов**  
 Выберите данный параметр, чтобы отображать аналитические данные при помощи цветов из определенной палитры цветов.  
  
 **Отобразить данные при помощи диапазонов цвета**  
 Выберите данный параметр, чтобы отображать аналитические данные при помощи диапазона цветов для каждого элемента карты. Например, если установить «Красный» в качестве исходного цвета, «Желтый» в качестве промежуточного и «Зеленый» в качестве конечного цвета, значения в нижнем диапазоне будут красными, в середине — желтыми и в верхнем диапазоне — зелеными.  
  
 **Отобразить данные при помощи пользовательских цветов**  
 Выберите данный параметр, чтобы отображать аналитические данные при помощи определенного списка цветов.  
  
 **Поле данных**  
 Данный параметр доступен при выборе одного из параметров **Отобразить данные** .  
  
 В раскрывающемся списке выберите нужное поле аналитических данных. В зависимости от источника пространственных данных список отображает поля из источника пространственных данных и из набора данных отчета, который имеет связь между пространственными и аналитическими данными. Чтобы создать такую связь, задайте параметры данных на странице «Аналитические данные» для выбранного слоя карты.  
  
 **Задания**  
 Введите или выберите имя палитры цветов.  
  
 **Исходный цвет**  
 Укажите цвет, который будет использоваться для данных в нижней области диапазона данных.  
  
 **Промежуточный цвет**  
 Укажите цвет, который будет использоваться для данных в средней области диапазона данных. Выберите **Без цвета** , чтобы удалить данный диапазон.  
  
 **Конечный цвет**  
 Укажите цвет, который будет использоваться для данных в верхней области диапазона данных.  
  
 **Добавление**  
 Нажмите кнопку **Добавить** , чтобы добавить цвета для правила цвета.  
  
## <a name="see-also"></a>См. также:  
 [Карты (построитель отчетов и службы SSRS)](report-design/maps-report-builder-and-ssrs.md)   
 [Изменение условных обозначений карты, цветовой шкалы и связанных правил (построитель отчетов и службы SSRS)](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  