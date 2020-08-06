---
title: Параметр состояния (средство администрирования распределенного воспроизведения) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ce3d07bc357c5f3788fb6f995a43399021b3553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727681"
---
# <a name="status-option-distributed-replay-administration-tool"></a>Параметр состояния (средство администрирования распределенного воспроизведения)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Средство администрирования распределенное воспроизведение `DReplay.exe` — это средство командной строки, которое можно использовать для взаимодействия с контроллером распределенного воспроизведения. В этой статье описан параметр командной строки **status** и соответствующий синтаксис.

 Параметр **status** опрашивает контроллер и отображает его текущее состояние.

 ![Значок ссылки на раздел](../../database-engine/media/topic-link.gif "Значок ссылки на раздел") Дополнительные сведения о синтаксических обозначениях, используемых в синтаксисе средства администрирования, см. в разделе [Синтаксические обозначения в Transact-SQL (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Синтаксис

```

dreplay status [-mcontroller] [-fstatus_interval]
```

#### <a name="parameters"></a>Параметры
 *контроллер* **-m** указывает имя компьютера контроллера. Локальный компьютер можно указать как «`localhost`» или «`.`».

 Если параметр **-m** не задан, то используется локальный компьютер.

 **-f** *status_interval* указывает частоту (в секундах) вывода состояния.

 Если параметр **-f** не задан, то интервал по умолчанию составляет 30 секунд.

## <a name="examples"></a>Примеры
 В следующем примере текущий статус отображается каждые 60 секунд. Значение `localhost` указывает, что служба контроллера запущена на том же компьютере, что и средство администрирования.

```
dreplay status -m localhost -f 60
```

## <a name="permissions"></a>Разрешения
 Средство администрирования должно запускаться как интерактивный пользователь, с учетной записью локального пользователя или пользователя домена. Для использования учетной записи локального пользователя средство администрирования и контроллер должны быть запущены на одном компьютере.

 Дополнительные сведения см. в статье [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>См. также:
 [Отладчик Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md) [SQL Server распределенное воспроизведение](sql-server-distributed-replay.md)


