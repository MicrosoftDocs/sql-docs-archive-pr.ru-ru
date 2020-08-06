---
title: Состояние сервера отчетов (службы SSRS в собственном режиме) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c2fb2860fd80b827e48ad72b59192573d16b8a4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654747"
---
# <a name="report-server-status-ssrs-native-mode"></a>Состояние сервера отчетов (службы Reporting Services в собственном режиме)
  Эта страница позволяет просмотреть сведения о состоянии экземпляра сервера отчетов, с которым в настоящий момент установлено соединение. Данная страница является начальной для настройки сервера отчетов. Доступны также дополнительные страницы, предназначенные для настройки URL-адресов, учетной записи службы, базы данных сервера отчетов, доставки электронной почты сервера отчетов, параметров масштабного развертывания и ключей шифрования.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим.  
  
 Чтобы открыть эту страницу, запустите диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и подключитесь к экземпляру сервера отчетов. Дополнительные сведения см. в разделе [диспетчер конфигурации служб Reporting Services &#40;del&#41;](reporting-services-configuration-manager-native-mode.md).  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Configuration Manager (RSConfigTool.exe) устанавливается с уровнем привилегий "highestAvailable". В этом весь замысел. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требует подключения к API-интерфейсам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI. Для некоторых средств [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI требуется более высокий уровень прав администратора.  
  
 Если при подключении к серверу отчетов все ссылки страницы затенены, убедитесь, что сервер отчетов запущен. **Состояние службы отчетов:** должно быть "запущено". Для определения состояния сервера также можно использовать консольное приложение «Службы» в «Администрировании».  
  
## <a name="options"></a>Варианты  
 **Экземпляр SQL Server**  
 Отображает сведения об экземпляре сервера отчетов, с которым имеется соединение в текущий момент. Имена экземпляров сервера отчетов создаются на основе именованных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Имя экземпляра по умолчанию — «MSSQLSERVER», а имя именованного экземпляра — значение, указанное во время установки. Дополнительные сведения об экземплярах служб см. в разделе [Работа с несколькими версиями и экземплярами SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
> [!NOTE]  
>  В выпуске SQL Server Express with Advanced Services экземпляром по умолчанию является SQLExpress.  
  
 **Instance ID**  
 Соответствует папке файловой системы, в которой хранятся программные файлы подключенного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение **Идентификатор экземпляра** присваивается программой установки в формате *компонент*.*экземпляр*, где *компонент* является значением, указывающим на компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а *экземпляр* — именем экземпляра. Имя экземпляра по умолчанию — MSSQLSERVER. Например, если устанавливаются экземпляры компонентов [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]по умолчанию и компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , будут созданы папки со следующими именами:  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 Если установить второй экземпляр компонента, который уже установлен, например [!INCLUDE[ssDE](../../includes/ssde-md.md)] , и имя экземпляра Contoso, то **идентификатором экземпляра** будет MSSQL12. Компанией.  
  
 **Выпуск**  
 Отображает сведения о выпуске. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](https://go.microsoft.com/fwlink/?linkid=232473).  
  
 **Версия продукта**  
 Отображает устанавливаемую версию служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 **База данных сервера отчетов**  
 Отображает имя базы данных сервера отчетов, в которой хранятся данные о приложении для текущего экземпляра сервера отчетов.  
  
 **Режим сервера отчетов**  
 В этом поле всегда должно отображаться значение **Собственный**. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживает только серверы отчетов, работающие в собственном режиме. Если отображается значение **Режим интеграции с SharePoint**, это может указывать на то, что развертывание собственного режима настроено неправильно, в связи с чем требуется подключиться к каталогу отчетов, работающему в собственном режиме. На странице **База данных** диспетчера конфигурации измените базу данных и либо создайте новую базу данных, либо подключитесь к существующему каталогу баз данных сервера отчетов, работающего в собственном режиме.  
  
 **Состояние сервера**  
 Указывает, запущена ли служба сервера отчетов.  
  
 **Начало**  
 Запускает службу сервера отчетов. Перезапуск службы необходим после некоторых изменений конфигурации (например, при перенастройке сервера отчетов после изменения имени компьютера). При изменении конфигурации резервирования URL-адресов служба перезапустится автоматически. Кроме того, перезапуск необходим для того, чтобы применить изменения.  
  
 **Остановить**  
 Останавливает службу сервера отчетов. Остановка службы приводит к прекращению работы сервера отчетов. Дополнительные сведения см. в разделе [Запуск и завершение службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер конфигурации служб Reporting Services разделы справки F1 &#40;служб SSRS в собственном режиме&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Диспетчер конфигурации служб Reporting Services &#40;del&#41;](/sql/sql-server/install/reporting-services-configuration-manager-native-mode)   
 [Инициализация сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
