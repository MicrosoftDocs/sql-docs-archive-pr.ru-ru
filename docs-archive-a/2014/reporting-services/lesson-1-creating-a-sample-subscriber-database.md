---
title: Занятие 1. Создание образца базы данных подписчика | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ee49f0858b28c0c4b00fd391b0db7b4d2c54b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751808"
---
# <a name="lesson-1-creating-a-sample-subscriber-database"></a>Занятие 1. Создание образца базы данных подписчика
  Для определения управляемой данными подписки нужен источник данных, предоставляющий данные подписки. На этом этапе будет создана небольшая база данных для хранения данных подписки, используемых при работе с этим учебником. Позже, после обработки подписки, сервер отчетов получит эти данные и использует их для настройки выходных данных отчетов, параметров доставки и формата представления отчетов.  
  
 В этом занятии предполагается, что вы используете [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] для создания [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] базы данных.  
  
### <a name="to-create-a-sample-subscriber-database"></a>Создание образца базы данных подписчика  
  
1.  Запустите среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] и установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Щелкните правой кнопкой мыши "Базы данных" и выберите команду **Создать базу данных...**  
  
3.  В диалоговом окне Создание базы данных в поле Имя базы данных введите *Подписчики*. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  Нажмите кнопку **Создать запрос** на панели инструментов.  
  
5.  Скопируйте следующие инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] в пустой запрос:  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
6.  Нажмите кнопку **! Выполнить** на панели инструментов.  
  
7.  С помощью инструкции SELECT удостоверьтесь, что создано три строки данных. Например: `select * from OrderInfo`  
  
## <a name="next-steps"></a>Next Steps  
 Успешно завершено создание данных подписки, которые будут управлять распространением отчетов и изменять выходные данные отчетов в соответствии с параметрами настройки для каждого из подписчиков. Далее предстоит изменить свойства источника данных отчета, который будет распространяться среди подписчиков. Изменение свойств источника данных нужно, чтобы подготовить отчет для распространения управляемой данными подписки. Вы также измените конструкцию отчета, включив в нее параметр, который будет использоваться подпиской с данными подписчика. [Занятие 2. изменение свойств источника данных отчета](lesson-2-modifying-the-report-data-source-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание управляемой данными подписки (учебник по службам SSRS)](create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Создание базы данных](../relational-databases/databases/create-a-database.md)   
 [Создание простого табличного отчета (учебник по службам SSRS)](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
