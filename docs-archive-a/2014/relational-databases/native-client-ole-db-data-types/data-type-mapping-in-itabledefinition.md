---
title: Сопоставление типов данных в интерфейсе ITableDefinition | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e58f61231f3e2acfdccaa52117d360a7ba261f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655705"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Сопоставление типов данных в интерфейсе ITableDefinition
  При создании таблиц с помощью функции **ITableDefinition:: CreateTable** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель поставщика OLE DB собственного клиента может указывать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных в *pwszTypeName* члене передаваемого массива DBCOLUMNDESC. Если потребитель указывает тип данных столбца по имени, то сопоставление типов OLE DB, представляемое элементом *wType* структуры DBCOLUMNDESC, не учитывается.  
  
 При указании новых типов данных столбцов с OLE DB типами данных с помощью элемента *wType* Structure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB сопоставляет OLE DB типы данных следующим образом.  
  
|Тип данных OLE DB|SQL Server<br /><br /> тип данных|Дополнительные сведения|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** или **varbinary(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента проверяет элемент *ULCOLUMNSIZE* структуры DBCOLUMNDESC. Основываясь на значении и версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента сопоставляет тип с **изображением**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных **binary** , то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB проверяет элемент DBCOLUMNDESC *rgPropertySets* . Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB Native Client сопоставляет тип с **двоичным**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB Native Client сопоставляет тип с типом **varbinary**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца SQL Server.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик собственного клиента OLE DB проверяет элементы Дбколумдеск *БпреЦисион* и *bScale* , чтобы определить точность и масштаб для **числового** столбца.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** или **varchar(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента проверяет элемент *ULCOLUMNSIZE* структуры DBCOLUMNDESC. Основываясь на значении и версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента сопоставляет тип с **текстом**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных с многобайтовой кодировкой, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента проверяет элемент DBCOLUMNDESC *rgPropertySets* . Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента сопоставляет тип с типом **char**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB Native Client сопоставляет тип с типом **varchar**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBTYPE_UDT|**UDT**|Следующие сведения используются в `DBCOLUMNDESC` структурах с помощью **ITableDefinition:: CreateTable** , если требуются столбцы определяемого пользователем типа:<br /><br /> -   *pwSzTypeName* игнорируется.<br />-   *rgPropertySets* должен включать `DBPROPSET_SQLSERVERCOLUMN` набор свойств, как описано в разделе об `DBPROPSET_SQLSERVERCOLUMN` [использовании определяемых пользователем типов](../native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** или **nvarchar(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента проверяет элемент *ULCOLUMNSIZE* структуры DBCOLUMNDESC. Основываясь на значении, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB сопоставляет тип с типом **ntext**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных character в Юникоде, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента проверяет элемент DBCOLUMNDESC *rgPropertySets* . Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента сопоставляет тип с типом **nchar**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB Native Client сопоставляет тип с типом **nvarchar**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  При создании новой таблицы поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставляет только значения перечислений типов данных OLE DB, указанные в предшествующей таблице. Попытка создать таблицу со столбцом любого другого типа данных OLE DB приводит к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (OLE DB)](data-types-ole-db.md)  
  
  
