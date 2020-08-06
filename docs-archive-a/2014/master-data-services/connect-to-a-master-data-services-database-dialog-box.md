---
title: Диалоговое окно "Подключение к базе данных служб Master Data Services" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.srvconnect.f1
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 731e195ca60ca09bc76934af09ae1efeba7a0093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728430"
---
# <a name="connect-to-a-master-data-services-database-dialog-box"></a>Диалоговое окно «Подключение к базе данных служб Master Data Services»
  Используйте диалоговое окно **Подключение к базе данных служб Master Data Services** для выбора базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]это диалоговое окно доступно на следующих страницах:  
  
-   На странице **Конфигурация базы данных** нажмите **Выбор базы данных** . Используйте это диалоговое окно для выбора базы данных, у которой надо настроить системные параметры.  
  
-   На странице **Веб-кофигурация** в **Связать веб-приложение с базой данных**щелкните **Выбрать** , чтобы выбрать базу данных для связи с веб-сайтом [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] или приложением.  
  
## <a name="select-database"></a>Выбор базы данных  
 Укажите информацию для соединения с локальным или удаленным экземпляром [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] , на котором размещена база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Для подключения к удаленному экземпляру должны быть разрешены удаленные соединения.  
  
|Название элемента управления|Описание|  
|------------------|-----------------|  
|**Экземпляр SQL Server**|Задайте имя экземпляра [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] , на котором будет размещаться база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Можно использовать экземпляр по умолчанию или именованный экземпляр на локальном или удаленном компьютере. Укажите сведения, введя следующее:<br /><br /> Точка (.) для подключения к экземпляру по умолчанию на локальном компьютере.<br /><br /> Имя или IP-адрес сервера, чтобы подключиться к экземпляру по умолчанию на указанном локальном или удаленном компьютере.<br /><br /> Имя или IP-адрес сервера и имя экземпляра, чтобы подключиться к именованному экземпляру на указанном локальном или удаленном компьютере. Укажите эти сведения в формате *server_name* \\ *instance_name*.|  
|**Тип проверки подлинности**|Выберите тип проверки подлинности, который будет использоваться для соединения с указанным экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Учетные данные, используемые для соединения, определяют базы данных, отображающиеся в раскрывающемся списке **База данных служб Master Data Services** . Имеются следующие типы проверки подлинности.<br /><br /> **Текущий пользователь — встроенная безопасность**. использует встроенную проверку подлинности Windows для подключения с использованием учетных данных текущей учетной записи пользователя Windows. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] использует учетные данные Windows для пользователя, который вошел в систему и открыл приложение. Другие учетные данные Windows указать в приложении нельзя. Если необходимо подключиться с другими учетными данными, то следует войти в систему как пользователь с такими учетными данными, а затем открыть [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].<br /><br /> **Учетная запись SQL Server**. Для подключения используется учетная запись SQL Server. При выборе этого параметра поля **Имя пользователя** и **Пароль** доступны для ввода и необходимо указать учетные данные учетной записи [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для заданного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**User name**|Укажите имя пользовательской учетной записи, которая будет использоваться для подключения к заданному экземпляру SQL-сервера. Учетная запись должна входить в роль **sysadmin** для указанного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :<br /><br /> Если **тип проверки подлинности** — **текущий пользователь — встроенная безопасность**, поле **имя пользователя** доступно только для чтения и отображает имя учетной записи пользователя Windows, выполнившего вход на компьютер.<br /><br /> Если **Тип проверки подлинности** — это **Учетная запись SQL Server**, поле **Имя пользователя** доступно для ввода и в нем необходимо указать учетные данные учетной записи [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для заданного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**Пароль**|Укажите пароль для этой учетной записи пользователя:<br /><br /> Если **тип проверки подлинности** — **текущий пользователь — встроенная безопасность**, поле **пароль** доступно только для чтения, а учетные данные указанной учетной записи пользователя Windows используются для подключения.<br /><br /> Если **Тип проверки подлинности** — это **Учетная запись SQL Server**, поле **Пароль** доступно для ввода и в нем необходимо указать пароль, связанный с указанной учетной записью пользователя.|  
|**Подключить**|Подключение к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с указанными учетными данными.|  
|**База данных Master Data Services**|Отображает базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] в указанном экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на основании следующих критериев.<br /><br /> Если пользователь входит в роль сервера **sysadmin** для этого экземпляра, отображаются все базы данных этого экземпляра [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> Если пользователь входит в роль **db_owner** каких-либо баз данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] этого экземпляра, отображаются эти базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> <br /><br /> Дополнительные сведения о ролях SQL Server см. в разделах [Роли уровня сервера](../relational-databases/security/authentication-access/server-level-roles.md) и [Роли уровня базы данных](../relational-databases/security/authentication-access/database-level-roles.md).|  
  
## <a name="see-also"></a>См. также:  
 [Страница конфигурации базы данных &#40;диспетчер конфигурации Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Настройка базы данных и веб-сайта для служб Master Data Services](set-up-the-database-and-website-for-master-data-services.md)  
  
  
