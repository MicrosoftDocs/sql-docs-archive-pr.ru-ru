---
title: Включение или отключение сбора данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], disabling
- data collector [SQL Server], enabling
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af5cc647a63d3a9451086fc9e2211dec809e88fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656418"
---
# <a name="enable-or-disable-data-collection"></a>Включение или отключение сбор данных
  В этом разделе описывается включение и отключение сбора данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Включение или отключение сбора данных с помощью следующих средств**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных **dc_admin** или **dc_operator** (с разрешением EXECUTE).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-enable-the-data-collector"></a>Включение сборщика данных  
  
1.  В обозревателе объектов раскройте узел **Управление** .  
  
2.  Щелкните правой кнопкой мыши **Сбор данных**, затем выберите **Включить сбор данных**.  
  
#### <a name="to-disable-the-data-collector"></a>Отключение сборщика данных  
  
1.  В обозревателе объектов раскройте узел **Управление** .  
  
2.  Щелкните правой кнопкой мыши пункт **Сбор данных**и выберите команду **Отключить сбор данных**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-enable-the-data-collector"></a>Включение сборщика данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется хранимая процедура [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) для включения сборщика данных.  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### <a name="to-disable-the-data-collector"></a>Отключение сборщика данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется хранимая процедура [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) для отключения сборщика данных.  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## <a name="see-also"></a>См. также:  
 [Сбор данных](data-collection.md)   
 [Системные хранимые процедуры (Transact-SQL)](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)  
  
  
