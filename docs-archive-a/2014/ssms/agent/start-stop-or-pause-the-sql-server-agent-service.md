---
title: Запуск, остановка или приостановка службы агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2feb6a18c602271b1bec871fbfc9793979b100e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727889"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Start, Stop, or Pause the SQL Server Agent Service
  В этом разделе описывается, как запустить, остановить или перезапустить службу агента SQL Server в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить для автоматического запуска вместе с операционной системой или запуска вручную для выполнения определенных заданий. Службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно остановить или приостановить, чтобы прекратить выполнение заданий, уведомления операторов и оповещения.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   [Запуск, остановка и перезапуск службы агента SQL Server с использованием среды SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Для автоматизации административных задач агент должен работать как служба. Дополнительные сведения см. в статье [Configure SQL Server Agent](configure-sql-server-agent.md).  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
 Дополнительные сведения о разрешениях Windows, необходимых для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы агента, см. в разделе [Выбор учетной записи для службы агент SQL Server](select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>Запуск, остановка и перезапуск службы агента SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, на котором нужно управлять службой агента SQL Server.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**и выберите команду **Запуск**, **Стоп**или **Перезапуск**.  
  
3.  В диалоговом окне **Контроль учетных записей** нажмите **Да**.  
  
4.  При появлении запроса о необходимости выполнения действия нажмите кнопку **Да**.  
  
 Дополнительные сведения можно найти в разделе  
  
-   [Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
-   [Автоматический запуск агента SQL Server (среда SQL Server Management Studio)](autostart-sql-server-agent-sql-server-management-studio.md)  
  
  
