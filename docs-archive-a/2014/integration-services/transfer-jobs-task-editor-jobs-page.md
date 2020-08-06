---
title: Редактор задачи «перемещение заданий» (страница «задания») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d2d506da6997965e40d66521f7dccb8218e165fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669471"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a>Редактор задачи «Передача заданий» (страница «Задания»)
  Используйте страницу **Задания** диалогового окна **Редактор задачи «Передача заданий»** для определения свойств копирования одного или более заданий агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в другой. Дополнительные сведения о задаче «Передача заданий» см. в разделе [Transfer Jobs Task](control-flow/transfer-jobs-task.md).  
  
> [!NOTE]  
>  Для доступа к задачам на исходном сервере пользователи должны быть членами хотя бы одной предопределенной роли базы данных **SQLAgentUserRole** на этом сервере. Для успешного создания задания на целевом сервере пользователь должен быть членом предопределенной роли сервера **sysadmin** или одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и их разрешениях см. в разделе [Предопределенные роли базы данных агента SQL Server](../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="options"></a>Параметры  
 **SourceConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<New connection...>** , чтобы создать новое подключение к исходному серверу.  
  
 **DestinationConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<New connection...>** , чтобы создать новое подключение к целевому серверу.  
  
 **TransferAllJobs**  
 Укажите, должна задача копировать с исходного сервера на целевой все задания или только те, которые указаны агентом [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Копировать все задания.|  
|**False**|Копировать только выбранные задания.|  
  
 **JobsList**  
 Нажмите кнопку обзора **(…)** , чтобы выбрать задания для копирования. Необходимо выбрать хотя бы одно задание.  
  
> [!NOTE]  
>  Прежде чем выбирать задания для копирования, укажите свойство **SourceConnection** .  
  
 Параметр **JobsList** недоступен, если параметр **TransferAllJobs** равен **True**.  
  
 **IfObjectExists**  
 Определите, как задача должна обрабатывать задания с именем, которое уже есть на целевом сервере.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**FailTask**|Задача завершается сбоем, если задание с таким именем уже есть на целевом сервере.|  
|**Overwrite**|Задача перезаписывает задание с таким же именем на целевом сервере.|  
|**Skip**|Задача пропускает задание, если задание с таким именем уже есть на целевом сервере.|  
  
 **EnableJobsAtDestination**  
 Определите, будут ли активированы задания, скопированные на целевой сервер.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Включить задания на целевом сервере.|  
|**False**|Отключить задания на целевом сервере.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор задачи "перемещение заданий" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Страница «Выражения»](expressions/expressions-page.md)   
 [Диспетчер соединений SMO](connection-manager/smo-connection-manager.md)  
  
  
