---
title: Настройка безопасности диалогов для уведомлений о событиях | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], security
ms.assetid: 12afbc84-2d2a-4452-935e-e1c70e8c53c1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d83bfe63c3a9b24c2be8d08916dd2384c59edc93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666994"
---
# <a name="configure-dialog-security-for-event-notifications"></a>Настройка безопасности диалогов для уведомлений о событиях
  [!INCLUDE[ssSB](../../includes/sssb-md.md)] на удаленном сервере, необходимо настроить безопасность диалога. Безопасность диалога должна настраиваться вручную согласно модели полной безопасности диалога компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Модель полной безопасности включает шифрование и дешифрование сообщений, посылаемых на удаленный сервер и принимаемых с этого сервера. Хотя уведомления о событиях посылаются в одном направлении, другие сообщения, например ошибки, возвращаются в противоположном направлении.  
  
## <a name="configuring-dialog-security-for-event-notifications"></a>Настройка безопасности диалога для уведомлений о событиях  
 Процесс, необходимый для реализации безопасности диалога для уведомлений о событиях, описан в последующих шагах. Эти шаги включают в себя действия, которые должны предприниматься как на исходном сервере, так и на целевом сервере. Исходным сервером является сервер, на котором создаются уведомления о событиях. Целевым сервером является сервер, получающий сообщение уведомления о событии. Действия в каждом шаге как для исходного, так и для целевого сервера должны быть завершены перед переходом к следующему шагу.  
  
> [!IMPORTANT]  
>  Все сертификаты должны создаваться с допустимыми датами начала и окончания.  
  
 **Шаг 1. Задайте номер порта TCP и имя целевой службы.**  
  
 Задайте порт TCP, через который как исходный, так и целевой серверы будут получать сообщения. Необходимо также определить имя целевой службы.  
  
 **Шаг 2. Настройте шифрование и совместное использование сертификата для проверки подлинности на уровне базы данных.**  
  
 Как на исходном, так и на целевом серверах выполните следующие действия.  
  
|Исходный сервер|Целевой сервер|  
|-------------------|-------------------|  
|Выберите или создайте базу данных, в которой будут содержаться уведомление о событии и главный ключ.|Выберите или создайте базу данных, в которой будет содержаться главный ключ.|  
|Если для базы данных-источника не существует главного ключа, [создайте главный ключ](/sql/t-sql/statements/create-master-key-transact-sql). Главный ключ необходим как в исходной, так и в целевой базах данных для защиты их соответствующих сертификатов.|Если для целевой базы данных не существует главного ключа, создайте главный ключ.|  
|[Создайте имя входа](/sql/t-sql/statements/create-login-transact-sql) и соответствующую [учетную запись пользователя](/sql/t-sql/statements/create-user-transact-sql) для базы данных-источника.|Создайте имя входа и соответствующую учетную запись пользователя для целевой базы данных.|  
|[Создайте сертификат](/sql/t-sql/statements/create-certificate-transact-sql) , владельцем которого является пользователь базы данных-источника.|Создайте сертификат, владельцем которого является пользователь целевой базы данных.|  
|[Создайте резервную копию сертификата](/sql/t-sql/statements/backup-certificate-transact-sql) в файле, доступ к которому может иметь целевой сервер.|Создайте резервную копию сертификата в файле, доступ к которому может иметь исходный сервер.|  
|[Создайте учетную запись пользователя](/sql/t-sql/statements/create-user-transact-sql), задав пользователя для целевой базы данных, а также указав WITHOUT LOGIN. Этот пользователь будет владеть сертификатом целевой базы данных, который должен быть создан из файла резервной копии. Пользователь не должен быть сопоставлен с входным именем, т.к. единственной целью этого пользователя является владение сертификатом целевой базы данных, созданным на следующем шаге 3.|Создайте учетную запись пользователя, задав пользователя для базы данных-источника, а также указав WITHOUT LOGIN. Этот пользователь будет владеть сертификатом базы данных-источника, который должен быть создан из файла резервной копии. Пользователь не должен быть сопоставлен с входным именем, т.к. единственной целью этого пользователя является владение сертификатом базы данных-источника, созданным на следующем шаге 3.|  
  
 **Шаг 3. Сделайте общими сертификаты и предоставьте разрешения для проверки подлинности на уровне базы данных.**  
  
 Как на исходном, так и на целевом серверах выполните следующие действия.  
  
|Исходный сервер|Целевой сервер|  
|-------------------|-------------------|  
|[Создайте сертификат](/sql/t-sql/statements/create-certificate-transact-sql) из файла резервной копии целевого сертификата, задав в качестве владельца пользователя целевой базы данных.|Создайте сертификат из файла резервной копии исходного сертификата, задав в качестве владельца пользователя базы данных-источника.|  
|[Предоставьте разрешение](/sql/t-sql/statements/grant-transact-sql) для создания уведомления о событии пользователю базы данных-источника. Дополнительные сведения об этом разрешении см. в разделе [CREATE EVENT NOTIFICATION (Transact-SQL)](/sql/t-sql/statements/create-event-notification-transact-sql).|Предоставьте разрешение REFERENCES пользователю целевой базы данных на существующий контракт компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] для уведомлений о событиях: `https://schemas.microsoft.com/SQL/Notifications/PostEventNotification`.|  
|[Создайте привязку удаленной службы](/sql/t-sql/statements/create-remote-service-binding-transact-sql) к целевой службе и задайте учетные данные пользователя целевой базы данных. Привязка удаленной службы обеспечивает то, что при помощи открытого ключа в сертификате, владельцем которого является пользователь базы данных-источника, будет осуществляться проверка подлинности сообщений, посылаемых на целевой сервер.|[Предоставьте](/sql/t-sql/statements/grant-transact-sql) разрешения CREATE QUEUE, CREATE SERVICE и CREATE SCHEMA пользователю целевой базы данных.|  
||Если вы еще не подключены к базе данных в качестве пользователя целевой базы данных, выполните это теперь.|  
||[Создайте очередь](/sql/t-sql/statements/create-queue-transact-sql) для приема сообщений с уведомлениями о событиях и [создайте службу](/sql/t-sql/statements/create-service-transact-sql) для доставки сообщений.|  
||[Предоставьте разрешение SEND](/sql/t-sql/statements/grant-transact-sql) на целевую службу пользователю базы данных-источника.|  
|Предоставьте целевому серверу идентификатор компонента service broker базы данных-источника. Этот идентификатор можно получить, запросив столбец **service_broker_guid** представления каталога [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) . Для уведомления о событии на уровне сервера используйте идентификатор компонента Service Broker базы данных **msdb**.|Предоставьте исходному серверу идентификатор компонента service broker целевой базы данных.|  
  
 **Шаг 4. Создайте маршруты и настройте проверку подлинности на уровне сервера.**  
  
 Как на исходном, так и на целевом серверах выполните следующие действия.  
  
