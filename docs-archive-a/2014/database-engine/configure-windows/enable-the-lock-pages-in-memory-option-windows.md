---
title: Включение параметра "Блокировка страниц в памяти" (Windows) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13290940c3a94a7ba79582d892a5e28670f24b29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664492"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a>Включение параметра «Блокировка страниц в памяти» (Windows)
  Эта политика Windows определяет, какие учетные записи могут использовать процесс для сохранения данных в физической памяти, чтобы система не отправляла страницы данных в виртуальную память на диске.  
  
> [!NOTE]  
>  Блокировка страниц в памяти может повысить производительность, если требуется подкачка памяти на диск.  
  
 Для включения этой политики для учетной записи, используемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], воспользуйтесь средством «Групповая политика Windows» (gpedit.msc). Чтобы изменить эту политику, необходимо быть системным администратором.  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a>Включение параметра «Блокировка страниц в памяти»  
  
1.  В меню **Пуск** выберите команду **Выполнить**. В поле **Открыть** введите `gpedit.msc` .  
  
2.  В консоли **Редактор локальных групповых политик** разверните узел **Конфигурация компьютера**, затем узел **Конфигурация Windows**.  
  
3.  Разверните узлы **Настройки безопасности**и **Локальные политики**.  
  
4.  Выберите папку **Назначение прав пользователя** .  
  
     Политики будут показаны на панели подробностей.  
  
5.  На этой панели дважды щелкните параметр **Блокировка страниц в памяти**.  
  
6.  В диалоговом окне **Параметр локальной безопасности — блокировка страниц в памяти** щелкните **Добавить пользователя или группу**.  
  
7.  В диалоговом окне **Выбор: пользователи, учетные записи служб или группы** добавьте учетную запись, обладающую правами доступа для запуска sqlservr.exe.  
  
8.  Чтобы изменения вступили в силу, выйдите из системы и снова войдите в нее.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера «Server Memory»](server-memory-server-configuration-options.md)  
  
  
