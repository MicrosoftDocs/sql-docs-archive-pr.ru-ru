---
title: Защита SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- database objects [SQL Server], security
- SQL Server, security
- operating systems [SQL Server], security
- security [SQL Server], planning
- applications [SQL Server], security
ms.assetid: 4d93489e-e9bb-45b3-8354-21f58209965d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b8cb69c88d1f8eee98093c8fc8227db8e67ed7fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730322"
---
# <a name="securing-sql-server"></a>Обеспечение безопасности SQL Server
  Защиту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно рассматривать как последовательность шагов, затрагивающих четыре области: платформу, проверку подлинности, объекты (включая данные) и приложения, получающие доступ к системе. В приведенных ниже разделах описано создание и реализация эффективного плана обеспечения безопасности.  
  
 Дополнительные сведения о безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. на веб-сайте [SQL Server](https://go.microsoft.com/fwlink/?LinkID=31629) . Они включают руководство с рекомендациями и контрольный список безопасности. Кроме того, этот веб-сайт содержит сведения о пакетах обновлений и файлы для загрузки.  
  
## <a name="platform-and-network-security"></a>Безопасность платформы и сети  
 Платформа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает в себя физическое оборудование и сетевые компьютеры, с помощью которых клиенты соединяются с серверами базы данных, а также двоичные файлы, применяемые для обработки запросов базы данных.  
  
### <a name="physical-security"></a>Физическая безопасность  
 Рекомендуется строго ограничивать доступ к физическим серверам и компонентам оборудования. Например, оборудование сервера базы данных и сетевые устройства должны находиться в закрытых охраняемых помещениях. Доступ к резервным носителям также следует ограничить. Для этого их рекомендуется хранить в отдельных охраняемых помещениях.  
  
 Реализация физической сетевой безопасности начинается с запрета доступа неавторизованных пользователей к сети. Следующая таблица содержит дополнительные сведения об источниках сведений по сетевой безопасности.  
  
|Сведения о|См.|  
|---------------------------|---------|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)] и сетевой доступ к другим выпускам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Раздел «Настройка и обеспечение безопасности среды сервера» в электронной документации по [!INCLUDE[ssEW](../../includes/ssew-md.md)]|  
  
### <a name="operating-system-security"></a>Безопасность операционной системы  
 В состав пакетов обновления и отдельных обновлений для операционной системы входят важные дополнения, позволяющие усилить безопасность. Все обновления для операционной системы необходимо устанавливать только после их тестирования с приложениями базы данных.  
  
 Кроме того, эффективную безопасность можно реализовать с помощью брандмауэров. Брандмауэр, распределяющий или ограничивающий сетевой трафик, можно настроить в соответствии с корпоративной политикой информационной безопасности. Использование брандмауэра повышает безопасность на уровне операционной системы, обеспечивая узкую область, на которой можно сосредоточить меры безопасности. Следующая таблица содержит дополнительные сведения по использованию брандмауэра с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Настройка брандмауэра для работы со службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Настройка брандмауэра Windows для доступа к компоненту Database Engine](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)|  
|Настройка брандмауэра для работы со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[Настройка параметров брандмауэра Windows для доступа к службам SSIS](../../integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)|  
|Настройка брандмауэра для работы со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|[Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|  
|Открытие конкретных портов брандмауэра, чтобы предоставить доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|  
|Настройка поддержки расширенной защиты для проверки подлинности с помощью привязки каналов и привязки служб|[Соединение с компонентом Database Engine с использованием расширенной защиты](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md)|  
  
 Уменьшение контактной зоны является мерой безопасности, предполагающей остановку или отключение неиспользуемых компонентов. Уменьшение контактной зоны повышает уровень безопасности за счет уменьшения числа возможных способов атаковать систему. Важную роль в ограничении контактной зоны [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] играет запуск необходимых служб по принципу «минимума прав доступа», согласно которому службам и пользователям предоставляются только необходимые для работы права. Следующая таблица содержит дополнительные сведения по службам и доступу к системе.  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Службы, необходимые для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)|  
  
 Если в системе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются службы IIS, необходимы дополнительные действия для обеспечения безопасности контактной зоны платформы. Следующая таблица содержит сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и службах IIS.  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Безопасность служб IIS в [!INCLUDE[ssEW](../../includes/ssew-md.md)]|«Безопасность служб IIS» в электронной документации по [!INCLUDE[ssEW](../../includes/ssew-md.md)]|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Проверка подлинности|[Проверка подлинности в службах Reporting Services](../../reporting-services/extensions/security-extension/authentication-in-reporting-services.md)|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)] и доступ к службам IIS|«Блок-схема безопасности служб IIS» в электронной документации по [!INCLUDE[ssEW](../../includes/ssew-md.md)]|  
  
### <a name="sql-server-operating-system-files-security"></a>Безопасность файлов операционной системы SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует файлы операционной системы для работы и хранения данных. Оптимальным решением для обеспечения безопасности файлов будет ограничение доступа к ним. Следующая таблица содержит сведения об этих файлах.  
  
