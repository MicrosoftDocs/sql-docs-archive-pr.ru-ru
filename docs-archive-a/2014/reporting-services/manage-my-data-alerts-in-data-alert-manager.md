---
title: Управление предупреждениями данных в диспетчере предупреждений данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 371c62c2f97334e20280a659c8039ab20852ccfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736125"
---
# <a name="manage-my-data-alerts-in-data-alert-manager"></a>Управление предупреждениями данных в диспетчере предупреждений данных
  Пользователи SharePoint могут просматривать список созданных ими предупреждений об изменении данных и сведения о них. Также вы можете удалять свои предупреждения, открывать определения предупреждений для их изменения в конструкторе предупреждений об изменении данных и запускать свои предупреждения. На следующем рисунке показаны функции, доступные пользователям в диспетчере предупреждений об изменении данных.  
  
 ![Возможности диспетчера предупреждений для пользователей SharePoint](media/rs-alertmanageriw.gif "Возможности диспетчера предупреждений для пользователей SharePoint")  
  
### <a name="to-view-a-list-of-your-alerts"></a>Просмотр списка своих предупреждений  
  
1.  Перейдите к библиотеке документов SharePoint, в которой сохранены отчеты, для которых были созданы предупреждения об изменении данных.  
  
2.  Щелкните значок, чтобы развернуть раскрывающееся меню для отчета, и выберите пункт **Управление предупреждениями об изменении данных**. Раскрывающееся меню показано на следующем рисунке.  
  
     ![Открытие конструктора предупреждений из контекстного меню отчета](media/rs-openalertmanager.gif "Открытие конструктора предупреждений из контекстного меню отчета")  
  
     Откроется диспетчер предупреждений об изменении данных. По умолчанию в нем перечислены предупреждения для отчета, выбранного в библиотеке.  
  
3.  Щелкните стрелку вниз рядом со списком **Просмотр предупреждений для отчета** и выберите отчет для просмотра его предупреждений или нажмите кнопку **Показать все** , чтобы получить список всех предупреждений.  
  
    > [!NOTE]  
    >  Если выбранный отчет не имеет предупреждений, то возвращаться в библиотеку и искать отчет, имеющий их, не требуется. Вместо этого щелкните **Показать все** , чтобы увидеть список всех предупреждений.  
  
     Таблица содержит имя предупреждения, имя отчета, ваше имя в качестве имени создателя предупреждения, сколько раз предупреждение было отправлено, время последнего изменения определения предупреждения и состояние предупреждения. Если предупреждение не удалось создать или отправить, в столбце состояния содержатся сведения об ошибке, которые помогают устранить проблему.  
  
### <a name="to-edit-an-alert-definition"></a>Редактирование определения предупреждения  
  
-   Щелкните правой кнопкой мыши предупреждение, определение которого требуется изменить, и выберите **Изменить**.  
  
     Определение предупреждения откроется в конструкторе предупреждений об изменении данных. Дополнительные сведения см. в разделах [Изменение предупреждения в конструкторе предупреждений](edit-a-data-alert-in-alert-designer.md) и [Конструктор предупреждений данных](../../2014/reporting-services/data-alert-designer.md).  
  
    > [!NOTE]  
    >  Изменить определение предупреждения об изменении данных может только пользователь, который его создал.  
  
    > [!NOTE]  
    >  Если отчет был изменен и изменились веб-каналы данных, созданные на основе отчета, то определение предупреждения может стать недопустимым. Это происходит, когда столбец, на который ссылается предупреждение в своих правилах, удаляется из отчета, меняет тип данных или включается в другой веб-канал данных или в случае, когда отчет был удален или перемещен. Недопустимое определение предупреждения можно открыть, но нельзя повторно сохранить до тех пор, пока оно не станет допустимым для текущей версии веб-канала данных отчета, на котором оно основано. Дополнительные сведения о создании веб-каналов данных на основе отчетов см. в разделе [Формирование веб-каналов данных из отчетов (построитель отчетов и службы SSRS)](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
### <a name="to-delete-an-alert-definition"></a>Удаление определения предупреждения  
  
-   Щелкните правой кнопкой мыши предупреждение об изменении данных, которое необходимо удалить, и выберите пункт **Удалить**.  
  
     Если предупреждение было удалено, дальнейшая отправка предупреждающих сообщений прекращается.  
  
### <a name="to-run-an-alert"></a>Запуск предупреждения  
  
-   Щелкните правой кнопкой мыши предупреждение об изменении данных, которое необходимо запустить, и выберите пункт **Запустить**.  
  
     Вне зависимости от того, какие параметры расписания были заданы в диспетчере предупреждений об изменении данных, будет создан экземпляр предупреждения и будет немедленно отправлено предупреждающее сообщение. Например, предупреждение, настроенное на еженедельную отправку и только в случае изменения результатов.  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер предупреждений данных для оповещения администраторов](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Предупреждения об изменении данных в службах Reporting Services](../ssms/agent/alerts.md)  
  
  