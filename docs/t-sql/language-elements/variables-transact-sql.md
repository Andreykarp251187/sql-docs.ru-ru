---
title: Переменные (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f372ae86-a003-40af-92de-fa52e3eea13f
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab0a3bff6159d098ce8a53631e4f4da49f81fba9
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980158"
---
# <a name="variables-transact-sql"></a>Переменные (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Локальная переменная Transact-SQL представляет собой объект, содержащий одно значение определенного типа. Переменные обычно используются в пакетах и скриптах: 

* в качестве счетчика цикла;
* для хранения значения, которое необходимо проверить инструкцией управления потоком;
* для хранения значения, возвращенного функцией или хранимой процедурой.

> [!NOTE]
> Имена некоторых системных функций Transact-SQL начинаются с двух символов *@* (\@\@). Хотя в предыдущих версиях сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \@\@функции называются глобальными переменными, они не являются переменными и используются иначе. \@\@функции являются системными, и использование их синтаксиса соответствует правилам вызова функций.

Следующий скрипт создает небольшую тестовую таблицу из 26 строк. Переменная используется в скрипте в качестве: 

* счетчика цикла для управления количеством вставляемых строк;
* значения, вставляемого в столбец целочисленного типа;
* аргумента функции, формирующей строку, которая вставляется в столбец символьного типа:  

```sql
-- Create the table.
CREATE TABLE TestTable (cola int, colb char(3));
GO
SET NOCOUNT ON;
GO
-- Declare the variable to be used.
DECLARE @MyCounter int;

-- Initialize the variable.
SET @MyCounter = 0;

-- Test the variable to see if the loop is finished.
WHILE (@MyCounter < 26)
BEGIN;
   -- Insert a row into the table.
   INSERT INTO TestTable VALUES
       -- Use the variable to provide the integer value
       -- for cola. Also use it to generate a unique letter
       -- for each row. Use the ASCII function to get the
       -- integer value of 'a'. Add @MyCounter. Use CHAR to
       -- convert the sum back to the character @MyCounter
       -- characters after 'a'.
       (@MyCounter,
        CHAR( ( @MyCounter + ASCII('a') ) )
       );
   -- Increment the variable to count this iteration
   -- of the loop.
   SET @MyCounter = @MyCounter + 1;
END;
GO
SET NOCOUNT OFF;
GO
-- View the data.
SELECT cola, colb
FROM TestTable;
GO
DROP TABLE TestTable;
GO
```

## <a name="declaring-a-transact-sql-variable"></a>Объявление переменных в языке Transact-SQL
Инструкция DECLARE инициализирует переменную Transact-SQL следующим образом: 
* Назначение имени. Первым символом имени должен быть одиночный символ \@.
* Назначение длины и типа данных, определяемого системой или пользователем. Для числовых переменных задаются также точность и масштаб. Для переменных типа XML может быть дополнительно задана коллекция схем.
* Присваивает созданной переменной значение NULL.

Например, следующая инструкция **DECLARE** создает локальную переменную **\@mycounter** типа int.  
```sql
DECLARE @MyCounter int;
```
Инструкция DECLARE позволяет объявить несколько переменных одинакового или разного типов через запятую.

Например, следующая инструкция **DECLARE** создает три локальные переменные с именем **\@LastName**, **\@FirstName** и **\@StateProvince**, присваивая каждой из них значение NULL:  
```sql
DECLARE @LastName nvarchar(30), @FirstName nvarchar(20), @StateProvince nchar(2);
```

Областью видимости переменной называют диапазон инструкций Transact-SQL, которые могут к ней обращаться. Областью видимости переменной являются все инструкции между ее объявлением и концом пакета или хранимой процедуры, где она объявлена. Например, следующий скрипт содержит синтаксическую ошибку, поскольку переменная объявлена в одном пакете, а используется в другом:  
```sql
USE AdventureWorks2014;
GO
DECLARE @MyVariable int;
SET @MyVariable = 1;
-- Terminate the batch by using the GO keyword.
GO 
-- @MyVariable has gone out of scope and no longer exists.

-- This SELECT statement generates a syntax error because it is
-- no longer legal to reference @MyVariable.
SELECT BusinessEntityID, NationalIDNumber, JobTitle
FROM HumanResources.Employee
WHERE BusinessEntityID = @MyVariable;
```

Переменные имеют локальную область видимости и доступны только внутри пакета или процедуры, где они объявлены. В следующем примере вложенная область видимости, созданная для выполнения процедуры sp_executesql, не имеет доступа к переменной, объявленной в более высокой области видимости, и возвращает ошибку:  

```sql
DECLARE @MyVariable int;
SET @MyVariable = 1;
EXECUTE sp_executesql N'SELECT @MyVariable'; -- this produces an error
```

## <a name="setting-a-value-in-a-transact-sql-variable"></a>Присвоение значения переменной в языке Transact-SQL

При объявлении переменной присваивается значение NULL. Чтобы изменить значение переменной, применяется инструкция SET. Этот способ присвоения значений переменным является предпочтительным. Кроме того, переменной можно присвоить значение, указав ее в списке выбора инструкции SELECT.

Чтобы присвоить значение переменной при помощи инструкции SET, необходимо указать ее имя и присваиваемое значение. Этот способ присвоения значений переменным является предпочтительным. Например, следующий пакет объявляет две переменные, присваивает им значения и использует их в предложении `WHERE` инструкции `SELECT`:  

```sql
USE AdventureWorks2014;
GO
-- Declare two variables.
DECLARE @FirstNameVariable nvarchar(50),
   @PostalCodeVariable nvarchar(15);

-- Set their values.
SET @FirstNameVariable = N'Amy';
SET @PostalCodeVariable = N'BA5 3HX';

-- Use them in the WHERE clause of a SELECT statement.
SELECT LastName, FirstName, JobTitle, City, StateProvinceName, CountryRegionName
FROM HumanResources.vEmployee
WHERE FirstName = @FirstNameVariable
   OR PostalCode = @PostalCodeVariable;
GO
```

Переменной можно присвоить значение, указав ее в списке выбора. Если список выбора ссылается на переменную, то ей должно быть присвоено скалярное значение, или инструкция SELECT должна возвращать только одну строку. Пример:  

```sql
USE AdventureWorks2014;
GO
DECLARE @EmpIDVariable int;

SELECT @EmpIDVariable = MAX(EmployeeID)
FROM HumanResources.Employee;
GO
```

> [!WARNING]
> Когда при выполнении инструкции SELECT переменной присваивается несколько значений, сервер SQL Server не гарантирует порядок вычисления выражений. Обратите внимание, что этот эффект проявляется, только если инструкция присваивает значение переменной.

Если инструкция SELECT возвращает более одной строки и переменная ссылается на нескалярное выражение, ей присваивается значение, которое возвращается для выражения в последней строке результирующего набора. Например, в следующем пакете переменной **\@EmpIDVariable** присваивается значение идентификатора **BusinessEntityID** последней возвращенной строки, равное 1:  

```sql
USE AdventureWorks2014;
GO
DECLARE @EmpIDVariable int;

SELECT @EmpIDVariable = BusinessEntityID
FROM HumanResources.Employee
ORDER BY BusinessEntityID DESC;

SELECT @EmpIDVariable;
GO
```

## <a name="see-also"></a>См. также:  
 [Declare @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
 [SET @local_variable](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
 [SELECT @local_variable](../../t-sql/language-elements/select-local-variable-transact-sql.md)  
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)   
  
  
