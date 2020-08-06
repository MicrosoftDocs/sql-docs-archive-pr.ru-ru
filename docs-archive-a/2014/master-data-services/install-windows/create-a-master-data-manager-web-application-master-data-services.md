---
title: Создание веб-приложения диспетчера основных данных (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 241d46d7-8008-47f6-bebd-0dfff1cc856a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd81188b499850397aa8ffd2e40cfcb91c648288
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656433"
---
# <a name="create-a-master-data-manager-web-application-master-data-services"></a>Создание веб-приложения мастера основных данных (службы Master Data Services)
  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] предоставляет интерфейс пользователям для работы с основными данными, а администраторам — для настройки и администрирования MDS.  
  
 Веб-приложение всегда должно располагаться на веб-сайте. Для создания веб-приложения можно использовать один из следующих способов.  
  
-   Использовать веб-сайт по умолчанию, а затем создать веб-приложение.  
  
-   Использовать существующий веб-сайт, а затем создать веб-приложение.  
  
-   Создать новый веб-сайт с автоматическим созданием нового веб-приложения.  
  
 После того как вы создали веб-приложение, необходимо связать его с базой данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Дополнительные сведения о требованиях, предъявляемых к компьютеру, на котором размещается веб-приложение, см. в разделе [Требования веб-приложений (Master Data Services)](web-application-requirements-master-data-services.md).  
  
## <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a>Создание веб-приложения диспетчера основных данных на новом веб-сайте  
 При создании нового веб-сайта корневое веб-приложение является веб-приложением [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . Это веб-приложение будет также добавляется в новый пул приложений.  
  
> [!NOTE]  
>  При выполнении этой процедуры нельзя указать виртуальный путь и псевдоним для веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . Если необходимо указать виртуальный путь и псевдоним для [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], веб-приложение следует создать на существующем веб-сайте, причем он не должен быть настроен в качестве веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
 Следует также учитывать, что [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] поддерживает создание сайтов только с HTTP-привязками. Для добавления привязки HTTPS создайте новый сайт и приложение в [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , а затем см. дополнительные сведения в разделе [Обеспечение безопасности веб-приложения диспетчера основных данных](secure-a-master-data-manager-web-application.md) .  
  
#### <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a>Создание веб-приложения диспетчера основных данных на новом веб-сайте  
  
1.  Откройте среду [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
3.  На странице **Веб-конфигурация** в списке «Веб-сайт» выберите **Создать новый веб-сайт**.  
  
4.  В диалоговом окне **Создание веб-сайта** укажите данные для нового веб-сайта. Дополнительные сведения о параметрах пользовательского интерфейса в этом диалоговом окне см. в разделе [Диалоговое окно "Создание веб-сайта" (диспетчер конфигурации Master Data Services)](../create-website-dialog-box-master-data-services-configuration-manager.md).  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a>Создание веб-приложения диспетчера основных данных на существующем веб-сайте  
 При создании веб-приложения на существующем веб-сайте для него можно выбрать виртуальный путь и псевдоним. Это веб-приложение будет добавлено в новый пул приложений.  
  
#### <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a>Создание веб-приложения диспетчера основных данных на существующем веб-сайте  
  
1.  Откройте среду [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
3.  На странице **Веб-конфигурация** в списке **Веб-сайт** выберите веб-сайт, на котором нужно создать веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
4.  Нажмите кнопку **Создать приложение**.  
  
5.  В диалоговом окне **Создание веб-приложения** укажите данные для нового веб-приложения. Дополнительные сведения о параметрах пользовательского интерфейса в этом диалоговом окне см. в разделе [Диалоговое окно "Создание веб-приложения" (диспетчер конфигурации Master Data Services)](../create-web-application-dialog-box-master-data-services-configuration-manager.md).  
  
6.  Нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   Свяжите веб-приложение с базой данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Связывание базы данных служб Master Data Services и веб-приложения](associate-a-master-data-services-database-and-web-application.md).  
  
-   В случае если требуется шифровать содержимое при помощи протокола SSL, на веб-сайте, содержащем веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , можно настроить использование HTTPS-привязки. Для настройки сертификата сервера для веб-сервера, а также настройки HTTPS-привязки и параметров SSL для сайта необходимо использовать средства служб IIS, например диспетчер IIS. Дополнительные сведения см. в статье [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Master Data Services](install-master-data-services.md)  
  
  
