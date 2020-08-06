---
title: Работа с несколькими версиями и экземплярами SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- concurrent installations [SQL Server]
- versions [SQL Server], multiple
- side-by-side installations [SQL Server]
- multiple SQL Server component versions
- installing SQL Server, side-by-side installations
- Setup [SQL Server], side-by-side installations
- 64-bit edition [SQL Server]
- 32-bit edition [SQL Server]
- editions [SQL Server], side-by-side installations
ms.assetid: 93acefa8-bb41-4ccc-b763-7801f51134e0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81d582a863c451fc818243373f3841a9e840562d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659091"
---
# <a name="work-with-multiple-versions-and-instances-of-sql-server"></a>Работа с несколькими версиями и экземплярами SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает на одном компьютере несколько экземпляров компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Кроме того, можно обновить уже установленные на компьютере предыдущие версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]либо установить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этот же компьютер с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поддерживаемые сценарии обновления см. в разделе [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
## <a name="version-components-and-numbering"></a>Версии компонентов и нумерация  
 Следующие основные понятия могут оказаться полезными для понимания поведения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при параллельной работе экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Стандартный формат версии продукта для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — MM.nn.bbbb.rr, в котором сегменты определяются следующим образом:  
  
 MM — основная версия  
  
 nn — дополнительная версия  
  
 bbbb — номер сборки  
  
 rr — номер редакции сборки  
  
 В каждой основной и дополнительной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]номер версии увеличивается, что позволяет отличить ее от предыдущих. Такое изменение номера версии служит для достижения нескольких разных целей. В их число входит отображение информации о версии в пользовательском интерфейсе, управление способом замены файлов при выполнении обновления, применении пакетов обновления, а также механизмы функционального дифференцирования между последующими версиями.  
  
### <a name="components-shared-by-all-versions-of-ssnoversion"></a>Общие компоненты для всех версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Определенные компоненты, которые являются общими для всех установленных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При параллельной установке различных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на одном компьютере эти компоненты обновляются до последней версии. Такие компоненты обычно удаляются автоматически при удалении последнего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Примеры: браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и модуль записи VSS [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="components-shared-across-all-instances-of-the-same-major-version-of-ssnoversion"></a>Компоненты, общие для всех экземпляров основной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Версии, общие для всех экземпляров основной версии, имеют общие компоненты во всех экземплярах. Если общие компоненты выбираются при выполнении обновления, то существующие компоненты обновляются до последней версии.  
  
 Примеры: [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]и электронная документация по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="components-shared-across-minor-versions"></a>Общие компоненты для всех дополнительных версий  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Версии, имеющие общие компоненты версии основной.дополнительный.  
  
 Пример .  
  
### <a name="components-specific-to-an-instance-of-ssnoversion"></a>Компоненты, принадлежащие только определенному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Некоторые компоненты и службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] принадлежат определенному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Такие компоненты называются привязанными к экземпляру. Они имеют ту же версию, что и экземпляр, которому они принадлежат, и используются только для этого экземпляра.  
  
 Примеры: [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
### <a name="components-that-are-independent-of-the-ssnoversion-versions"></a>Компоненты, не зависящие от версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Некоторые компоненты устанвливаются при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но не зависят от версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Они могут совместно использоваться всеми версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Примеры: Microsoft Sync Framework, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компактной установке см. в разделе [Install SQL Server 2014 мастера установки &#40;&#41;установки ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md). Дополнительные сведения об удалении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact см. в разделе [Удаление существующего экземпляра SQL Server (программа установки)](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md).  
  
## <a name="using-ssnoversion-side-by-side-with-previous-versions-of-ssnoversion"></a>Применение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параллельно с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить на компьютер, где уже запущены экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] одной из предыдущих версий. Поскольку экземпляр по умолчанию на компьютере уже имеется, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть установлен как именованный экземпляр.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep не поддерживает параллельную установку подготовленных экземпляров [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с выпущенными ранее версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на том же компьютере. Например, возможность подготавливать экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] параллельно с подготовленным экземпляром [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]отсутствует. Однако можно установить несколько подготовленных экземпляров одной и той же основной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параллельно на одном компьютере. Дополнительные сведения см. в разделе [Considerations for Installing SQL Server Using SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
>   
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] нельзя установить параллельно с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере с Windows Server 2008 R2 Server Core с пакетом обновления 1 (SP1). Дополнительные сведения об установке основных серверных компонентов см. в разделе [Install SQL Server 2014 на Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
 В следующей таблице показана поддержка параллельной эксплуатации для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Существующий экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|Поддержка параллельной работы|  
|--------------------------------------------------|----------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (32-разрядная версия)|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (32-разрядная версия)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (64-разрядная версия) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|  
  
## <a name="preventing-ip-address-conflicts"></a>Предотвращение конфликтов IP-адресов  
 Если экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен параллельно с отдельным экземпляром компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], то необходимо исключить возникновение конфликта номера порта TCP с IP-адресами. Конфликты обычно возникают в том случае, когда два экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] одновременно настроены на использование стандартного порта TCP (1433). Чтобы предотвратить возникновение конфликтов, настройте один экземпляр на использование фиксированного порта, отличного от установленного по умолчанию. Обычно настройку фиксированного порта проще всего выполнить на отдельном экземпляре. Настройка компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на использование различных портов позволит предотвратить непредвиденные конфликты IP-адресов и TCP, которые блокируют запуск экземпляра в случае ошибки экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при переходе на режим ожидания.  
  
## <a name="see-also"></a>См. также:  
 [Требования к оборудованию и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)   
 [Установка SQL Server 2014 с помощью мастера установки &#40;установки&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)   
 [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Обновление до SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)   
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Обратная совместимость](../../../2014/getting-started/backward-compatibility.md)   
 [Использование помощника по обновлению для подготовки к обновлениям](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
  
