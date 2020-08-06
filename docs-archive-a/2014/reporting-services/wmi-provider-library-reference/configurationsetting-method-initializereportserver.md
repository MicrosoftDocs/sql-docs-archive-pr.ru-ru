---
title: Метод InitializeReportServer (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6a8e44a98320ca2c9add6a1b6eef9362eef7731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658630"
---
# <a name="initializereportserver-method-wmi-msreportserver_configurationsetting"></a>Метод InitializeReportServer (WMI MSReportServer_ConfigurationSetting)
  Инициализирует указанный экземпляр службы отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Параметры  
 *InstallationID*  
 Строка, используемая для шифрования ключа шифрования перед его возвращением.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 При вызове этого метода ключ шифрования, который обращается к защищенным сведениям в базе данных сервера отчетов, зашифровывается с помощью открытого ключа сервера отчетов, определенного параметром *InstallationID*.  
  
 Указанный открытый ключ сервера отчетов должен быть предварительно записан в базу данных сервера отчетов.  
  
 Метод *InitializeReportServer* должен вызываться для сервера отчетов, который уже имеет доступ к защищенным сведениям, и поэтому может расшифровать ключ шифрования. Полученный зашифрованный ключ шифрования сохраняется в базе данных сервера отчетов.  
  
 Если [для свойства "](configurationsetting-property-isinitialized.md) InitializeReportServer" сервера отчетов задано значение `true` при вызове метода, метод возвращает результат, не пытаясь зашифровать ключ шифрования.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
