---
title: Создание учетной записи компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], accounts
- accounts [Database Mail]
ms.assetid: c07abbc6-fc6a-470b-8fa3-532f2e06b16a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec7d1c9147998b5a19cc0e6af13220bd64e165fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657815"
---
# <a name="create-a-database-mail-account"></a>Создание учетной записи компонента Database Mail
  Для создания учетной записи компонента Database Mail применяется **мастер настройки компонента Database Mail** или [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   **Перед началом работы**  [Предварительные требования](#Prerequisites)  
  
-   **Создание учетной записи компонента Database Mail с использованием:**  [мастера настройки компонента Database Mail](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [Следующие действия по настройке компонента Database Mail](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Определите имя сервера и номер порта для сервера протокола SMTP, который используется для отправки электронной почты. Если SMTP-сервер требует проверки подлинности, определите имя пользователя и пароль для SMTP-сервера.  
  
-   Также можно указать тип сервера и номер его порта. Для исходящих сообщений всегда используется тип сервера «SMTP». Большинство SMTP-серверов по умолчанию используют порт 25.  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> Использование мастера настройки компонента Database Mail  
 **Создание учетной записи компонента Database Mail с использованием мастера**  
  
-   В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого необходимо настроить компонент Database Mail, и разверните дерево сервера.  
  
-   Разверните узел **Управление**  
  
-   Дважды щелкните компонент Database Mail, чтобы открыть мастер настройки компонента Database Mail.  
  
-   На странице **Выбор задачи настройки** выберите **Управление учетными записями и профилями компонента Database Mail**и нажмите **Далее**.  
  
-   На странице **Управление учетными записями и профилями** выберите **Создать новую учетную запись** и нажмите **Далее**.  
  
-   На странице **Создать учетную запись** задайте имя учетной записи, описание, сведения о почтовом сервере и тип проверки подлинности. Нажмите кнопку **Далее**  
  
-   На странице **Завершение работы мастера** просмотрите действия, подлежащие выполнению, и нажмите **Готово** , чтобы завершить создание новой учетной записи.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Создание учетной записи компонента Database Mail с помощью инструкций Transact-SQL**  
  
 Выполните хранимую процедуру **msdb.dbo.sysmail_add_account_sp** , чтобы создать учетную запись, и задайте следующие сведения:  
  
-   Имя создаваемой учетной записи.  
  
-   Необязательное описание учетной записи.  
  
-   Обратный адрес электронной почты, который будет вставляться в исходящие электронные сообщения.  
  
-   Имя отправителя, которое будет отображаться в исходящих электронных сообщениях.  
  
-   Имя SMTP-сервера.  
  
-   Имя пользователя для входа на SMTP-сервер, если этот сервер требует проверки подлинности.  
  
-   Пароль для входа на SMTP-сервер, если этот сервер требует проверки подлинности.  
  
 В следующем примере создается новая учетная запись компонента Database Mail.  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
##  <a name="follow-up-next-steps-to-configuring-the-database-mail"></a><a name="FollowUp"></a> Дальнейшие действия. Следующие действия по настройке компонента Database Mail  
  
-   [Создание профиля компонента Database Mail](create-a-database-mail-profile.md)  
  
  
