---
title: Свойство State (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- State Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7456113d9ec4444507d1057892a65adf241992f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733710"
---
# <a name="state-property-sqlservice-class"></a>Свойство State (класс SqlService)
  Возвращает или задает текущее состояние службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.State [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, определяющее состояние службы.  
  
 Может иметь одно из следующих значений.  
  
 1  
 Остановлена. служба остановлена.  
  
 2  
 Ожидание запуска. Служба ожидает запуска.  
  
 3  
 Ожидание остановки. Служба ожидает остановки.  
  
 4  
 Выполняется. Служба запущена.  
  
 5  
 Ожидание продолжения. Служба ожидает продолжения.  
  
 6  
 Ожидание приостановки. Служба ожидает приостановки.  
  
 7  
 приостановлено Служба приостановлена.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
