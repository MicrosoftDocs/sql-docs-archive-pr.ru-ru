---
title: Задача 5. Настройка отношений на основе Терма | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1589ec5843053baa6c42a0b9b0dec019c887da9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735578"
---
# <a name="task-5-setting-term-based-relationships"></a>Задача 5. Задание связей на основе термина
  В этой задаче вы определяете несколько связей на основе термина для значений в домене **имени поставщика** . Связь на основе терма позволяет исправить терм, являющийся частью значения в домене. Это позволяет считать идентичными синонимами несколько значений, идентичных по написанию во всем, кроме отдельных частей. Например, **Inc.** можно исправить на « **включено**». Службы DQS используют эти связи при обнаружении знаний, очистке и сопоставлении. Дополнительные сведения см. в разделе [Создание связей на основе термина](https://msdn.microsoft.com/library/hh510404.aspx) .  
  
1.  Выберите **имя поставщика** в **списке Домен**.  
  
2.  Перейдите на вкладку **связи на основе термина** в правой области.  
  
3.  Нажмите кнопку **Добавить новую связь** на панели инструментов, чтобы добавить связь с таблицей.  
  
4.  Введите **Co.** для поля **значения** и **компании** для поля **исправить на** .  
  
5.  Повторите предыдущие два шага для следующих значений:  
  
    |Значение|Исправить на|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Связи на основе термина](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Связи на основе термина")  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 6. Задание синонимов](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  