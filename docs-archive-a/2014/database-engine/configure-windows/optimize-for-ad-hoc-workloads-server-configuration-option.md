---
title: Параметр конфигурации сервера "optimize for ad hoc workloads" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b217e48d6e4b0ffa0f687ff170f16d4d77ad17d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729802"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a>Параметр конфигурации сервера «optimize for ad hoc workloads»
  Параметр **optimize for ad hoc workloads** используется для повышения эффективности кэширования планов рабочих нагрузок, содержащих много отдельных нерегламентированных пакетов. Если этот параметр имеет значение 1, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] при первой компиляции пакета сохраняет в кэше планов небольшую скомпилированную заглушку плана, а не полный откомпилированный план. Это несколько снижает требования к памяти, так как кэш планов не заполняется скомпилированными, не используемыми повторно планами.  
  
 Откомпилированная заглушка плана позволяет компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] понять, что данный нерегламентированный пакет компилировался ранее, но от него сохранилась только заглушка. При повторном вызове этого пакета для компиляции или выполнения компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] откомпилирует пакет, удалит из кэша планов откомпилированную заглушку плана и добавит туда полный скомпилированный план.  
  
 Когда параметру **optimize for ad hoc workloads** присваивается значение 1, это влияет только на новые планы; те планы, которые уже находятся в кэше планов, остаются неизменными.  
  
 Скомпилированная заглушка плана принадлежит к объектам cacheobjtypes, которые можно просмотреть в представлении каталога sys.dm_exec_cached_plans. У каждой заглушки есть уникальный дескриптор SQL и дескриптор плана. Со скомпилированной заглушкой плана не связан план выполнения. Запрос по дескриптору плана не вернет XML-код Showplan.  
  
 Флаг трассировки 8032 восстанавливает параметры предела кэша до значения в RTM-версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , что обычно позволяет увеличить размер кэша. Используйте этот параметр, если часто используемые повторно записи кэша не помещаются в кэш и параметру конфигурации сервера *Оптимизировать для нерегламентированной рабочей нагрузки* не удалось разрешить эту проблему с помощью кэша планов.  
  
> [!WARNING]  
>  Применение флага трассировки 8032 может привести к снижению производительности, если увеличение кэша приводит к уменьшению объема памяти, доступной для других потребителей памяти, например для буферного пула.  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_exec_cached_plans (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)  
  
  
