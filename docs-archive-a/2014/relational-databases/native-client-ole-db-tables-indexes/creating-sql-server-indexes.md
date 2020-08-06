---
title: Создание индексов SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: rothja
ms.author: jroth
ms.openlocfilehash: 3693355eec7a290c03658c10db500161aa52062d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739785"
---
# <a name="creating-sql-server-indexes"></a>Создание индексов SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик собственного клиента OLE DB предоставляет функцию **IIndexDefinition:: CreateIndex** , позволяющую потребителям определять новые индексы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицах.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента создает индексы таблицы как индексы или ограничения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет право создания ограничений владельцу таблицы, владельцу базы данных и членам некоторых административных ролей. По умолчанию только владелец таблицы может создавать в ней индекс. Таким образом, успех или сбой функции **CreateIndex** зависит не только от прав доступа пользователя приложения, но и от типа создаваемого индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Параметр *pIndexID* может иметь значение null, а если это так, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB создает уникальное имя для индекса. Потребитель может сам задать имя индекса, указав для DBID допустимый указатель в параметре *ppIndexID*.  
  
 Потребитель может задать имя индекса в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* параметра *pIndexID*. Элемент *eKind* параметра *pIndexID* должен быть равен DBKIND_NAME.  
  
 Потребитель указывает столбец или столбцы, входящие в индекс, по имени. Для каждой структуры DBINDEXCOLUMNDESC, используемой в функции **CreateIndex**, элемент *eKind* параметра *pColumnID* должен быть DBKIND_NAME. Имя столбца задается в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* параметра *pColumnID*.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик собственного клиента OLE DB и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает сортировку по возрастанию значений в индексе. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает E_INVALIDARG, если потребитель указывает DBINDEX_COL_ORDER_DESC в любой структуре дбиндексколумндеск.  
  
 Функция **CreateIndex** интерпретирует свойства индекса указанным ниже образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|Ч/З Чтение/запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_CLUSTERED|Ч/З Чтение/запись<br /><br /> Значение по умолчанию: VARIANT_FALSE<br /><br /> Описание: управляет кластеризацией индекса.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента пытается создать кластеризованный индекс для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает не более одного кластеризованного индекса в любой таблице.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента пытается создать некластеризованный индекс для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.|  
|DBPROP_INDEX_FILLFACTOR|Ч/З Чтение/запись<br /><br /> По умолчанию: 0<br /><br /> Описание: указывает процент страниц индекса, используемых для хранения. Дополнительные сведения см. в разделе [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql).<br /><br /> Тип варианта — VT_I4. Значение должно находиться в диапазоне от 1 до 100.|  
|DBPROP_INDEX_INITIALIZE|Ч/З Чтение/запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLCOLLATION|Ч/З Чтение/запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLS|Ч/З Чтение/запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_PRIMARYKEY|Ч/З Чтение/запись<br /><br /> Значение по умолчанию: VARIANT_FALSE Description: создает индекс как ссылочную целостность, ограничение ПЕРВИЧного ключа.<br /><br /> VARIANT_TRUE: индекс создается для поддержки ограничения PRIMARY KEY таблицы. Столбцы не должны иметь значений NULL.<br /><br /> VARIANT_FALSE: индекс не используется в качестве ограничения PRIMARY KEY для значений строк таблицы.|  
|DBPROP_INDEX_SORTBOOKMARKS|Ч/З Чтение/запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TEMPINDEX|Ч/З Чтение/запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TYPE|Ч/З Чтение/запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_UNIQUE|Ч/З Чтение/запись<br /><br /> Значение по умолчанию: VARIANT_FALSE<br /><br /> Описание: создает индекс в виде ограничения UNIQUE для определенного столбца или столбцов.<br /><br /> VARIANT_TRUE: индекс используется для уникального ограничения значений в строках таблицы.<br /><br /> VARIANT_FALSE: индекс не используется для уникального ограничения значений строк.|  
  
 В DBPROPSET_SQLSERVERINDEX свойств, зависящих от поставщика, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента определяет следующее свойство сведений об источнике данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|Тип: VT_BOOL (R/W)<br /><br /> Значение по умолчанию: VARIANT_FALSE<br /><br /> Описание: если при вызове метода IIndexDefinition::CreateIndex это свойство указывается со значением VARIANT_TRUE, создается первичный XML-индекс, соответствующий индексированному столбцу. Если это свойство имеет значение VARIANT_TRUE, параметр cIndexColumnDescs должен быть равен 1. В противном случае возникает ошибка.|  
  
 В данном примере создается индекс первичного ключа.  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
