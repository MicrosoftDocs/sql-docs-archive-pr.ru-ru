---
title: Редактор диспетчера подключений SQL Server Compact Edition (страница «все») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f881d63de5435426475c3aed4b666870d706b40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658304"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a>Редактор диспетчера соединений SQL Server Compact Edition (страница «Все»)
  Диалоговое окно **Диспетчер соединений SQL Server Compact Edition** позволяет задать свойства для соединения с базой данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 Дополнительные сведения о диспетчере соединений [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition см. в разделе [Диспетчер соединений SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md).  
  
## <a name="options"></a>Варианты  
 **Пороговое значение для автосжатия**  
 Укажите в виде процентов допустимый размер свободного пространства в базе данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact перед запуском процесса автосжатия.  
  
 **Укрупнение блокировок по умолчанию**  
 Определите число блокировок базы данных, которые установит база данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact, прежде чем попытается укрупнить блокировки.  
  
 **Время ожидания блокировок по умолчанию**  
 Укажите время по умолчанию (в миллисекундах) ожидания транзакцией блокировок базы данных.  
  
 **Интервал записи**  
 Определите интервал (в секундах) между записями данных на диск зафиксированными транзакциями.  
  
 **Идентификатор локали**  
 Задайте идентификатор локали (LCID) базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Максимальный размер буфера**  
 Определите максимальный объем памяти (в килобайтах), используемый базой данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact перед записью данных на диск.  
  
 **Максимальный размер базы данных**  
 Укажите максимальный размер (в мегабайтах) базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Режим**  
 Укажите файловый режим, в котором будет открываться база данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact. Значение этого свойства по умолчанию равно **Чтение и запись**.  
  
 Параметр «Режим» имеет четыре значения, описанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Только чтение**|Определяет доступ к базе данных только для чтения.|  
|**Чтение и запись**|Назначает разрешения на чтение и запись базы данных.|  
|**Монопольный доступ**|Задает монопольный доступ к базе данных.|  
|**Общий доступ на чтение**|Определяет возможность одновременного чтения базы данных другими пользователями.|  
  
 **Persist Security Info**  
 Определите, будет ли осуществляться возврат сведений о безопасности в виде части строки соединения. Значение по умолчанию этого параметра равно **False**.  
  
 **Каталог временных файлов**  
 Задайте расположение временных файлов базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Источник данных**  
 Укажите имя базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Пароль**  
 Введите пароль для базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  
