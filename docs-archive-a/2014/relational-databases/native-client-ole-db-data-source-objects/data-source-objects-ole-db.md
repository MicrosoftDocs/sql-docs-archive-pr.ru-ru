---
title: Объекты источника данных (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cf3f0b0308d655b50149c174547c19966f550ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728229"
---
# <a name="data-source-objects-ole-db"></a>Объекты источников данных (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Собственный клиент использует термин источник данных для набора OLE DB интерфейсов, используемых для установления связи с хранилищем данных, например [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Создание экземпляра объекта источника данных поставщика является первой задачей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителя собственного клиента.  
  
 Каждый поставщик OLE DB объявляет свой идентификатор класса (CLSID). Идентификатором CLSID для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика собственного клиента OLE DB является GUID C/C++, CLSID_SQLNCLI10 (символ SQLNCLI_CLSID будет разрешаться в правильный идентификатор ProgID в файле sqlncli. h, на который вы ссылаетесь). Используя CLSID, потребитель может вызвать функцию OLE **CoCreateInstance** для создания экземпляра объекта источника данных.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Собственный клиент — это внутрипроцессный сервер. Экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов поставщика собственного клиента OLE DB создаются с помощью макроса CLSCTX_INPROC_SERVER для указания контекста исполняемого файла.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Объект источника данных поставщика собственного клиента OLE DB предоставляет интерфейсы инициализации OLE DB, позволяющие потребителю подключаться к существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базам данных.  
  
 Каждое подключение, устанавливаемое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком OLE DB собственного клиента, задает эти параметры автоматически:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 В этом примере используется макрос идентификатора класса для создания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB объекта источника данных поставщика и получения ссылки на его интерфейс **IDBInitialize** .  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 При успешном создании экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекта источника данных поставщика собственного клиента OLE DB приложение-потребитель может продолжать работу, инициализируя источник данных и создавая сеансы. Сеансы OLE DB предоставляют интерфейсы, через которые можно получать доступ к данным и манипулировать ими.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента выполняет свое первое подключение к указанному экземпляру в ходе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] успешной инициализации источника данных. Соединение с источником данных поддерживается до тех пор, пока хранятся ссылки на любой интерфейс инициализации источника данных или пока не вызван метод **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Свойства источника данных &#40;OLE DB&#41;](data-source-properties-ole-db.md)  
  
-   [Свойства сведений об источнике данных](data-source-information-properties.md)  
  
-   [Свойства инициализации и авторизации](initialization-and-authorization-properties.md)  
  
-   [Сеансы](sessions.md)  
  
-   [Свойства сеанса](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Материализованные данные исходного объекта](persisted-data-source-objects.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (OLE DB)](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
