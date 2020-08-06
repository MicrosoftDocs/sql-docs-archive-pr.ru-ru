---
title: Просмотр и настройка параметров соединения с удаленным сервером (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 73fe5e484d62cde025d1a560937e8cbcf5ec361d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729786"
---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a>Просмотр и настройка параметров соединения с удаленным сервером (SQL Server)
  В этом разделе описываются способы просмотра и настройки параметров подключения к удаленному серверу на уровне сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр и настройка параметров соединения с удаленным сервером с использованием**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметров соединения с удаленным сервером](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для выполнения хранимой процедуры **sp_serveroption** необходимо разрешение ALTER ANY LINKED SERVER на сервер.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a>Просмотр и настройка параметров соединения с удаленным сервером  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Свойства SQL Server — \<***server_name***>** щелкните **Соединения**.  
  
3.  На странице **Соединения** просмотрите параметры **Соединения с удаленными серверами** и измените их при необходимости.  
  
4.  Повторите шаги 1-3 на другом сервере данной пары серверов.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-remote-server-connection-options"></a>Просмотр параметров соединения удаленным сервером  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере хранимая процедура [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) используется для возврата сведений обо всех удаленных серверах.  
  
```sql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a>Настройка параметров соединения с удаленным сервером  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано использование хранимой процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) для настройки удаленного сервера. В следующем примере удаленный сервер настраивается в соответствии с другим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, для совместимости параметров сортировки с локальным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="follow-up-after-you-configure-remote-server-connection-options"></a><a name="FollowUp"></a> Дальнейшие действия. После настройки параметров соединения с удаленным сервером  
 Чтобы изменения вступили в силу, необходимо остановить и перезапустить удаленный сервер.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [Удаленные серверы](remote-servers.md)   
 [Связанные серверы (компонент Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [sp_linkedservers (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql)   
 [sp_helpserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql)   
 [sp_serveroption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
