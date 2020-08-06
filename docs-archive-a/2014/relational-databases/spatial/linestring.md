---
title: LineString | Документация Майкрософт
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- LineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: e50d0b86-8b31-4285-be71-ad05c7712cbd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5a0f77959cfe4492eca6c38951ba2868452d41ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668192"
---
# <a name="linestring"></a>LineString
  `LineString` является одномерным объектом, представляющим последовательность точек и соединяющих их линейных сегментов.

## <a name="linestring-instances"></a>Экземпляры LineString
 На рисунке ниже приведены примеры экземпляров `LineString`.

 ![Примеры объектов LineString типа geometry](../../database-engine/media/linestring.gif "Примеры объектов LineString типа geometry")

 На рисунке представлены:

-   на рисунке 1 представлен простой незамкнутый экземпляр объекта `LineString`;

-   на рисунке 2 представлен отличный от простого незамкнутый экземпляр объекта `LineString`;

-   на рисунке 3 продемонстрирован простой замкнутый экземпляр объекта `LineString`, представляющий собой кольцо;

-   на рисунке 4 продемонстрирован замкнутый непростой экземпляр объекта `LineString`, не являющийся кольцом.

### <a name="accepted-instances"></a>Принимаемые экземпляры
 Принятые экземпляры `LineString` могут быть введены в переменную геометрии, но они могут быть недействительными экземплярами `LineString`. Для принятия экземпляра `LineString` должны соблюдаться следующие критерии. Экземпляр должен быть сформирован по меньшей мере двумя точками или же должен быть пустым. Следующие экземпляры LineString допустимы.

```
DECLARE @g1 geometry = 'LINESTRING EMPTY';
DECLARE @g2 geometry = 'LINESTRING(1 1,2 3,4 8, -6 3)';
DECLARE @g3 geometry = 'LINESTRING(1 1, 1 1)';
```

 `@g3` показывает, что, хотя экземпляр `LineString` допустим, он недействителен.

 Следующий экземпляр `LineString` недопустим. Он выдаст исключение `System.FormatException`.

```
DECLARE @g geometry = 'LINESTRING(1 1)';
```

### <a name="valid-instances"></a>Допустимые экземпляры
 Чтобы экземпляр `LineString` был действителен, он должен соответствовать следующим критериям.

1.  Экземпляр `LineString` должен быть принят.

2.  Если экземпляр `LineString` не является пустым, он должен содержать по меньшей мере две различные точки.

3.  Экземпляр `LineString` не может перекрывать сам себя на интервале из двух или более последовательных точек.

 Следующие экземпляры `LineString` являются действительными.

```
DECLARE @g1 geometry= 'LINESTRING EMPTY';
DECLARE @g2 geometry= 'LINESTRING(1 1, 3 3)';
DECLARE @g3 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0)';
DECLARE @g4 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();

```

 Следующие экземпляры `LineString` не являются действительными.

```
DECLARE @g1 geometry = 'LINESTRING(1 4, 3 4, 2 4, 2 0)';
DECLARE @g2 geometry = 'LINESTRING(1 1, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

> [!WARNING]
>  Определение пересечений `LineString` основано на расчетах с плавающей запятой, которые не являются точными.

## <a name="examples"></a>Примеры
 В следующем примере показано, как создать экземпляр `geometry``LineString` с тремя точками и значением SRID, равным 0:

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1, 2 4, 3 9)', 0);
```

 Каждая точка экземпляра `LineString` может содержать значения Z (уровень) и M (мера). В данном примере значения М добавляются к экземпляру `LineString` , созданному в примере выше. M и Z могут принимать значения NULL.

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1 NULL 0, 2 4 NULL 12.3, 3 9 NULL 24.5)', 0);
```

 В следующем примере показано, как создать экземпляр `geometry LineString` с двумя одинаковыми точками. Вызов `IsValid` указывает, что экземпляр `LineString` не является действительным, а вызов `MakeValid` преобразует экземпляр `LineString` в `Point`.

```sql
DECLARE @g geometry
SET @g = geometry::STGeomFromText('LINESTRING(1 3, 1 3)',0);
IF @g.STIsValid() = 1
  BEGIN
     SELECT @g.ToString() + ' is a valid LineString.';  
  END
ELSE
  BEGIN
     SELECT @g.ToString() + ' is not a valid LineString.';
     SET @g = @g.MakeValid();
     SELECT @g.ToString() + ' is a valid Point.';  
  END

```

 Вышеприведенный фрагмент кода вернет следующее:

```
LINESTRING(1 3, 1 3) is not a valid LineString
POINT(1 3) is a valid Point.
```

## <a name="see-also"></a>См. также:
 [STLength &#40;тип данных geometry&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;тип данных geometry&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;тип данных geometry&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) тип данных geometry&#41;STNumPoints [&#40;геометрическая](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) тип данных&#41;STIsRing [&#40;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) Geometry Data Type&#41;[STIsClosed &#40;тип данных geometry&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;тип данных geometry&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [пространственные данные &#40;](../spatial/spatial-data-sql-server.md) SQL Server


