---
title: VAR (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- VAR
- VAR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statistical variances
- expressions [SQL Server], statistical variance
- VAR function [Transact-SQL]
ms.assetid: 71dfc339-16c8-42f9-8555-ad45400f7f9b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4cbee19e0b2f2b176663b76b565285eab167c18d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65946310"
---
# <a name="var-transact-sql"></a>VAR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает статистическую дисперсию всех значений в указанном выражении. За функцией может следовать [предложение OVER](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```    
-- Aggregate Function Syntax   
VAR ( [ ALL | DISTINCT ] expression )  
  
-- Analytic Function Syntax  
VAR ([ ALL ] expression) OVER ( [ partition_by_clause ] order_by_clause)  
```  
  
## <a name="arguments"></a>Аргументы  
 **ALL**  
 Применяет функцию ко всем значениям. ALL является параметром по умолчанию.  
  
 DISTINCT  
 Указывает, что учитывается каждое уникальное значение.  
  
 *expression*  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) категории точного числового или приблизительного числового типа данных, за исключением типа данных **bit**. Агрегатные функции и вложенные запросы не допускаются.  
  
 OVER **(** [ _partition\_by\_clause_ ] _order\_by\_clause_ **)**  
 *partition_by_clause* делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция. Если этот параметр не указан, функция обрабатывает все строки результирующего набора запроса как отдельные группы. _order\_by\_clause_ определяет логический порядок, в котором выполняется операция. _order\_by\_clause_ — это обязательный элемент. Дополнительные сведения см. в статье [Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **float**  
  
## <a name="remarks"></a>Remarks  
 Если в инструкции SELECT функция VAR используется для всех элементов, то при вычислении учитывается каждое значение результирующего набора. Функцию VAR можно использовать только для числовых столбцов. Значения NULL пропускаются.  
  
 VAR — это детерминированная функция, если она используется без предложений OVER и ORDER BY. Она не детерминирована при использовании с предложениями OVER и ORDER BY. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-var"></a>A. Использование функции VAR  
 В следующем примере возвращается дисперсия для заполнения всех значений премии в таблице `SalesPerson` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT VAR(Bonus)  
FROM Sales.SalesPerson;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-var"></a>Б. Использование функции VAR  
 В приведенном ниже примере возвращается статистическая дисперсия для значений квот на продажу в таблице `dbo.FactSalesQuota`. Первый столбец содержит дисперсию всех уникальных значений, а второй — дисперсию всех значений, включая повторяющиеся.  
  
```  
-- Uses AdventureWorks  
  
SELECT VAR(DISTINCT SalesAmountQuota)AS Distinct_Values, VAR(SalesAmountQuota) AS All_Values  
FROM dbo.FactSalesQuota;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Distinct_Values   All_Values
----------------  ----------------
159180469909.18   158762853821.10
 ```  
  
### <a name="c-using-var-with-over"></a>В. Использование функции VAR с предложением OVER  
 В приведенном ниже примере возвращается статистическая дисперсия для значений квот на продажу в каждом квартале календарного года. Обратите внимание на то, что ORDER BY в предложении OVER упорядочивает статистическую дисперсию, а ORDER BY в инструкции SELECT упорядочивает результирующий набор.  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear AS Year, CalendarQuarter AS Quarter, SalesAmountQuota AS SalesQuota,  
       VAR(SalesAmountQuota) OVER (ORDER BY CalendarYear, CalendarQuarter) AS Variance  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear = 2002  
ORDER BY CalendarQuarter;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Year  Quarter  SalesQuota              Variance
----  -------  ----------------------  -------------------
2002  1         91000.0000             null
2002  2        140000.0000             1200500000.00
2002  3         70000.0000             1290333333.33
2002  4        154000.0000             1580250000.00
 ```  
  
## <a name="see-also"></a>См. также:  
 [Агрегатные функции (Transact-SQL)](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md)  
  
  

