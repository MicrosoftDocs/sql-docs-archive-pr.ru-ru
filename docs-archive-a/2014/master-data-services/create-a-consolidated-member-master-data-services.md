---
title: Создание объединенного элемента (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c41673f6f3bf1f4de2a831ecd659321b273b6af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734209"
---
# <a name="create-a-consolidated-member-master-data-services"></a>Create a Consolidated Member (Master Data Services)
  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]объединенный элемент создается, когда нужен родительский узел для явной иерархии. Консолидированные элементы могут содержать собственные атрибуты. Они используются для группировки. Как показано в следующем примере, консолидированные элементы можно использовать для групп учетных записей, содержащих учетные записи.

 ![Консолидированные члены MDS](../../2014/master-data-services/media/mds-consolidated-members.png "Консолидированные члены MDS")

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этой процедуры:

-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .

-   как минимум, необходимо разрешение **Обновление** на объединенный объект модели для сущности, в которую нужно добавить элемент.

### <a name="to-create-a-consolidated-member"></a>Создание объединенного элемента

1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .

2.  Выберите версию из списка **Версия** .

3.  Нажмите кнопку **Браузер**.

4.  В строке меню наведите указатель мыши на **Иерархии** и щелкните имя иерархии, к которой нужно добавить объединенный элемент.

5.  Над сеткой выберите вариант **Консолидированные элементы** или **Все Консолидированные элементы в иерархии** .

6.  Нажмите кнопку **Добавить**.

7.  Заполните поля на панели справа.

8.  Необязательный элемент. В поле **Заметки** введите комментарий о том, для чего добавлен элемент. Заметку могут просматривать все пользователи, которые имеют доступ к элементу.

9. Нажмите кнопку **ОК**.

## <a name="next-steps"></a>Next Steps

-   [Перемещение элементов в иерархии &#40;Master Data Services&#41;](move-members-within-a-hierarchy-master-data-services.md)

## <a name="see-also"></a>См. также:
 [Создание явной иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [создания конечного элемента &#40;Master Data Services](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)&#41;[загрузки или обновления элементов в Master Data Services с помощью элементов промежуточного процесса](add-update-and-delete-data-master-data-services.md) [&#40;Master Data Services](../../2014/master-data-services/members-master-data-services.md)&#41;[явных иерархий &#40;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) Master Data Services&#41;


