---
title: Использование пользовательских сборок с отчетами | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f77b9da44ebb57617bd45e43d1e1e847e9074662
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730221"
---
# <a name="using-custom-assemblies-with-reports"></a>Использование пользовательских сборок с отчетами
  В службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно создавать пользовательский код для значений элементов отчета, стилей и форматирования. Так, пользовательский код можно использовать для форматирования валют в зависимости от настроек локали, для применения к определенным значениям специальных методов форматирования или для использования других бизнес-правил, установленных в конкретной компании. Одним из способов включения этого кода в отчеты является создание сборки пользовательского кода с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] коллекции, на которую можно ссылаться из файлов определения отчета. Сервер вызывает функции пользовательских сборок при выполнении отчета. Пользовательские сборки можно применять для получения значений специализированных функций, которые намечено использовать в отчетах.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Ссылки на сборки в RDL-файле](referencing-assemblies-in-an-rdl-file.md)  
 Описывает способ создания ссылок на пользовательские сборки в файле языка определения отчета.  
  
 [Развертывание пользовательской сборки](deploying-a-custom-assembly.md)  
 Описывает способ развертывания пользовательских сборок в конструкторе отчетов и на сервере отчетов.  
  
 [Использование пользовательских сборок со строгими именами](using-strong-named-custom-assemblies.md)  
 Описывает способ применения пользовательских сборок со строгими именами.  
  
 [Проверка предположений о наличии разрешений в пользовательских сборках](asserting-permissions-in-custom-assemblies.md)  
 Описывает способ развертывания пользовательских сборок с ограниченными и конкретными разрешениями, а также способ подтверждения этих разрешений в коде.  
  
 [Доступ к пользовательским сборкам посредством выражений](accessing-custom-assemblies-through-expressions.md)  
 Описывает способ вызова методов пользовательских сборок в виде выражений отчетов в определениях отчетов.  
  
 [Инициализация объектов пользовательских сборок](initializing-custom-assembly-objects.md)  
 Описывает способ инициализации значений для объектов пользовательских сборок, вызываемых из отчета.  
  
 [Руководство. Отладка пользовательских сборок](how-to-debug-custom-assemblies.md)  
 Описывает способ отладки кода пользовательских сборок.  
  
## <a name="see-also"></a>См. также:  
 [Язык определения отчетов (службы SSRS)](../reports/report-definition-language-ssrs.md)  
  
  
