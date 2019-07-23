---
title: Общие сведения о пространственных типах данных | Документация Майкрософт
ms.date: 11/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2abe169f1666a1ce44b96130a52ef8edbc5a788e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048524"
---
# <a name="spatial-data-types-overview"></a>Основные сведения о типах пространственных данных
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  
Существует два типа пространственных данных. Тип данных **geometry** поддерживает планарные или эвклидовы данные (система координат для плоской Земли). Тип данных **geometry** соответствует спецификации "Simple Features for SQL" консорциума OGC версии 1.1.0 и стандарту SQL MM (стандарт ISO).
Кроме того, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает тип данных **geography** , который используется для хранения эллиптических данных, таких как координаты GPS широты и долготы.

##  <a name="objects"></a> Объекты пространственных данных  
Типы данных **geometry** и **geography** поддерживают шестнадцать объектов пространственных данных или типов экземпляров. Однако только одиннадцать из этих типов экземпляров являются *материализуемыми*. Такие экземпляры можно создавать в базе данных и работать с ними. Эти экземпляры наследуют от родительских типов данных некоторые свойства, которые разделяют их на **Points**, **LineStrings, CircularStrings**, **CompoundCurves**, **Polygons**, **CurvePolygons** или несколько экземпляров **geometry** или **geography** в коллекции **GeometryCollection**. Тип**Geography** имеет дополнительный тип экземпляра **FullGlobe**.  

На рисунке ниже изображена иерархия **geometry** , на которой основаны типы данных **geometry** и **geography** . Инстанциируемые типы **geometry** и **geography** выделены синим.  

![geom_hierarchy](../../relational-databases/spatial/media/geom-hierarchy.gif) 

Как показано на рисунке, десятью материализуемыми типами **geometry** и **geography** являются **Point**, **MultiPoint**, **LineString**, **CircularString**, **MultiLineString**, **CompoundCurve**, **Polygon**, **CurvePolygon**, **MultiPolygon**и **GeometryCollection**. Есть один дополнительный тип, допускающий создание экземпляров, для типа данных geography: **FullGlobe**. Типы данных **geometry** и **geography** могут распознавать определенный экземпляр, если он имеет правильный формат, даже в том случае, если он не был определен явно. Например, если определить экземпляр **Point** явно с помощью метода STPointFromText(), то типы данных **geometry** и **geography** будут распознавать экземпляр как **Point**, если входные данные метода имели правильный формат. Если определить такой же экземпляр с помощью метода `STGeomFromText()` , то оба типа данных **geometry** и **geography** будут распознавать экземпляр как **Point**.  

Подтипы для типов geometry и geography делятся на простые типы и типы-коллекции.  Некоторые методы, например `STNumCurves()` , работают только с простыми типами.  

Простые типы:  
-   [Point](../../relational-databases/spatial/point.md)  
-   [LineString](../../relational-databases/spatial/linestring.md)  
-   [CircularString](../../relational-databases/spatial/circularstring.md)  
-   [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)  
-   [Многоугольник](../../relational-databases/spatial/polygon.md)  
-   [CurvePolygon](../../relational-databases/spatial/curvepolygon.md)  

Типы-коллекции:  
-   [MultiPoint](../../relational-databases/spatial/multipoint.md)  
-   [MultiLineString](../../relational-databases/spatial/multilinestring.md)  
-   [MultiPolygon](../../relational-databases/spatial/multipolygon.md)  
-   [GeometryCollection](../../relational-databases/spatial/geometrycollection.md)  

##  <a name="differences"></a> Различия между типами данных geometry и geography  
Два типа пространственных данных часто демонстрируют одинаковое поведение, однако у них имеется ряд ключевых различий в способе хранения и управления данными.  

### <a name="how-connecting-edges-are-defined"></a>Определение границ соединения  
Определяющими данными для типов **LineString** и **Polygon** могут быть только вершины.  Границей соединения между двумя вершинами в типе geometry является прямая линия.  Однако границей соединения между двумя вершинами в типе geography является короткая большая эллиптическая кривая, проложенная между вершинами.  Большой эллипс представляет собой пересечение эллипсоида с плоскостью, проходящей через его центр, а большая эллиптическая кривая представляет собой сегмент кривой на большом эллипсе.  

### <a name="how-circular-arc-segments-are-defined"></a>Определение сегментов дуги  
Сегменты дуги для типов geometry определяются на декартовой координатной плоскости XY (значения Z не учитываются). Сегменты дуги для типов geography определяются сегментами кривой на эталонной сфере. Любую параллель на эталонной сфере можно определить двумя взаимодополняющими дугами, где точки для обеих дуг имеют постоянный угол широты.  

