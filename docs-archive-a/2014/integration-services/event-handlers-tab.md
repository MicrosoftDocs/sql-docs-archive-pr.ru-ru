---
title: Вкладка "обработчики событий" | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.eventhandlerwindow.f1
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5f25a9b0d602a3189feab797b7ef9c333decabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665028"
---
# <a name="event-handlers-tab"></a>Вкладка «Обработчики событий»
  Используйте вкладку **Обработчики событий** конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , чтобы сформировать поток управления в пакете служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Обработчик события запускается в ответ на событие, инициированное либо пакетом, либо задачей или контейнером в пакете.  
  
## <a name="options"></a>Параметры  
 **Исполняемый объект**  
 Выберите исполняемый объект, для которого необходимо создать обработчик события. Исполняемый объект может быть либо пакетом, либо задачей или контейнером в пакете.  
  
 **Обработчик событий**  
 Выберите тип обработчика события. Создайте обработчик события, перетащив элементы из **Области элементов**.  
  
 **Удаление**  
 Выберите обработчик события и удалите его из пакета, нажав кнопку **Удалить**.  
  
 **Щелкните здесь, чтобы создать \<event handler name> для исполняемого файла \<executable name>**  
 Нажмите, чтобы создать обработчик события.  
  
 Создайте поток управления, перетащив графические объекты, которые представляют задачи и контейнеры служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , из **Области элементов** в область конструктора вкладки **Обработчики событий** , соединяя затем объекты при помощи объектов управления очередностью, чтобы определить последовательность их запуска.  
  
 Кроме того, чтобы добавить заметки, щелкните правой кнопкой мыши в области конструктора и выберите из меню команду **Добавить заметку**.  
  
## <a name="see-also"></a>См. также:  
 [Обработчики событий в службах Integration Services (SSIS)](integration-services-ssis-event-handlers.md)   
 [Поток управления](control-flow/control-flow.md)   
 [Конструктор служб SSIS](ssis-designer.md)   
 [Обработчики событий в службах Integration Services (SSIS)](integration-services-ssis-event-handlers.md)  
  
  
