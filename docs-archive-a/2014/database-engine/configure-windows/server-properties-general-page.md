---
title: Свойства сервера (страница "Общие") — среда SQL Server Management Studio | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.prodinfo.f1
- sql12.swb.serverproperties.setsapassword.f1
- sql12.swb.serverproperties.activedirectory.f1
ms.assetid: 10ac57f1-b4bd-4528-bb66-3e47ccf663e7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7dc3ff21d145964c99ffaab57d157f8ec7cd203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665117"
---
# <a name="server-properties-general-page---sql-server-management-studio"></a>Свойства сервера (страница «Общие») — среда SQL Server Management Studio
  Эта страница выводит доступные только для чтения данные об установленной конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="property-grid"></a>Сетка свойств  
 Показывает свойства выбранного сервера — имя сервера, установленную ОС и число процессоров.  
  
 **имя**;  
 Отображает имя экземпляра сервера.  
  
 **Продукт**  
 Выводит выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенный в данный момент.  
  
 **Операционная система**  
 Отображает версию работающей в настоящий момент ОС [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Платформа**  
 Описывает ОС и оборудование, на которых запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Версия**  
 Выводит номер версии запущенного в настоящий момент выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Язык**  
 Выводит язык, поддерживаемый запущенным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Память**  
 Выводит объем ОЗУ, установленного на данном сервере.  
  
 **Процессоры**  
 Выводит число установленных ЦП.  
  
 **Корневой каталог**  
 Выводит путь к данному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , обычно "C:\Program Files\Microsoft SQL Server\\".  
  
 **Параметры сортировки сервера**  
 Выводит параметры сортировки, поддерживаемые сервером. Параметры сортировки задают кодовую страницу и порядок сортировки для работы с данными в Юникоде и других форматах.  
  
 **Кластеризован**  
 Содержит значение **True** , если экземпляр сервера настроен для работы в отказоустойчивом кластере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо значение **False** , если экземпляр сервера не кластеризован.  
  
 **Режим HADR включен**  
 Содержит значение **True** , если служба [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] включена, или **False** , если служба [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] отключена. Дополнительные сведения о включении и отключении [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] см. в статье [Включение и отключение групп доступности AlwaysOn (SQL Server)](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
## <a name="description-field"></a>Поле описания  
 Содержит дополнительные сведения о свойствах сервера.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)  
  
  
