---
title: Удалите определяемые пользователем типы, названные после зарезервированных геометрических и географических типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4977d45d53e1114edc8e04ad504963bae0b9eb9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751699"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a>Удалите определяемые пользователем типы с именами, совпадающими с зарезервированными типами данных GEOMETRY и GEOGRAPHY
  Помощник по обновлению обнаружил определяемый пользователем тип, имя которого совпадает с именем, зарезервированным для типа данных `geometry` или `geography`. Типы данных `geometry` и `geography` являются частью компонента для обработки пространственных данных.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Имена терминов, используемых в типах пространственных данных, не должны использоваться в качестве имен определяемых пользователем типов среды CLR или их псевдонимов.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите определяемый пользователем тип и создайте его повторно с именем, отличным от зарезервированного.  
  
## <a name="external-resources"></a>Внешние ресурсы  
 [Создание определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
