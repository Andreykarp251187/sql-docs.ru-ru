---
title: ShortestLineTo (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ShortestLineTo_TSQL
- ShortestLineTo
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geography)
ms.assetid: 9d7c9885-5d1b-49ae-af31-5ef9fb8acaba
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: c136de737c3cd3eec886ff2e5ce470ab4d67296e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936266"
---
# <a name="shortestlineto-geography-data-type"></a>ShortestLineTo (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает экземпляр **LineString** с двумя точками, представляющий кратчайшее расстояние между двумя экземплярами **geography**. Длина возвращаемого экземпляра **LineString** равна расстоянию между двумя экземплярами **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ShortestLineTo ( geography_other )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_other*  
 Указывает второй экземпляр **geography**, кратчайшее расстояние до которого пытается определить вызывающий экземпляр **geography**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемого значения CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает экземпляр **LineString** с двумя конечными точками, лежащими на границах двух сравниваемых непересекающихся экземпляров **geography**. Длина возвращаемого экземпляра **LineString** равна кратчайшему расстоянию между двумя экземплярами **geography**. Пустой экземпляр **LineString** возвращается, когда два экземпляра **geography** пересекаются друг с другом.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. Вызов функции ShortestLineTo() для непересекающихся экземпляров  
 В этом примере ищется кратчайшее расстояние между экземпляром `CircularString` и экземпляром `LineString` и возвращается экземпляр `LineString`, соединяющий эти две точки:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>Б. Вызов функции ShortestLineTo() для пересекающихся экземпляров  
 Этот пример возвращает пустой экземпляр `LineString`, поскольку экземпляр `LineString` пересекает экземпляр `CircularString`:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.348 47.649, -122.681 47.655)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
``` 
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
