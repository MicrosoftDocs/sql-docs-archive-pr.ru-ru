---
title: Настройка почты агента SQL Server на использование компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31d116c0bc8d7e148fc2ef6d2e344400516ad923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728346"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Настройка почты агента SQL Server на использование компонента Database Mail
  В этом разделе описывается настройка в агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использования компонента Database Mail для отправки уведомлений и предупреждений в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Перед началом работы**  
  
-   [Предварительные требования](#Prerequisites)  
  
-   [Безопасность](#Security)  
  
-   [Настройка агента SQL Server на использование компонента Database Mail с помощью среды SQL Server Management Studio](#SSMSProcedure)  
  
-   [Задачи дальнейших действий](#Follow_Up)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Включить компонент Database Mail.  
  
-   Создать учетную запись компонента Database Mail для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Создать профиль компонента Database Mail для учетной записи агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы сделать пользователя членом роли **DatabaseMailUserRole** в базе данных **msdb** .  
  
-   Сделать профиль используемым по умолчанию в базе данных **msdb** .  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Пользователь, создающий учетные записи профилей и выполняющий хранимые процедуры, должен быть членом предопределенной роли сервера sysadmin.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Настройка агента SQL Server на использование компонента Database Mail**  
  
-   Разверните экземпляр сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в обозревателе объектов.  
  
-   Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
-   Нажмите **Система предупреждений**.  
  
-   Выберите **Включить почтовый профиль**.  
  
-   В списке **Почтовая система** выберите **Компонент Database Mail**.  
  
-   В **Списке почтовых профилей**выберите почтовый профиль для компонента Database Mail.  
  
-   Перезапустите агент SQL Server.  
  
##  <a name="follow-up-tasks"></a><a name="Follow_Up"></a> Задачи дополнительной работы  
 Следующие задачи необходимо выполнить для завершения конфигурации агента на отправку предупреждений и уведомлений.  
  
-   [Оповещения](../../ssms/agent/alerts.md)  
  
     Предупреждения могут быть настроены на уведомление оператора о возникновении в базе данных определенного события или о формировании в операционной системе определенных условий.  
  
-   [Операторы](../../ssms/agent/operators.md)  
  
     Операторы — это псевдонимы для людей или групп, которые могут получать электронные уведомления.  
  
  
