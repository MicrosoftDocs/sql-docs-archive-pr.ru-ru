---
title: Редактор задачи «перенос главных хранимых процедур» (страница «Общие») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a25a5c9c6ed3802e21ac522e94163ce5fb9e8c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734285"
---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a>Редактор задачи «Передача главных хранимых процедур» (страница «Общие»)
  Используйте страницу **Общие** в диалоговом окне **Редактор задачи «Передача главных хранимых процедур»** , чтобы назвать и описать задачу переноса главных хранимых процедур. Дополнительные сведения об этой задаче см. в разделе [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Эта задача передает только пользовательские хранимые процедуры, принадлежащие **dbo** , из базы данных **master** на исходном сервере в базу данных **master** на целевом сервере. Пользователям должно быть предоставлено разрешение CREATE PROCEDURE в базе данных **master** на целевом сервере, или они должны быть членами предопределенной роли сервера **sysadmin** на целевом сервере, чтобы создавать на нем хранимые процедуры.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Введите уникальное имя для задачи «Передача главных хранимых процедур». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Введите описание для задачи «Передача главных хранимых процедур».  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор задачи "перенос главных хранимых процедур" &#40;страницу хранимых процедур&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
