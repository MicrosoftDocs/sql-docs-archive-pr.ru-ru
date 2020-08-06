---
title: Настройка брандмауэра для доступа к серверу отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b578c980522d24f5a24a73fdfd080ec425335aac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665826"
---
# <a name="configure-a-firewall-for-report-server-access"></a>Configure a Firewall for Report Server Access
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и опубликованным отчетам производится по URL-адресам, которые состоят из IP-адреса, номера порта и имени виртуального каталога. Если включен брандмауэр Windows, то порт, на который настроен сервер отчетов, скорее всего, закрыт. Обычно это выражается в том, что при обращении с удаленного клиентского компьютера к отчету или к диспетчеру отчетов выдается пустая страница.  
  
 Открыть порт можно при помощи брандмауэра Windows на компьютере сервера отчетов. Службы Reporting Services не открывают порты автоматически, этот шаг необходимо выполнить вручную.  
  
 По умолчанию сервер отчетов слушает HTTP-запросы для порта 80. Следующие пошаговые инструкции позволяют настроить порт. Если URL-адреса сервера отчетов настроены на другой порт, при выполнении описанных ниже инструкций необходимо указывать его номер.  
  
 При обращении к реляционным базам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на внешних компьютерах или в случае, если база данных сервера отчетов находится на внешнем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо открыть порт 1433 и 1434 на внешнем компьютере. Дополнительные сведения о брандмауэре Windows см. в статье [Настройка брандмауэра Windows для доступа к компоненту Database Engine](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) в электронной документации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на компоненты [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="prerequisites"></a>предварительные требования  
 Выполнение следующих инструкций предполагает, что создана база данных сервера отчетов, настроена учетная запись службы и URL-адреса диспетчера отчетов и веб-службы сервера отчетов. Дополнительные сведения см. в разделе [Управление сервером отчетов служб Reporting Services в собственном режиме](manage-a-reporting-services-native-mode-report-server.md).  
  
 Кроме этого, необходимо проверить доступность экземпляра сервера отчетов из веб-браузера через локальное соединение. Этот шаг необходим для проверки работоспособности установки. Прежде чем приступать к открытию портов, необходимо проверить правильность настройки установки. Чтобы выполнить этот шаг в Windows Server, потребуется также добавить сервер отчетов к доверенным сайтам. Дополнительные сведения см. в разделе [Настройка сервера отчетов, работающего в основном режиме, для локального администрирования (службы SSRS)](configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="opening-ports-in-windows-firewall"></a>Открытие портов в брандмауэре Windows  
 В разных версиях брандмауэра Windows эта процедура выполняется по-разному.  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a>Открытие порта 80 в Windows 7, Windows Server 2008 R2, Windows Server 2012 и 2012 R2  
  
1.  В меню **Пуск** выберите **Панель управления**, **Система и безопасность**и **Брандмауэр Windows**. Если на панели управления не включено представление по категориям, сразу выберите **Брандмауэр Windows**.  
  
2.  Нажмите кнопку **Дополнительные параметры**.  
  
3.  Выберите **Правила для входящих подключений.**  
  
4.  Выберите **Создать правило** в окне **Действия****.**  
  
5.  Выберите **Тип правила** в разделе **Порт**.  
  
6.  Щелкните **Далее**.  
  
7.  На странице **Протокол и порты** выберите **TCP**.  
  
8.  Выберите **Указанные локальные порты** и введите значение **80**.  
  
9. Щелкните **Далее**.  
  
10. На странице **Действие** выберите **Разрешить соединение**.  
  
11. Щелкните **Далее**.  
  
12. На странице **Профиль** выберите необходимые параметры для среды.  
  
13. Щелкните **Далее**.  
  
14. На странице **Имя** введите имя**ReportServer (TCP через порт 80)**.  
  
15. Нажмите кнопку **Готово**.  
  
16. Перезагрузите компьютер.  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a>Открытие порта 80 в Windows Vista или Windows Server 2008  
  
1.  В меню **Пуск** выберите пункт **Панель управления**, щелкните **Безопасность**, а затем щелкните **Брандмауэр Windows**.  
  
2.  Выберите элемент **Разрешение запуска программы через брандмауэр Windows**.  
  
3.  Нажмите кнопку **Продолжить**.  
  
4.  На вкладке Исключения нажмите кнопку **Добавить порт**.  
  
5.  В окне Имя введите **ReportServer (TCP через порт 80)**.  
  
6.  В списке номер порта введите **80**.  
  
7.  Убедитесь, что выбран параметр **TCP** .  
  
8.  Щелкните **изменить область**.  
  
9. Щелкните **только мою сеть (подсеть)** и нажмите кнопку **ОК**.  
  
10. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
11. Перезагрузите компьютер.  
  
## <a name="next-steps"></a>Next Steps  
 После открытия порта, прежде чем удаленные пользователи смогут производить доступ к серверу отчетов, им необходимо предоставить доступ к корневой папке и на уровне сайта. Даже если порт правильно открыт, пользователи не смогут соединяться с сервером отчетов, если им не предоставлены необходимые разрешения. Дополнительные сведения см. в разделе [Предоставление пользователям доступа к серверу отчетов (диспетчер отчетов)](../security/grant-user-access-to-a-report-server.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Правильность открытия порта можно также проверить, открыв диспетчер отчетов с другого компьютера. Дополнительные сведения см. в разделе [Диспетчер отчетов (службы SSRS в собственном режиме)](../report-manager-ssrs-native-mode.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Создание базы данных сервера отчетов &#40;службы SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Управление сервером отчетов Reporting Services в собственном режиме](manage-a-reporting-services-native-mode-report-server.md)  
  
  
