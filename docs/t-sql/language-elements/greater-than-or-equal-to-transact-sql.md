---
title: '&gt;= (больше или равно) (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Greater
- '>='
- '>= (Greater Than or Equal To)'
- Equal To
- '>=_TSQL'
- Greater Than
- Equal
dev_langs:
- TSQL
helpviewer_keywords:
- greater than or equal to operator (>=)
- '>= (greater than or equal to operator)'
ms.assetid: 641ee28d-7536-46dd-a48a-6c63c2d59278
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 721a7795f027e3641e3a8f5ab2c740e17c9cff57
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982285"
---
# <a name="gt-greater-than-or-equal-to-transact-sql"></a>&gt;= (больше или равно) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Сравнивает два выражения на верность того, больше или равно одно выражение другому (оператор сравнения).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое выражение [expression](../../t-sql/language-elements/expressions-transact-sql.md). Оба выражения должны иметь типы данных, допускающие неявное преобразование. Преобразование зависит от правил [приоритетов типов данных](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Типы результата  
 Логическое значение  
  
## <a name="remarks"></a>Примечания  
 При сравнении выражений, чьи значения отличны от NULL, результат будет равен TRUE, если левый операнд имеет значение, большее или равное значению правого операнда; иначе результат равен FALSE.  
  
 В отличие от оператора сравнения = (равенство) результат сравнения >= двух значений, равных NULL, не зависит от свойства ANSI_NULLS.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using--in-a-simple-query"></a>A. Использование >= в простом запросе  
 В следующем примере возвращаются все строки из таблицы `HumanResources.Department`, содержащие в столбце `DepartmentID` значение, которое больше или равно 13.  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID >= 13  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
13           Quality Assurance  
14           Facilities and Maintenance  
15           Shipping and Receiving  
16           Executive  
  
(4 row(s) affected)  
  
```  
  
## <a name="see-also"></a>См. также  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [= (равно) (Transact-SQL)](../../t-sql/language-elements/equals-transact-sql.md)   
 [> (больше) (Transact-SQL)](../../t-sql/language-elements/greater-than-transact-sql.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
