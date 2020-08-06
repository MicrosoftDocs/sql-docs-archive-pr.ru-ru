---
title: Параметр конфигурации сервера "clr enabled" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b83cd0e00bdd32c8b44667209544c8e81b1e90c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655364"
---
# <a name="clr-enabled-server-configuration-option"></a>Параметр конфигурации сервера «clr enabled»
  Используйте параметр «clr enabled», чтобы указать, может ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполнять пользовательские сборки. Параметр clr enabled предлагает следующие значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Выполнение сборок не разрешается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|1|Выполнение сборок разрешается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 Чтобы изменения этого параметра вступили в силу, необходимо перезагрузить серверы WOW64. Для других типов серверов перезагрузка необязательна.  
  
> [!NOTE]  
>  При выполнении инструкции RECONFIGURE и изменении значения параметра «clr enabled» с 1 на 0 все домены приложений, содержащих пользовательские сборки, немедленно выгружаются.  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Отключите один из двух параметров: clr enabled или lightweight pooling. Функции, зависящие от среды CLR и неправильно работающие в режиме волокон, включают тип данных `hierarchy`, репликацию и управление на основе политик.  
  
## <a name="example"></a>Пример  
 В следующем примере сначала отображается текущая настройка параметра clr enabled, а затем параметр включается с заданием значения 1. Чтобы отключить этот параметр, задайте значение 0.  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера «использование упрощенных пулов»](lightweight-pooling-server-configuration-option.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Параметр конфигурации сервера «использование упрощенных пулов»](lightweight-pooling-server-configuration-option.md)  
  
  
