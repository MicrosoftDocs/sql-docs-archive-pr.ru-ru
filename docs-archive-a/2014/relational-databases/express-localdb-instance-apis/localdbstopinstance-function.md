---
title: Функция Локалдбстопинстанце | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 4bd73187-0aac-4f03-ac54-2b78e41917e5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 48b014e65e0a02a5f866e5301b12dae3cd255b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728254"
---
# <a name="localdbstopinstance-function"></a>Функция LocalDBStopInstance
  Останавливает указанный запущенный экземпляр SQL Server Express LocalDB.  
  
 **Файл заголовка:** sqlncli.h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT LocalDBStopInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           ULONG ulTimeout   
);  
```  
  
## <a name="parameters"></a>Параметры  
 *пинстанценаме*  
 [Вход] Имя останавливаемого экземпляра LocalDB.  
  
 *dwFlags*  
 [Вход] Значение или сочетание значений флагов, задающее способ остановки экземпляра.  
  
 Доступные флаги:  
  
 LOCALDB_SHUTDOWN_KILL_PROCESS  
 Завершает работу немедленно с помощью команды уничтожения процесса операционной системы.  
  
 LOCALDB_SHUTDOWN_WITH_NOWAIT  
 Завершает работу с использованием параметра WITH NOWAIT команды Transact-SQL.  
  
 Если ни один из флагов не установлен, работа экземпляра LocalDB завершается с помощью команды Transact-SQL SHUTDOWN. Если установлены оба флага, приоритет имеет флаг LOCALDB_SHUTDOWN_KILL_PROCESS.  
  
 *ултимеаут*  
 [Вход] Время ожидания выполнения операции в секундах. Если это значение равно 0, функция немедленно возвращает управление, не ожидая остановки локального экземпляра LocalDB.  
  
## <a name="returns"></a>Возвращаемое значение  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 Компонент SQL Server Express LocalDB не установлен на компьютере.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Один или несколько указанных входных параметров недопустимы.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 Указанное имя экземпляра недопустимо.  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 Экземпляр не существует.  
  
 [LOCALDB_ERROR_WAIT_TIMEOUT](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 При попытке получения блокировок синхронизации истекло время ожидания.  
  
 [LOCALDB_ERROR_INSTANCE_STOP_FAILED](../express-localdb-error-messages/localdb-error-instance-stop-failed.md)  
 Операцию остановки не удалось завершить в течение заданного времени.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Длина пути к месту хранения экземпляра больше MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 Не удалось получить папку профиля пользователя.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 Не удалось получить доступ к папке экземпляра.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Не удалось получить доступ к реестру экземпляра.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Конфигурация экземпляра повреждена.  
  
 [LOCALDB_ERROR_CALLER_IS_NOT_OWNER](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 Вызывающий API не является владельцем экземпляра LocalDB.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="remarks"></a>Remarks  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также:  
 [Заголовок и сведения о версии SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  
