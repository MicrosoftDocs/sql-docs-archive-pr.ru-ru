---
title: MSSQLSERVER_8974 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8974 (Database Engine error)
ms.assetid: 52098678-0858-4a14-ad07-37ebbafca5fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff3107f5b62caf04e232532c2d2b93d5da19fb53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669417"
---
# <a name="mssqlserver_8974"></a>MSSQLSERVER_8974
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8974|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS|  
|Текст сообщения|Ошибка таблицы: идентификатор объекта O_ID, идентификатор индекса I_ID, идентификатор секции PN_ID, идентификатор единицы распределения A_ID (тип TYPE). На данный внестрочный узел данных на странице P_ID1, область памяти S_ID1, идентификатор текста TEXT_ID, ссылается страница P_ID2, область памяти S_ID2 и страница P_ID3, область памяти P_ID3.|  
  
## <a name="explanation"></a>Объяснение  
 Во внестрочном узле данных есть две записи данных или индекса, которые фиксируют его как дочерний узел. У узла может быть только один родительский узел.  
  
## <a name="user-action"></a>Действие пользователя  
  
### <a name="look-for-hardware-failure"></a>Поиск сбоев оборудования  
 Выполните диагностику оборудования и исправьте все найденные проблемы. Кроме того, просмотрите журнал системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и журнал приложений, а также журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы определить, была ли ошибка вызвана сбоем оборудования. Исправьте все неполадки оборудования, обнаруженные в журналах.  
  
 Если постоянно возникают проблемы с повреждением данных, попробуйте изменить некоторые компоненты оборудования, чтобы локализовать проблему. Убедитесь, что в системе не включено кэширование записи для контроллера дисков. Если есть подозрение, что неполадки вызваны кэшированием записи, обратитесь к поставщику оборудования.  
  
 В конце концов можно попробовать сменить оборудование. Это может включать форматирование дисков и переустановку операционной системы.  
  
### <a name="restore-from-backup"></a>Восстановление из резервной копии  
 Если неполадка не связана с оборудованием и есть безошибочная резервная копия, восстановите базу данных из этой копии.  
  
### <a name="run-dbcc-checkdb"></a>Запуск DBCC CHECKDB  
 Если безошибочной резервной копии нет, выполните инструкцию DBCC CHECKDB без предложения REPAIR, чтобы определить степень повреждения. Инструкция DBCC CHECKDB выдаст рекомендацию по тому, какое предложение REPAIR следует использовать. После этого выполните инструкцию DBCC CHECKDB с соответствующим предложением REPAIR, чтобы устранить повреждение.  
  
> [!CAUTION]  
>  Если достоверно неизвестно, к каким последствиям приведет выполнение инструкции DBCC CHECKDB с выбранным предложением REPAIR, перед выполнением этой инструкции обратитесь к вашему основному поставщику услуг технической поддержки.  
  
 Если в результате выполнения инструкции DBCC CHECKDB с одним из предложений REPAIR неполадка устранена не была, обратитесь к вашему основному поставщику услуг технической поддержки.  
  
#### <a name="results-of-running-repair-options"></a>Результаты выполнения инструкции REPAIR  
 Внестрочный узел данных на странице *P_ID1* будет удален, как и обе ссылки на страницах *P_ID2* и *P_ID3*.  
  
> [!CAUTION]  
>  Эта операция может привести к потере данных.  
  
  