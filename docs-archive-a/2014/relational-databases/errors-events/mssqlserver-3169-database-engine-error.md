---
title: MSSQLSERVER_3169 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "3169"
helpviewer_keywords:
- 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b13d9c1c17eddb34648bc4a536e2fccf371b99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664241"
---
# <a name="mssqlserver_3169"></a>MSSQLSERVER_3169
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3169|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|Н/Д|  
|Текст сообщения|Резервная копия базы данных создана на сервере, на котором выполняется версия %ls. Эта версия несовместима с данным сервером, на котором работает версия %ls. Необходимо восстановить базу данных на сервере, который поддерживает эту резервную копию, либо использовать резервную копию, совместимую с данным сервером.|  
  
## <a name="explanation"></a>Объяснение  
 Некоторые особенности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] влияют на структуру файлов базы данных. При восстановлении базы данных на другом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл форматирования может оказаться несовместимым с другой версией компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Например, эта ошибка может возникнуть при использовании формата хранения vardecimal в более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с последующей попыткой восстановить файлы базы данных в более ранней версии, чем [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 2 (SP2).  
  
## <a name="user-action"></a>Действие пользователя  
 Определите версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенную на исходном сервере. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] либо щелкните правой кнопкой мыши сервер, а затем выберите пункт **свойства** или введите `SELECT @@VERSION` в окне запроса. Откройте базу данных с помощью исходной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Изучите функции, которые включены в исходной базе данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Измените параметры для работы с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в которой будет выполняться восстановление базы данных.  
  
  