### <a name="measurements-in-spatial-data-types"></a>Измерения в пространственных типах данных  
В планарной модели (или модели плоской Земли) измерение расстояний и площадей проводятся в таких же единицах измерения, в каких представляются координаты. При использовании типа данных **geometry** расстояние между точками (2, 2) и (5, 6) составляет 5 единиц, независимо от используемых единиц.  

В эллиптической модели, или модели круглой Земли, координаты указываются в градусах долготы и широты. Однако длины и площади обычно измеряются в метрах и квадратных метрах, хотя измерения могут зависеть от идентификатора пространственной ссылки (SRID) экземпляра **geography** . Самой распространенной единицей измерения типа данных **geography** является метр.  

### <a name="orientation-of-spatial-data"></a>Ориентация пространственных данных  
В планарной системе ориентация кольца многоугольника является несущественным фактором. Например, многоугольник ((0, 0), (10, 0), (0, 20), (0, 0)) идентичен многоугольнику ((0, 0), (0, 20), (10, 0), (0, 0)). Спецификация «Simple Features for SQL» консорциума OGC не определяет положение кольца, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] его не учитывает.  

В эллиптической модели без указания ориентации многоугольник не определен или является неоднозначным. Например, описывает ли кольцо вокруг экватора северное или южное полушарие? При использовании типа данных **geography** для хранения пространственного экземпляра необходимо указать ориентацию кольца и точно описать расположение экземпляра. Внутренняя часть многоугольника в эллиптической модели определяется правилом левой руки.  

Если уровень совместимости [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] равен 100 или ниже, тип данных **geography** имеет следующие ограничения:  
-   Любой экземпляр **geography** должен лежать в пределах одного полушария. Не допускается сохранение пространственных объектов больше размера полушария.  
-   Любой экземпляр **geography** в представлении консорциума OGC Well-Known Text (WKT) или Well-Known Binary (WKB), порождающий объект больше полушария, приводит к возникновению исключения **ArgumentException**.  
-   Методы типа данных **geography** , требующие указания двух экземпляров **geography** , такие как STIntersection(), STUnion(), STDifference() и STSymDifference(), возвратят NULL, если результаты методов не умещаются в одном полушарии. Метод STBuffer() также возвращает значение NULL, если выходные данные выходят за пределы одного полушария.  

В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]тип **FullGlobe** представляет разновидность Polygon, охватывающую весь земной шар. Объект**FullGlobe** имеет площадь, но не имеет границ и вершин.  

### <a name="outer-and-inner-rings-not-important-in-geography-data-type"></a>Для типа данных `geography` внешнее и внутреннее кольца не важны  
В спецификации "Simple Features for SQL" консорциума OGC обсуждаются внешние и внутренние кольца, но их различие не имеет особого значения для типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** . Любое кольцо многоугольника можно считать внешним кольцом.  

