---
title: Материализованные объекты источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- SQL Server Native Client OLE DB provider, persisted data source objects
- persisted data source objects
ms.assetid: dfdacc81-42fe-4f20-8969-bed1f743defe
author: rothja
ms.author: jroth
ms.openlocfilehash: d6d115b6640c910a70a9a29a36607a122f650c3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655711"
---
# <a name="persisted-data-source-objects"></a>Материализованные данные исходного объекта
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента поддерживает сохраненные объекты источника данных с помощью интерфейса **IPersistFile** .  
  
## <a name="examples"></a>Примеры  
 **А. Сохранение инициализации источника данных**  
  
 В данном примере показана функция, которая сохраняет свойства инициализации источника данных, определяющих сервер, базу данных и использование для соединения режима проверки подлинности Windows. Имена сервера и базы данных получаются в параметрах *pLocation* и *pDatasource* функции.  
  
```  
HRESULT SetAndSaveInitProps  
    (  
    IDBInitialize* pIDBInitialize,  
    WCHAR* pDataSource,  
    WCHAR* pCatalog,  
    BOOL bUseWinNTAuth  
    )  
    {  
    const ULONG     nProps = 4;  
    ULONG           nSSProps;  
    ULONG           nPropSets;  
    ULONG           nProp;  
    IDBProperties*  pIDBProperties  = NULL;  
    IPersistFile*   pIPersistFile   = NULL;  
    DBPROP          aInitProps[nProps];  
    DBPROP*         aSSInitProps    = NULL;  
    DBPROPSET*      aInitPropSets   = NULL;  
    HRESULT         hr;  
  
        nSSProps = 0;  
        nPropSets = 1;  
  
    aInitPropSets = new DBPROPSET[nPropSets];  
  
    // Initialize common property options.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        VariantInit(&aInitProps[nProp].vValue);  
        aInitProps[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        aInitProps[nProp].colid = DB_NULLID;  
        }  
  
    // Level of prompting that will be done to complete the connection  
    // process.  
    aInitProps[0].dwPropertyID = DBPROP_INIT_PROMPT;  
    aInitProps[0].vValue.vt = VT_I2;  
    aInitProps[0].vValue.iVal = DBPROMPT_NOPROMPT;       
  
    // Server name.  
    aInitProps[1].dwPropertyID = DBPROP_INIT_DATASOURCE;      
    aInitProps[1].vValue.vt = VT_BSTR;  
    aInitProps[1].vValue.bstrVal = SysAllocString(pDataSource);  
  
    // Database.  
    aInitProps[2].dwPropertyID = DBPROP_INIT_CATALOG;  
    aInitProps[2].vValue.vt = VT_BSTR;  
    aInitProps[2].vValue.bstrVal = SysAllocString(pCatalog);  
  
    aInitProps[3].dwPropertyID = DBPROP_AUTH_INTEGRATED;  
    if (bUseWinNTAuth == TRUE)  
    {  
        aInitProps[3].vValue.vt = VT_BSTR;  
        aInitProps[3].vValue.bstrVal = SysAllocString(L"SSPI");  
    } //end if  
  
    // Now that properties are set, construct the PropertySet array.  
    aInitPropSets[0].guidPropertySet = DBPROPSET_DBINIT;  
    aInitPropSets[0].cProperties = nProps;  
    aInitPropSets[0].rgProperties = aInitProps;  
  
    // Set initialization properties  
    pIDBInitialize->QueryInterface(IID_IDBProperties,  
        (void**) &pIDBProperties);  
    hr = pIDBProperties->SetProperties(nPropSets, aInitPropSets);  
    if (FAILED(hr))  
        {  
        // Display error from failed SetProperties.  
        }  
    pIDBProperties->Release();  
  
    // Free references on OLE known strings.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        if (aInitProps[nProp].vValue.vt == VT_BSTR)  
            SysFreeString(aInitProps[nProp].vValue.bstrVal);  
        }  
  
    for (nProp = 0; nProp < nSSProps; nProp++)  
        {  
        if (aSSInitProps[nProp].vValue.vt == VT_BSTR)  
            SysFreeString(aSSInitProps[nProp].vValue.bstrVal);  
        }  
  
    // Free dynamically allocated memory.  
    delete [] aInitPropSets;  
    delete [] aSSInitProps;  
  
    // On success, persist the data source.  
    if (SUCCEEDED(hr))  
        {  
        pIDBInitialize->QueryInterface(IID_IPersistFile,  
            (void**) &pIPersistFile);  
  
        hr = pIPersistFile->Save(OLESTR("MyDataSource.txt"), FALSE);  
  
        if (FAILED(hr))  
            {  
            // Display errors from IPersistFile interface.  
            }  
        pIPersistFile->Release();  
        }  
  
    return (hr);  
    }  
```  
  
 **Б. Использование инициализации материализованных источников данных**  
  
 Данный пример использует материализованный объект источника данных с дополнительными свойствами инициализации, который предоставляет имя входа и пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
