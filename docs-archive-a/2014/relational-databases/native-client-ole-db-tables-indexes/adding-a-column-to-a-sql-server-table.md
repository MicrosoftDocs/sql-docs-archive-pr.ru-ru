---
title: Добавление столбца к таблице SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 97aa2656ccde662a34e1dd80fd662b22f601d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739800"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Добавление столбца к таблице SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB Native Client предоставляет функцию **ITableDefinition:: addColumn** . Это позволяет пользователю добавить столбец в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При добавлении столбца в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель поставщика OLE DB собственного клиента ограничивается следующим образом:  
  
-   Если значение DBPROP_COL_AUTOINCREMENT равно VARIANT_TRUE, то значение DBPROP_COL_NULLABLE должно быть равно VARIANT_FALSE.  
  
-   Если столбец принадлежит к типу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**, значение DBPROP_COL_NULLABLE должно быть равно VARIANT_FALSE.  
  
-   Для столбца любого другого типа DBPROP_COL_NULLABLE должно быть равно VARIANT_TRUE.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Имя столбца задается в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в элементе *dbcid* параметра *pColumnDesc* типа DBCOLUMNDESC. Элемент *eKind* должен быть равен DBKIND_NAME.  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
