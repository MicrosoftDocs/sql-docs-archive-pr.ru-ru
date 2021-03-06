---
title: Указание пути расположения (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dfa1717afe55c1599ccaba4b5d044c6e5a20e84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664807"
---
# <a name="specifying-a-location-path-sqlxml-40"></a>Указание пути доступа (SQLXML 4.0)
  Запросы XPath указываются в форме выражения. Существуют различные типы выражений. Путь доступа представляет собой выражение для выбора набора узлов относительно контекстного узла. Результатом вычисления пути доступа является набор узлов.  
  
## <a name="types-of-location-paths"></a>Типы путей доступа  
 Путь доступа может иметь две следующие формы.  
  
-   **Абсолютный путь доступа**  
  
     Абсолютный путь доступа начинается с корневого узла документа. Он состоит из косой черты (/), за которой необязательно следует относительный путь доступа. Косая черта (/) выбирает корневой узел документа.  
  
-   **Относительный путь доступа**  
  
     Относительный путь доступа начинается с контекстного узла документа. Путь доступа состоит из последовательности одного или нескольких шагов доступа, разделенных косой чертой (/). Каждый шаг доступа выбирает набор узлов относительно контекстного узла. Начальная последовательность шагов доступа выбирает набор узлов относительно контекстного узла. Каждый узел в этом наборе используется как контекстный узел для следующего шага доступа. Наборы узлов, определенные этим шагом, соединяются. Например, **дочерний элемент:: Order/child:: OrderDetail** выбирает **\<OrderDetail>** дочерние элементы **\<Order>** дочерних элементов узла контекста.  
  
    > [!NOTE]  
    >  В реализации XPath в SQLXML 4.0 каждый запрос XPath начинается в корневом контексте, даже если XPath не является явно абсолютным. Например, запрос XPath, начинающийся с «Customer» рассматривается как «/Customer». В запросе XPath **Customer [Order]** клиент начинает с корневого контекста, но порядок начинается в контексте клиента. Дополнительные сведения см. [в статье Введение в использование XPath запросов &#40;SQLXML 4,0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="location-steps"></a>Шаги доступа  
 Путь доступа (абсолютный или относительный) состоит из шагов доступа, составленных из следующих трех частей.  
  
-   **Ось**  
  
     Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются оси `parent`, `child`, `attribute` и `self`. Если ось `child` задана в пути доступа, все узлы, выбранные запросом, будут дочерними элементами контекстного узла. Если задана ось `parent`, выбранный узел будет родительским узлом контекстного узла. Если задана ось `attribute`, выбранные узлы будут атрибутами контекстного узла.  
  
-   **Проверка узла**  
  
     Проверка узла задает тип узла, выбранного на шаге доступа. Каждая ось (`child`, `parent`, `attribute` и `self`) имеет основной тип узла. Для `attribute` оси тип основного узла — **\<attribute>** . Для `parent` осей, `child` и `self` Тип основного узла — **\<element>** .  
  
     Например, если путь к расположению определяет **дочерний элемент:: Customer**, **\<Customer>** выбираются дочерние элементы узла контекста. Так как `child` ось имеет **\<element>** Тип основного узла, проверка узла, Customer, принимает значение true, если клиент является **\<element>** узлом.  
  
-   **Предикаты выбора (ноль или больше)**  
  
     Предикат фильтрует набор узлов относительно оси. Указание предикатов выбора в выражении XPath напоминает указание предложения WHERE в инструкции SELECT. Предикат указывается в квадратных скобках. Применение проверки, указанной в предикатах выбора, фильтрует узлы, возвращаемые проверкой узла. Для каждого узла в фильтруемом наборе узлов выражение предиката вычисляется с этим узлом в качестве узла контекста, а количество узлов в наборе определяет размер контекста. Если для данного узла выражение предиката дает значение TRUE, то узел включается в результирующий набор узлов.  
  
     Синтаксис шага доступа: имя оси и проверки узла, разделенные двумя двоеточиями, за которыми следует ноль или более выражений — каждое в квадратных скобках. Например, выражение XPath (путь расположения) **дочерний:: Customer [ @CustomerID = ' ALFKI ']** выбирает все **\<Customer>** дочерние элементы узла контекста. Затем тест в предикате применяется к набору узлов, который возвращает только **\<Customer>** узлы элементов со значением "ALFKI" атрибута **CustomerID** .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Указание оси &#40;SQLXML 4,0&#41;](specifying-an-axis-sqlxml-4-0.md)  
 Содержит примеры указания оси.  
  
 [Указание проверки узла в пути расположения &#40;SQLXML 4,0&#41;](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 Содержит примеры указания проверки узла.  
  
 [Указание предикатов выбора в пути расположения &#40;SQLXML 4,0&#41;](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 Содержит примеры указания предикатов выбора.  
  
  
