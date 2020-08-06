---
title: Сохранение пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 102e2c3eab001c230722bf3485d6ea9731aa99a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738513"
---
# <a name="save-packages"></a>Сохранение пакетов
  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] пакеты создаются с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и сохраняются в файловой системе как XML-файлы (DTSX-файлы). Копии XML-файла пакета можно также сохранять в базе данных msdb в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов. Хранилище пакетов представляет собой папки в определенном месте файловой системы, управляемые службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 При сохранении пакета в файловой системе можно в дальнейшем использовать службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , чтобы выполнить импорт пакета в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов. Дополнительные сведения см. в разделе [Импорт и экспорт пакетов (службы SSIS)](../../2014/integration-services/import-and-export-packages-ssis-service.md).  
  
 Можно также использовать программу командной строки **dtutil**для копирования пакета между файловой системой и базой данных msdb. Дополнительные сведения см. в статье [dtutil Utility](dtutil-utility.md).  
  
### <a name="to-save-a-package"></a>Сохранение пакета  
  
-   [Сохранение пакета в файловой системе](../../2014/integration-services/save-a-package-to-the-file-system.md)  
  
-   [Сохранение копии пакета](../../2014/integration-services/save-a-copy-of-a-package.md)  
  
  
