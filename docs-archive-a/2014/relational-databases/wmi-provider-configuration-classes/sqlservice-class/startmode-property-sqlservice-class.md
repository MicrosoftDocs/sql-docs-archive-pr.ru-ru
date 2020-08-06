---
title: Свойство StartMode (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartMode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bafffcc3c8f82f69896d0a22e9b0a9060e04cd10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733722"
---
# <a name="startmode-property-sqlservice-class"></a>Свойство StartMode (класс SqlService)
  Возвращает режим запуска службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.StartMode [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, определяющее режим службы.  
  
 Может иметь одно из следующих значений.  
  
 Загрузка  
 Значение = 0. Служба запускается загрузчиком операционной системы. Этот параметр допустим только для служб драйверов.  
  
 Система  
 Значение = 1. Служба запускается методом `IoInitSystem`. Этот параметр допустим только для служб драйверов.  
  
 Автоматически  
 Значение = 2. Служба запускается автоматически диспетчером управления службами во время запуска системы.  
  
 Вручную  
 Значение = 3. Служба запускается оснасткой «Управление компьютером», когда процесс вызывает метод `StartService`.  
  
 Выключено  
 Значение = 4. Служба не может быть запущена.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
