---
title: Параметр конфигурации сервера "lightweight pooling" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default lightweight pooling
- decreasing overhead
- lightweight pooling option
- system overhead [SQL Server]
- performance [SQL Server], lightweight pooling
- context switching [SQL Server], lightweight pooling option
- excessive context switching [SQL Server]
- reducing overhead
- overhead [SQL Server]
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 549ff7451a31b48459b5a290b94ad406c3768a91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665119"
---
# <a name="lightweight-pooling-server-configuration-option"></a>Параметр конфигурации сервера «использование упрощенных пулов»
  Чтобы обеспечить уменьшение системных издержек, связанных с излишним переключением контекста, что иногда случается при симметричной многопроцессорной обработке, воспользуйтесь параметром **lightweight pooling** . В случае, когда наблюдается излишнее переключение контекста, использование упрощенных пулов, может обеспечить лучшую производительность за счет встроенного переключения контекстов, помогая таким образом уменьшить количество переходов пользователь/ядро.  
  
 Режим волокон предназначен для ситуаций, когда главным фактором, ограничивающим производительность, является переключение контекста рабочих потоков UMS. Поскольку такая ситуация является нестандартной, использование режима волокон редко увеличивает производительность или масштабируемость типичной системы. Улучшенное переключение контекста в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] также снижает потребность в режиме волокон. Использовать планирование в режиме волокон для выполнения распространенных операций не рекомендуется. Это может привести к снижению производительности, мешая нормальной работе переключения контекста. Кроме того, некоторые компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые используют локальное хранилище потоков (TLS) или объекты, принадлежащие потокам, такие как мьютексы (тип объекта ядра Win32), не выполняются правильно в режиме волокон.  
  
 Значение параметра **использование упрощенных пулов** , равное 1, приводит к переключению [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на расписание режима волокон. Значение этого свойства по умолчанию равно 0.  
  
 Параметр **использование упрощенных пулов** является дополнительным. При вызове системной хранимой процедуры **sp_configure** параметр **lightweight pooling** может быть изменен только в том случае, если параметр **show advanced options** установлен равным 1. Установка параметра вступает в силу после перезапуска сервера.  
  
> [!NOTE]  
>  Использование упрощенных пулов не поддерживается операционными системами [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP. [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] обеспечивает полную поддержку использования упрощенных пулов.  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Отключите один из двух параметров: clr enabled или lightweight pooling. Функции, зависящие от среды CLR и неправильно работающие в режиме волокон, включают иерархический тип данных, репликацию и управление на основе политик.  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера «clr enabled»](clr-enabled-server-configuration-option.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Параметр конфигурации сервера «clr enabled»](clr-enabled-server-configuration-option.md)  
  
  
