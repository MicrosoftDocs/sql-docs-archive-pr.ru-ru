---
title: Добавление в отчет параметра с несколькими значениями | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5269293b6a21f3b1d82eb6835efbd275e3be9620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729078"
---
# <a name="add-a-multi-value-parameter-to-a-report"></a>Добавление в отчет параметра с несколькими значениями
  В отчет можно добавить параметр, который позволит пользователю выбирать несколько значений для этого параметра.  
  
 Можно передавать отчету несколько значений параметра в URL-адресе отчета. Пример URL-адреса, содержащего многозначный параметр, см. в разделе [Передача параметров отчета в URL-адресе](../pass-a-report-parameter-within-a-url.md).  
  
 Сведения о том, как передавать несколько значений параметра хранимой процедуре, см. в статье [Working With Multi-Select Parameters for SSRS Reports](https://go.microsoft.com/fwlink/?LinkId=321529) (Работа с многозначными параметрами для отчетов служб SSRS) на сайте mssqltips.com.  
  
### <a name="to-add-a-multi-value-parameter"></a>Добавление многозначного параметра  
  
1.  В построителе отчетов откройте отчет, в который требуется добавить многозначный параметр.  
  
2.  Щелкните правой кнопкой мыши набор данных отчета и выберите пункт **Свойства набора данных**.  
  
3.  Добавьте переменную в запрос к набору данных, либо изменив текст запроса в поле **Запрос** , либо добавив фильтр с помощью конструктора запросов. Дополнительные сведения см. в статье [Построение запроса в конструкторе реляционных запросов (построитель отчетов и службы SSRS)](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).  
  
    > [!IMPORTANT]  
    >  Текст запроса не должен включать инструкцию DECLARE для переменной запроса.  
  
    > [!IMPORTANT]  
    >  Текст для переменной запроса должен содержать оператор `IN`, как показано в следующем примере.  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  Если не включить круглые скобки вокруг переменной, как показано выше, отчет не будет отображен и отобразится сообщение об ошибке "необходимо объявить скалярную переменную".  
  
     Параметр набора данных для внедренного или общего набора данных создается для переменной запроса автоматически. Параметр отчета создается автоматически для параметра набора данных.  
  
4.  В области **Данные отчета** разверните узел **Параметры** , щелкните правой кнопкой мыши параметр отчета, созданный автоматически для параметра набора данных, а затем щелкните **Свойства параметра**.  
  
5.  На вкладке **Общие** выберите **Разрешить несколько значений** , чтобы позволить пользователю выбирать несколько значений для этого параметра.  
  
6.  На вкладке значений **Доступные** укажите список значений, которые могут быть отображены для пользователя (необязательно).  
  
     Список допустимых значений ограничивает значения, которые может выбрать пользователь, набором допустимых значений. В случае нескольких значений в верхней позиции списка будет расположено значение **Выделить все** , предоставляя пользователю возможность выбрать или очистить все значения одним щелчком. Если значения, доступные для параметра отчета, выбираются из запроса к набору данных, следует выбрать набор данных, который не содержит переменной запроса, которая связана с тем же параметром запроса.  
  
     Дополнительные сведения см. в разделе [Добавление, изменение и удаление допустимых значений параметра отчета (построитель отчетов и службы SSRS)](add-change-or-delete-available-values-for-a-report-parameter.md).  
  
### <a name="to-add-a-multi-value-parameter"></a>Добавление многозначного параметра  
  
1.  В построителе отчетов откройте отчет, в который требуется добавить многозначный параметр.  
  
2.  Щелкните правой кнопкой мыши набор данных отчета и выберите пункт **Свойства набора данных**.  
  
3.  Добавьте переменную в запрос к набору данных, либо изменив текст запроса в поле **Запрос** , либо добавив фильтр с помощью конструктора запросов. Дополнительные сведения см. в статье [Построение запроса в конструкторе реляционных запросов (построитель отчетов и службы SSRS)](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).  
  
    > [!IMPORTANT]  
    >  Текст запроса не должен включать инструкцию DECLARE для переменной запроса.  
  
    > [!IMPORTANT]  
    >  Текст для переменной запроса должен содержать оператор `IN`, как показано в следующем примере.  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  Если не включить круглые скобки вокруг переменной, как показано выше, отчет не будет отображен и отобразится сообщение об ошибке "необходимо объявить скалярную переменную".  
  
     Параметр набора данных для внедренного или общего набора данных создается для переменной запроса автоматически. Параметр отчета создается автоматически для параметра набора данных.  
  
4.  В области **Данные отчета** разверните узел **Параметры** , щелкните правой кнопкой мыши параметр отчета, созданный автоматически для параметра набора данных, а затем щелкните **Свойства параметра**.  
  
5.  На вкладке **Общие** выберите **Разрешить несколько значений** , чтобы позволить пользователю выбирать несколько значений для этого параметра.  
  
6.  На вкладке значений **Доступные** укажите список значений, которые могут быть отображены для пользователя (необязательно).  
  
     Список допустимых значений ограничивает значения, которые может выбрать пользователь, набором допустимых значений. В случае нескольких значений в верхней позиции списка будет расположено значение **Выделить все** , предоставляя пользователю возможность выбрать или очистить все значения одним щелчком. Если значения, доступные для параметра отчета, выбираются из запроса к набору данных, следует выбрать набор данных, который не содержит переменной запроса, которая связана с тем же параметром запроса.  
  
     Дополнительные сведения см. в разделе [Добавление, изменение и удаление допустимых значений параметра отчета (построитель отчетов и службы SSRS)](add-change-or-delete-available-values-for-a-report-parameter.md).  
  
## <a name="see-also"></a>См. также:  
 [Добавление каскадных параметров в построитель отчетов &#40;отчетов и SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Добавление, изменение или удаление параметра отчета (построитель отчетов и службы SSRS)](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  