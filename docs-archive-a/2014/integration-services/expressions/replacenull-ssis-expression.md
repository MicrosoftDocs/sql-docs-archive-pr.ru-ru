---
title: REPLACENULL (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f10bb6ef6102076fe7b1cc236461e2358ad96372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732821"
---
# <a name="replacenull-ssis-expression"></a>REPLACENULL (выражение служб SSIS)
  Возвращает значение второго параметра выражения, если значение первого параметра равно NULL. В противном случае возвращает значение первого выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a>Аргументы  
 *выражение 1*  
 Результат этого выражения проверяется на соответствие значению NULL.  
  
 *выражение 2*  
 Результат этого выражения возвращается, если значением первого выражения является NULL.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
  
-   Длина *expression 2* может быть нулевой.  
  
-   Функция REPLACENULL возвращает NULL, если значение любого из аргументов равно NULL.  
  
-   Столбцы типа BLOB (DT_TEXT, DT_NTEXT, DT_IMAGE) не поддерживаются ни для одного из параметров.  
  
-   Предполагается, что два выражения будут иметь одинаковый возвращаемый тип. Если это не так, то функция попытается преобразовать второе выражение в возвращаемый тип первого выражения, что может привести к возникновению ошибки, если типы данных несовместимы.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В следующем примере все значения NULL в столбце базы данных заменяются строкой (1900-01-01). Эта функция применяется сугубо в стандартных шаблонах производных столбцов, где значения NULL необходимо заменить другими значениями.  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]  
>  Следующий пример демонстрирует, как это было выполнено в [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? "1900-01-01" : MyColumn)   
```  
  
  
