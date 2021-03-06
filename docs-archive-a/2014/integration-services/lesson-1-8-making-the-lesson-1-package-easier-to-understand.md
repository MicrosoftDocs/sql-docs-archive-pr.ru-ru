---
title: Шаг 8. Облегчение чтения пакета, созданного на занятии 1 | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fb8e2adb9062b5b777acc14df0ddc5b45884ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664343"
---
# <a name="step-8-making-the-lesson-1-package-easier-to-understand"></a>Шаг 8. Облегчение чтения пакета, созданного на занятии 1
  После завершения настройки пакета, созданного на занятии 1, можно приступить к приведению его макета в порядок. Если фигуры в макетах элементов управления и потока данных имеют случайные размеры или если эти элементы не упорядочены или не сгруппированы, то функциональность пакета трудно понять.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools предоставляет средства, которые облегчают и ускоряют форматирование макета пакета. К функциям форматирования относится возможность создавать элементы одного размера, выравнивать их, а также управлять горизонтальным и вертикальным пространством между элементами.  
  
 Другим способом добиться лучшего понимания функциональности пакета является добавление заметок, описывающих функциональность пакета.  
  
 В этой задаче будут использованы функции форматирования [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools, чтобы улучшить макет потока данных и добавить к нему заметку.  
  
### <a name="to-format-the-layout-of-the-data-flow"></a>Форматирование макета потока данных  
  
1.  Если пакет, созданный на занятии 1, еще не открыт, дважды щелкните Lesson 1.dtsx в обозревателе решений.  
  
2.  Перейдите на вкладку **Поток данных** .  
  
3.  Установите курсор на верхний правый угол преобразования «Извлечение валюты образца», щелкните и протащите курсор через все компоненты потока данных.  
  
4.  В меню **Формат** выберите команду **Установить тот же размер**и щелкните **Оба**.  
  
5.  При выделенных объектах потока данных в меню **Формат** выберите команду **Выравнивание**и щелкните **Слева**.  
  
### <a name="to-add-an-annotation-to-the-data-flow"></a>Добавление заметки к потоку данных  
  
1.  Щелкните правой кнопкой мыши в области конструктора потока данных и выберите команду **Добавить заметку**.  
  
2.  В окне заметки введите или вставьте копированием следующий текст.  
  
     **Поток данных извлекает данные из файла, находит значения в столбце CurrencyKey таблицы DimCurrency и в столбце DateKey таблицы DimDate, после чего записывает данные в таблицу NewFactCurrencyRate.**  
  
     Чтобы в окне заметки перенести текст на следующую строку, поместите курсор в то место, где должна начинаться новая строка, и нажмите клавишу ВВОД.  
  
     Если в окне заметки не введен никакой текст, то окно закрывается при щелчке за его пределами.  
  
## <a name="next-steps"></a>Next Steps  
 [Шаг 9. Проверка учебного пакета, созданного на занятии 1](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
