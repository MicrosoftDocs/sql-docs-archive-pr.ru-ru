---
title: Соединение с сервером (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectoserverunknownservertype.f1
- sql12.swb.connection.login.sqlserver.f1
- sql12.swb.connection.login.sqlce.f1
- sql12.swb.manageSS2k.f1
- sql12.swb.connecttoce.f1
- sql12.swb.connecttoce.connectionproperties.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca227d1a3bbc13160962ba2fcad23ff011c950f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733481"
---
# <a name="connect-to-server-database-engine"></a>Соединение с сервером (ядро СУБД)
  Используйте это диалоговое окно для просмотра или настройки параметров при подключении к [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. В большинстве случаев при подключении в поле **Имя сервера** нужно ввести имя компьютера, на котором расположена база данных, а затем нажать кнопку **Соединить**. Если выполняется соединение с [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], введите имя компьютера, а после него — **\sqlexpress**.  
  
 На возможность подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]влияют многие факторы.  
  
## <a name="options"></a>Параметры  
 **Тип сервера**  
 При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]или [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера c панели "Зарегистрированные серверы" поле **Тип сервера** не может быть изменено и совпадает с типом сервера, показанного в компоненте "Зарегистрированные серверы". Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)]или службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
 **Имя сервера**  
 Выберите экземпляр сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
> [!NOTE]  
>  Для подключения к активному экземпляру [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] выполните подключение с использованием протокола именованных каналов, указав имя канала, например "\\\\.\pipe\3C3DF6B1-2262-47\tsql\query". Дополнительные сведения см. в документации по [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] .  
  
 **Аутентификация**  
 При подключении к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] доступны два режима проверки подлинности.  
  
 **Режим проверки подлинности Windows (проверка подлинности Windows)**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Режим проверки подлинности Windows позволяет подключаться с учетной записью Windows.  
  
 **Проверка подлинности SQL Server**  
 При подключении пользователя с указанным именем входа и паролем не через доверенное соединение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет проверку подлинности самостоятельно по наличию учетной записи входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и совпадения указанного пароля с ранее сохраненным. Если в службе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не задана учетная запись входа, проверка подлинности завершается ошибкой, о которой пользователь получит сообщение.  
  
> [!IMPORTANT]  
>  По возможности используйте аутентификацию Windows.  
  
 **User name**  
 Введите имя пользователя для соединения. Этот параметр доступен только при соединении с использованием метода проверки подлинности Windows.  
  
 **Имя входа**  
 Введите имя входа для подключения. Этот параметр доступен только в том случае, если выбрано соединение с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Пароль**  
 Введите пароль для этого имени входа. Этот параметр доступен для редактирования только при подключении с проверкой подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Подключить**  
 Нажмите, чтобы подключиться к выбранному выше серверу.  
  
 **Параметры**  
 Нажмите, чтобы вывести дополнительные параметры соединения с сервером, такие как регистрация сервера и запоминание пароля.  
  
  
