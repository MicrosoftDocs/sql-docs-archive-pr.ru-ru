---
title: Удаление определяемого пользователем типа&#39;s с именем, зарезервированным типами данных даты и времени | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 827f060b309a7a620fd448554b074f45d78d3cb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666363"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a>Удалить определяемый пользователем тип&#39;s с именем, зарезервированным типом данных даты и времени
  Помощник по обновлению обнаружил определяемый пользователем тип, имя которого совпадает с именем, зарезервированным для типа данных `date` или `time`.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Имена терминов, используемых для типов данных, не должны использоваться в качестве имен определяемых пользователем типов среды CLR или их псевдонимов.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите определяемый пользователем тип и создайте его повторно с именем, отличным от зарезервированного.  
  
  
