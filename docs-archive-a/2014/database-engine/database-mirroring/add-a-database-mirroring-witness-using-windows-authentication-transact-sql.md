---
title: Добавление следящего сервера для зеркального отображения базы данных с использованием проверки подлинности Windows (язык Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- Windows authentication [SQL Server]
- database mirroring [SQL Server], witness
ms.assetid: bf5e87df-91a4-49f9-ae88-2a6dcf644510
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 88684c3a1ca12ea579859759ed804ca281647fa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657302"
---
# <a name="add-a-database-mirroring-witness-using-windows-authentication-transact-sql"></a>Добавление следящего сервера для зеркального отображения базы данных с использованием проверки подлинности Windows (язык Transact-SQL)
  Чтобы настроить следящий сервер для базы данных, ее владелец назначает экземпляру компонента Database Engine роль следящего сервера. Экземпляр следящего сервера может быть запущен на том же компьютере, что и экземпляры основного или зеркального серверов, но это значительно уменьшает надежность автоматической отработки отказа.  
  
 Настоятельно рекомендуется размещать следящий сервер на отдельном компьютере. Указанный сервер может быть задействован в нескольких одновременных сеансах зеркального отображения базы данных с одними и теми же или разными участниками. В некоторых сеансах указанный сервер может быть участником, в некоторых — следящим сервером.  
  
 Следящий сервер предназначен исключительно для режима высокой надежности с автоматической отработкой отказа. Перед установкой следящего сервера настоятельно рекомендуется убедиться, что для свойства SAFETY установлено значение FULL.  
  
> [!IMPORTANT]  
>  Настройку зеркального отображения базы данных рекомендуется выполнять в часы с наименьшей загрузкой, поскольку этот процесс может оказать влияние на производительность.  
  
### <a name="to-establish-a-witness"></a>Настройка следящего сервера  
  
1.  Убедитесь, что на экземпляре следящего сервера существует конечная точка зеркального отображения. Независимо от числа сеансов зеркального отображения, которые будут поддерживаться, на экземпляре сервера должна быть только одна конечная точка зеркального отображения. Если вы планируете использовать этот экземпляр сервера исключительно в качестве следящего сервера в сеансах зеркального отображения базы данных, назначьте роль следящего сервера конечной точке ( **=** следящий сервер роли). Если экземпляр данного сервера может выступать как участник одного или несколько сеансов зеркального отображения, назначьте конечной точке роль ALL.  
  
     Чтобы выполнить инструкцию SET WITNESS, нужно сначала открыть сеанс зеркального отображения базы данных (между партнерами), а состоянием конечной точки следящего сервера должно быть STARTED.  
  
     Чтобы определить, есть ли на экземпляре следящего сервера конечная точка зеркального отображения его базы данных, а также узнать ее роль и состояние, выполните следующую инструкцию Transact-SQL:  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  Если конечная точка зеркального отображения базы данных существует и уже используется, рекомендуется использовать эту конечную точку для каждого сеанса экземпляра сервера. Удаление используемой конечной точки разрушает связь существующих сеансов. Если для сеанса указан следящий сервер, удаление конечной точки зеркального отображения базы данных может привести к тому, что основной сервер этого сеанса потеряет кворум, вследствие чего база данных будет переведена в режим «вне сети» и ее пользователи будут отключены. Дополнительные сведения см. в статье [Кворум. Как следящий сервер влияет на доступность базы данных &#40;зеркальное отображение базы данных&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
     Если конечная точка на следящем сервере отсутствует, см. раздел [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).  
  
2.  Если экземпляры участников запущены от имени пользователей других доменов, создайте имя входа для разных учетных записей в базе данных master каждого экземпляра. Дополнительные сведения см. в разделе [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).  
  
3.  Подключите следящий сервер к основному, выполнив следующую инструкцию:  
  
     ALTER DATABASE *<database_name>* SET следящи **=** _<server_network_address>_  
  
     Здесь *<имя_базы_данных>*  — имя базы данных, подлежащей зеркальному отображению (это имя является одинаковым в обоих партнерах), а *<сетевой_адрес_сервера>*  — сетевой адрес экземпляра следящего сервера.  
  
     Чтобы указать сетевой адрес сервера, используйте следующий синтаксис:  
  
     TCP **://** \<_system-address> _**:**\<*port>*  
  
     где \<*system-address>* — строка, однозначно идентифицирующая целевой компьютер, а \<*port>* — номер порта, используемого конечной точкой зеркального отображения экземпляра сервера-участника. Дополнительные сведения см. в разделе [Указание сетевого адреса сервера (зеркальное отображение базы данных)](specify-a-server-network-address-database-mirroring.md).  
  
     Например, на экземпляре основного сервера следующая инструкция ALTER DATABASE установит следящий сервер. Имя базы данных — **AdventureWorks**, адрес системы — DBSERVER3 (имя следящей системы), а порт, используемый конечной точкой зеркального отображения базы данных на следящем сервере, — `7022`:  
  
    ```  
    ALTER DATABASE AdventureWorks   
      SET WITNESS = 'TCP://DBSERVER3:7022'  
    ```  
  
## <a name="example"></a>Пример  
 В следующем примере настраивается следящий сервер зеркального отображения. На экземпляре следящего сервера (экземпляр по умолчанию на компьютере `WITNESSHOST4`):  
  
1.  Создайте конечную точку для экземпляра сервера с ролью WITNESS и портом `7022`.  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    ```  
  
2.  Создайте имя входа для учетной записи пользователя домена экземпляров-участников, если они находятся в другом домене, например пусть следящий сервер запущен от имени `SOMEDOMAIN\witnessuser`, а участники — от имени `MYDOMAIN\dbousername`. Создайте имя входа для партнеров таким образом:  
  
    ```  
    --Create a login for the partner server instances,  
    --which are both running as MYDOMAIN\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [MYDOMAIN\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [MYDOMAIN\dbousername];  
    GO  
    ```  
  
3.  На каждом экземпляре сервера-участника создайте имя входа для экземпляра следящего сервера:  
  
    ```  
    --Create a login for the witness server instance,  
    --which is running as SOMEDOMAIN\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [SOMEDOMAIN\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [SOMEDOMAIN\witnessuser];  
    GO  
    ```  
  
4.  На основном сервере определите следящий сервер (запущенный на компьютере `WITNESSHOST4`):  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4:7022'  
    GO  
    ```  
  
> [!NOTE]  
>  Сетевой адрес сервера определяет целевой экземпляр сервера по номеру порта, который соответствует конечной точке этого экземпляра.  
  
 Подробный пример настройки зеркального отображения базы данных, в котором показана настройка защиты, подготовка зеркальной базы данных, настройка партнеров и добавление следящего сервера, см. в разделе [Настройка зеркального отображения базы данных (SQL Server)](database-mirroring-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [Разрешение сетевого доступа к конечной точке зеркального отображения базы данных с использованием проверки подлинности Windows (SQL Server)](../database-mirroring-allow-network-access-windows-authentication.md)   
 [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (Transact-SQL)](database-mirroring-establish-session-windows-authentication.md)   
 [Удаление следящего сервера из сеанса зеркального отображения базы данных (SQL Server)](remove-the-witness-from-a-database-mirroring-session-sql-server.md)   
 [Следящий сервер зеркального отображения базы данных](database-mirroring-witness.md)  
  
  