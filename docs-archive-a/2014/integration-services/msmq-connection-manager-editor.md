---
title: Редактор диспетчера MSMQ Connection Manager | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41d4231ce121d596c8d818485eccf5ddf6127470
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655822"
---
# <a name="msmq-connection-manager-editor"></a>редактор диспетчера MSMQ-сеансов
  Диалоговое окно **Диспетчер MSMQ-сеансов** используется для указания пути к очереди сообщений MSMQ.  
  
 Дополнительные сведения о диспетчере MSMQ-сеансов см. в разделе [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Диспетчер соединений MSMQ поддерживает локальные частные и общие очереди, а также удаленные общие очереди. Он не поддерживает удаленные частные очереди. Метод, обходящий это ограничение, использует задачу «Скрипт». Дополнительные сведения см. в разделе [Отправка в удаленную закрытую очередь сообщений в задаче «Скрипт»](control-flow/script-task.md).  
  
## <a name="options"></a>Параметры  
 **Название**  
 Задайте уникальное имя для диспетчера MSMQ-сеансов в рабочем процессе. Выбранное имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Описание**  
 Задайте описание диспетчера соединений. Рекомендуется описать назначение диспетчера соединений, чтобы сделать пакеты самодокументируемыми и более простыми в использовании.  
  
 **Путь**  
 Введите полный путь очереди сообщений. Формат пути зависит от типа очереди.  
  
|Тип очереди|Образец пути|  
|----------------|-----------------|  
|Общедоступные|\<computer name>\\<имя очереди\>|  
|Private|\<computer name>\Private$\\<имя очереди\>|  
  
 Для представления локального компьютера можно использовать знак точки «.».  
  
 **Тест**  
 После настройки диспетчера MSMQ-сеансов убедитесь, что соединение работоспособно, нажав кнопку **Проверка**.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
