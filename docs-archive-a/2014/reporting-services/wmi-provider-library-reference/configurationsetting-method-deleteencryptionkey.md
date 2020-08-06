---
title: Метод DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptionKey method
ms.assetid: ed2f25b6-6a63-468d-9279-a577ca01b096
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e302659615bd620b3b0ed802b83aafc4e9506d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658634"
---
# <a name="deleteencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="830da-102">Метод DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="830da-102">DeleteEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="830da-103">Удаляет ключи шифрования из базы данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="830da-103">Deletes the encryption keys from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="830da-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="830da-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptionKeys(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptionKeys(string InstallationID, out Int32 HRESULT,   
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="830da-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="830da-105">Parameters</span></span>  
 <span data-ttu-id="830da-106">*InstallationID*</span><span class="sxs-lookup"><span data-stu-id="830da-106">*InstallationID*</span></span>  
 <span data-ttu-id="830da-107">Код установки сервера отчетов, который находится в таблице ключей в базе данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="830da-107">The installation ID of a report server that is in the keys table of the report server database.</span></span>  
  
 <span data-ttu-id="830da-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="830da-108">*HRESULT*</span></span>  
 <span data-ttu-id="830da-109">[out] Значение, которое указывает, окончился ли вызов успехом или сбоем.</span><span class="sxs-lookup"><span data-stu-id="830da-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="830da-110">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="830da-110">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="830da-111">[out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.</span><span class="sxs-lookup"><span data-stu-id="830da-111">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="830da-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="830da-112">Return Value</span></span>  
 <span data-ttu-id="830da-113">Возвращает значение HRESULT, которое является признаком успешного или неуспешного завершения вызова метода.</span><span class="sxs-lookup"><span data-stu-id="830da-113">Returns an HRESULT indicating success or failure of the method call.</span></span> <span data-ttu-id="830da-114">Значение 0 указывает, что вызов метода завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="830da-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="830da-115">Ненулевое значение указывает, что произошла ошибка.</span><span class="sxs-lookup"><span data-stu-id="830da-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="830da-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="830da-116">Remarks</span></span>  
 <span data-ttu-id="830da-117">Метод *DeleteEncryptionKey* удаляет записи из таблицы ключей для любых серверов отчетов, у которых есть доступ к защищенным сведениям в базе данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="830da-117">The *DeleteEncryptionKey* method deletes entries from the keys table for any report servers that have access to the secure information in the report server database.</span></span> <span data-ttu-id="830da-118">Если указанный параметр *InstallationID* не соответствует коду установки в базе данных, то метод возвращает ошибку.</span><span class="sxs-lookup"><span data-stu-id="830da-118">If the *InstallationID* parameter specified does not correspond to an installation ID in the database, the method returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="830da-119">Требования</span><span class="sxs-lookup"><span data-stu-id="830da-119">Requirements</span></span>  
 <span data-ttu-id="830da-120">**Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="830da-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="830da-121">См. также:</span><span class="sxs-lookup"><span data-stu-id="830da-121">See Also</span></span>  
 [<span data-ttu-id="830da-122">Элементы MSReportServer_ConfigurationSetting</span><span class="sxs-lookup"><span data-stu-id="830da-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
