---
title: AsTextZM (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsTextZM_TSQL
- AsTextZM
- AsTextZM (geometry Data Type)
- AsTextZM_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM (geometry Data Type)
ms.assetid: 08ac8aa0-aff7-4b22-87e0-1a1d55dcbc04
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 437859afd1f21cba5c47f93c86173d71e3ae89d9
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68027638"
---
# <a name="astextzm-geometry-data-type"></a>AsTextZM (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает представление WKT консорциума OGC экземпляра geometry, дополненного всеми значениями **Z** (высота) и **M** (мера) этого экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **nvarchar(max)**  
  
 Тип возвращаемых данных CLR: **SqlChars**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере создается экземпляр `Point`, содержащий значения **Z** (высота) и **M** (мера). Метод `STAsText()` выбирает значения WKT (1 2); метод `AsTextZM()` выбирает те же самые значения WKT, а также возвращает значения для **Z** и **M** (1 2 3 4).  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [M (тип данных geometry)](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [Z (тип данных geometry)](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  

