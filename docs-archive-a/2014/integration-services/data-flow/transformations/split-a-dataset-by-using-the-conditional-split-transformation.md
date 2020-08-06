---
title: Разбиение набора данных с помощью преобразования "Условное разбиение" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2efbc3973db1ab1b6b61f6de879e451319b50e49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667308"
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a>Разбиение набора данных с помощью преобразования «Условное разбиение»
  Чтобы добавить и настроить преобразование «Условное разбиение», пакет должен содержать по крайней мере одну задачу потока данных и один источник.  
  
### <a name="to-conditionally-split-a-dataset"></a>Чтобы условно разбить набор данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток данных** и перенесите преобразование «Условное разбиение» из окна **Область элементов**в область конструктора.  
  
4.  Подключите преобразование «Условное разбиение» к потоку данных, перетащив соединитель из источника данных или предыдущего преобразования в преобразование «Условное разбиение».  
  
5.  Дважды щелкните преобразование «Условное разбиение».  
  
6.  В окне **Редактор преобразования «Условное разбиение»** постройте выражения для использования в качестве условий, перетащив необходимые переменные, столбцы, функции и операторы в столбец **Условие** сетки. Можно также ввести выражение в столбец **Условие** .  
  
    > [!NOTE]  
    >  Переменная или столбец могут быть использованы в нескольких выражениях.  
  
    > [!NOTE]  
    >  Если выражение недопустимо, его текст выделяется, а в подсказке к столбцу появляется описание ошибки.  
  
7.  При необходимости измените значения в столбце **Имя выхода** . Имена по умолчанию — «Case 1», «Case 2» и т. д.  
  
8.  Для изменения последовательности оценки условий нажмите кнопку со стрелкой вверх или вниз.  
  
    > [!NOTE]  
    >  Поместите условия, которые будут выполняться чаще всего, в начало списка.  
  
9. Можно изменить имя выхода по умолчанию для строк данных, которые не подходят ни под одно из условий.  
  
10. Для настройки вывода ошибок нажмите **Настроить вывод ошибок**. Дополнительные сведения см. в разделе [Настройка вывода ошибок в компоненте потока данных](../../configure-an-error-output-in-a-data-flow-component.md).  
  
11. Нажмите кнопку **ОК**.  
  
12. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [Conditional Split Transformation](conditional-split-transformation.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)   
 [Пути служб Integration Services](../integration-services-paths.md)   
 [Типы данных служб Integration Services](../integration-services-data-types.md)   
 [Задача потока данных](../../control-flow/data-flow-task.md)   
 [Выражения служб Integration Services (SSIS)](../../expressions/integration-services-ssis-expressions.md)  
  
  
