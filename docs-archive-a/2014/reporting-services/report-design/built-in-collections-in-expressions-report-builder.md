---
title: Встроенные коллекции в выражениях (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 78d5e3b8-9320-4e4b-a025-e2de3cf7afa7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55ceebd69d98506bb461cf4fc55b4d395453b652
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664724"
---
# <a name="built-in-collections-in-expressions-report-builder-and-ssrs"></a>Встроенные коллекции в выражениях (построитель отчетов и службы SSRS)
  В выражение в отчете можно включить ссылки на следующие встроенные коллекции: ReportItems, Parameters, Fields, DataSets, DataSources, Variables и встроенные поля для общих сведений, таких как имя отчета. В диалоговом окне **Выражения** отображаются не все коллекции. Коллекции DataSets и DataSources доступны только во время выполнения для отчетов, опубликованных на сервере отчетов. Коллекция ReportItems является коллекцией текстовых полей в области отчета, например текстовых полей на странице или в верхнем колонтитуле.  
  
 Дополнительные сведения см. в разделе [Выражения (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="understanding-built-in-collections"></a><a name="Collections"></a> Основные сведения о встроенных коллекциях  
 В следующей таблице перечислены встроенные коллекции, доступные при написании выражения. Каждая строка включает программное имя коллекции с учетом регистра, признак, можно ли использовать диалоговое окно «Выражение» для интерактивного добавления в коллекцию ссылки, пример и описание, включающее сведения о том, когда инициализируются и становятся доступными для использования значения коллекции.  
  
|Встроенная коллекция|Категория в диалоговом окне «Выражение»|Пример|Description|  
|--------------------------|-------------------------------------------|-------------|-----------------|  
|`Globals`|Встроенные поля|`=Globals.ReportName`<br /><br /> `- or -`<br /><br /> `=Globals.PageNumber`|Представляет глобальные переменные, полезные для отчетов, например для имени отчета или номера страницы. Доступна всегда.<br /><br /> Дополнительные сведения см. в разделе [Встроенные глобальные значения и ссылки на пользовательские поля (построитель отчетов и службы SSRS)](built-in-collections-built-in-globals-and-users-references-report-builder.md).|  
|`User`|Встроенные поля|`=User.UserID`<br /><br /> -или-<br /><br /> `=User.Language`|Представляет коллекцию сведений о пользователе, выполняющем отчет, например языковые настройки или идентификатор пользователя. Доступна всегда.<br /><br /> Дополнительные сведения см. в разделе [Встроенные глобальные значения и ссылки на пользовательские поля (построитель отчетов и службы SSRS)](built-in-collections-built-in-globals-and-users-references-report-builder.md).|  
|`Parameters`|Параметры|`=Parameters("ReportMonth").Value`<br /><br /> -или-<br /><br /> `=Parameters!ReportYear.Value`|Представляет коллекцию параметров отчета, каждый из которых может быть однозначным или многозначным. Недоступна до завершения обработки инициализации. Дополнительные сведения см. в разделе [Ссылки на коллекцию параметров (построитель отчетов и службы SSRS)](built-in-collections-parameters-collection-references-report-builder.md).|  
|`Fields(` *\<Dataset>* `)`|Поля|`=Fields!Sales.Value`|Представляет коллекцию полей набора данных, доступных для отчета. Доступна после получения данных из источника данных в набор данных. Дополнительные сведения см. в разделе [Ссылки на коллекцию полей набора данных (построитель отчетов и службы SSRS)](built-in-collections-dataset-fields-collection-references-report-builder.md).|  
|`DataSets`|Не отображается|`=DataSets("TopEmployees").CommandText`|Представляет коллекцию наборов данных, к которым выполняется обращение из тела определения отчета. Не включает источники данных, которые используются только в верхних или нижних колонтитулах. Недоступна в режиме локального предварительного просмотра. Дополнительные сведения см. в разделе [Ссылки на коллекции DataSources и DataSets (построитель отчетов и службы SSRS)](built-in-collections-datasources-and-datasets-references-report-builder.md).|  
|`DataSources`|Не отображается|`=DataSources("AdventureWorks2012").Type`|Представляет коллекцию источников данных, к которым выполняется обращение из тела отчета. Не включает источники данных, которые используются только в верхних или нижних колонтитулах. Недоступна в режиме локального предварительного просмотра. Дополнительные сведения см. в разделе [Ссылки на коллекции DataSources и DataSets (построитель отчетов и службы SSRS)](built-in-collections-datasources-and-datasets-references-report-builder.md).|  
|`Variables`|`Variables`|`=Variables!CustomTimeStamp.Value`|Представляет коллекцию переменных отчета и групповых переменных. Дополнительные сведения см. в разделе [Ссылки на коллекции переменных отчета и группы (построитель отчетов и службы SSRS)](built-in-collections-report-and-group-variables-references-report-builder.md).|  
|`ReportItems`|Не отображается|`=ReportItems("Textbox1").Value`|Представляет коллекцию текстовых полей для элемента отчета. Эта коллекция может использоваться для суммирования элементов на странице для включения в верхний или нижний колонтитул. Дополнительные сведения см. в разделе [Ссылки на коллекцию ReportItems (построитель отчетов и службы SSRS)](built-in-collections-reportitems-collection-references-report-builder.md).|  
  
##  <a name="using-collection-syntax-in-an-expression"></a><a name="Syntax"></a> Использование в выражениях синтаксиса коллекций  
 Для ссылки на коллекцию из выражения используйте стандартный [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] синтаксис для элемента в коллекции. В следующей таблице показаны примеры синтаксиса коллекций.  
  
|Синтаксис|Пример|  
|------------|-------------|  
|*Набор! ObjectName. свойство*|`=Fields!Sales.Value`|  
|*Набор! ObjectName ("свойство")*|`=Fields!Sales("Value")`|  
|*Collection("ObjectName").Property*|`=Fields("Sales").Value`|  
|*Collection("Member")*|`=User("Language")`|  
|*Collection. Member*|`=User.Language`|  
  
## <a name="see-also"></a>См. также:  
 [Добавление построитель отчетов &#40;выражений и служб SSRS&#41;](add-an-expression-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)  
  
  
