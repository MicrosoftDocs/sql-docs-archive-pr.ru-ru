---
title: Занятие 2. Оценка рекомендаций для политик по расписанию | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a454e38ec2f07bf9867183a3894ac4ea001a942e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657437"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a>Урок 2. Выполнение политик рекомендаций по расписанию
  Можно настроить запланированные оценки рекомендованных политик на одном или нескольких экземплярах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Чтобы настроить рекомендованные политики на выполнение в соответствии с расписанием, необходимо импортировать эти политики в целевой экземпляр.  
  
 Чтобы развернуть запланированные политики на нескольких серверах, можно импортировать политики на одном экземпляре, настроить расписания для каждой из них, экспортировать запланированные политики в одну из папок, а затем развертывать эти запланированные политики на целевых экземплярах с помощью зарегистрированных серверов.  
  
> [!IMPORTANT]  
>  На целевом экземпляре должен быть запущен [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] или более поздняя версия. Автоматизация требует локального сохранения политик на экземпляре, что не поддерживается версиями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
 На этом занятии будут выполнены следующие действия.  
  
-   Импорт рекомендованных политик в экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Настройка политик на запуск по расписанию.  
  
-   Развертывание запланированных рекомендованных политик на нескольких экземплярах, управляемых через окно «Зарегистрированные серверы».  
  
 Это занятие содержит следующие разделы:  
  
-   [Импорт политик в один экземпляр](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [Планирование политик](../../2014/tutorials/schedule-the-policies.md)  
  
-   [Развертывание запланированных политик на нескольких экзмплярах](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a>См. также:  
 [Администрирование нескольких серверов с помощью центральных серверов управления](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
