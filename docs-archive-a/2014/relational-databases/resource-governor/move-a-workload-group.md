---
title: Перемещение группы рабочей нагрузки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties_moveworkloadgroup.f1
helpviewer_keywords:
- workload groups [SQL Server], move
- Resource Governor, workload group move
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f73b48f0ec2255760b4ee55acfaf91dc02af7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731469"
---
# <a name="move-a-workload-group"></a>Перемещение группы рабочей нагрузки
  Группу рабочей нагрузки регулятора ресурсов можно переместить в другой пул ресурсов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью Transact-SQL.  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Перемещение группы рабочей нагрузки с использованием:**  [среды SQL Server Management Studio](#MoveWGSSMS), [Transact-SQL](#MoveWGTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
 Перемещение группы рабочей нагрузки становится невозможным, если имеется ожидающая выполнения операция настройки регулятора ресурсов.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Ограничения  
 Перемещение группы рабочей нагрузки становится невозможным, если имеется ожидающая выполнения операция настройки регулятора ресурсов. Чтобы выяснить, находится ли конфигурация в состоянии ожидания, выполните запрос к динамическому административному представлению [sys.dm_resource_governor_configuration (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql), получив текущее состояние is_configuration_pending.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для перемещения группы рабочей нагрузки требуется разрешение CONTROL SERVER.  
  
##  <a name="move-a-workload-group-using-sql-server-management-studio"></a><a name="MoveWGSSMS"></a> Перемещение группы рабочей нагрузки с использованием среды SQL Server Management Studio  
 **Перемещение группы рабочей нагрузки в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**  
  
1.  В обозревателе объектов рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши **Регулятор ресурсов** и выберите пункт **Свойства**, после чего откроется страница **Свойства регулятора ресурсов** .  
  
3.  В окне **Пулы ресурсов** щелкните пул ресурсов, содержащий группу рабочей нагрузки, которая должна быть перемещена. Теперь в окне **Группы рабочей нагрузки** появятся списки групп рабочей нагрузки в этом пуле ресурсов.  
  
4.  Чтобы переместить группу рабочей нагрузки, выделите соответствующую ей строку, щелкните правой кнопкой мыши указатель в начале строки и выберите команду **Переместить** , укажите новое расположение и нажмите кнопку **Переместить**. Будет отображено окно **Перемещение группы рабочей нагрузки** .  
  
5.  Доступные пулы ресурсов отображаются в окне. Щелкните имя пула ресурсов, в который нужно перенести группу рабочей нагрузки, а затем нажмите кнопку **ОК** , чтобы выполнить это действие.  
  
6.  Действие не завершено, пока не будет нажата кнопка **ОК**. При нажатии кнопки **ОК**выполняется инструкция ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
7.  Если операция создания или изменения конфигурации пула ресурсов или группы рабочей нагрузки завершилась неуспешно, под заголовком страницы свойств будет отображено сводное сообщение об ошибке. Чтобы просмотреть подробное сообщение об ошибке, щелкните стрелку вниз рядом с ним.  
  
##  <a name="move-a-workload-group-using-transact-sql"></a><a name="MoveWGTSQL"></a> Перемещение группы рабочей нагрузки с использованием Transact-SQL  
 **Перемещение группы рабочей нагрузки с использованием Transact-SQL**  
  
1.  Выполните инструкцию `ALTER WORKLOAD GROUP`, указав имя группы рабочей нагрузки для перемещения, и пул ресурсов, в который она должна быть перемещена.  
  
2.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано, как переместить группу рабочей нагрузки с именем `groupAdhoc` в пул ресурсов по умолчанию.  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](resource-governor.md)   
 [Активация регулятора ресурсов](enable-resource-governor.md)   
 [Создание пула ресурсов](create-a-resource-pool.md)   
 [Создание группы рабочей нагрузки](create-a-workload-group.md)   
 [ALTER WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/alter-workload-group-transact-sql)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
