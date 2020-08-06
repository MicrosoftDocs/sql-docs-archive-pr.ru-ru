---
title: Функция LocalDBFormatMessage | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBFormatMessage
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 31b3152a-94cf-4f75-a31b-296d7dd16dbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ece28f19e3488fae248bf26c3a54a018ba6efd0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752160"
---
# <a name="localdbformatmessage-function"></a>Функция LocalDBFormatMessage
  Возвращает локализованное текстовое описание для указанной ошибки SQL Server Express LocalDB.  
  
 **Файл заголовка:** sqlncli.h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT LocalDBFormatMessage(  
           HRESULT hrLocalDB,  
           DWORD dwFlags,   
           DWORD dwLanguageId,   
           LPWSTR wszMessage,   
           LPDWORD lpcchMessage   
);  
```  
  
## <a name="parameters"></a>Параметры  
 *хрлокалдб*  
 [Вход] Код ошибки LocalDB.  
  
 *dwFlags*  
 [Вход] Флаги, задающие поведение этой функции.  
  
 Доступные флаги:  
  
 LOCALDB_TRUNCATE_ERR_MESSAGE  
 Если размер входного буфера окажется недостаточным, сообщение об ошибке урезается до длины буфера.  
  
 *двлангуажеид*  
 [Вход] Требуемый язык (LANGID) или значение 0. В последнем случае используется порядок языков Win32 FormatMessage.  
  
 *wszMessage*  
 [Выход] Буфер для сохранения сообщения об ошибке LocalDB.  
  
 *лпкчмессаже*  
 [Вход/выход] На входе содержит размер буфера *wszMessage* в символах. На выходе, если указан недостаточный размер буфера, содержит требуемый размер буфера в символах, включая любые конечные символы NULL. При успешном завершении работы функции содержит количество символов в сообщении без учета конечных символов NULL.  
  
## <a name="returns"></a>Возвращаемое значение  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 Компонент SQL Server Express LocalDB не установлен на компьютере.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Один или несколько указанных входных параметров недопустимы.  
  
 [LOCALDB_ERROR_UNKNOWN_ERROR_CODE](../express-localdb-error-messages/localdb-error-unknown-error-code.md)  
 Запрошенное сообщение не существует.  
  
 [LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID](../express-localdb-error-messages/localdb-error-unknown-language-id.md)  
 Сообщение недоступно на запрошенном языке.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Размер входного буфера *wszMessage* недостаточный; усечение не было запрошено.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="remarks"></a>Remarks  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также:  
 [Заголовок и сведения о версии SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  
