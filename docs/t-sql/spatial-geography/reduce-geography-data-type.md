---
title: Reduce (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs:
- TSQL
helpviewer_keywords:
- Reduce method
ms.assetid: c5dfa8c1-6764-41d8-9150-f3cb30633d3e
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: b89d42d050c32f10bac8c8796a4bfa4dd9355ba0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65935794"
---
# <a name="reduce-geography-data-type-"></a>Reduce (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает приближение заданного экземпляра **geography**, полученное путем применения алгоритма Дугласа-Пекера к экземпляру с заданной погрешностью.  
  
 Этот метод типа данных **geography** поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Аргументы  
  
|||  
|-|-|  
|Термин|Определение|  
|*tolerance*|Значение типа **float**. Аргумент *tolerance* представляет собой допуск, который должен быть введен в алгоритм Дугласа-Пекера. *tolerance* должен быть положительным числом.|  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемого значения CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Для типов коллекции этот алгоритм работает независимо для каждого экземпляра **geography**, содержащегося в экземпляре. Этот алгоритм не изменяет экземпляры **Point**.  
  
 Этот метод выполнит попытку сохранения конечных точек экземпляров **LineString**, но при этом может произойти ошибка для сохранения действительного результата.  
  
 Если `Reduce()` вызывается с отрицательным значением, то будет вызвано исключение **ArgumentException**. Отклонения, используемые в функции `Reduce()`, должны быть положительными.  
  
 Алгоритм Дугласа-Пекера применяется для каждой кривой или кольца в экземпляре **geography** путем удаления всех точек за исключением начальной и конечной точки. Каждая удаленная точка затем добавляется обратно, начиная с самой удаленной точки, пока не останется точек более чем в *tolerance* от результата. После этого результат преобразуется в допустимый при необходимости, поскольку гарантируется получение допустимого результата.  
  
 В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] этот метод расширен для включения экземпляров **FullGlobe**.  
  
 Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и используется метод `Reduce()` для упрощения этого экземпляра.  
  
```  
DECLARE @g geography = 'LineString(120 45, 120.1 45.1, 199.9 45.2, 120 46)'  
SELECT @g.Reduce(10000).ToString()  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
