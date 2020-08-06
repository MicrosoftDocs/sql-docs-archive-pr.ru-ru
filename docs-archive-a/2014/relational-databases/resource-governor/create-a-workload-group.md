---
title: Создание группы рабочей нагрузки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group create
- workload groups [SQL Server], create
ms.assetid: 072868ec-ceff-4db6-941b-281af731a067
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 144bcef57b3d6e191b03b1539e9e7382a9085c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658186"
---
# <a name="create-a-workload-group"></a>Создание группы рабочей нагрузки
  Группы рабочей нагрузки можно создавать в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Создание группы рабочей нагрузки с использованием:**  [среды SQL Server Management Studio](#CreWGProp), [Transact-SQL](#CreWGTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Ограничения  
 **REQUEST_MAX_MEMORY_GRANT_PERCENT**  
  
 Объем памяти, затрачиваемой на создание индекса в невыровненной секционированной таблице, пропорционален количеству секций, охватываемых индексом. Если общий объем необходимой памяти превышает лимит для каждого запроса (REQUEST_MAX_MEMORY_GRANT_PERCENT), установленный параметром для группы рабочей нагрузки, то создание этого индекса может завершиться ошибкой. Для обеспечения совместимости с версией SQL Server 2005 группа рабочей нагрузки по умолчанию позволяет запросу превысить лимит для каждого запроса с учетом минимального объема памяти, необходимого при запуске, поэтому пользователь может запустить тот же процесс создания индекса в группе рабочей нагрузки по умолчанию, если в пуле ресурсов по умолчанию достаточно памяти, настроенной для выполнения такого запроса.  
  
 Разрешено создание индексов для использования большего объема памяти рабочей области, чем было указано изначально, в целях повышения производительности. Эта специальная обработка поддерживается регулятором ресурсов, однако изначально предоставленная память и любая дополнительная выделенная память ограничены настройками группы рабочей нагрузки и пула ресурсов.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для создания группы рабочей нагрузки требуется разрешение CONTROL SERVER.  
  
##  <a name="create-a-workload-group-using-sql-server-management-studio"></a><a name="CreWGProp"></a> Создание группы рабочей нагрузки в среде SQL Server Management Studio  
 **Создание группы рабочей нагрузки с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  В обозревателе объектов рекурсивно разверните узел **Управление** вплоть до узла «Пул ресурсов», содержащего группу рабочей нагрузки, которую необходимо изменить.  
  
2.  Щелкните правой кнопкой мыши папку **Группы рабочей нагрузки** и выберите команду **Создать группу рабочей нагрузки**.  
  
3.  Убедитесь в том, что в сетке **Пулы ресурсов** выделен подсветкой пул ресурсов, в который должна быть добавлена группа рабочей нагрузки.  
  
4.  В сетке **Группы рабочей нагрузки для пула ресурсов** будет присутствовать новая строка с пустым именем и значениями по умолчанию в других столбцах.  
  
5.  Щелкните ячейку **Имя** и введите имя для группы рабочей нагрузки.  
  
6.  Щелкните или дважды щелкните все прочие ячейки в строке, для которых необходимо задать параметры, отличные от применяемых по умолчанию, и введите новые значения.  
  
7.  Чтобы сохранить изменения, нажмите кнопку **ОК**.  
  
##  <a name="create-a-workload-group-using-transact-sql"></a><a name="CreWGTSQL"></a> Создание группы рабочей нагрузки с помощью Transact-SQL  
 **Создание группы рабочей нагрузки с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Выполните инструкцию CREATE WORKLOAD GROUP, указав значения свойств, которые необходимо установить.  
  
2.  Выполните инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере создается группа рабочей нагрузки с именем `groupAdhoc` , которая находится в пуле ресурсов с именем `poolAdhoc`.  
  
```  
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](resource-governor.md)   
 [Активация регулятора ресурсов](enable-resource-governor.md)   
 [Создание пула ресурсов](create-a-resource-pool.md)   
 [Изменение параметров группы рабочей нагрузки](change-workload-group-settings.md)   
 [Создание и проверка определяемой пользователем функции-классификатора](create-and-test-a-classifier-user-defined-function.md)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/create-workload-group-transact-sql)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
