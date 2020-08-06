---
title: Удаление модуля подготовки отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77a8a9ac44b35f338f978913985617e4f264ddb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664748"
---
# <a name="removing-a-rendering-extension"></a>Удаление модуля подготовки отчетов
  Чтобы удалить [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модуль подготовки отчетов, просто удалите `Extension` элемент для модуля подготовки отчетов из файла rsreportserver.config, расположенного в папке **%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<Instance Name> Папка \Reporting Services\ReportServer** . Если вы внесли записи для конструктор отчетов, а также для сервера отчетов, удалите `Extension` элемент из [файла конфигурации RSReportDesigner](../../report-server/rsreportdesigner-configuration-file.md) . После удаления сведений о конфигурации модуль подготовки отчетов становится недоступным компоненту.  
  
## <a name="see-also"></a>См. также:  
 [Файлы конфигурации служб Reporting Services](../../report-server/reporting-services-configuration-files.md)   
 [Реализация модуля подготовки отчетов](implementing-a-rendering-extension.md)   
 [Общие сведения о модулях подготовки отчетов](rendering-extensions-overview.md)   
 [Реализация интерфейса IRenderingExtension](implementing-the-irenderingextension-interface.md)   
 [Рекомендации по обеспечению безопасности для модулей](../security-considerations-for-extensions.md)   
 [Развертывание модуля подготовки отчетов](deploying-a-rendering-extension.md)  
  
  
