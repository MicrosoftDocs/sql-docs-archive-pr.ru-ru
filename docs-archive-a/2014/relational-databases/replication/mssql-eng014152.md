---
title: MSSQL_ENG014152 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 615b9cf2996653d86c44d6e43a83e01e8287b110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658213"
---
# <a name="mssql_eng014152"></a>MSSQL_ENG014152
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14152|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Репликация-%s: назначено повторное выполнение агента %s. %s|  
  
## <a name="explanation"></a>Объяснение  
 Для указанного агента репликации было запланировано повторное выполнение запрошенной операции. Повторные попытки продолжаются до тех пор, пока не будет достигнуто максимальное число попыток, настроенное для шага задания.  
  
 Причиной повторного выполнения обычно становится одно из следующего.  
  
-   Превышено значение **QueryTimeout** .  
  
-   Превышено значение **LoginTimeout** .  
  
-   Процесс репликации был выбран как жертва взаимоблокировки.  
  
## <a name="user-action"></a>Действие пользователя  
 Если сообщение о повторном выполнении появляется нечасто, никакие пользовательские действия не требуются.  
  
 Используйте процедуру [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) для проверки текущего значения максимального числа повторений шага **Запустить агент** для указанного агента репликации. **@retry_attempts**Параметр хранимой процедуры [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) можно использовать для настройки числа повторных попыток выполнения шага задания.  
  
 Если сообщение о повторном выполнении появляется часто, способ устранения неполадок зависит от сообщения, вызывающего повтор. Проверьте в журнале агента наличие сообщений, указывающих причину назначения повторного выполнения. В некоторых случаях может потребоваться включить ведение более подробного журнала для агента репликации. Дополнительные сведения о настройке ведения журнала репликации см. в статье базы знаний Майкрософт [312292](https://support.microsoft.com/kb/312292).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
