---
title: CircularString | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c701cdc2e8538a5b91093e17714fd9f6508d1c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655577"
---
# <a name="circularstring"></a>CircularString
  Объект `CircularString` — это коллекция, состоящая из нуля или большего количества непрерывных круговых сегментов дуги. Сегмент дуги — это сегмент кривой, определяемый тремя точками на двумерной плоскости; первая точка не может совпадать с третьей. Если все три точки сегмента дуги лежат на одной прямой, сегмент дуги считается линейным сегментом.

> [!IMPORTANT]
>  Подробное описание и примеры новых пространственных функций, появившихся в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , включая `CircularString` подтип, см. в техническом документе [новые функции пространственных данных в SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).

## <a name="circularstring-instances"></a>Экземпляры CircularString
 На следующем рисунке показаны допустимые экземпляры `CircularString`.

 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")

### <a name="accepted-instances"></a>Правильные экземпляры
 `CircularString`Экземпляр принимает значение, если он пуст или содержит нечетное число точек, n, где n > 1. Следующие экземпляры `CircularString` правильные.

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';
```

 Пример `@g3` показывает, что экземпляр `CircularString` может быть правильным, но недопустимым. Следующее объявление экземпляра CircularString неверно. Это объявление вызывает исключение `System.FormatException`.

```sql
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';
```

### <a name="valid-instances"></a>Допустимые экземпляры
 Допустимый экземпляр `CircularString` должен быть пуст или иметь следующие атрибуты:

-   Он должен содержать хотя бы один сегмент дуги (то есть не менее трех точек).

-   Последняя конечная точка каждого из отрезков дуги в последовательности, кроме последнего, должна совпадать с первой конечной точкой следующего сегмента в последовательности.

-   Количество точек должно быть нечетным.

-   Он не должен перекрываться собой.

-   Хотя экземпляры `CircularString` могут содержать линейные сегменты, эти линейные сегменты должны определяться тремя лежащими на одной прямой точками.

 В следующем примере показаны допустимые экземпляры `CircularString`.

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();
```

 Для определения окружности экземпляр `CircularString` должен содержать как минимум два сегмента дуги. Для определения окружности экземпляр `CircularString` не может содержать один сегмент дуги (например, (1 1, 3 1, 1 1)). Для определения окружности используйте (1 1, 2 2, 3 1, 2 0, 1 1).

 В следующем примере показаны недопустимые экземпляры CircularString.

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

### <a name="instances-with-collinear-points"></a>Экземпляры с точками, лежащими на прямой
 Сегмент дуги будет считаться линейным сегментом в следующих случаях.

-   Когда все три точки лежат на одной прямой (например, (1 3, 4 4, 7 5)).

-   Когда первая и средняя точки совпадают, а третья точка отличается от них (например, (1 3, 1 3, 7 5)).

-   Когда средняя и последняя точки совпадают, а первая точка отличается от них (например, (1 3, 4 4, 4 4)).

## <a name="examples"></a>Примеры

### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a>A. Создание экземпляра Geometry с пустым экземпляром CircularString
 В этом примере показано, как создать пустой экземпляр `CircularString`:

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');
```

### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a>Б. Создание экземпляра Geometry с экземпляром CircularString, содержащим один сегмент дуги
 В следующем примере показывается создание экземпляра `CircularString` с одним сегментом дуги (полукруга):

```sql
DECLARE @g geometry;
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);
SELECT @g.ToString();
```

### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a>В. Создание экземпляра Geometry с помощью экземпляра CircularString с несколькими сегментами дуги
 В следующем примере показывается создание экземпляра `CircularString` с несколькими сегментами дуги (окружности):

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```

 Выводятся следующие результаты.

```
Circumference = 6.28319
```

 Сравните вывод, получаемый при использовании `LineString` вместо `CircularString`:

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));
```

 Выводятся следующие результаты.

```
Perimeter = 5.65685
```

 Обратите внимание, что значение для этого `CircularString` примера — близкое к 2&#x03c0; (2 * PI), то есть фактическая длина окружности.

### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a>Г. Объявление и создание экземпляра Geometry с экземпляром CircularString в одной инструкции
 В этом фрагменте кода показывается объявление и создание экземпляра `geometry` с экземпляром `CircularString` в одной инструкции:

```sql
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';
```

### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a>Д. Создание экземпляра Geography с экземпляром CircularString
 В следующем примере показывается объявление и создание экземпляра `geography` с экземпляром `CircularString`:

```sql
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';
```

### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a>Е. Создание экземпляра Geometry с экземпляром CircularString, представляющим прямую
 В следующем примере показывается создание экземпляра `CircularString`, представляющего прямую:

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);
```

## <a name="see-also"></a>См. также:
 [Общие сведения о типах пространственных данных](spatial-data-types-overview.md) . [CompoundCurve](compoundcurve.md) [MakeValid &#40;тип данных geography&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [MakeValid &#40;тип данных geometry&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [STIsValid &#40;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) тип данных geometry&#41;STIsValid &#40;[Geography](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) тип данных&#41;STLength &#40;тип данных geometry [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [&#41;STStartPoint &#40;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) геометрическая тип данных&#41;STEndpoint &#40;тип данных geometry [&#41;STPointN &#40;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [тип данных](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [LineString](linestring.md) Geometry [&#41;STNumPoints &#40;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STPointN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)


