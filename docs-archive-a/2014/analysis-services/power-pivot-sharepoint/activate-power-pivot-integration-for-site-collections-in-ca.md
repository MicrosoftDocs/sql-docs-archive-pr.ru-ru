---
title: Активация интеграции функций PowerPivot для семейств веб-сайтов в центре администрирования | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
ms.openlocfilehash: b565434cba197d04327e833d4ac6eab3caf96646
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730926"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>Активация интеграции функций PowerPivot для семейств веб-сайтов в центре администрирования
  При использовании параметра установки существующей фермы для установки SQL Server PowerPivot для SharePoint необходимо активировать интеграцию компонента PowerPivot для определенных семейств веб-сайтов. Если надстройка PowerPivot для SharePoint была установлена с параметром «Новый сервер», эту задачу можно пропустить, поскольку программа установки SQL Server уже активировала интеграцию компонента PowerPivot для корневого семейства веб-сайтов при настройке системы.  
  
 Активация компонента на уровне семейств веб-сайтов необходима, чтобы сделать страницы и шаблоны приложения доступными для веб-сайтов, в том числе страницы конфигурации для планового обновления данных страницы приложений для библиотеки PowerPivot Gallery и библиотек потоков данных.  
  
 Необходимо активировать интеграцию PowerPivot для всех семейств веб-сайтов, поддерживающих обработку запросов PowerPivot.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Пользователь должен быть администратором семейства веб-сайтов.  
  
## <a name="activate-powerpivot-features"></a>Активация функций PowerPivot  
  
1.  На сайте SharePoint нажмите кнопку **Действия сайта**.  
  
     По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что часто к сайту SharePoint можно получить доступ, введя http://\<computer name>, чтобы открыть корневое семейство веб-сайтов.  
  
2.  Щелкните элемент **Настройки сайта**.  
  
3.  В области "Администрирование семейства веб-сайтов" щелкните ссылку **Возможности семейства узлов**.  
  
4.  Прокрутите страницу вниз, пока не найдете **компонент коллекция веб-сайтов интеграции с PowerPivot**.  
  
5.  Щелкните **Активировать**.  
  
6.  Повторите эти действия для дополнительных семейств веб-сайтов, открыв каждый из сайтов и щелкнув **Действия сайта**.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование и настройка сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [PowerPivot для SharePoint &#40;начальной конфигурации&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [Установка PowerPivot для SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
