---
title: Просмотр или изменение свойств сервера (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- viewing server properties
- server properties [SQL Server]
- displaying server properties
- servers [SQL Server], viewing
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 415d4e2d1aaa3166ae4df2dea53b34e064544e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729790"
---
# <a name="view-or-change-server-properties-sql-server"></a>Просмотр или изменение свойств сервера (SQL Server)
  В этом разделе описывается просмотр и изменение свойств экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или диспетчера конфигурации SQL Server.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для просмотра или изменения свойств сервера используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Диспетчер конфигурации SQL Server](#PowerShellProcedure)  
  
-   **Дальнейшие действия**  [После изменения свойств сервера](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Используя sp_configure, необходимо выполнить инструкцию RECONFIGURE или инструкцию RECONFIGURE WITH OVERRIDE после установки параметра конфигурации. Инструкция RECONFIGURE WITH OVERRIDE обычно употребляется для параметров конфигурации, которые должны использоваться с особой осторожностью. Однако инструкция RECONFIGURE WITH OVERRIDE пригодна для всех параметров конфигурации, и ее можно использовать вместо инструкции RECONFIGURE.  
  
    > [!NOTE]  
    >  Инструкция RECONFIGURE выполняется внутри транзакции. Если какая-либо из операций повторной настройки завершится ошибкой, ни одна из операций повторной настройки не возымеет действия.  
  
-   Некоторые страницы со свойствами предоставляют сведения, полученные через инструментарий управления Windows (WMI). Для отображения этих страниц на компьютере, где работает среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], должен быть установлен инструментарий WMI.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Дополнительные сведения см. в статье [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md).  
  
 Разрешения на выполнение для без `sp_configure` параметров или только по первому параметру по умолчанию предоставляются всем пользователям. Чтобы выполнить `sp_configure` с обоими параметрами для изменения параметра конфигурации или выполнения инструкции RECONFIGURE, пользователю необходимо предоставить разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-change-server-properties"></a>Просмотр или изменение свойств сервера  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Свойства сервера** щелкните страницу, чтобы просмотреть или изменить содержащиеся на сервере сведения об этой странице. Некоторые свойства доступны только для чтения.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-server-properties-by-using-the-serverproperty-built-in-function"></a>Просмотр свойств сервера с помощью встроенной функции SERVERPROPERTY  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется встроенная функция [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) в инструкции `SELECT` для возврата сведений о текущем сервере. Этот сценарий полезен, когда на сервере Windows установлено несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и клиенту приходится открывать другое соединение с тем же экземпляром, который используется текущим соединением.  
  
    ```sql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysservers-catalog-view"></a>Просмотр свойств сервера с помощью представления каталога sys.servers  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере запрашивается представление каталога [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) для получения имени (`name`) и идентификатора (`server_id`) текущего сервера, а также имя поставщика OLE DB (`provider`) для подключения к связанному серверу.  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysconfigurations-catalog-view"></a>Просмотр свойств сервера с помощью представления каталога sys.configurations  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере запрашивается представление каталога [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) , чтобы вернуть сведения о каждом параметре конфигурации для текущего сервера. В примере возвращается имя (`name`) и описание (`description`) параметра, а также указывается, является ли параметр дополнительным (`is_advanced`).  
  
    ```sql
    USE AdventureWorks2012;
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;
    GO
    ```  
  
#### <a name="to-change-a-server-property-by-using-sp_configure"></a>Изменение свойства сервера с помощью процедуры sp_configure  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано, как изменить свойство сервера с помощью процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) . В примере значение параметра `fill factor` меняется на `100`. Чтобы изменение вступило в силу, необходимо перезапустить сервер.  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="PowerShellProcedure"></a> Использование диспетчера конфигурации SQL Server  
 Некоторые свойства сервера можно просматривать и изменять с помощью диспетчера конфигурации SQL Server. Например, можно просмотреть версию и выпуск экземпляра SQL Server или изменить расположение файлов журнала ошибок. Эти свойства также можно просмотреть, запросив [динамические административные представления и функции динамического управления, относящиеся к серверу](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql).  
  
#### <a name="to-view-or-change-server-properties"></a>Просмотр или изменение свойств сервера  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
2.  В **диспетчере конфигурации SQL Server**выберите **Службы SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой мыши **SQL Server (\<***instancename***>)** и выберите пункт **Свойства**.  
  
4.  В диалоговом окне **SQL Server (\<***instancename***>) Свойства** измените свойства сервера на вкладке **Служба** или на вкладке **Дополнительно** и нажмите кнопку **OK**.  
  
##  <a name="follow-up-after-you-change-server-properties"></a><a name="FollowUp"></a>Дальнейшие действия. После изменения свойств сервера  
 Для некоторых свойств необходимо перезапустить сервер, чтобы изменения вступили в силу.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [Инструкции SET (Transact-SQL)](/sql/t-sql/statements/set-statements-transact-sql)   
 [SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)   
 [Диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
 [Функции настройки (Transact-SQL)](/sql/t-sql/functions/configuration-functions-transact-sql)   
 [Динамические административные представления и функции, связанные с сервером (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)  
