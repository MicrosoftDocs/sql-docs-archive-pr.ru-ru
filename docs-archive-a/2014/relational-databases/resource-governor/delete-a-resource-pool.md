---
title: Удаление пула ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a67b0e2262fa3007597091b6087cc937bb0f3276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731478"
---
# <a name="delete-a-resource-pool"></a>Удаление пула ресурсов
  Регулятор ресурсов можно удалить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью Transact-SQL.  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Удаление пула ресурсов с использованием:** [среды SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
 Пул ресурсов нельзя удалить, если он содержит группы рабочей нагрузки.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Ограничения  
 Нельзя удалять пулы регулятора ресурсов по умолчанию или внутренние пулы ресурсов. Пул ресурсов нельзя удалить, если он содержит группы рабочей нагрузки. Дополнительные сведения см. в статье [Delete a Workload Group](delete-a-workload-group.md).  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для удаления пула ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="delete-a-resource-pool-using-object-explorer"></a><a name="DelRPSSMS"></a> Удаление пула ресурсов с помощью обозревателя объектов  
 **Удаление пула ресурсов в среде SQL Server Management Studio**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши пул ресурсов, который необходимо удалить, а затем нажмите кнопку **Удалить**.  
  
3.  В окне **Удаление объекта** этот пул ресурсов будет указан в списке **Объект для удаления** . Чтобы удалить пул ресурсов, нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  Если удаляемый пул ресурсов содержит группы рабочей нагрузки, удалить его не удастся.  
  
##  <a name="delete-a-resource-pool-using-transact-sql"></a><a name="DelRPTSQL"></a> Удаление пула ресурсов с помощью Transact-SQL  
 **Удаление пула ресурсов с помощью Transact-SQL**  
  
1.  Выполните инструкцию `DROP RESOURCE POOL`, указав имя пула ресурсов, который необходимо удалить.  
  
2.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере удаляется группа рабочей нагрузки с именем `poolAdhoc`.  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](resource-governor-resource-pool.md)   
 [Создание пула ресурсов](create-a-resource-pool.md)   
 [Изменение параметров пула ресурсов](change-resource-pool-settings.md)   
 [Группа рабочей нагрузки регулятора ресурсов](resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](resource-governor-classifier-function.md)   
 [DROP WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/drop-workload-group-transact-sql)   
 [DROP RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/drop-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
