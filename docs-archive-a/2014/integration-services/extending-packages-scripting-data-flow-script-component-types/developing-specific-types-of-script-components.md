---
title: Разработка компонентов скрипта определенных типов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 114c9ddca90ea02a8e1847444b28b9d5876650a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664994"
---
# <a name="developing-specific-types-of-script-components"></a>Разработка компонентов скрипта определенных типов
  Компонент скрипта является настраиваемым средством, которое можно использовать в потоке данных пакета, чтобы выполнить практическое любое требование, которое не удается выполнить с помощью источников, преобразований и назначений, входящих в состав служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом разделе содержатся образцы кода компонента скрипта, с помощью которых демонстрируются четыре варианта настройки компонента скрипта:  
  
-   В качестве источника.  
  
-   В качестве преобразования с синхронными выходами.  
  
-   В качестве преобразования с асинхронными выходами.  
  
-   В качестве назначения.  
  
 Дополнительные примеры компонента скрипта, см. в разделе [Дополнительные примеры компонента скрипта](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Создание источника с помощью компонента скрипта](creating-a-source-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать источник потока данных с помощью компонента скрипта.  
  
 [Создание синхронного преобразования с помощью компонента скрипта](creating-a-synchronous-transformation-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать преобразование потока данных с синхронными выходами с помощью компонента скрипта. При подобном преобразовании строки данных изменяются на месте по мере их обработки компонентом.  
  
 [Создание асинхронного преобразования с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать преобразование потока данных с асинхронными выходами с помощью компонента скрипта. При таком преобразовании необходимо считать все строки данных, прежде чем добавить к данным, обрабатываемым компонентом, дополнительные сведения, например, вычисляемое статистическое выражение.  
  
 [Создание назначения с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать назначение потока данных с помощью компонента скрипта.  
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Сравнение решений со скриптами и пользовательских объектов](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Разработка компонентов потока данных определенных типов](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
