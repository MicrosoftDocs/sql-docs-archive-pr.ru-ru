---
title: Очистка журнала заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
author: stevestein
ms.author: sstein
ms.openlocfilehash: 813c2c7c86a769eea09a093f2de999460d78ef54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668599"
---
# <a name="clear-the-job-history-log"></a>Clear the Job History Log
  В этом разделе описано, как удалить содержимое [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнала заданий агента в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющие объекты SQL Server.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для очистки журнала заданий используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-clear-the-job-history-log"></a>Очистка журнала заданий  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , а затем разверните этот экземпляр.  
  
2.  Раскройте узел **Агент SQL Server**, а затем узел **Задания**.  
  
3.  Щелкните правой кнопкой мыши задание и выберите **Просмотреть журнал**.  
  
4.  В **Программе просмотра файла журнала**выберите задание, журнал которого нужно очистить, и выполните одно из следующих действий.  
  
    -   В окне **Удалить журнал**нажмите кнопку **Удалить** , затем **Удалить весь журнал** . Можно удалить как весь журнал заданий, так и только записи, сделанные до указанной даты. Чтобы удалить весь журнал заданий, нажмите кнопку **Удалить весь журнал**. Чтобы удалить из журнала заданий записи определенной давности, нажмите кнопку **Удалить журнал до**и укажите дату.  
  
    -   Чтобы очистить журнал многосерверного задания, нажмите кнопку **Состояние задания** . Нажмите кнопку **Задание**, выберите имя задания, а затем выберите пункт **Просмотреть удаленный журнал заданий**.  
  
5.  Щелкните **Удалить**.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-clear-the-job-history-log"></a>Очистка журнала заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  
 **Очистка журнала заданий**  
  
 Вызовите метод `PurgeJobHistory` класса `JobServer`, используя выбранный язык программирования, например Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
