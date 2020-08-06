---
title: Копировать элементы проекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], copying
- packages [Integration Services], copying
- copying data source views
- copying data sources
- copying packages
- data source views [Integration Services], copying
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3456209c467c3b8474e130181d02304911098d2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665054"
---
# <a name="copy-project-items"></a>Копирование элементов проекта
  В этом разделе описывается, как копировать объекты в проекте [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или между проектами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Также вы можете скопировать объекты между другими типами проектов [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Чтобы можно было выполнить копирование между проектами, они должны быть частью одного решения среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] . Дополнительные сведения см. в разделе [Проекты служб Integration Services (SSIS)](integration-services-ssis-projects-and-solutions.md).  
  
### <a name="to-copy-project-level-items"></a>Копирование элементов уровня проекта  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или решение, с которым собираетесь работать.  
  
2.  Разверните проект и папку, из которой будет выполняться копирование.  
  
3.  Щелкните правой кнопкой мыши элемент и выберите **Копировать**.  
  
4.  Щелкните правой кнопкой мыши проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], в который будет выполняться копирование, и выберите **Вставить**.  
  
     Элементы автоматически копируются в нужную папку. При копировании элементов в проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , которые не являются пакетами, элементы копируются в папку **Разное** .  
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;пакетов&#41; SSIS](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Копирование объектов пакета](../../2014/integration-services/copy-package-objects.md)  
  
  
