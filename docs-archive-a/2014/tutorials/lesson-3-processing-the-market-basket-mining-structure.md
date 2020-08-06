---
title: Занятие 3. Обработка структуры интеллектуального анализа данных для потребительской корзины | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce2c2e6944d524a38edc331d2cd128ca7cf7d419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727518"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a>Урок 3. Обработка структуры интеллектуального анализа данных «Потребительская корзина»
  На этом занятии для обработки структур и моделей интеллектуального анализа данных, созданных на занятии 1, вы будете использовать инструкцию [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) , а также VAssocSeqLineItems и vAssocSeqOrders в образце базы. для этого нужно создать структуру интеллектуального анализа данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] для [рынка](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) и [занятие 2: Добавление моделей интеллектуального анализа данных в структуру интеллектуального анализа данных для рынка](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).  
  
 При обработке структуры интеллектуального анализа данных службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] считывают исходные данные и создают структуры, поддерживающие модели интеллектуального анализа данных. При обработке модели интеллектуального анализа данных, данные, определенные структурой интеллектуального анализа данных, обрабатываются выбранным алгоритмом интеллектуального анализа данных. Алгоритм находит тренды и шаблоны и сохраняет эти данные в модели интеллектуального анализа данных. Поэтому в модели интеллектуального анализа данных содержатся не фактические исходные данные, а данные, выявленные алгоритмом. Дополнительные сведения об обработке моделей интеллектуального анализа данных см. в разделе [требования к обработке и рекомендации &#40;&#41;интеллектуального анализа ](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Повторная обработка структуры интеллектуального анализа данных нужна только в случае, когда изменяются столбцы структуры или исходные данные. При добавлении модели интеллектуального анализа данных к уже обработанной структуре интеллектуального анализа данных, можно использовать инструкцию `INSERT INTO MINING MODEL` для обучения новой модели интеллектуального анализа данных с помощью существующих данных.  
  
 Так как структура интеллектуального анализа данных «Потребительская корзина» содержит вложенную таблицу, потребуется определить столбцы интеллектуального анализа данных, которые нужно обучить с помощью структуры этой таблицы, и использовать команду `SHAPE`, чтобы определить запросы, которые получат обучающие данные из исходных таблиц.  
  
## <a name="insert-into-statement"></a>Инструкция INSERT INTO  
 Чтобы обучить структуру интеллектуального анализа данных «Потребительская корзина» и связанные с ней модели интеллектуального анализа данных, используйте инструкцию [INSERT в &#40;DMX&#41;](/sql/dmx/insert-into-dmx) . Код инструкции можно разбить на следующие части.  
  
-   Определение структуры интеллектуального анализа данных  
  
-   Список столбцов структуры интеллектуального анализа  
  
-   Определение обучающих данных с помощью инструкции `SHAPE`  
  
 Далее приведен общий пример инструкции `INSERT INTO`:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],'<nested SELECT statement>')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 В первой строчке кода задается структура интеллектуального анализа данных, которую необходимо обучить:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Следующие строки кода указывают столбцы, определенные структурой интеллектуального анализа данных. Необходимо перечислить все столбцы структуры интеллектуального анализа данных, и каждый столбец должен сопоставляться с каким-либо столбцом из данных исходного запроса. Можно использовать инструкцию `SKIP`, чтобы не обрабатывать столбцы, существующие в исходных данных, но не в структуре интеллектуального анализа данных. Дополнительные сведения об использовании `SKIP` см. [в разделе вставка в &#40;DMX&#41;](/sql/dmx/insert-into-dmx).  
  
```  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
```  
  
 Последние строки кода определяют данные, которые будут использованы для обучения структуры интеллектуального анализа данных. Так как исходные данные содержатся в двух таблицах, для их связывания будет использована инструкция `SHAPE`.  
  
```  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],''<nested SELECT statement>'')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 На этом занятии требуется определить исходные данные с помощью инструкции `OPENQUERY`. Дополнительные сведения о других методах определения запроса к исходным данным см. в разделе [&#60;Source Data query&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии требуется выполнить следующую задачу:  
  
-   Обработка структуры интеллектуального анализа данных «Потребительская корзина»  
  
## <a name="processing-the-market-basket-mining-structure"></a>Обработка структуры интеллектуального анализа данных «Потребительская корзина»  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>Обработка структуры интеллектуального анализа данных с помощью инструкции INSERT INTO  
  
1.  В окне **Обозреватель объектов**щелкните правой кнопкой мыши экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], укажите **Создать запрос**, а затем выберите пункт **Расширения интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
2.  Скопируйте стандартный пример использования инструкции INSERT INTO в пустое окно запроса.  
  
3.  Вместо  
  
    ```  
    [<mining structure>]  
    ```  
  
     на:  
  
    ```  
    Market Basket  
    ```  
  
4.  Вместо  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     на:  
  
    ```  
    [OrderNumber],  
    [Products]   
    (SKIP, [Model])  
    ```  
  
     В инструкции параметр `Products` относится к таблице продуктов, определенной инструкцией SHAPE. Столбец `SKIP` используется для пропуска столбца «Model», который существует в исходных данных в качестве ключа, но не используется структурой интеллектуального анализа данных.  
  
5.  Вместо  
  
    ```  
    SHAPE {  
      OPENQUERY([<datasource>],'<SELECT statement>') }  
    APPEND  
    (   
      {OPENQUERY([<datasource>],'<nested SELECT statement>')  
    }  
    RELATE [<case key>] TO [<foreign key>]  
    ) AS [<nested table>]  
    ```  
  
     на:  
  
    ```  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
     Исходный запрос ссылается на [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] источник данных, определенный в [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] образце проекта. Он использует этот источник данных для доступа к представлениям vAssocSeqLineItems и vAssocSeqOrders. Эти представления содержат исходные данные, которые будут использованы для обучения модели интеллектуального анализа данных. Если вы не создали этот проект или эти представления, см. [учебник по основам интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
     Внутри команды `SHAPE` будет использоваться предложение `OPENQUERY` для определения двух запросов. Первый запрос определяет родительскую таблицу, второй — вложенную. Две таблицы связаны с помощью столбца OrderNumber, который присутствует в обеих таблицах.  
  
     Полная инструкция теперь должна выглядеть следующим образом.  
  
    ```  
    INSERT INTO MINING STRUCTURE [Market Basket]  
    (  
       [OrderNumber],[Products] (SKIP, [Model])  
    )  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
6.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
7.  В диалоговом окне **Сохранить как** перейдите в соответствующую папку и присвойте файлу имя `Process Market Basket.dmx` .  
  
8.  На панели инструментов нажмите кнопку **Выполнить** .  
  
 После завершения выполнения запроса можно просмотреть найденные закономерности и наборы элементов, просмотреть взаимосвязи или фильтровать результаты в зависимости от набора элементов, вероятности или важности. Чтобы просмотреть эти сведения, в щелкните [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] правой кнопкой мыши имя модели данных, а затем нажмите кнопку **Обзор**.  
  
 В следующем занятии будут созданы несколько прогнозов, основанных на моделях интеллектуального анализа данных, которые были добавлены в структуру «Потребительская корзина».  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 4: Прогнозирование покупательского поведения](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
