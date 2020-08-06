---
title: MultiLineString | Документация Майкрософт
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fdd093d99d055df8e15fc22e3e570e6805e35d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668184"
---
# <a name="multilinestring"></a>MultiLineString
  `MultiLineString`— Это коллекция из нуля или более `geometry` экземпляров или **geographyLineString** .  
  
## <a name="multilinestring-instances"></a>Экземпляры MultiLineString  
 На рисунке ниже приведены примеры экземпляров `MultiLineString`.  
  
 ![Примеры объектов MultiLineString типа geometry](../../database-engine/media/multilinestring.gif "Примеры объектов MultiLineString типа geometry")  
  
 На рисунке представлены:  
  
-   На рисунке 1 показан простой `MultiLineString` экземпляр, граница которого состоит из четырех конечных точек двух `LineString` элементов.  
  
-   Изображение 2 представляет простой экземпляр `MultiLineString`, поскольку пересекаются только конечные точки элементов `LineString`. Граница образована двумя неперекрывающимися конечными точками.  
  
-   Изображение 3 представляет непростой экземпляр `MultiLineString`, поскольку имеется пересечение внутренней части одного из элементов `LineString` этого экземпляра. Границей данного экземпляра `MultiLineString` являются четыре конечные точки.  
  
-   На рисунке 4 представлен отличный от простого незамкнутый экземпляр объекта `MultiLineString`.  
  
-   Изображение 5 представляет простой, незамкнутый экземпляр `MultiLineString`. Он не закрыт, поскольку его `LineStrings` элементы не закрыты. Экземпляр является простым, поскольку внутренние стороны экземпляров `LineStrings` не пересекаются.  
  
-   Изображение 6 представляет простой, замкнутый экземпляр `MultiLineString`. Экземпляр является замкнутым, поскольку все его элементы замкнуты. Экземпляр является простым, поскольку внутренние области его элементов не пересекаются.  
  
### <a name="accepted-instances"></a>Правильные экземпляры  
 Чтобы экземпляр `MultiLineString` был принят, он должен либо быть пустым, либо содержать только принимаемые экземпляры `LineString`. Дополнительные сведения о принятых `LineString` экземплярах см. в разделе [LineString](../spatial/linestring.md). В следующих примерах показаны принятые экземпляры `MultiLineString`.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 Следующий пример формирует исключение `System.FormatException`, так как второй экземпляр `LineString` недействителен.  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Чтобы экземпляр `MultiLineString` был действителен, он должен соответствовать следующим критериям.  
  
1.  Все экземпляры, составляющие экземпляр `MultiLineString`, должны быть действительными экземплярами `LineString`.  
  
2.  Никакие два экземпляра `LineString`, составляющие экземпляр `MultiLineString`, не могут перекрывать сами себя на интервале. Экземпляры `LineString` могут взаимодействовать или соприкасаться только с собой или с другими экземплярами `LineString` в конечном числе точек.  
  
 В следующем примере показаны три действительных экземпляра `MultiLineString` и один экземпляр `MultiLineString`, который недействителен.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 Значение `@g4` является недействительным, так как второй экземпляр `LineString` пересекается с первым экземпляром `LineString` на интервале. Они соприкасаются в бесконечном количестве точек.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается простой экземпляр `geometry``MultiLineString` , содержащий два элемента `LineString` со значением SRID 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 Чтобы создать экземпляр с другим значением SRID, используйте функции `STGeomFromText()` или `STMLineStringFromText()`. Можно также использовать функцию `Parse()` , а затем изменить SRID, как показано в следующем примере.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a>См. также:  
 [STLength (тип данных geometry)](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STIsClosed (тип данных geometry)](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [LineString](../spatial/linestring.md)   
 [Пространственные данные (SQL Server)](../spatial/spatial-data-sql-server.md)  
  
  
