---
title: Занятие 2. Задание информации о соединении (службы Reporting Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c187f0abdc4b277a5f1428407b5c42ca4fd6fee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731426"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Занятие 2. Задание информации о соединении (службы Reporting Services)
  После добавления отчета к проекту Tutorial следует задать *источник данных*, который представляет собой сведения о соединении, используемые отчетом для доступа к данным, которые располагаются в реляционной базе данных, многомерной базе данных или ином ресурсе.  
  
 В этом занятии в качестве источника данных используется образец базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]. В этом учебнике предполагается, что эта база данных находится в экземпляре по умолчанию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] , установленном на локальном компьютере.  
  
### <a name="to-set-up-a-connection"></a>Настройка соединения  
  
1.  В области **данных отчета** нажмите кнопку **создать** , а затем выберите **источник данных..**..  
  
    > [!NOTE]  
    >  Если область **Данные отчета** не отображается, в меню **Вид** выберите пункт **Данные отчета**.  
  
2.  В поле **Имя**введите [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].  
  
3.  Убедитесь в том, что выбран параметр **Внедренное соединение** .  
  
4.  В поле **Тип**выберите **Microsoft SQL Server**.  
  
5.  В поле **Строка подключения**введите следующее:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     Эта строка соединения подразумевает, что на локальном компьютере установлены среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], сервер отчетов и база данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] , а у пользователя имеется разрешение на подключение к базе данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  
  
    > [!NOTE]  
    >  В случае использования версии [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services или именованного экземпляра строка соединения должна включать сведения об экземпляре:  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  Дополнительные сведения о строках подключения см. [в разделе подключения к данным, источники данных и строки подключения в Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) и [диалоговом окне Свойства источника данных — Общие](data-source-properties-dialog-box-general.md).  
  
6.  На панели слева щелкните **Учетные данные** и выберите **Использовать проверку подлинности Windows (встроенная безопасность)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]Источник данных [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] добавляется в область **данных отчета** .  
  
## <a name="next-task"></a>Следующая задача  
 Соединение с образцом базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] успешно создано. Далее предстоит создать отчет. См. [Занятие 3. Определение набора данных для табличного отчета (службы Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Подключения данных, Источники данных и Строки подключения в службе Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
