---
title: Журнал ошибок агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea9a723695c6993f4f07897f49d8014a86ce78b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731318"
---
# <a name="sql-server-agent-error-log"></a>Журнал ошибок агента SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент создает журнал ошибок, в который по умолчанию записываются предупреждения и ошибки. В журнале отображаются следующие предупреждения и ошибки:  
  
-   Предупреждающие сообщения, содержащие сведения о потенциальных проблемах, например "задание \<*job_name*> было удалено во время его выполнения".  
  
-   Сообщения об ошибках, обычно требующих вмешательства системного администратора, например «Невозможно начать почтовый сеанс». Сообщения об ошибках могут отправляться конкретному пользователю или на конкретный компьютер с помощью команды **net send**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает до девяти журналов ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Каждый архивируемый журнал снабжается расширением, указывающим относительный срок давности журнала. Например, расширение .1 указывает на новейший архивированный журнал ошибок, а расширение .9 — на наиболее старый.  
  
 По умолчанию сообщения трассировки выполнения не записываются в журнал ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так как они могут его переполнить. При заполнении журнала ошибок снижается возможность выбора и анализа более сложных ошибок. Так как ведение журнала увеличивает нагрузку на сервер, важно правильно оценить эффект, получаемый при захвате сообщений трассировки выполнения в журнал ошибок. В общем случае захват всех сообщений будет наилучшим вариантом только при отладке конкретной проблемы.  
  
 Когда агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остановлен, размещение журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно изменить. Если журнал ошибок пустой, открыть его невозможно. Журнал агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно в любое время циклически перезаписывать без остановки агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Просмотр журнала ошибок агента SQL Server**  
  
-   [Просмотр журнала ошибок агента SQL Server (среда SQL Server Management Studio)](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 **Переименование журнала ошибок агента SQL Server**  
  
-   [Переименование журнала ошибок агента SQL Server (среда SQL Server Management Studio)](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 **Отправка сообщений об ошибках агента SQL Server**  
  
-   [Send SQL Server Agent Error Messages](send-sql-server-agent-error-messages.md)  
  
 **Запись сообщений трассировки выполнения в журнал ошибок агента SQL Server**  
  
-   [Запись сообщений трассировки выполнения в журнал ошибок агента SQL Server (среда SQL Server Management Studio)](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  
