---
title: Соединение с сервером (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.analysisserver.f1
ms.assetid: 7e277d22-8d4b-422e-8882-7c5dd7a6d915
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3530f38534e09ef19e77293880129274dfc211b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727342"
---
# <a name="connect-to-server-analysis-services"></a>Соединение с сервером (службы Analysis Services)
  Используйте это диалоговое окно для просмотра или настройки параметров при подключении к [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Тип сервера**  
 При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера c панели "Зарегистрированные серверы" поле **Тип сервера** не может быть изменено и совпадает с типом сервера, показанного в компоненте "Зарегистрированные серверы". Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
 **Имя сервера**  
 Выберите экземпляр сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
 **Аутентификация**  
 При подключении к экземпляру службы Analysis Services поддерживаются следующие режимы проверки подлинности: проверка подлинности [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows.  
  
 **Режим проверки подлинности Windows (проверка подлинности Windows)**  
 Режим **проверки подлинности Windows** позволяет пользователю подключаться с помощью учетной записи пользователя Windows.  
  
 **User name**  
 Этот параметр недоступен в данном выпуске. Введите имя пользователя для соединения. Этот параметр доступен только в случае выбора режима **Проверка подлинности Windows**для подключения.  
  
 **Пароль**  
 Этот параметр недоступен в данном выпуске. Введите пароль для этого имени входа. Этот параметр доступен для редактирования только при подключении с проверкой подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Подключить**  
 Нажмите, чтобы подключиться к выбранному выше серверу.  
  
 **Параметры**  
 Нажмите, чтобы вывести дополнительные параметры соединения с сервером, такие как регистрация сервера и запоминание пароля.  
  
  