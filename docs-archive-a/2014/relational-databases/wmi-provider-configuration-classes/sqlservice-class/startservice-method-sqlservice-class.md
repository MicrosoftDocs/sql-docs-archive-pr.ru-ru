---
title: Метод StartService (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartService method
ms.assetid: 83dfb6bd-dbd5-45d8-aad2-a11926317f91
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d91646da2ac2c9f636655ff6c65808ba115e28f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733717"
---
# <a name="startservice-method-sqlservice-class"></a>Метод StartService (класс SqlService)
  Пытается перевести службу в состояние запуска.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.StartService()  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32 определяет одно из следующих состояний запуска.  
  
 0  
 Успешно. Запрос принят.  
  
 1  
 Не поддерживается. Запрос не поддерживается.  
  
 2  
 Доступ запрещен. Пользователь не имеет соответствующих прав доступа.  
  
 3  
 Запущены зависимые службы. Службу нельзя остановить, так как от нее зависят другие работающие службы.  
  
 4  
 Недопустимый управляющий код службы. Запрошенный управляющий код недопустим или неприемлем для данной службы.  
  
 5  
 Служба не принимает управляющий код. Запрошенный управляющий код не может быть отправлен службе, так как ее состояние (Win32_BaseService:State) равно 0, 1 или 2.  
  
 6  
 Служба неактивна. Служба не запущена.  
  
 7  
 Истекло время ожидания запроса службы. Служба не ответила на запрос запуска за отведенное время.  
  
 8  
 Неизвестный сбой. При запуске службы произошла неизвестная ошибка.  
  
 9  
 Путь не найден. Не найден каталог исполняемого файла службы.  
  
 10  
 Служба уже запущена. Служба уже запущена.  
  
 11  
 База данных служб заблокирована. База данных для добавления новой службы заблокирована.  
  
 12  
 Удалена зависимость службы. Служба, от которой зависит эта служба, была удалена из системы.  
  
 13  
 Сбой зависимости службы. Этой службе не удалось найти службу, которая необходима зависимой службе.  
  
 14  
 Служба отключена. Эта служба была отключена в системе.  
  
 15  
 Сбой входа службы в систему. Эта служба не поддерживает проверку подлинности, необходимую для работы в системе.  
  
 16  
 Служба помечена для удаления. Служба удаляется из системы.  
  
 17  
 Служба без потоков. Отсутствует поток исполнения для этой службы.  
  
 18  
 Состояние «Циклическая зависимость». При запуске службы обнаружены циклические зависимости.  
  
 19  
 Состояние «Повторяющееся имя». Служба с таким именем уже запущена.  
  
 20  
 Состояние «Недопустимое имя». В имени службы присутствуют недопустимые символы.  
  
 21  
 Состояние «Недопустимый параметр». Службе переданы недопустимые параметры.  
  
 22  
 Состояние «Недействительная учетная запись службы». Учетная запись, под именем которой должна выполняться служба, неверна или не обладает разрешениями для запуска этой службы.  
  
 23  
 Состояние «Служба существует». Служба существует в базе данных доступных в системе служб.  
  
 24  
 Служба уже приостановлена. Служба в данный момент приостановлена в системе.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
