---
title: Типы данных и поведение при выполнении групповой загрузки XML (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b03423f3bb88166d0d9ce5b0df450d4455e7ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665969"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Типы данных и массовая загрузка XML (SQLXML 4.0)
  Типы данных, заданные в схеме сопоставления (тип XSD, XDR и `sql:datatype`), как правило, пропускаются, за исключением следующих случаев.  
  
 В XSD.  
  
-   Если данные имеют тип `dateTime` или `time`, необходимо задать `sql:datatype`, поскольку в ходе массовой загрузки XML выполняется преобразование данных перед их отправкой в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   При выполнении групповой загрузки в столбец `uniqueidentifier` типа в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , а значение XSD — это идентификатор GUID, включающий фигурные скобки ({и}), необходимо указать **SQL: datatype = "uniqueidentifier"** , чтобы удалить фигурные скобки перед вставкой значения в столбец. Если атрибут `sql:datatype` не задан, то значение передается вместе с фигурными скобками и вставка завершается ошибкой.  
  
 Дополнительные сведения о см `sql:datatype` . [в разделе приведение типов данных и аннотация SQL: datatype &#40;&#41;SQLXML 4,0 ](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 В XDR:  
  
-   Если `dt:type` имеет тип `datetime`, `time`, `dateTime.tz` или `time.tz`, необходимо задать типы данных `dt:type` и `sql:datatype`, поскольку при массовой загрузке XML выполняется преобразование данных перед отправкой в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Если XML-данные имеют тип `uuid` , `sql:datatype` необходимо указать. **DT: Type = "UUID"** также требуется, если только данные не являются строковыми данными. Если атрибут `dt:uuid` не задан, то при массовой загрузке XML строки с фигурными скобками принимаются (фигурные скобки при необходимости удаляются).  
  
-   Если данные XML имеют тип `bin.base64` или `bin.hex`, необходимо указать тип данных XML с атрибутом `dt:type`. В таком случае при массовой загрузке XML данные загружаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в шестнадцатеричном представлении.  
  
  
