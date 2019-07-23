---
title: NULLIF (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- NULLIF
- NULLIF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], equivalent expressions
- expressions [SQL Server], null values
- NULLIF function
- equivalent expressions [SQL Server]
ms.assetid: 44c7b67e-74c7-4bb9-93a4-7a3016bd2feb
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8876fe591eadb0946b3f54cdf52644b39c040089
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68121983"
---
# <a name="nullif-transact-sql"></a>Функция NULLIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает значение NULL, если два указанных выражения равны. Например, `SELECT NULLIF(4,4) AS Same, NULLIF(5,7) AS Different;` возвращает значение NULL для первого столбца (4 и 4), так как два входных значения одинаковы. Для второго столбца возвращается первое значение (5), так как два входных значения различаются. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
NULLIF ( expression , expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое скалярное [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает значение того же типа, что и у первого выражения *expression*.  
  
 Если выражения не равны, функция NULLIF возвращает первое выражение *expression*. Если они равны, функция NULLIF возвращает значение NULL с типом, соответствующим типу первого выражения *expression*.  
  
## <a name="remarks"></a>Remarks  
 Функция NULLIF аналогична поисковому выражению CASE, в котором два выражения равны, а результирующее выражение равно NULL.  
  
 В функции NULLIF не рекомендуется использовать такие зависимые от времени функции, как RAND(). Это может приводить к тому, что функция будет вычисляться дважды с возвратом различных результатов для каждого из вызовов.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-budget-amounts-that-have-not-changed"></a>A. Возвращение неизменившихся сумм бюджета  
 В следующем примере производится создание таблицы `budgets` для отображения отдела (`dept`), его текущего (`current_year`) и предыдущего бюджета (`previous_year`). Для текущего года для отдела, бюджет которого не изменился с предыдущего года, выводится значение `NULL`, а значение `0` указывается для указания того, что бюджет еще не определен. Для получения среднего значения только для тех отделов, которым уже назначен бюджет и включения значения прошлогоднего бюджета (используется значение `previous_year`, если `current_year` равен `NULL`), используются функции `NULLIF` и `COALESCE`.  
  
```sql  
CREATE TABLE dbo.budgets  
(  
   dept            tinyint   IDENTITY,  
   current_year      decimal   NULL,  
   previous_year   decimal   NULL  
);  
INSERT budgets VALUES(100000, 150000);  
INSERT budgets VALUES(NULL, 300000);  
INSERT budgets VALUES(0, 100000);  
INSERT budgets VALUES(NULL, 150000);  
INSERT budgets VALUES(300000, 250000);  
GO    
SET NOCOUNT OFF;  
SELECT AVG(NULLIF(COALESCE(current_year,  
   previous_year), 0.00)) AS 'Average Budget'  
FROM budgets;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Average Budget  
 --------------  
 212500.000000  
 (1 row(s) affected)
 ```  
  
### <a name="b-comparing-nullif-and-case"></a>Б. Сравнение функции NULLIF и выражения CASE  
 Для демонстрации схожести функции `NULLIF` и выражения `CASE` в следующих запросах вычисляется, равны ли значения столбцов `MakeFlag` и `FinishedGoodsFlag`. В первом запросе используется функция `NULLIF`. Во втором — выражение `CASE`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,   
   NULLIF(MakeFlag,FinishedGoodsFlag)AS 'Null if Equal'  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,'Null if Equal' =  
   CASE  
       WHEN MakeFlag = FinishedGoodsFlag THEN NULL  
       ELSE MakeFlag  
   END  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
```  

### <a name="c-returning-budget-amounts-that-contain-no-data"></a>В. Возвращение сумм бюджета, не содержащих данных  
 В приведенном ниже примере создается таблица `budgets`, загружаются данные, а затем с помощью `NULLIF` возвращается значение NULL, если ни в `current_year`, ни в `previous_year` нет данных.  
  
```sql  
CREATE TABLE budgets (  
   dept           tinyint,  
   current_year   decimal(10,2),  
   previous_year  decimal(10,2)  
);  
  
INSERT INTO budgets VALUES(1, 100000, 150000);  
INSERT INTO budgets VALUES(2, NULL, 300000);  
INSERT INTO budgets VALUES(3, 0, 100000);  
INSERT INTO budgets VALUES(4, NULL, 150000);  
INSERT INTO budgets VALUES(5, 300000, 300000);  
  
SELECT dept, NULLIF(current_year,  
   previous_year) AS LastBudget  
FROM budgets;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 dept   LastBudget  
 ----   -----------  
 1      100000.00  
 2      null 
 3      0.00  
 4      null  
 5      null
 ```  
  
## <a name="see-also"></a>См. также:  
 [CASE (Transact-SQL)](../../t-sql/language-elements/case-transact-sql.md)   
 [decimal и numeric (Transact-SQL)](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