|Сведения о|См.|  
|---------------------------|---------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программные файлы|[Расположение файлов для экземпляра по умолчанию и именованных экземпляров SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяют повысить безопасность. Для определения новейшего доступного пакета обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]перейдите на веб-сайт [SQL Server](https://go.microsoft.com/fwlink/?LinkID=31629) .  
  
 С помощью приведенного ниже скрипта можно определить установленный в системе пакет обновления.  
  
```  
SELECT CONVERT(char(20), SERVERPROPERTY('productlevel'));  
GO  
```  
  
## <a name="principals-and-database-object-security"></a>Безопасность участников и объектов базы данных  
 Участники — это отдельные пользователи, группы и процессы, которым предоставлен доступ к ресурсам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Защищаемые объекты — это сервер, база данных и объекты, которые содержит база данных. У каждого из них существует набор разрешений, с помощью которых можно уменьшить контактную зону [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Следующая таблица содержит сведения об участниках и защищаемых объектах.  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Пользователи, роли и процессы сервера и базы данных|[Участники (компонент Database Engine)](authentication-access/principals-database-engine.md)|  
|Безопасность объектов сервера и базы данных|[Защищаемые объекты](securables.md)|  
|Иерархия безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Иерархия разрешений (компонент Database Engine)](permissions-hierarchy-database-engine.md)|  
  
### <a name="encryption-and-certificates"></a>Шифрование и сертификаты  
 Шифрование не решает проблемы управления доступом. Однако оно повышает безопасность, ограничивая потерю данных даже в тех редких случаях, когда средства управления доступом удается обойти. Например, если главный компьютер, на котором установлена база данных, был настроен неправильно, и злонамеренный пользователь смог получить конфиденциальные данные (например, номера кредитных карточек), то украденная информация будет бесполезна, если она была предварительно зашифрована. В следующей таблице содержатся дополнительные сведения о шифровании в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Иерархия шифрования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Иерархия средств шифрования](encryption/encryption-hierarchy.md)|  
|Реализация безопасных соединений|[Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)|  
|Функции шифрования|[Криптографические функции (Transact-SQL)](/sql/t-sql/functions/cryptographic-functions-transact-sql)|  
  
 Сертификаты — это совместно используемые на двух серверах программные «ключи», которые позволяют обеспечить безопасную передачу данных с помощью надежной проверки подлинности. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет создавать и использовать сертификаты для повышения безопасности объектов и соединений. Следующая таблица содержит дополнительные сведения об использовании сертификатов с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Создание сертификата, который будет использоваться [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql)|  
|Использование сертификатов при зеркальном отображении базы данных|[Использование сертификатов для конечной точки зеркального отображения базы данных (Transact-SQL)](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|  
  
## <a name="application-security"></a>Безопасность приложений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рекомендуется разрабатывать защищенные клиентские приложения.  
  
 Дополнительные сведения об обеспечении безопасности клиентских приложений на сетевом уровне см. в разделе [Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="sql-server-security-tools-utilities-views-and-functions"></a>Средства, программы, представления и функции безопасности SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусмотрены средства, программы, представления и функции, которые используются для настройки и управления безопасностью.  
  
### <a name="sql-server-security-tools-and-utilities"></a>Средства и программы безопасности SQL Server  
 Следующая таблица содержит сведения о средствах и программах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с помощью которых можно настраивать и администрировать безопасность.  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Использование среды SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)|  
|Соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и запуск запросов из командной строки|[Программа sqlcmd](../../tools/sqlcmd-utility.md)|  
|Настройка сети и управление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Диспетчер конфигурации SQL Server](../sql-server-configuration-manager.md)|  
|Включение и отключение компонентов с помощью средства управления на основе политики|[Администрирование серверов с помощью управления на основе политик](../policy-based-management/administer-servers-by-using-policy-based-management.md)|  
|Управление симметричными ключами для сервера отчетов|[Программа rskeymgmt (SSRS)](../../reporting-services/tools/rskeymgmt-utility-ssrs.md)|  
  
### <a name="sql-server-security-catalog-views-and-functions"></a>Представления каталога и функции безопасности SQL Server  
 В компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)] сведения о безопасности доступны через несколько представлений и функций, оптимизированных для наибольшей производительности и полезности. Следующая таблица содержит сведения о представлениях и функциях безопасности.  
  
|Сведения о|См.|  
|---------------------------|---------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представления каталога безопасности, которые возвращают сведения о разрешениях, участниках, ролях и других сущностях уровня базы данных и сервера. Кроме того, существуют представления каталога, содержащие сведения о ключах шифрования, сертификатах и учетных данных.|[Представления каталога безопасности (Transact-SQL)](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые возвращают сведения о текущем пользователе, разрешениях и схемах.|[Функции безопасности &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Динамические представления управления и функции, связанные с безопасностью (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql)|  
  
## <a name="related-content"></a>См. также  
 [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
 [Центр безопасности для ядра СУБД SQL Server и Базы данных Azure SQL](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
