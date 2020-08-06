---
title: Имена входа, пользователи и роли базы данных (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], database roles
- database [Master Data Services], users
- security [Master Data Services], database users
- database [Master Data Services], roles
- database [Master Data Services], logins
- security [Master Data Services], database logins
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: eadd6fb4d5b9798920d65119386aa2c58afebfa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736464"
---
# <a name="database-logins-users-and-roles-master-data-services"></a>Имена входа, пользователи и роли базы данных (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] включает имена входа, пользователей и роли, которые автоматически устанавливаются на экземпляр [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] , где размещена база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Изменять этих пользователей, имена входа и роли не рекомендуется.  
  
## <a name="logins"></a>Имена входа  
  
|Вход|Описание|  
|-----------|-----------------|  
|`mds_dlp_login`|Разрешает создание сборок UNSAFE.<br /><br /> — Отключенное имя входа со случайно созданным паролем.<br /><br /> — Сопоставляет со схемой dbo для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> — Для msdb это имя входа сопоставляется с mds_clr_user.<br /><br /> <br /><br /> Дополнительные сведения см. в статье [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).|  
|`mds_email_login`|Включенное имя входа, используемое для уведомлений.<br /><br /> Для msdb и базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] это имя входа сопоставляется с mds_email_user.|  
  
## <a name="msdb-users"></a>Пользователи msdb  
  
|Пользователь|Описание|  
|----------|-----------------|  
|`mds_clr_user`|Не используется.<br /><br /> Сопоставляется с mds_dlp_login.|  
|`mds_email_user`|Используется для уведомлений.<br /><br /> Сопоставляется с mds_email_login.<br /><br /> Является членом роли: DatabaseMailUserRole.|  
  
## <a name="master-data-services-database-users"></a>Пользователи базы данных Master Data Services  
  
|Пользователь|Описание|  
|----------|-----------------|  
|`mds_email_user`|Используется для уведомлений.<br /><br /> Имеет разрешение SELECT для схемы mdm.<br /><br /> Имеет разрешение EXECUTE для определяемого пользователем табличного типа mdm.MemberGetCriteria.<br /><br /> Имеет разрешение EXECUTE для хранимой процедуры mdm.udpNotificationQueueActivate.|  
|**mds_schema_user**|Владеет схемами mdm и mdq. Схема по умолчанию — mdm.<br /><br /> Не имеет сопоставленного имени входа.|  
|**mds_ssb_user**|Используется для выполнения задач компонента Service Broker.<br /><br /> Имеет разрешения DELETE, INSERT, REFERENCES, SELECT и UPDATE для всех схем.<br /><br /> Не имеет сопоставленного имени входа.|  
  
## <a name="master-data-services-database-role"></a>Роль базы данных служб Master Data Services  
  
|Роль|Описание|  
|----------|-----------------|  
|`mds_exec`|Эта роль содержит учетную запись, создаваемую в службах [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] при создании веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и учетной записи для пула приложений. Роль mds_exec имеет следующие разрешения:<br /><br /> Разрешение **EXECUTE** для всех схем.<br /><br /> Разрешения **ALTER**, **INSERT**и **SELECT** для этих таблиц:<br />mdm.tblStgMember<br />mdm.tblStgMemberAttribute<br />mdm.tbleStgRelationship<br /><br /> Разрешение **SELECT** для этих таблиц:<br />mdm.tblUser<br />mdm.tblUserGroup<br />mdm.tblUserPreference<br /><br /> Разрешение **SELECT** для этих представлений:<br />mdm.viw_SYSTEM_SECURITY_NAVIGATION<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL_MEMBER<br />mdm.viw_SYSTEM_SECURITY_USER_MODEL|  
  
## <a name="schemas"></a>Схемы  
  
|Роль|Описание|  
|----------|-----------------|  
|`mdm`|Содержит все объекты базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] и компонента Service Broker кроме функций, содержащихся в схеме mdq.|  
|`mdq`|Содержит функции базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , относящиеся к фильтрации результирующих элементов на основе регулярных выражений или подобия, а также для форматирования уведомлений по электронной почте.|  
|**stg**|Содержит таблицы базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , хранимые процедуры и представления, связанные с промежуточным процессом. Запрещается удалять любые из этих объектов. Дополнительные сведения о промежуточном процессе см. в разделе [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).|  
  
## <a name="see-also"></a>См. также:  
 [Защита объектов базы данных (службы Master Data Services)](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  
