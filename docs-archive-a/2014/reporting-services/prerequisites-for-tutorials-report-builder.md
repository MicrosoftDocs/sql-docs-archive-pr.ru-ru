---
title: Предварительные условия для использования учебников (построитель отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b1f037d1a19fdce566a5a22c7e6a3274fb10ed7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654894"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Предварительные условия для использования учебников (построитель отчетов)
  При использовании учебников по построителю отчетов предполагается возможность просмотра и сохранения отчетов на сервере отчетов или сайте SharePoint, интегрированном с сервером отчетов. Во всех учебниках для данных используются запросы, которые необходимо обработать с помощью экземпляра [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 Если нет доступа к серверу отчетов, сайту или источнику данных, изучить работу с построителем отчетов можно путем построения отчета вне сети. См. раздел [Учебник. Создание стандартного отчета с диаграммой в режиме "вне сети" (построитель отчетов)](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
## <a name="requirements"></a>Требования  
 Чтобы завершить учебники по построителю отчетов, должны быть выполнены следующие условия.  
  
-   Доступ к [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Построитель отчетов. Построитель отчетов можно запустить с помощью изолированной версии построителя отчетов или версии ClickOnce, которая доступна из диспетчера отчетов или с сайта SharePoint. Для версии ClickOnce отличается только первый шаг — открытие построителя отчетов.  
  
     Чтобы использовать диспетчер отчетов, откройте диспетчер отчетов и щелкните **Построитель отчетов**. По умолчанию URL-адресом для диспетчер отчетов является http:// \<*servername*> /Reports.  
  
     Чтобы начать работу с сайтом SharePoint, перейдите на сайт, щелкните вкладку «Документы», выберите «Создать документ» и в раскрывающемся списке выберите «Отчет построителя отчетов», Например, http:// \<servername> /СИТЕС/мисите/Репортс. Администратор сайта SharePoint должен включить функцию «Отчет построителя отчетов» для всех библиотек документов.  
  
-   URL-адрес сервера отчетов служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] или сайта SharePoint, интегрированного с сервером отчетов служб [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] . Необходимы следующие разрешения: на сохранение и просмотр отчетов, общих источников данных, общих наборов данных, элементов отчетов и моделей. URL-адрес сервера отчетов по умолчанию — http:// \<servername> /reportserver. URL-адрес для сайта SharePoint по умолчанию — http:// \<sitename> или http:// \<server> /Сите.  
  
-   Имя экземпляра [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] и учетные данные, необходимые для доступа только для чтения к базе данных. Запросы набора данных в учебниках используют статические данные, но все запросы должны обрабатываться экземпляром [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] для возвращения метаданных, необходимых для набора данных отчета. Например, следующая строка подключения определяет только сервер: `data source=<servername>`. У вас должны быть права на доступ к базе данных по умолчанию, назначенной вам системным администратором, который предоставляет разрешения на доступ к серверу. Также можно указать базу данных, как показано в следующей строке подключения: `data source=<servername>;initial catalog=<database>`.  
  
-   Для работы с учебником, включающим карту, сервер отчетов необходимо настроить для поддержки мозаичного фона Bing Map. Дополнительные сведения см. в разделе [Планирование поддержки отчетов-карт](plan-for-map-report-support.md) в [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] документации по [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) MSDN.Microsoft.com.  
  
-   Учебник. [Создание детализированных и главных отчетов &#40;построитель отчетов&#41;](tutorial-creating-drillthrough-and-main-reports-report-builder.md), использует Демонстрационный набор данных бизнес-аналитики contoso. Этот набор включает хранилище данных ContosoDW и базу данных оперативной аналитической обработки (OLAP) Contoso_Retail. Создаваемые в данном учебнике отчеты извлекают данные из куба Contoso Sales. Базу данных OLAP Contoso_Retail можно скачать в [Центре загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=18279). Необходимо скачать только файл ContosoBIdemoABF.exe. Он содержит базу данных OLAP.  
  
     Второй файл, ContosoBIdemoBAK.exe, относится к хранилищу данных ContosoDW, которое не используется в данном учебнике.  
  
     На веб-сайте приведены инструкции по извлечению и восстановлению файла резервной копии ContosoRetail.abf в базу данных Contoso_Retail OLAP.  
  
     Необходимо иметь доступ к экземпляру служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], где будет установлена база данных OLAP.  
  
 Администратор сервера отчетов может предоставить необходимые разрешения на сервере отчетов, настроить папки для служб [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] , а также параметры по умолчанию для построителя отчетов. Дополнительные сведения см. в разделе [Установка, удаление и поддержка построитель отчетов](install-uninstall-and-report-builder-support.md).  
  
## <a name="see-also"></a>См. также:  
 [Учебники &#40;построитель отчетов&#41;](report-builder-tutorials.md)  
  
  
