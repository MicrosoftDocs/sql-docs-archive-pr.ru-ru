---
title: Страница "Конфигурация базы данных" (диспетчер конфигурации служб Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 800eb48d602c799bcc609e283d83c1b1a72c3303
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734197"
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>Страница «Конфигурация базы данных» (диспетчер конфигурации служб Master Data Services)
  Страница **Настройка база данных** служит для изменения системных настроек базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Системные настройки влияют на все веб-приложения и веб-службы, связанные с выбранной базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Чтобы системные настройки стали доступными для изменения, необходимо выбрать или создать базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="current-database"></a>Текущая база данных  
 Выберите существующую базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] или создайте новую, для которой будут редактироваться системные настройки. Новая база данных будет выбрана по умолчанию после ее создания.  
  
|Название элемента управления|Описание|  
|------------------|-----------------|  
|**Экземпляр SQL Server**|Отображает имя выбранного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Не содержит значения до подключения к экземпляру и выбора или создания базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**База данных Master Data Services**|Отображает имя выбранной базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Не содержит значения до подключения к экземпляру и выбора или создания базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Версия базы данных Master Data Services**|Версия схемы базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Create Database**|Открывает **мастер создания базы данных** для соединения с экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и создания базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] на этом экземпляре.|  
|**Выбор базы данных**|Откройте диалоговое окно **Подключение к базе данных** для подключения к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выбора базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Обновление базы данных**|Открывает мастер, с помощью которого можно обновить указанную базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Эта кнопка включена только в тех случаях, когда требуется обновление определенной базы данных.|  
|**Исправление базы данных**|Эта кнопка позволяет убедиться в правильности установки базы данных MDS. Эта возможность может оказаться полезной при создании и восстановлении резервной копии базы данных MDS на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , где база данных MDS ранее не размещалась.|  
  
## <a name="system-settings"></a>Системные настройки  
 Изменение системных параметров для всех веб-приложений и веб-служб, связанных с выбранной базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Эти параметры доступны в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] и хранятся в таблице системных параметров (mdm.tblSystemSetting) базы данных. Список параметров см. в разделе [Системные параметры (службы Master Data Services)](system-settings-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройка базы данных и веб-сайта для Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Требования к базе данных (службы Master Data Services)](install-windows/database-requirements-master-data-services.md)  
  
  
