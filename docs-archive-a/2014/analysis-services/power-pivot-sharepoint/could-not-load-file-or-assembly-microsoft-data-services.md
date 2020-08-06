---
title: Не удалось загрузить файл или сборку &#39;Microsoft. AnalysisServices. SharePoint. Integration&#39; | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: b7ba75bdbd8e25f98d11d822c22fa7881352ad88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666804"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a>Не удалось загрузить файл или сборку &#39;Microsoft. AnalysisServices. SharePoint. Integration&#39;
  В среде SharePoint 2010, в которой установлен PowerPivot для SharePoint, эта ошибка возникает, если решение на уровне приложений для PowerPivot развернуто неправильно.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Применяется к|PowerPivot для SharePoint|  
|Версия продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Решение Powerpivotwebapp не развернуто или развернуто неправильно.|  
|Текст сообщения|Не удалось загрузить файл или сборку Microsoft.AnalysisServices.SharePoint.Integration|  
  
## <a name="explanation"></a>Объяснение  
 PowerPivot для SharePoint использует пакеты решений для развертывания своих компонентов на сервере SharePoint. Одно из решений развернуто неправильно. Поэтому при попытке открыть галерею PowerPivot или другие страницы приложения PowerPivot на сайте SharePoint возникает эта ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните развертывание пакета решения.  
  
1.  В разделе «Системные параметры» центра администрирования выберите **Управление решениями фермы**.  
  
2.  Щелкните **Powerpivotwebapp**.  
  
3.  Нажмите **Развернуть решение**.  
  
4.  Выберите веб-приложение, для которого возникает эта ошибка. Если имеются несколько веб-приложений, выполните повторное развертывание для них всех.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Развертывание решений PowerPivot в SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
