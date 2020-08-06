---
title: Настройка Analysis Services. Подготовка учетных записей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services configuration
- account provisioning
ms.assetid: 169b1af2-6fe2-467f-8ca4-919f24c620ce
author: heidisteen
ms.author: heidist
ms.openlocfilehash: 109b5d9ddddf2b78c0bb8947cfa876d233f804ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659250"
---
# <a name="analysis-services-configuration---account-provisioning"></a>Настройка служб Analysis Services — провизионирование учетных записей
  На этой странице можно выбрать режим сервера и предоставить административные разрешения пользователям или службам, которым требуется неограниченный доступ к службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Программа установки не добавляет автоматически локальную группу Windows BUILTIN\Администраторы в роль администратора сервера служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] устанавливаемого экземпляра. Если к роли администратора сервера требуется добавить локальную группу администраторов, необходимо явно указать эту группу.  
  
 При установке [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] необходимо предоставить административные разрешения администраторам ферм SharePoint или администраторам служб, отвечающим за развертывание сервера [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]. Дополнительные сведения о [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] требованиях к установке и учетной записи службы см. [в разделе Install SQL Server BI Features with SharePoint &#40;PowerPivot and Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).  
  
## <a name="options"></a>Варианты  
 **Режим сервера**. Указывает тип баз данных служб Analysis Services, которые могут быть развернуты на сервере. Режимы сервера задаются во время установки, впоследствии изменить их будет невозможно. Каждый режим является взаимоисключающим, в силу чего необходимо будет установить два экземпляра служб Analysis Services, каждый из которых будет настроен для работы в другом режиме, чтобы обеспечить поддержку классических решений OLAP и табличных моделей.  
  
 **Определить администраторов** — для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо указать хотя бы одного администратора сервера. Указанные пользователи или группы станут членами роли администратора сервера устанавливаемого экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. В домене, где зарегистрирован компьютер, на который выполняется установка программного обеспечения, должны иметься учетные записи пользователей домена Windows.  
  
> [!NOTE]  
>  Контроль учетных записей представляет собой средство безопасности Windows, которое требует, чтобы администратор явно одобрил административные действия или приложения, прежде чем будет разрешено их выполнение. Поскольку контроль учетных записей включен по умолчанию, администратор получает запрос на разрешение определенных операций, требующих более высокого уровня привилегий. Можно настроить контроль учетных записей, изменив поведение по умолчанию, или задать определенную конфигурацию для конкретных программ. Дополнительные сведения о конфигурации UAC и UAC см. [в разделе Управление учетными записями пользователей](https://go.microsoft.com/fwlink/?linkid=196350) пошаговое руководств и [Управление учетными записями пользователей (Википедии)](https://go.microsoft.com/fwlink/?linkid=196351).  
  
## <a name="see-also"></a>См. также:  
 [Настройка учетных записей служб &#40;Analysis Services&#41;](../../../2014/analysis-services/instances/configure-service-accounts-analysis-services.md)   
 [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
