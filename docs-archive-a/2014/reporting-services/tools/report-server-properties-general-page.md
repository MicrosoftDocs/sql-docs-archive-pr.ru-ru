---
title: Свойства сервера (страница "Общие") | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66199e35c180790cba5120cb839be67e43052be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751724"
---
# <a name="server-properties-general-page"></a>Свойства сервера (страница «Общие»)
  Данная страница позволяет просмотреть или изменить заголовок, используемый в диспетчере отчетов, включить или отключить папку «Мои отчеты», выбрать определение роли для защиты папки «Мои отчеты», а также включить или отключить клиентское средство управления печатью.  
  
 Чтобы открыть эту страницу, запустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , подключитесь к экземпляру сервера отчетов, щелкните правой кнопкой мыши имя сервера отчетов и выберите пункт **свойства**.  
  
 Свойства сервера, для которых доступна настройка, определяются режимом сервера. Если сервер отчетов настроен для работы в режиме интеграции с SharePoint, то включить папку «Мои отчеты» или установить заголовок приложения для диспетчера отчетов нельзя.  
  
## <a name="options"></a>Параметры  
 **имя**;  
 Введите имя приложения, которое отображается в диспетчере отчетов. По умолчанию это значение равно [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Указанное имя отображается только в диспетчере отчетов.  
  
 **Version**  
 Это свойство доступно только для чтения. Задает используемую версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 **Выпуск**  
 Это свойство доступно только для чтения. Задает текущий экземпляр сервера отчетов. Диспетчер отчетов имеется не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **Режим проверки подлинности**  
 Это свойство доступно только для чтения. Оно определяет типы запросов на проверку подлинности, принимаемые экземпляром сервера отчетов. Чтобы изменить режим проверки подлинности, необходимо изменить файл RSReportServer.config. Дополнительные сведения см. в статье [Authentication with the Report Server](../security/authentication-with-the-report-server.md).  
  
 **URL-адрес**  
 Это свойство доступно только для чтения. Задает URL-адрес для веб-службы сервера отчетов. Это значение указывается в средстве настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в статье [Настройка URL-адреса (диспетчер конфигурации служб SSRS)](../install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
 **Включить папку «Мои отчеты» для каждого пользователя**  
 Папка «Мои отчеты» становится доступной для пользователей. Этот параметр доступен только при работе с серверами отчетов в собственном режиме.  
  
 **Выбрать роль, которая будет применяться к каждой папке «Мои отчеты»**  
 Задает определение роли для защиты папки «Мои отчеты». Это определение роли обозначает набор задач, которые поддерживаются во время работы в каждой папке «Мои отчеты».  
  
 **Разрешить загрузку элемента управления ActiveX для клиента печати**  
 Позволяет задать системное свойство `EnableClientPrinting` сервера отчетов. Если клиентская печать разрешена, у пользователей, имеющих разрешения локального администратора, имеется возможность загрузки подписанного элемента управления ActiveX для печати HTML-отчетов. Дополнительные сведения см. в разделе [Включение и отключение печати на стороне клиента для служб Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка свойств сервера отчетов &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Соединение с сервером отчетов в Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Включение и отключение Мои отчеты](../report-server/enable-and-disable-my-reports.md)   
 [Сервер отчетов в справке Management Studio F1](report-server-in-management-studio-f1-help.md)   
 [Обеспечение безопасности «Моих отчетов»](../security/secure-my-reports.md)  
  
  
