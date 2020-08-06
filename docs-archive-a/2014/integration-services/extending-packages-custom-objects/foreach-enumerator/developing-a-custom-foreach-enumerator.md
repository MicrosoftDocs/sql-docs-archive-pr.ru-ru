---
title: Разработка пользовательского перечислителя по каждому элементу | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services]
- custom foreach enumerators [Integration Services], about custom foreach enumerators
- foreach enumerators [Integration Services]
ms.assetid: bffe26e0-1b9a-47ad-bae6-6b708cb4cf4f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3d61f98266320f63d7ee56262b7c85dfb64d39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664428"
---
# <a name="developing-a-custom-foreach-enumerator"></a>Разработка пользовательского перечислителя по каждому элементу
  Для итерации по элементам коллекции и выполнения одинаковых задач для каждого элемента службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] используют перечислители по каждому элементу. Службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] содержат ряд различных перечислителей по каждому элементу, которыми поддерживается большинство наиболее часто используемых коллекций, например, все файлы в папке, все таблицы в базе данных или все элементы в списке, хранящемся в переменной пакета. Если предлагаемый выбор перечислителей по каждому элементу и коллекций не отвечает потребностям пользователя, можно создать пользовательский перечислитель по каждому элементу.  
  
 Для создания пользовательского перечислителя по каждому элементу необходимо создать класс, наследующий от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>, применить атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> к новому классу и переопределить важные методы и свойства базового класса, в том числе метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>.  
  
## <a name="in-this-section"></a>в этом разделе  
 В этом разделе описывается, как создавать, настраивать и кодировать пользовательский перечислитель по каждому элементу и, при необходимости, его пользовательский интерфейс.  
  
 [Создание пользовательского перечислителя по каждому элементу](creating-a-custom-foreach-enumerator.md)  
 Описывает, как создать классы для проекта пользовательского перечислителя по каждому элементу.  
  
 [Написание кода пользовательского перечислителя по каждому элементу](coding-a-custom-foreach-enumerator.md)  
 Описывает, как реализовать пользовательский перечислитель по каждому элементу путем переопределения методов и свойств базового класса.  
  
 [Разработка пользовательского интерфейса для пользовательского перечислителя по каждому элементу](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
 Описывает, как реализовать класс пользовательского интерфейса и форму, используемую для настройки пользовательского перечислителя по каждому элементу.  
  
## <a name="related-topics"></a>См. также  
  
### <a name="information-common-to-all-custom-objects"></a>Общие сведения для всех пользовательских объектов  
 Сведения, общие для всех типов пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательских объектов для служб Integration Services](../developing-custom-objects-for-integration-services.md)  
 Описывает основные шаги по реализации всех типов пользовательских объектов для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Сохранение пользовательских объектов](../persisting-custom-objects.md)  
 Описывает пользовательский механизм сохраняемости, при необходимости приводя пояснения.  
  
 [Сборка, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md)  
 Описывает методы построения, подписывания, развертывания и отладки пользовательских объектов.  
  
### <a name="information-about-other-custom-objects"></a>Сведения о других пользовательских объектах  
 Сведения о других типах пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательской задачи](../task/developing-a-custom-task.md)  
 Описывает программирование пользовательских задач.  
  
 [Разработка пользовательского диспетчера соединений](../connection-manager/developing-a-custom-connection-manager.md)  
 Описывает вопросы программирования пользовательских диспетчеров соединений.  
  
 [Разработка пользовательского регистратора](../log-provider/developing-a-custom-log-provider.md)  
 Описывает вопросы программирования пользовательских регистраторов.  
  
 [Разработка пользовательского компонента потока данных](../data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
