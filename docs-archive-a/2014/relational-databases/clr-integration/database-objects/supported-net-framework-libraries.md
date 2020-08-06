---
title: Поддерживаемые библиотеки .NET Framework | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f92e3eadccc869452cf35534f786724c8e259a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654343"
---
# <a name="supported-net-framework-libraries"></a>Поддерживаемые библиотеки платформы .NET Framework
  Если среда CLR размещается в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то появляется возможность разрабатывать на управляемом коде хранимые процедуры, триггеры, определяемые пользователем функции, определяемые пользователем типы и определяемые пользователем статистические функции. Функциональность, реализованная в библиотеках классов платформы .NET Framework, предоставляет доступ к предварительно построенным классам для операций со строками, сложных математических операций, доступа к файлам, шифрования и т. д. Доступ к этим классам легко получить из любой управляемой хранимой процедуры, определяемого пользователем типа, триггера, определяемой пользователем функции или определяемой пользователем статистической функции.  
  
> [!NOTE]  
>  При обслуживании или обновлении неподдерживаемых сборок в глобальном кэше сборок (GAC) ваш [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Если сборка существует и в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] интеграции со средой CLR. При обслуживании или обновлении любых сборок в глобальном кэше сборок, которые также зарегистрированы в базе данных, в том числе неподдерживаемых сборок платформы .NET Framework, необходимо обеспечить обслуживание или обновление копии сборки в базах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции `ALTER ASSEMBLY`. Дополнительные сведения см. в [статье базы знаний 949080](https://support.microsoft.com/kb/949080).  
  
## <a name="supported-libraries"></a>Поддерживаемые библиотеки  
 Начиная с [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] имеет список поддерживаемых .NET Framework библиотек, проверенных на соответствие стандартам надежности и безопасности для взаимодействия с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] загрузкой их непосредственно из глобального кэша сборок (GAC).  
  
 Библиотеки и пространства имен, поддерживаемые интеграцией со средой CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   CustomMarshalers  
  
-   Microsoft.VisualBasic  
  
-   Microsoft.VisualC  
  
-   mscorlib  
  
-   Система  
  
-   System.Configuration  
  
-   System.Data  
  
-   System.Data.OracleClient  
  
-   System.Data.SqlXml  
  
-   System.Deployment  
  
-   System.Security  
  
-   System.Transactions  
  
-   System.Web.Services  
  
-   System.Xml  
  
-   System.Core.dll  
  
-   System.Xml.Linq.dll  
  
## <a name="unsupported-libraries"></a>Неподдерживаемые библиотеки  
 Неподдерживаемые библиотеки могут быть вызваны из управляемых хранимых процедур, триггеров, определяемых пользователем функций, определяемых пользователем типов и определяемых пользователем статистических функций. Неподдерживаемые библиотеки должны быть сначала зарегистрированы в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции `CREATE ASSEMBLY`, прежде чем ее можно будет использовать в пользовательском коде. Любая неподдерживаемая библиотека, зарегистрированная и работающая на сервере, должна быть просмотрена и проверена в отношении безопасности и надежности.  
  
 Например, не поддерживается пространство имен `System.DirectoryServices`. Необходимо зарегистрировать сборку System.DirectoryServices.dll с разрешением `UNSAFE`, прежде чем ее можно будет вызвать из пользовательского кода. Разрешение `UNSAFE` необходимо, так как классы в пространстве имен `System.DirectoryServices` не соответствуют требованиям для разрешений `SAFE` и `EXTERNAL_ACCESS`. Дополнительные сведения см. в разделе [ограничения модели программирования интеграции со средой CLR](clr-integration-programming-model-restrictions.md) и [Безопасность доступа к коду интеграции CLR](../security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание сборки](../assemblies/creating-an-assembly.md)   
 [Безопасность доступа к коду при интеграции со средой CLR](../security/clr-integration-code-access-security.md)   
 [Ограничения модели программирования на основе интеграции со средой CLR](clr-integration-programming-model-restrictions.md)  
  
  
