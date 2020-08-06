---
title: Записи подсистемы аудита SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audit records [SQL Server]
ms.assetid: 7a291015-df15-44fe-8d53-c6d90a157118
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 19e9ba9013d592d752189adadfb761f1741fd91a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656285"
---
# <a name="sql-server-audit-records"></a>Записи подсистемы аудита SQL Server
  Подсистема аудита [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяет выполнять аудит событий и групп событий на уровне сервера и уровне базы данных. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (ядро СУБД)](sql-server-audit-database-engine.md). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Аудит содержит ноль или более элементов действия аудита, записываемых в *цель*аудита. Цель аудита может быть двоичным файлом, журналом событий приложений Windows или журналом событий безопасности Windows. Записи, переданные в цель, могут содержать элементы, описанные в следующей таблице.  
  
|Имя столбца|Описание|Тип|Доступна всегда|  
|-----------------|-----------------|----------|----------------------|  
|**event_time**|Дата-время срабатывания действия, доступного для аудита.|`datetime2`|Да|  
|**sequence_no**|Отслеживает последовательность записей в одной записи аудита, слишком большой, чтобы уместиться в буфере записи для аудитов.|`int`|Да|  
|**action_id**|Идентификатор действия.<br /><br /> Совет. Для использования значения **action_id** в качестве предиката его необходимо преобразовать из строки символов в числовое значение. Дополнительные сведения см. в статье [Фильтрация подсистемы аудита SQL Server по предикату action_id / class_type](https://docs.microsoft.com/archive/blogs/sqlsecurity/filter-sql-server-audit-on-action_id-class_type-predicate).|`varchar(4)`|Да|  
|**succeeded**|Показывает, было ли успешным действие, запустившее событие.|`bit`-1 = успешное завершение, 0 = сбой|Да|  
|**permission_bitmask**|Когда применимо, отображаются предоставленные, запрещенные или отмененные разрешения.|`bigint`|Нет|  
|**is_column_permission**|Флаг, обозначающий разрешение уровня столбца.|`bit`-1 = true, 0 = false|Нет|  
|**session_id**|Идентификатор сеанса, в котором произошло событие.|`int`|Да|  
|**server_principal_id**|Идентификатор контекста имени входа, в котором выполнено действие.|`int`|Да|  
|**database_principal_id**|Идентификатор контекста пользователя базы данных, в котором выполнено действие.|`int`|Нет|  
|**Идентификатор object_**|Основной идентификатор сущности, над которой произведен аудит. В том числе:<br /><br /> объекты серверов;<br /><br /> базы данных<br /><br /> объекты базы данных<br /><br /> объекты схемы;|`int`|Нет|  
|**target_server_principal_id**|Участник на уровне сервера, к которому применимо действие, доступное для аудита.|`int`|Да|  
|**target_database_principal_id**|Участник базы данных, к которому применимо действие, доступное для аудита.|`int`|Нет|  
|**class_type**|Тип доступной для аудита сущности, для которой проводится аудит.|`varchar(2)`|Да|  
|**session_server_principal_name**|Участник сервера для данного сеанса.|`sysname`|Да|  
|**server_principal_name**|Текущее имя входа.|`sysname`|Да|  
|**server_principal_sid**|Идентификатор безопасности текущего имени входа.|`varbinary`|Да|  
|**database_principal_name**|Текущий пользователь.|`sysname`|Нет|  
|**target_server_principal_name**|Целевое имя входа действия.|`sysname`|Нет|  
|**target_server_principal_sid**|Идентификатор безопасности целевого имени входа.|`varbinary`|Нет|  
|**target_database_principal_name**|Целевой пользователь действия.|`sysname`|Нет|  
|**server_instance_name**|Имя экземпляра сервера, где проводился аудит. Используется стандартный формат «компьютер\экземпляр».|`nvarchar(120)`|Да|  
|**database_name**|Контекст базы данных, в котором выполнялось действие.|`sysname`|Нет|  
|**schema_name**|Контекст схемы, в котором выполнялось действие.|`sysname`|Нет|  
|**object_name**|Имя сущности, для которой проводился аудит. В том числе:<br /><br /> объекты серверов;<br /><br /> базы данных<br /><br /> объекты базы данных<br /><br /> объекты схемы;<br /><br /> инструкция TSQL (если имеется)|`sysname`|Нет|  
|**инструкция**|инструкция TSQL (если имеется)|`nvarchar(4000)`|Нет|  
|**additional_information**|Любые дополнительные сведения о событии хранятся в виде XML.|`nvarchar(4000)`|Нет|  
  
## <a name="remarks"></a>Remarks  
 Некоторые действия имеют незаполненное значение в столбце, так как оно может быть неприменимо к действию.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] хранит 4 000 символов данных для символьных полей в записи аудита. Если значения **additional_information** и **statement** , возвращенные из действия, доступного для аудита, возвращают более 4000 символов, то столбец **sequence_no** используется для записи нескольких записей в отчет аудита для одного действия аудита, чтобы зарегистрировать эти данные. Применяется следующая обработка.  
  
-   Столбец **statement** делится на фрагменты по 4 000 символов.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] записывает в первую строку запись аудита с частичными данными. Все другие поля повторяются в каждой строке.  
  
-   Значение **sequence_no** увеличивается.  
  
-   Этот процесс повторяется до тех пор, пока не будут записаны все данные.  
  
 Можно подключиться к данным, последовательно считывая строки с помощью значения **sequence_no** и столбцов **event_Time**, **action_id** и **session_id** для идентификации действия.  
  
## <a name="related-content"></a>См. также  
 [CREATE SERVER AUDIT (Transact-SQL)](/sql/t-sql/statements/create-server-audit-transact-sql)  
  
 [ALTER SERVER AUDIT (Transact-SQL)](/sql/t-sql/statements/alter-server-audit-specification-transact-sql)  
  
 [DROP SERVER AUDIT (Transact-SQL)](/sql/t-sql/statements/drop-server-audit-transact-sql)  
  
 [CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/create-server-audit-specification-transact-sql)  
  
 [ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/alter-server-audit-transact-sql)  
  
 [DROP SERVER AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/drop-server-audit-specification-transact-sql)  
  
 [CREATE DATABASE AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/create-database-audit-specification-transact-sql)  
  
 [ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/alter-database-audit-specification-transact-sql)  
  
 [DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/drop-database-encryption-key-transact-sql)  
  
 [ALTER AUTHORIZATION (Transact-SQL)](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
 [sys.fn_get_audit_file (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)  
  
 [sys.server_audits (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-audits-transact-sql)  
  
 [sys.server_file_audits (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-file-audits-transact-sql)  
  
 [sys.server_audit_specifications (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql)  
  
 [sys.server_audit_specification_details (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql)  
  
 [sys.database_audit_specifications (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql)  
  
 [sys.database_audit_specification_details (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql)  
  
 [sys.dm_server_audit_status (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql)  
  
 [sys.dm_audit_actions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql)  
  
 [sys.dm_audit_class_type_map (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql)  
  
  
