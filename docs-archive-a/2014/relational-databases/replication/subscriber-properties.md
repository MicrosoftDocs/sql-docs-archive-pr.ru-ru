---
title: Свойства подписчика | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81ab9cf5f277ccfe1044e5a7083f019db9d843ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749703"
---
# <a name="subscriber-properties"></a>Свойства подписчика
  Диалоговое окно **Свойства подписчика** содержит сведения, относящиеся к подписчикам, использующим версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], предшествующие [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="options"></a>Параметры  
 **Соединение агента с подписчиком**  
 Контекст, в котором агент распространителя и агент слияния устанавливают соединение от распространителя к подписчику. Применяется только к версиям, предшествующим [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Выберите **Выполнять олицетворение учетной записи процесса агента** для соединения с подписчиком при помощи контекста учетной записи агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на распространителе или укажите **Проверка подлинности SQL Server**, а затем введите значения в поля **Имя входа** и **Пароль**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выбрать пункт **Выполнять олицетворение учетной записи процесса агента**.  
  
 Для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий данные о соединении указываются для каждой подписки в мастере создания подписки, их можно изменить в диалоговом окне **Свойства подписки** .  
  
 **Расписания агентов по умолчанию**  
 Расписание по умолчанию, используемое в мастере создания подписки для подписчиков, использующих версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предшествующие [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 **Разное**  
 Содержит сведения о подписчике и типе подписчика.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md)   

 [Подписка на публикации](subscribe-to-publications.md)  
  
  
