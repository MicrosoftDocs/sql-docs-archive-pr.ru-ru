---
title: Изменение проверочного ограничения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8377c80590612c8b68c315f7c37823eb8f5c5093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665250"
---
# <a name="modify-check-constraints"></a>Изменение проверочного ограничения
  Изменение проверочных ограничений в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] осуществляется в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] , если необходимо изменить выражение ограничения или параметры, включающие или отключающие ограничение для конкретных условий.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Изменение проверочного ограничения с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-check-constraint"></a>Изменение проверочного ограничения  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, содержащую проверочное ограничение, и выберите пункт **Конструктор**.  
  
2.  В меню **Конструктор таблиц** выберите **Проверочные ограничения...** .  
  
3.  В диалоговом окне **Проверочные ограничения** выберите ограничение, которое нужно изменить, из списка **Выбранное проверочное ограничение**.  
  
4.  Выполните действие из следующей таблицы.  
  
    |Чтобы|Выполните следующее|  
    |--------|------------------------|  
    |Изменить выражение ограничения|Введите новое выражение в поле **Выражение** .|  
    |Переименуйте ограничение|Введите новое имя в поле **Имя** .|  
    |Применить ограничение к существующим данным|Установите флажок **Проверить существующие данные при создании или включении** .|  
    |Отключить ограничение при добавлении в таблицу новых данных или обновлении существующих данных таблицы.|Снимите флажок **Принудительное ограничение для инструкций INSERT и UPDATE** .|  
    |Отключить ограничение при вставке или обновлении данных в таблице агентом репликации.|Снимите флажок **Включить использование для репликации** .|  
  
    > [!NOTE]  
    >  В некоторых базах данных проверочные ограничения различаются по функциональности.  
  
5.  Щелкните **Закрыть**.  
  
6.  В меню **Файл** выберите пункт **Сохранить**_table name_.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение проверочного ограничения**  
  
 Чтобы изменить ограничение `CHECK` с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)], нужно удалить существующее ограничение `CHECK` и повторно создать его с новым определением. Дополнительные сведения см. в разделах [Удаление проверочного ограничения](delete-check-constraints.md) и [Создание ограничений CHECK](create-check-constraints.md).  
  
###  <a name="TsqlExample"></a>  
