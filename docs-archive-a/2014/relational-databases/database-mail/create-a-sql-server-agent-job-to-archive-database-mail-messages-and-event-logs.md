---
title: Создание задания агента SQL Server по архивации сообщений и журналов событий компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- archiving mail messages and attachments [SQL Server]
- removing mail messages and attachements
- Database Mail [SQL Server], archiving
- saving mail messages and attachments
ms.assetid: 8f8f0fba-f750-4533-9b76-a9cdbcdc3b14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b958b280c358a8aeb752600dee1c2aee31d14db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657813"
---
# <a name="create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs"></a>Создание задания агента SQL Server по архивации сообщений компонента Database Mail и журналов событий базы данных
  Копии сообщений компонента Database Mail и их вложения хранятся в таблицах **msdb** , расположенных в журнале событий компонента Database Mail. Может возникнуть потребность периодического уменьшения объема ненужных таблиц и архивных сообщений и событий. Представленные ниже процедуры используются для создания задания агента SQL Server для автоматизации указанного процесса.  
  
-   **Перед началом работы:**  , [Необходимые компоненты](#Prerequisites), [Рекомендации](#Recommendations), [Разрешения](#Permissions)  
  
-   **Для архивации сообщений и журналов компонента Database Mail рекомендуется использовать:**  [агент SQL Server](#Process_Overview)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
 Новые таблицы для хранения архивных данных могут быть расположены в специальной архивной базе данных. Кроме того, строки можно экспортировать в текстовый файл.  
 
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
 В случае сбоя задания в процессе работы, возможно, понадобится провести дополнительную проверку и отправить уведомления операторам.  
  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Чтобы выполнить хранимые процедуры, описанные в данном разделе, пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
  
###  <a name="overview-of-the-process"></a><a name="Process_Overview"></a> Общие сведения о процессе  
  
-   Первая процедура, которая создает задание с именем «Archive Database Mail», состоит из следующих действий.  
  
    1.  Скопируйте все сообщения из таблиц компонента Database Mail в новую таблицу с именем прошлого месяца в формате **DBMailArchive_** _<год_месяц>_ .  
  
    2.  Скопируйте вложения, прикрепленные к сообщениям, скопированным на первом шаге из таблиц компонента Database Mail, в новую таблицу с именем прошлого месяца в формате **DBMailArchive_Attachments_** _<год_месяц>_ .  
  
    3.  Скопируйте из журналов событий компонента Database Mail события, имеющие отношение к сообщениям, скопированным на первом шаге, из таблиц компонента Database Mail в новую таблицу с именем прошлого месяца в формате **DBMailArchive_Log_** _<год_месяц>_ .  
  
    4.  Удаление всех скопированных элементов из таблиц компонента Database Mail.  
  
    5.  Удаление всех событий, связанных со скопированными элементами, хранящихся в журнале событий компонента Database Mail.  
  
-   Планирование задания для периодического выполнения.  
 
  
## <a name="to-create-a-sql-server-agent-job"></a>Создание задания агента SQL Server  
  
1.  В обозревателе объектов разверните узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , правой кнопкой мыши щелкните элемент **Задания**и выберите команду **Создать задание**.  
  
2.  В диалоговом окне **Создание задания** в поле **Имя** введите **Archive Database Mail**.  
  
3.  В окне **Владелец** подтвердите принадлежность владельца к предопределенной роли сервера **sysadmin** .  
  
4.  В окне **Категория** выберите **Обслуживание базы данных**.  
  
5.  В поле **Описание** введите **Archive Database Mail messages**, а затем выберите вкладку **Шаги**.  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-messages"></a>Создание шага по архивации сообщений компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовое поле **Имя шага** введите **Copy Database Mail Items**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)** .  
  
4.  В поле **База данных** выберите **msdb**.  
  
5.  Чтобы создать таблицу с именем прошлого месяца, в которой будут храниться все строки данных за предыдущие месяцы, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_' + @LastMonth + '] FROM sysmail_allitems WHERE send_request_date < ''' + @CopyDate +'''';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-attachments"></a>Создание шага по архивации вложений компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовое поле **Имя шага** введите **Copy Database Mail Attachments**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)** .  
  
4.  В поле **База данных** выберите **msdb**.  
  
5.  Чтобы создать таблицу с именем прошлого месяца, в которой будут храниться все вложения, связанные с сообщениями, скопированными на предыдущем шаге, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Attachments_' + @LastMonth + '] FROM sysmail_attachments   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-log"></a>Создание шага по архивации журнала компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовом поле **Имя шага** введите **Copy Database Mail Log**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)** .  
  
4.  В поле **База данных** выберите **msdb**.  
  
5.  Чтобы создать таблицу с именем прошлого месяца, в которой будут храниться все записи журнала, связанные с сообщениями, скопированными на предыдущих шагах, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Log_' + @LastMonth + '] FROM sysmail_Event_Log   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-rows-from-database-mail"></a>Создание шага по удалению архивных строк из компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовом поле **Имя шага** введите **Remove rows from Database Mail**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)** .  
  
4.  В поле **База данных** выберите **msdb**.  
  
5.  Чтобы удалить из таблиц компонента Database Mail строки, созданные ранее начала текущего месяца, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @CopyDate ;  
    ```  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-items-from-database-mail-event-log"></a>Создание шага по удалению архивных элементов из журнала событий компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовом поле **Имя шага** введите **Remove rows from Database Mail event log**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)** .  
  
4.  Чтобы удалить из журнала событий компонента Database Mail строки, созданные ранее начала текущего месяца, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_log_sp @logged_before = @CopyDate ;  
    ```  
  
5.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
  
  
## <a name="to-schedule-the-job-to-run-periodically"></a>Планирование периодического выполнения задания  
  
1.  В диалоговом окне **Создание задания** выберите **Расписания**.  
  
2.  На странице **Расписания** нажмите кнопку **Создать**.  
  
3.  В текстовое поле **Имя** введите **Archive Database Mail**.  
  
4.  В окне **Тип расписания** выберите **Циклический**.  
  
5.  В области **Периодичность** задайте параметр выполнения периодического задания, например, первое число каждого месяца.  
  
6.  В области **Сколько раз в день** выберите **Проводится один раз в день в \<time>** .  
  
7.  Убедитесь, что другие параметры настроены правильно, и сохраните расписание, нажав кнопку **OK** .  
  
8.  Нажмите кнопку **ОК** , чтобы сохранить задание.  
  
  
  
  
