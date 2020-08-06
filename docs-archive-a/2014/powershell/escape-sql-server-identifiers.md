---
title: Экранирование идентификаторов SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1821187632aeeea0b7a18bf9c4d51d933e947d43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664277"
---
# <a name="escape-sql-server-identifiers"></a>Применение escape-символов к идентификаторам SQL Server
  Часто можно использовать escape-символ обратной кавычки Windows PowerShell (`) для экранирования символов, применение которых допускается в идентификаторах с разделителями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , но не в именах путей Windows PowerShell. Тем не менее экранирование некоторых символов невозможно. Например, в среде Windows PowerShell нельзя экранировать символ двоеточия (:). Идентификаторы с этим символом должны быть закодированы. Кодировка более надежна, чем экранирование, поскольку действует для всех символов.  
  
## <a name="before-you-begin"></a>Перед началом  
 Символ обратной кавычки (`) обычно расположен на клавише в верхнем левом углу клавиатуры, под клавишей ESC.  
  
## <a name="examples"></a>Примеры  
 Ниже приведен пример экранирования символа #:  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 Это пример экранирования скобок при указании (local) в качестве имени компьютера:  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server идентификаторов в PowerShell](sql-server-identifiers-in-powershell.md)   
 [Поставщик SQL Server PowerShell](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