Дополнительные сведения о спецификациях OGC см. в одном из следующих источников:  
-   [Спецификации OGC, простой доступ к функциям, часть 1 — общая архитектура](https://go.microsoft.com/fwlink/?LinkId=93627)  
-   [Спецификации OGC, простой доступ к функциям, часть 2 — параметры SQL](https://go.microsoft.com/fwlink/?LinkId=93628)  

##  <a name="circular"></a> Сегменты дуги  
Три допускающих создание экземпляров типа могут принимать сегменты дуги: **CircularString**, **CompoundCurve** и **CurvePolygon**.  Сегмент дуги определяется тремя точками на двумерной плоскости, при этом третья точка не может совпадать с первой.  

Фигуры A и B являются типичными сегментами дуги. Обратите внимание, что каждая из трех точек лежит на периметре круга.  

Фигуры C и D демонстрируют, как можно определить сегмент линии с помощью сегмента дуги.  Обратите внимание, что для определения сегмента дуги по-прежнему требуются три точки, тогда как обычный сегмент линии можно определить с помощью двух точек.  
Методы, работающие с типами сегментов дуги, для приближения дуги используют сегменты прямой линии. Количество сегментов, используемых для приближения дуги, зависит от длины и кривизны дуги. Значения Z можно сохранять для каждого типа сегмента дуги. Однако методы не используют значения Z в своих вычислениях.  

> [!NOTE]  
> Если для сегментов дуги даются значения Z, они должны совпадать для всех точек сегмента дуги. Только в этом случае они могут быть приняты в качестве ввода. Например: `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` принимается, но `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` не принимается.  

### <a name="linestring-and-circularstring-comparison"></a>Сравнение типов LineString и CircularString  
В следующем примере показано, как сохранить одинаковые равнобедренные треугольники с помощью экземпляра **LineString** и экземпляра **CircularString**:  

```sql
DECLARE @g1 geometry;
DECLARE @g2 geometry;
SET @g1 = geometry::STGeomFromText('LINESTRING(1 1, 5 1, 3 5, 1 1)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(1 1, 3 1, 5 1, 4 3, 3 5, 2 3, 1 1)', 0);
IF @g1.STIsValid() = 1 AND @g2.STIsValid() = 1
  BEGIN
      SELECT @g1.ToString(), @g2.ToString()
      SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length]
  END
```  

Обратите внимание, что экземпляру **CircularString** требуется семь точек для определения треугольника, тогда как экземпляру **LineString** для этого достаточно всего четырех точек. Причиной этого является то, что экземпляр **CircularString** хранит сегменты дуги, а не сегменты линии. Поэтому сторонами треугольника, хранящегося в экземпляре **CircularString** , являются ABC, CDE и EFA, а сторонами треугольника, хранящегося в экземпляре **LineString** , — AC, CE и EA.  

Рассмотрим следующий пример:  

```sql
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
LS LengthCS Length
5.65685...6.28318...
```

Экземпляры **CircularString** используют меньшее число точек для хранения границ кривой и обеспечивают большую точность, чем экземпляры **LineString**. Объекты**CircularString** полезны для хранения круговых границ, например область поиска радиусом в двадцать миль от указанной точки. Объекты**LineString** хорошо подходят для хранения линейных границ, например городского квартала.  

### <a name="linestring-and-compoundcurve-comparison"></a>Сравнение типов LineString и CompoundCurve  
В следующем примере кода показано, как одна и та же фигура сохраняется с помощью экземпляров **LineString** и **CompoundCurve** :

```sql
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');
```

В этих примерах фигура может храниться как экземпляр **LineString** или как экземпляр **CompoundCurve** .  В следующем примере тип **CompoundCurve** используется для хранения среза круговой диаграммы:  

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');  
```  

Экземпляр **CompoundCurve** может хранить сегмент дуги (2 2, 1 3, 0 2) непосредственно, в то время как экземпляру **LineString** пришлось бы преобразовать кривую в несколько сегментов строки меньшего размера.  

### <a name="circularstring-and-compoundcurve-comparison"></a>Сравнение типов CircularString и CompoundCurve  
В следующем примере кода показано, как можно сохранить срезы круговой диаграммы в экземпляре **CircularString** :  

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');
SELECT @g.ToString(), @g.STLength();
```

Для хранения среза круговой диаграммы с помощью экземпляра **CircularString** требуется три точки для каждого сегмента линии.  Если промежуточная точка неизвестна, необходимо либо вычислить ее, либо сдублировать конечную точку сегмента линии, как показано в следующем фрагменте кода:  

```sql
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');
```

Экземпляры**CompoundCurve** позволяют использовать компоненты **LineString** и **CircularString** , поэтому необходимо знать только две точки сегментов линии среза круговой диаграммы.  В этом примере кода показано, как использовать тип **CompoundCurve** для хранения той же фигуры:  
```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');
SELECT @g.ToString(), @g.STLength();
```

### <a name="polygon-and-curvepolygon-comparison"></a>Сравнение типов Polygon и CurvePolygon  
Экземпляры**CurvePolygon** могут использовать экземпляры **CircularString** и **CompoundCurve** instances when defining their exterior и interior rings.  Экземпляры **Polygon** не могут использовать типы сегментов дуги: **CircularString** и **CompoundCurve**.  

## <a name="see-also"></a>См. также:  
- [Пространственные данные (SQL Server)](https://msdn.microsoft.com/library/bb933790.aspx) 
- [Справочник по методам типа данных geometry](https://msdn.microsoft.com/library/bb933973.aspx) 
- [Справочник по методам типа данных geography](https://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e)   
- [STNumCurves (тип данных geometry)](../../t-sql/spatial-geometry/stnumcurves-geometry-data-type.md)   
- [STNumCurves (тип данных geography)](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)   
- [STGeomFromText (тип данных geometry)](../../t-sql/spatial-geometry/stgeomfromtext-geometry-data-type.md)   
- [STGeomFromText (тип данных geography)](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
