---
title: Редактор задачи «FTP» (страница «Общие») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0cb4ffe2fa44e76890f6b70912f84dbcaa8f2cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657155"
---
# <a name="ftp-task-editor-general-page"></a>Редактор задачи «FTP» (страница «Общие»)
  Используйте страницу **Общие** диалогового окна **Редактор задачи «FTP»** для задания диспетчера FTP-соединений, выполняющего соединение с FTP-сервером, с которым задача обменивается данными. Также здесь можно указать имя и описание задачи «FTP».  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача FTP](control-flow/ftp-task.md).  
  
## <a name="options"></a>Параметры  
 **FtpConnection**  
 Выберите существующий диспетчер подключений FTP или создайте его, щелкнув пункт \<**New connection...**>.  
  
> [!IMPORTANT]  
>  Диспетчер FTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
 **См. также**: [Диспетчер FTP-сеансов](connection-manager/ftp-connection-manager.md), [Редактор диспетчера FTP-сеансов](../../2014/integration-services/ftp-connection-manager-editor.md)  
  
 **StopOnFailure**  
 Укажите, следует ли завершить задачу «FTP» в случае ошибки операции с FTP.  
  
 **имя**;  
 Задайте уникальное имя задачи «FTP». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Введите описание задачи «FTP».  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "FTP" &#40;страницу "перенос файлов"&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
