---
title: обозреватель решений система управления версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual SourceSafe
- SQL Server Management Studio [SQL Server], source control services
- source-controlled files [SQL Server]
- source controls [SQL Server Management Studio], services
- version control services [SQL Server]
- file source control services [SQL Server]
- VSS [Visual SourceSafe]
ms.assetid: 6373adb8-3d81-4945-a9fc-1d0d5799d29a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 46471ba8149c26f80e78006bc3a8befc2e81b416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666204"
---
# <a name="solution-explorer-source-control"></a>Обозреватель решений системы управления версиями
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]Обозреватель решений можно интегрировать в отдельную систему управления версиями. После того как решение или проект будет интегрированы в систему управления версиями, появится возможность управлять доступом к файлам и версиями скриптов и запросов в проекте.  
  
## <a name="solution-and-project-source-control"></a>Система управления версиями решений и проектов  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]  
  
 Система управления версиями осуществляется в системе, в которой центральная часть программного обеспечения сервера реализует хранение и отслеживание версий файлов, а также управляет доступом к файлам. Обычная система управления версиями включает поставщика управления версиями и несколько клиентов управления версиями. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] может быть интегрирована в систему управления версиями. Это означает возможность использования данного инструмента в качестве клиента для существующего поставщика системы управления версиями. Не покидая среду, можно легко управлять индивидуальными проектами и работать над проектом в команде. Система управления версиями не включена в среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
#### <a name="to-select-a-source-control-provider"></a>Выбор системы управления версиями  
  
1.  Установите клиентскую часть своей системы управления версиями.  
  
2.  В среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]в меню **Сервис** выберите **Параметры**.  
  
3.  В диалоговом окне **Параметры** разверните узел **система управления версиями**и выберите страницу **Выбор подключаемого модуля** .  
  
4.  В поле **текущий подключаемый модуль системы управления** версиями выберите подключаемый модуль системы управления версиями.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Основы системы управления версиями](../../2014/database-engine/source-control-basics.md)|Определение базовой терминологии, относящейся к системе управления версиями, и описание преимуществ использования этих систем в проекте.|  
|[Добавление решений и проектов в систему управления версиями](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)|Добавление решений и проектов в систему управления версиями в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].|  
|[Открытие решений и проектов из системы управления версиями](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)|Открытие в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] решений и проектов, контролируемых системой управления версиями.|  
|[Управление извлечениями](../../2014/database-engine/manage-checkouts.md)|Извлечение решений и файлов из системы управления версиями.|  
|[Управление возвратами](../../2014/database-engine/manage-checkins.md)|Возврат решений и файлов в систему управления версиями.|  
|[Задание и получение сведений о версии](../../2014/database-engine/set-and-retrieve-version-information.md)|Получение журнала проекта или элемента, получение локальной копии элемента и сравнение двух версий элемента.|  
|||  
  
## <a name="see-also"></a>См. также:  
 [обозреватель решений](../ssms/solution/solution-explorer.md)   
 [Решения &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)   
 [Проекты &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md)   
 [Файлы для управления решениями и проектами](../ssms/solution/files-that-manage-solutions-and-projects.md)  
  
  
