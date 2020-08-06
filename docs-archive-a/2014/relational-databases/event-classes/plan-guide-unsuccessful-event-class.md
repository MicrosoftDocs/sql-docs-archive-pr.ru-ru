---
title: Класс событий Plan Guide Unsuccessful | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Plan Guide Unsuccessful event class
ms.assetid: ef9759f8-5613-4884-9257-86b609313f69
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb950f7cb35e6986396da4d80ee10f03e090ae76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666037"
---
# <a name="plan-guide-unsuccessful-event-class"></a>Plan Guide Unsuccessful, класс событий
  Класс событий Plan Guide Unsuccessful показывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось создать план выполнения для запроса или пакета, который содержал структуру плана. Вместо этого план был скомпилирован без использования структуры плана. Событие возникает, когда выполняются следующие условия.  
  
-   Уже выполняется пакет, совпадающий с пакетом или модулем в определении структуры плана.  
  
-   Уже выполняется запрос, совпадающий с запросом в определении структуры плана.  
  
-   Не удалось успешно применить к запросу или пакету указания в определении структуры плана, включая указание USE PLAN. Таким образом, скомпилированному плану запроса не удалось принять заданные указания, и план был скомпилирован без использования структуры плана.  
  
 Возможно, срабатывание события вызвано недопустимой структурой плана. Проверьте структуру плана, которая используется запросом или пакетом, с помощью функции [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) и исправьте ошибку, о которой сообщит эта функция.  
  
 Это событие включено в шаблон Tuning [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] .  
  
## <a name="plan-guide-unsuccessful-event-class-data-columns"></a>Столбцы данных класса событий Plan Guide Unsuccessful  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|ClientProcessID|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для указанного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|имя_базы_данных|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|EventClass|`int`|Тип события = 218.|27|Нет|  
|EventSequence|`int`|Последовательность указанного события в запросе.|51|Нет|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IsSystem|`int`|Указывает, вызвано ли событие системным процессом или пользовательским: 1 = системным, 0 = пользовательским.|60|Да|  
|LoginName|`nvarchar`|Имя учетной записи пользователя (имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа безопасности или [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетные данные входа Windows в формате домен \\ *имя_пользователя*).|11|Да|  
|LoginSid|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлениях каталога [sys.server_principals](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) или [sys.sql_logins](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|ObjectID|`int`|Идентификатор объекта модуля, скомпилированного при применении структуры плана. Если структура плана не была применена к модулю, в этом столбце будет указано значение NULL.|22|Да|  
|RequestID|`int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|ServerName|`nvarchar`|Имя трассируемого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|26|Нет|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|TextData|`ntext`|Имя структуры плана.|1|Да|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
|XactSequence|`bigint`|Токен, который описывает текущую транзакцию.|50|Да|  
  
## <a name="see-also"></a>См. также:  
 [Класс событий «успех структуры плана»](plan-guide-successful-event-class.md)   
 [Расширенные события](../extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sys. fn_validate_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql)   
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
