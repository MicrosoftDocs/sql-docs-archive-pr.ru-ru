---
title: Поиск отчетов и других элементов (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a964cbdbc674fb3d29e18b5e5075695f0033801e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654861"
---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a>Поиск отчетов и других элементов (построитель отчетов и службы SSRS)
  Можно использовать диспетчер отчетов для поиска на сервере отчетов заданных элементов по имени или описанию. Можно искать опубликованные отчеты, модели отчетов, папки, общие источники данных и ресурсы. Нельзя искать расписания, владельцев, назначения ролей, определенные моментальные снимки в журнале отчета или в подписках. Поиск выполняется в базе данных сервера отчетов, в которой хранятся элементы.  
  
> [!NOTE]  
>  Выполнение поиска системного файла не вернет результаты поиска для элементов, управляемых сервером отчетов.  
  
-   Чтобы начать поиск элементов в диспетчере отчетов, введите строку поиска в текстовом поле **Поиск** вверху страницы. Поиски начинаются с высшего узла иерархии папок и затем следуют через каждую ветку. Если отсутствует разрешение на доступ к определенной ветке, то эта ветка пропускается. Это относится к папкам «Мои отчеты», принадлежащим другим пользователям и другим папкам, которые обычно не доступны. Только отчеты и элементы, на которые есть разрешение просмотра, включаются в результаты поиска.  
  
-   Чтобы найти элемент по имени или описанию, укажите весь текст или часть текста, с которым нужно совпадение. В строке поиска регистр букв не учитывается. Для требования или исключения условия поиска нельзя использовать операторы поиска, такие как символы плюс (+) или минус (–).  
  
-   Для поиска определенного текста в отчете используется панель инструментов, расположенная в верхней части отчета.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Поиск и просмотр отчетов в диспетчер отчетов &#40;построитель отчетов и служб SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)   
 [Использование Мои отчеты &#40;построитель отчетов и служб SSRS&#41;](using-my-reports-report-builder-and-ssrs.md)   
 [Поиск, просмотр отчетов и управление ими &#40;построитель отчетов и SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Открытие и закрытие отчетов (диспетчер отчетов)](../reports/open-and-close-a-report-report-manager.md)  
  
  
