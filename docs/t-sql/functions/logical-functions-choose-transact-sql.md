---
title: CHOOSE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CHOOSE
- CHOOSE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CHOOSE function
ms.assetid: 1c382c83-7500-4bae-bbdc-c1dbebd3d83f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 07eb130323be8fe507e574d5cca85f5105091e1b
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65949177"
---
# <a name="logical-functions---choose-transact-sql"></a>Логические функции — CHOOSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает элемент по указанному индексу из списка значений в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CHOOSE ( index, val_1, val_2 [, val_n ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *index*  
 Целочисленное выражение, которое представляет отсчитываемый от 1 индекс в списке элементов, следующих за ним.  
  
 Если указанное значение индекса имеет числовой тип, отличный от типа **int**, то значение неявно преобразуется в целое. Если значение индекса выходит за границы массива значений, то инструкция CHOOSE возвращает значение NULL.  
  
 *val_1 ... val_n*  
 Список значений любого типа данных с разделителями-запятыми.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает тип данных с наивысшим приоритетом из переданного функции набора типов. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Инструкция CHOOSE действует подобно индексу массива, где массив состоит из следующих за аргументом индекса аргументов. Аргумент индекса определяет, какие из следующих за ним значений будут возвращены.  
  
## <a name="examples"></a>Примеры  

### <a name="a-simple-choose-example"></a>A. Простой пример функции CHOOSE

 В следующем примере возвращается третий элемент из списка указанных значений.  
 
```  
SELECT CHOOSE ( 3, 'Manager', 'Director', 'Developer', 'Tester' ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
-------------  
Developer  
  
(1 row(s) affected)  
```  

### <a name="b-simple-choose-example-based-on-column"></a>Б. Простой пример функции CHOOSE на основе столбца

 В следующем примере возвращается простая символьная строка на основании значения в столбце `ProductCategoryID`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductCategoryID, CHOOSE (ProductCategoryID, 'A','B','C','D','E') AS Expression1  
FROM Production.ProductCategory;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
ProductCategoryID Expression1  
----------------- -----------  
3                 C  
1                 A  
2                 B  
4                 D  
  
(4 row(s) affected)  
  
```  

### <a name="c-choose-in-combination-with-month"></a>В. CHOOSE в сочетании с MONTH
  
 В следующем примере возвращается время года, в котором сотрудник был принят на работу. Функция MONTH используется, чтобы вернуть значение месяца из столбца `HireDate`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT JobTitle, HireDate, CHOOSE(MONTH(HireDate),'Winter','Winter', 'Spring','Spring','Spring','Summer','Summer',   
                                                  'Summer','Autumn','Autumn','Autumn','Winter') AS Quarter_Hired  
FROM HumanResources.Employee  
WHERE  YEAR(HireDate) > 2005  
ORDER BY YEAR(HireDate);  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
JobTitle                                           HireDate   Quarter_Hired  
-------------------------------------------------- ---------- -------------  
Sales Representative                               2006-11-01 Autumn  
European Sales Manager                             2006-05-18 Spring  
Sales Representative                               2006-07-01 Summer  
Sales Representative                               2006-07-01 Summer  
Sales Representative                               2007-07-01 Summer  
Pacific Sales Manager                              2007-04-15 Spring  
Sales Representative                               2007-07-01 Summer  
  
```  
  
## <a name="see-also"></a>См. также:  
 [IIF (Transact-SQL)](../../t-sql/functions/logical-functions-iif-transact-sql.md)  
  
  
