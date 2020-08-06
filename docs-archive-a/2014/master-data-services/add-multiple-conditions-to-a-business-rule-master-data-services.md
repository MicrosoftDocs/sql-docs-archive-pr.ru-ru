---
title: Добавление нескольких условий к бизнес-правилу (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c62b8dfa4f459958d12bd384b85aa74bef382b21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666113"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>Добавление нескольких условий к бизнес-правилу (службы Master Data Services)
  Чтобы в среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]создать более сложное бизнес-правило, к нему с помощью операторов **AND** и **OR** можно добавить несколько условий.  
  
> [!NOTE]  
>  Если в создаваемом бизнес-правиле используется оператор **OR** , рассмотрите возможность создания отдельного правила для каждой из условных инструкций, которые можно применить независимо. При необходимости правила можно исключать, что повышает гибкость и упрощает устранение неполадок.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Должно существовать бизнес-правило. Дополнительные сведения см. в разделе [Создание и публикация бизнес-правила (службы Master Data Services)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>Добавление нескольких условий в бизнес-правило  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Обслуживание бизнес-правил** выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  В списке **тип члена** выберите тип члена.  
  
6.  Выберите из списка **Атрибут** атрибут или оставьте **Все**по умолчанию.  
  
7.  Щелкните строку, где указано бизнес-правило, которое требуется изменить.  
  
8.  Нажмите **Изменить выбранное бизнес-правило**.  
  
9. В области **компоненты** разверните узел **логические операторы** .  
  
10. Щелкните **и** или **или** и перетащите его в область **и** метку **If** .  
  
11. На панели **Компоненты** разверните узел **Условия** .  
  
12. Щелкните условие и перетащите его в область **If** , в метку **и** или **или** из шага 10.  
  
13. На панели **атрибуты** щелкните атрибут и перетащите его на значок **Выбор атрибута** в области **изменить условие** .  
  
14. На панели **Изменение условия** заполните все обязательные поля.  
  
15. На панели **Изменение условия** нажмите кнопку **Сохранить элемент**.  
  
16. При необходимости, чтобы добавить дополнительные условия, в области **компоненты** перетащите объект **и** или **или** в любой элемент **и** или **или в** область **If** . Затем выполните шаги 13–15.  
  
    > [!TIP]  
    >  Чтобы удалить условие, щелкните имя условия и на панели **изменить условие** нажмите кнопку **удалить элемент**.  
  
## <a name="see-also"></a>См. также:  
 [Бизнес-правила &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Измените имя бизнес-правила &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Настройка в бизнес-правилах отправки уведомлений (службы Master Data Services)](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  