HRESULT InitFromPersistedDS  
    (  
    IDBInitialize* pIDBInitialize,  
    WCHAR* pPersistedDSN,  
    WCHAR* pUID,  
    WCHAR* pPWD  
    )  
    {  
    //const ULONG   nProps = 3;  
    const ULONG     nProps = 1;  
    const ULONG     nPropSets = 1;  
    ULONG           nProp;  
    IDBProperties*  pIDBProperties  = NULL;  
    IPersistFile*   pIPersistFile   = NULL;  
    DBPROP          aInitProps[nProps];  
    DBPROPSET       aInitPropSets[nPropSets];  
    HRESULT         hr;  
  
    // First load the persisted data source information.  
    pIDBInitialize->QueryInterface(IID_IPersistFile,  
        (void**) &pIPersistFile);  
  
    hr = pIPersistFile->Load(pPersistedDSN, STGM_DIRECT);  
  
    if (FAILED(hr))  
        {  
        // Display errors from IPersistFile interface.  
        }  
    pIPersistFile->Release();  
  
    if (FAILED(hr))  
        {  
        return (hr);  
        }  
  
    // Initialize common property options.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        VariantInit(&aInitProps[nProp].vValue);  
        aInitProps[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        aInitProps[nProp].colid = DB_NULLID;  
        }  
  
    // Level of prompting that will be done to complete the connection  
    // process.  
    aInitProps[0].dwPropertyID = DBPROP_INIT_PROMPT;  
    aInitProps[0].vValue.vt = VT_I2;  
    aInitProps[0].vValue.iVal = DBPROMPT_NOPROMPT;      
  
    // Now that properties are set, construct the PropertySet array.  
    aInitPropSets[0].guidPropertySet = DBPROPSET_DBINIT;  
    aInitPropSets[0].cProperties = nProps;  
    aInitPropSets[0].rgProperties = aInitProps;  
  
    // Set initialization properties  
    pIDBInitialize->QueryInterface(IID_IDBProperties,  
        (void**) &pIDBProperties);  
    hr = pIDBProperties->SetProperties(nPropSets, aInitPropSets);  
    if (SUCCEEDED(hr))  
        {  
        hr = pIDBInitialize->Initialize();  
        if (FAILED(hr))  
            {  
            DumpError(pIDBInitialize, IID_IDBInitialize);  
            }  
        }  
    else  
        {  
        // Display error from failed SetProperties.  
        }  
    pIDBProperties->Release();  
  
    // Free references on OLE known strings.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        if (aInitProps[nProp].vValue.vt == VT_BSTR)  
            SysFreeString(aInitProps[nProp].vValue.bstrVal);  
        }  
  
    return (hr);  
    }  
```  
  
 Метод **IPersistFile::Save** можно вызвать до или после вызова метода **IDBInitialize::Initialize**. Вызов метода после успешного возвращения из метода **IDBInitialize::Initialize** гарантирует сохранение допустимой спецификации источника данных.  
  
## <a name="see-also"></a>См. также:  
 [Объекты источников данных (OLE DB)](data-source-objects-ole-db.md)  
  
  
