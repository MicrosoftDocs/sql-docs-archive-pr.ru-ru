---
title: Скрытие или удаление уровней в производной иерархии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 039b05633bcd1fdc69d226e565b3dc5211e9734f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665402"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>Скрытие или удаление уровней в производной иерархии (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно скрыть уровень в производной иерархии, если он необходим для группирования, но отображать этот уровень нежелательно. Если этот уровень не нужен для группирования, то можно удалить его.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>Скрытие и удаление уровней в производной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **представление модели** в строке меню наведите указатель мыши на пункт **Управление** и щелкните **производные иерархии**.  
  
3.  На странице **Обслуживание производной иерархии** выберите модель из списка **Модель** .  
  
4.  Выберите строку для производной иерархии, которую необходимо изменить.  
  
5.  Щелкните **изменить выбранную производную иерархию**.  
  
6.  На панели **Текущие уровни** :  
  
    -   Чтобы скрыть уровень, щелкните любой уровень (кроме верхнего и нижнего). В списке **Видимый** выберите **Нет**. Затем щелкните **Сохранить выбранный элемент иерархии**.  
  
    -   Чтобы удалить верхний уровень, щелкните **Удалить выбранный элемент иерархии**. В диалоговом окне подтверждения нажмите кнопку **ОК**. Можно удалить только верхний уровень.  
  
## <a name="see-also"></a>См. также:  
 [Перемещение элементов в иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)   
 [Производные иерархии (службы Master Data Services)](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
