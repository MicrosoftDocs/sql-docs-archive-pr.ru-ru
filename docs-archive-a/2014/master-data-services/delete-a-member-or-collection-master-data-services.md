---
title: Удаление элемента или коллекции (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9b248750c0e755c3fc9e32d45068c754e64957b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728421"
---
# <a name="delete-a-member-or-collection-master-data-services"></a>Удаление элемента или коллекции (службы Master Data Services)
  В службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]элементы и коллекции следует удалять, когда в них больше нет необходимости. Если необходимо удалить большое количество элементов, лучше воспользоваться промежуточным процессом. Дополнительные сведения см. [в разделе Отключение или удаление элементов с помощью промежуточного процесса &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).  
  
> [!NOTE]  
>  Невозможно удалить элемент, если он используется в качестве значения атрибута на основе домена для другого элемента.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Для членов необходимо иметь как минимум разрешение **Обновление** для объекта конечной модели, из которого удаляется элемент.  
  
-   Для коллекций необходимо как минимум разрешение **Обновление** на удаляемый конечный объект коллекции.  
  
### <a name="to-delete-a-member-or-collection"></a>Удаление элемента или коллекции  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  Для удаления  
  
    -   конечного элемента в строке меню наведите указатель мыши на **Сущности** и щелкните имя сущности, содержащей элемент;  
  
    -   объединенного элемента в строке меню наведите указатель мыши на **Иерархии** и щелкните имя иерархии, содержащей элемент. Затем щелкните узел в иерархии, содержащий элемент.  
  
    -   коллекции в строке меню наведите указатель мыши на **Коллекции** и щелкните имя сущности, содержащей коллекцию.  
  
5.  Щелкните в сетке строку удаляемого элемента или коллекции.  
  
6.  Нажмите кнопку **Удалить элемент**, **Удалить**или **Удалить коллекцию**.  
  
7.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Повторная активация элемента или коллекции &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [Master Data Services &#40;членов&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Коллекции (службы Master Data Services)](../../2014/master-data-services/collections-master-data-services.md)  
  
  
