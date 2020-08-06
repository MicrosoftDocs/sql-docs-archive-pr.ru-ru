---
title: Файлы базы данных источника | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31f0c0e0c633ead0c093bdc8e1f20c9b8f23cc28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751240"
---
# <a name="source-database-files"></a>Файлы базы данных-источника
  Диалоговое окно **Файлы базы данных-источника** используется для просмотра имен файлов базы данных и их размещения на исходном сервере, а также для указания общей сетевой папки в задаче «Передача базы данных». Дополнительные сведения об этой задаче см. в разделе [Задача "Передача базы данных"](control-flow/transfer-database-task.md).  
  
 Чтобы наполнить диалоговое окно именами файлов базы данных и ресурсов исходного сервера, сначала укажите параметры **SourceConnection** (Подключение к источнику) и **SourceDatabaseName** (Имя базы данных-источника) на странице **Базы данных** диалогового окна **Редактор задачи «Передача базы данных»** .  
  
## <a name="options"></a>Параметры  
 **Исходный файл**  
 Имена файлов базы данных на исходном сервере, которые будут перенесены. Параметр**Исходный файл** доступен только для чтения.  
  
 **Исходная папка**  
 Папка на исходном сервере, в которой хранятся файлы базы данных, подлежащей переносу. Параметр**Исходная папка** доступен только для чтения.  
  
 **Сетевая общая папка**  
 Сетевая общая папка на исходном сервере, из которой будут перенесены файлы базы данных. Параметр **Сетевая общая папка** используется при переносе базы данных в режиме вне сети путем задания значения **DatabaseOffline** (Автономный режим базы данных) параметру **Метод** на странице **Базы данных** диалогового окна **Редактор задачи «Передача базы данных»** .  
  
 Введите путь к общей сетевой папке или нажмите кнопку обзора **(...)** , чтобы найти эту папку.  
  
 При переносе базы данных в режиме вне сети файлы базы данных копируются в заданную параметром **Сетевая общая папка** папку на исходном сервере, прежде чем они будут перенесены на целевой сервер.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Перемещение базы данных" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "Передача базы данных" (страница "Базы данных")](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  