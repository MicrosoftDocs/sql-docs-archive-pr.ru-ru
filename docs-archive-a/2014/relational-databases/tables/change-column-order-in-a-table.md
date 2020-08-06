---
title: Изменение порядка столбцов в таблице | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d162f9dc793ceb9ea423d94922f7358f1729712e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664100"
---
# <a name="change-column-order-in-a-table"></a>Изменение порядка столбцов в таблице
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] порядок столбцов можно изменить в конструкторе таблиц с использованием [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!CAUTION]  
>  Изменение порядка столбцов в таблицы влияет на коды и приложения, которые зависят от определенного порядка столбцов. Это касается запросов, представлений, хранимых процедур, определяемых пользователем функций и клиентских приложений. Внимательно рассмотрите любые изменения, которые необходимо сделать со столбцом таблицы. Рекомендуется указывать порядок, в котором возвращаются столбцы, на уровне приложения и запроса. Не следует предполагать, что SELECT * будет возвращать все столбцы в ожидаемом порядке, основанном на порядке их определения в таблице. Всегда указывайте столбцы в запросах и приложениях по именам в том порядке, в котором они должны следовать.  
  
 **В этом разделе**  
  
-   **Изменение порядка столбцов с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-change-the-column-order"></a>Изменение порядка столбцов  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу со столбцами, которые нужно переупорядочить, и выберите пункт **Конструктор**.  
  
2.  Выберите окно, находящееся слева от названия столбца, который нужно переупорядочить.  
  
3.  Перетащите столбец в другое местоположение внутри таблицы.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение порядка столбцов**  
  
 Эту задачу нельзя выполнить с помощью инструкций Transact-SQL.  
  
###  <a name="TsqlExample"></a>  
