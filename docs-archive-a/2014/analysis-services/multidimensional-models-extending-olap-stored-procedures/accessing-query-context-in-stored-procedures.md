---
title: Доступ к контексту запроса в хранимых процедурах | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9da8ddb223ed03c0208fe524ea5cd7195a039c97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727437"
---
# <a name="accessing-query-context-in-stored-procedures"></a>Доступ к контексту запросов в хранимых процедурах
  Контекст выполнения хранимой процедуры доступен в рамках кода хранимой процедуры как объект `Context` модели объектов сервера ADOMD.NET. Этот контекст доступен только для чтения и не может быть изменен хранимой процедурой. На этом объекте доступны следующие свойства.  
  
|Свойство|Type|Описание|  
|--------------|----------|-----------------|  
|**CurrentCube**|Куб|Куб для текущего контекста запросов.|  
|**CurrentDatabaseName**|Строка|Идентификатор текущей базы данных.|  
|**CurrentConnection**|Соединение|Ссылка на объект подключения в текущем контексте.|  
|**Успех**|Целое число|Номера прохода для текущего контекста.|  
  
 Объект `Context` существует, когда модель объектов многомерных выражений используется в хранимой процедуре. Он не доступен, когда модель объектов многомерных выражений используется на клиенте. Объект `Context` не передается явным образом хранимой процедуре и не возвращается ею. Он доступен во время выполнения хранимой процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками многомерной модели](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Определение хранимых процедур](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
