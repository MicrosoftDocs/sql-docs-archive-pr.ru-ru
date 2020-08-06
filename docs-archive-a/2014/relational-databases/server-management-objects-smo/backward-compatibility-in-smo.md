---
title: Обратная совместимость в SMO | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73b6f4eebccf23850ccf08ec95ccb59dbc5c6293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664135"
---
# <a name="backward-compatibility-in-smo"></a>Обратная совместимость в SMO
  Приложения объектов SMO, написанные с помощью предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можно повторно компилировать с помощью объекта SMO в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="migrating-smo-applications"></a>Миграция приложений объектов SMO  
 Ссылки на DLL-библиотеки SMO в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны быть удалены, а на их место необходимо вставить ссылки на новые DLL-библиотеки SMO, представленные в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
 Необходимо предоставить ссылки, как минимум, на следующие файлы:  
  
-   Microsoft.SqlServer.ConnectionInfo  
  
-   Microsoft.SqlServer.Smo  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc  
  
 Эти файлы необходимы для классов соединений, служебных классов SMO и классов SFC.  
  
> [!NOTE]  
>  Файл SmoEnum.dll удален. Ссылка на этот файл должна быть удалена из проекта SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
 Пространства имен также были изменены. Воспользуйтесь следующими:  
  
##### <a name="for-visual-c"></a>Для Visual C#  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a>Для Visual Basic  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 Если в коде используется функциональность URN типа `Server.GetSqlSmoObject(Urn)`, необходимо установить связь с пространством имен Microsoft.SqlServer.Management.Sdk.Sfc.  
  
 Если данный код использует передачу объектов непосредственно, необходимо установить связь с пространством имен Microsoft.SqlServer.Management.SmoExtended.  
  
 В случае выполнения миграции кода, может понадобиться изменение кода. Это происходит потому, что некоторые функции [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]устарели. Дополнительные сведения об устаревших функциях см. в разделе [устаревшие ядро СУБД функции в SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] электронной документации по.  
  
  
