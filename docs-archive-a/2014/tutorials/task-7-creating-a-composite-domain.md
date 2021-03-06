---
title: Задача 7. Создание составного домена | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42936d25e267bcad5ba8ae512750f9e12f041579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654645"
---
# <a name="task-7-creating-a-composite-domain"></a>Задача 7. Создание составного домена
  В этой задаче вы создадите составной домен, который является **проверкой адреса**, которая включает домены **адресов**, **городов**, **Штатов**и **ZIP** -доменов. Составной домен позволяет определить междоменное правило, включающее несколько доменов. Есть и другие преимущества составных доменов, например возможность анализировать значение поля в нескольких доменах.  Например, значение для поля «Полное имя» может быть проанализировано в отдельных доменах «Имя», «Отчество» и «Фамилия». В этом учебнике вы определяете только междоменное правило. Дополнительные сведения см. [в разделе Управление составным доменом](https://msdn.microsoft.com/library/hh510399.aspx) .  
  
1.  В левой области нажмите кнопку **создать составной домен** на панели инструментов.  
  
     ![Кнопка панели инструментов «Создание составного домена»](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "Кнопка панели инструментов «Создание составного домена»")  
  
2.  Введите **проверку адреса** для **имени составного домена**.  
  
     ![Составной домен проверки адреса](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "Составной домен проверки адреса")  
  
3.  В списке Домен выберите **Строка адреса**, **город**, **штат**и **почтовый индекс** , а затем щелкните **стрелку вправо** , чтобы добавить их в список **домены в составном** списке доменов.  
  
4.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 8. Создание правила составного домена](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
