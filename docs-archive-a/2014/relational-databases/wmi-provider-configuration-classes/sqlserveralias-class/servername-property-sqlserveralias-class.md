---
title: Свойство ServerName (класс SqlServerAlias) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ServerName Property (SqlServerAlias Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ServerName property
ms.assetid: 58c82b19-b548-42fa-9c5a-059b606da097
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 793bcbeb63ab0e91ccf4c4c63b3ee42ec17d5c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668689"
---
# <a name="servername-property-sqlserveralias-class"></a>Свойство ServerName (класс SqlServerAlias)
  Возвращает имя экземпляра, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] заданного псевдонимом соединения сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.ServerName [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServerAlias](sqlserveralias-class.md) , представляющий псевдоним [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строковое значение, определяющее имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на который ссылается псевдоним соединения сервера.  
  
## <a name="remarks"></a>Remarks  
  
