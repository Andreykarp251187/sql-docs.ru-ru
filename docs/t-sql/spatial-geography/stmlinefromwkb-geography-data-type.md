---
title: STMLineFromWKB (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STMLineFromWKB_TSQL
- STMLineFromWKB (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STMLineFromWKB method
ms.assetid: 05ca6d65-4799-4b9a-9672-cfebae95f23e
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 4bd63a65268053f8f494631151bade48c42ef138
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65936650"
---
# <a name="stmlinefromwkb-geography-data-type"></a>STMLineFromWKB (географический тип данных)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает экземпляр **geographyMultiLineString** из WKB-представления открытого геопространственного консорциума (OGC).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STMLineFromWKB ( 'WKB_multilinestring' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *WKB_multilinestring*  
 WKB-представление возвращаемого экземпляра **geographyMultiLineString**. *WKB_multilinestring* — это выражение типа **varbinary(max)** .  
  
 *SRID*  
 Выражение типа **int**, представляющее идентификатор пространственной ссылки (SRID) возвращаемого экземпляра **geographyMultiLineString**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемого значения CLR: **SqlGeography**  
  
 Тип OGC: **MultiLineString**  
  
## <a name="remarks"></a>Remarks  
 Если входные данные имеют неверный формат, метод вызовет исключение **FormatException**.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере метод `STMLineFromWKB()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STMLineFromWKB(0x010500000002000000010200000005000000F4FDD478E9965EC0DD24068195D3474083C0CAA145965EC0508D976E12D3474083C0CAA145965EC04E62105839D44740F4FDD478E9965EC04E62105839D44740F4FDD478E9965EC0DD24068195D34740010200000005000000022B8716D9965EC0C1CAA145B6D34740022B8716D9965EC06ABC749318D447407593180456965EC06ABC749318D447407593180456965EC03333333333D34740022B8716D9965EC0C1CAA145B6D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Статические географические методы OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
