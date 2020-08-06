---
title: Модули служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ac942147c75424dae46d9a8e35dc57fba50755f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664742"
---
# <a name="reporting-services-extensions"></a>модули служб Reporting Services
  Модульная архитектура служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] обеспечивает возможность расширения. Доступен API управляемого кода, что позволяет легко разрабатывать, устанавливать модули, используемые многими компонентами служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а также управлять этими модулями. Можно создавать закрытые и общие сборки с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и добавлять в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] новые функции, чтобы соответствовать растущим потребностям бизнеса.  
  
 Уникальная расширяемая архитектура служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] позволяет разработчикам расширять отдельные функции продукта и его компонентов. В настоящее время поддерживается множество модулей, расширяющих возможности обработки данных в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. API обработки данных поддерживает знакомые конструкции и соглашения поставщиков данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], что позволяет разработчикам встраивать в службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] дополнительные возможности обработки данных. Эти модули обработки данных расширяют функциональные возможности сервера отчетов и конструктора отчетов, обеспечивая безукоризненную интеграцию пользовательских данных в отчеты.  
  
 Еще одним поддерживаемым модулем является модуль доставки. API доставки полностью интегрирован с архитектурой [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], что позволяет применять при отправке пользователям уведомлений об отчетах самые разнообразные механизмы доставки. Можно расширить возможности сервера отчетов, чтобы он предоставлял пользователям нестандартные модули доставки, а страницы управления подписками в диспетчере отчетов дополнить так, чтобы они включили поддержку подписок с нестандартными модулями доставки.  
  
 Еще один модуль сервера отчетов, модуль настройки определений отчетов (RDCE), позволяет динамически настроить определение отчета до передачи его механизму обработки. Отчеты могут настраиваться с учетом таких факторов, как пользователи или языки. Например, можно реализовать различные представления для разных пользователей (допустим, руководителей или сотрудников отдела) или настроить отчет на использование разных вариантов макета при подготовке отчета к просмотру, допустим, на французском или арабском языке.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Рекомендации по обеспечению безопасности для модулей](security-considerations-for-extensions.md)  
 Описывает проблемы защиты, связанные с разработкой и развертыванием расширений [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Реализация модуля обработки данных](data-processing/implementing-a-data-processing-extension.md)  
 Описывает требования и шаги по реализации модуля обработки данных для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Реализация модуля доставки](delivery-extension/implementing-a-delivery-extension.md)  
 Описывает требования и шаги по реализации модуля доставки для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Реализация модуля подготовки отчетов](rendering-extension/implementing-a-rendering-extension.md)  
 Содержит введение в разработку модулей подготовки отчетов.  
  
 [Реализация модуля безопасности](security-extension/implementing-a-security-extension.md)  
 Описывает требования и шаги по реализации модуля безопасности для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Библиотека модулей Reporting Services](reporting-services-extension-library.md)  
 Содержит справочник по программированию библиотеки API модулей для средств расширения компонента [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
  