|Исходный сервер|Целевой сервер|  
|-------------------|-------------------|  
|[Создайте маршрут](/sql/t-sql/statements/create-route-transact-sql) к целевой службе и задайте идентификатор компонента Service Broker целевой базы данных, а также согласованный номер порта TCP.|Создайте маршрут к исходной службе и задайте идентификатор компонента service broker базы данных-источника, а также согласованный номер порта TCP. Для задания исходной службы используйте следующую поставляемую службу: `https://schemas.microsoft.com/SQL/Notifications/EventNotificationService`.|  
|Переключитесь на базу данных **master** для настройки проверки подлинности на уровне сервера.|Переключитесь на базу данных **master** для настройки проверки подлинности на уровне сервера.|  
|Если для базы данных **master** не существует главного ключа, [создайте главный ключ](/sql/t-sql/statements/create-master-key-transact-sql).|Если для базы данных **master** не существует главного ключа, создайте главный ключ.|  
|[Создайте сертификат](/sql/t-sql/statements/create-certificate-transact-sql) , выполняющий проверку подлинности базы данных.|Создайте сертификат, выполняющий проверку подлинности базы данных.|  
|[Создайте резервную копию сертификата](/sql/t-sql/statements/backup-certificate-transact-sql) в файле, доступ к которому может иметь целевой сервер.|Создайте резервную копию сертификата в файле, доступ к которому может иметь исходный сервер.|  
|[Создайте конечную точку](/sql/t-sql/statements/create-endpoint-transact-sql)и задайте согласованный номер порта TCP, FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *имя_сертификата*) и имя сертификата, выполняющего проверку подлинности.|Создайте конечную точку и задайте согласованный номер порта TCP, FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *имя_сертификата*) и имя сертификата, выполняющего проверку подлинности.|  
|[Создайте имя входа](/sql/t-sql/statements/create-login-transact-sql)и задайте входное имя целевого сервера.|Создайте имя входа и задайте входное имя исходного сервера.|  
|[Предоставьте разрешение CONNECT](/sql/t-sql/statements/grant-transact-sql) на конечную точку для входного имени целевого средства проверки подлинности.|Предоставьте разрешение CONNECT на конечную точку для входного имени исходного средства проверки подлинности.|  
|[Создайте учетную запись пользователя](/sql/t-sql/statements/create-user-transact-sql)и задайте входное имя целевого средства проверки подлинности.|Создайте учетную запись пользователя и задайте входное имя исходного средства проверки подлинности.|  
  
 **Шаг 5. Сделайте общими сертификаты для проверки подлинности на уровне сервера и создайте уведомление о событии.**  
  
 Как на исходном, так и на целевом серверах выполните следующие действия.  
  
|Исходный сервер|Целевой сервер|  
|-------------------|-------------------|  
|[Создайте сертификат](/sql/t-sql/statements/create-certificate-transact-sql) из файла резервной копии целевого сертификата, задав в качестве владельца пользователя целевого средства проверки подлинности.|Создайте сертификат из файла резервной копии исходного сертификата, задав в качестве владельца пользователя исходного средства проверки подлинности.|  
|Переключитесь на базу данных-источник, на которой необходимо создать уведомление о событии, и если еще вы не подключены в качестве пользователя исходной базы данных, выполните это подключение.|Переключитесь на целевую базу данных для получения сообщений с уведомлениями о событиях.|  
|[Создайте уведомление о событии](/sql/t-sql/statements/create-event-notification-transact-sql)и задайте идентификатор компонента broker service целевой базы данных.||  
  
## <a name="see-also"></a>См. также:  
 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)   
 [BACKUP CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/backup-certificate-transact-sql)   
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [Иерархия средств шифрования](../security/encryption/encryption-hierarchy.md)   
 [Реализация уведомлений о событиях](event-notifications.md)   
 [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql)   
 [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)   
 [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)   
 [CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql)   
 [CREATE REMOTE SERVICE BINDING (Transact-SQL)](/sql/t-sql/statements/create-remote-service-binding-transact-sql)   
 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)   
 [CREATE ROUTE (Transact-SQL)](/sql/t-sql/statements/create-route-transact-sql)   
 [CREATE QUEUE (Transact-SQL)](/sql/t-sql/statements/create-queue-transact-sql)   
 [CREATE SERVICE (Transact-SQL)](/sql/t-sql/statements/create-service-transact-sql)   
 [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql)   
 [CREATE EVENT NOTIFICATION (Transact-SQL)](/sql/t-sql/statements/create-event-notification-transact-sql)  
  
  