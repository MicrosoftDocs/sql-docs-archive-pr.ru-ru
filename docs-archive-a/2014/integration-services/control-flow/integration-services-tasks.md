---
title: Задачи служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Integration Services], tasks
- files [Integration Services], task options
- workflow tasks [Integration Services]
- Integration Services, tasks
- adding package tasks
- tasks [Integration Services], listed
- SSIS tasks
- SSIS, tasks
- control flow [Integration Services], tasks
- tasks [Integration Services]
- grouping tasks
- tasks [Integration Services], about tasks
- SQL Server Integration Services tasks
- data preparation tasks [Integration Services]
- directory operations [Integration Services]
ms.assetid: 75c8901d-6966-4af3-abe5-10af6dd9313b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5fa58dec1e05a0333c295efc7f00a1d6df935792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658338"
---
# <a name="integration-services-tasks"></a>Задачи служб Integration Services
  Задачами называются элементы потока управления, которые определяют рабочие модули, выполняющиеся в потоке управления пакета. Пакет служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] состоит из одной задачи или нескольких. Если в пакете несколько задач, они связаны и упорядочены в потоке управления с помощью управления очередностью.  
  
 Можно также создавать пользовательские задачи на языке программирования, поддерживающем COM, например на Visual Basic, или на языке программирования для платформы .NET, например на C#.  
  
 Конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] — графическое средство служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для работы с пакетами — предоставляет область конструктора для создания потока управления пакета и специальные редакторы для настройки задач. Можно также использовать объектную модель служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для создания пакетов программными средствами.  
  
## <a name="types-of-tasks"></a>Типы задач  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержатся следующие типы задач.  
  
 Задача потока данных  
 Задача, создающая поток данных для извлечения данных, применения преобразований на уровне столбцов и загрузки данных.  
  
 Задачи подготовки данных  
 Эти задачи включают в себя следующие процессы: копирование файлов и каталогов, загрузку файлов и данных, запуск веб-методов, добавление операций в XML-документы и профилирование данных для очистки.  
  
 Задачи рабочего процесса  
 Задачи, связывающиеся с другими процессами для выполнения пакетов, программ или пакетных файлов, отправки и получения сообщений между пакетами, отправки сообщений электронной почты, считывания данных из инструментария управления Windows (WMI) и слежения за событиями WMI.  
  
 Задачи SQL Server  
 Задачи доступа к объектам и данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , их копирования, вставки, удаления и изменения.  
  
 Задачи сценариев  
 Задачи, расширяющие функциональность пакетов с помощью скриптов.  
  
 Задачи служб Analysis Services  
 Задачи, создающие, изменяющие, удаляющие и обрабатывающие объекты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Задачи обслуживания  
 Задачи, выполняющие функции администрирования, например создание резервных копий и сжатие баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , перестроение и изменение структуры индексов, а также выполнение заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Пользовательские задачи  
 Дополнительно можно создавать пользовательские задачи на языке программирования, поддерживающем COM, например Visual Basic, или на языке программирования для платформы .NET, например C#. Чтобы получить доступ к пользовательской задаче в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , можно создать и зарегистрировать пользовательский интерфейс для задачи. Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="configuration-of-tasks"></a>Настройка задач  
 Пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может содержать одну задачу, например задачу «Выполнение SQL», удаляющую записи из таблицы базы данных при выполнении пакета. Однако обычно в пакетах находится несколько задач, и каждая из них настроена так, чтобы выполняться в контексте потока управления пакета. У обработчиков событий, которые являются рабочими процессами, запускающимися в ответ на события времени выполнения, также могут быть задачи.  
  
 Дополнительные сведения о добавлении задачи в пакет с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в разделе [Добавление задачи или контейнера в поток управления или удаление их из него](add-or-delete-a-task-or-a-container-in-a-control-flow.md).  
  
 Дополнительные сведения о программном добавлении задач в пакет см. в разделе [Программное добавление задач](../building-packages-programmatically/adding-tasks-programmatically.md).  
  
 Каждая задача может быть настроена отдельно с помощью собственных диалоговых окон, предоставляемых конструктором служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , или в окне «Свойства» среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. В пакете может храниться несколько задач одного типа (например, шесть задач "Выполнение SQL"), и каждая из них может быть настроена по-разному. Дополнительные сведения см. в разделе [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="tasks-connections-and-groups"></a>Подключения и группы задач  
 Если задача содержит несколько задач, они связаны и упорядочены в потоке управления с помощью ограничений очередностью. Дополнительные сведения см. в статье [Precedence Constraints](precedence-constraints.md).  
  
 Задачи можно группировать и выполнять как одно целое либо повторять их выполнение в цикле. Дополнительные сведения см. в разделах [Foreach Loop Container](foreach-loop-container.md), [For Loop Container](for-loop-container.md)и [Sequence Container](sequence-container.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Добавление задачи или контейнера в поток управления или удаление их из него](add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
  
