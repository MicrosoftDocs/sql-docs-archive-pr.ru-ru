---
title: Виртуальный каталог имеет неподдерживаемый метод проверки подлинности (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67b1c027b8ed020f65fdea7c093f6d5454f02c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659120"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a>Виртуальный каталог использует неподдерживаемый метод проверки подлинности (советник по переходу)
  Помощник по обновлению обнаружил неподдерживаемый метод проверки подлинности в виртуальном каталоге диспетчера отчетов или сервера отчетов. Обновлением не поддерживаются следующие методы проверки подлинности: анонимный доступ, дайджест-проверка подлинности и .NET Passport.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Программа установки не может обновить установку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], где используется один из следующих методов проверки подлинности.  
  
-   Анонимный  
  
-   Digest (дайджест)  
  
-   Пароль .NET  
  
 Чтобы продолжить установку, либо измените метод проверки подлинности, заданный в виртуальных каталогах IIS служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], либо выполните миграцию установки. Дополнительные сведения о миграции установки см. в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы продолжить обновление, измените метод проверки подлинности в службах IIS для виртуальных каталогов ReportServer и Reports. Дополнительные сведения об изменении методов проверки подлинности в службах IIS см. в документации по службам IIS. После изменения метода проверки подлинности для виртуальных директорий служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] повторно запустите помощник по обновлению, чтобы убедиться в отсутствии проблем обновления.  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services проблем обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
