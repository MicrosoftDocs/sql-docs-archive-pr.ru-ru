---
title: Перемещение элементов в иерархии (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 37167f76b965197dbf8e37e365778395ec640d38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658303"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>Перемещение элементов в иерархии (службы Master Data Services)
  В службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] перемещение элементов в иерархии требуется для того, чтобы изменить местоположение элементов или родительский элемент.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Для явных иерархий необходимо иметь как минимум разрешение **Обновление** для сущности.  
  
-   Для производных иерархий необходимо иметь как минимум одно **Обновление** модели и всех атрибутов на основе домена, используемых в иерархии.  
  
### <a name="to-move-members-within-a-hierarchy"></a>Перемещение элементов в иерархии  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  В строке меню наведите указатель мыши на **иерархии** и щелкните *hierarchy_name*.  
  
5.  В области **Иерархия** , где иерархия отображается в древовидной структуре, установите флажок для каждого элемента, который требуется переместить.  
  
6.  В верхней части панели **Иерархия** нажмите кнопку **Вырезать**.  
  
7.  На панели **Иерархия** установите флажок для элемента, в который нужно переместить элементы.  
  
8.  Нажмите кнопку **Вставить**.  
  
    > [!NOTE]  
    >  В производных иерархиях элементы можно перемещать только на том же уровне. Кроме того, нельзя изменить порядок сортировки элементов.  
  
## <a name="see-also"></a>См. также:  
 [Перемещение элементов явной иерархии с помощью промежуточного процесса &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Производные иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Явные иерархии (службы Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
