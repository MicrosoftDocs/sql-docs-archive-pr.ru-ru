---
title: Задача "Выполнение инструкции T-SQL" (план обслуживания) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.tsql.f1
helpviewer_keywords:
- Execute T-SQL Statement Task dialog box
ms.assetid: fef3e259-0c47-4f6e-ade0-aee95e3d6c1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63738758ce228a51ab6c75eb11a681eec3b27352
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666574"
---
# <a name="execute-t-sql-statement-task-maintenance-plan"></a>Задача «Выполнение инструкции T-SQL» (план обслуживания)
  Для настройки своего плана обслуживания путем добавления выбранных инструкций **к этому плану используйте диалоговое окно** Задача "Выполнение инструкции T-SQL" [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
## <a name="options"></a>Параметры  
 **Соединение**  
 Выберите соединение с сервером, которое будет использоваться для выполнения этой задачи.  
  
 **Создать**  
 Создать новое соединение с сервером для его использования при выполнении этой задачи. Диалоговое окно **Создание соединения** описано ниже.  
  
 **Время ожидания выполнения**  
 Время (в секундах) ожидания завершения выполнения задачи (завершения задачи).  
  
 **Инструкция Т-SQL**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] подлежащие выполнению инструкции.  
  
 **Просмотр T-SQL**  
 Просмотрите инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , выполняемые для данной задачи по отношению к серверу, на основе выбранных параметров.  
  
> [!NOTE]  
>  Если количество затронутых объектов велико, построение этого отображения может занять значительное время.  
  
## <a name="new-connection-dialog-box"></a>Диалоговое окно «Создание соединения»  
 **Имя соединения**  
 Введите имя нового соединения.  
  
 **Выберите или введите имя сервера**  
 Выберите сервер для подключения при выполнении этой задачи.  
  
 **Обновить**  
 Обновите список доступных серверов.  
  
 **Введите данные для входа на сервер**  
 Укажите способ проверки подлинности на сервере.  
  
 **Использовать встроенную безопасность Windows**  
 Подключиться к экземпляру компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] c проверкой подлинности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Использовать указанные имя пользователя и пароль**  
 Подключиться к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот параметр недоступен.  
  
 **User name**  
 Укажите имя входа, используемое при проверке подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот параметр недоступен.  
  
 **Пароль**  
 Укажите используемый при проверке подлинности пароль. Этот параметр недоступен.  
  
  
