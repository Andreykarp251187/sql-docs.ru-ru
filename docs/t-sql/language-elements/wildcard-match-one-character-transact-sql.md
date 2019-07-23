---
title: _ (шаблон — совпадение одного символа) (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Match
- wildcard
- _TSQL
- Match One
- _
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- _ (wildcard - match one character)
ms.assetid: 11a2ed36-9e21-4bdf-ae20-a31db1434b97
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f6876003c64889d32e31266ebe74b6532c1a8f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68000301"
---
# <a name="-wildcard---match-one-character-transact-sql"></a>_ (шаблон — совпадение одного символа) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Используйте символ подчеркивания _ для совпадения с любым одиночным символом в операции сравнения строк, которая использует сопоставление шаблонов, например `LIKE` и `PATINDEX`.  
  
## <a name="examples"></a>Примеры  

## <a name="a-simple-example"></a>A. Простой пример   

В следующем примере возвращаются все имена баз данных, которые начинаются с буквы `m` и имеют третью букву `d`. Символ подчеркивания указывает, что вторым символом в имени может быть любая буква. Этому условию удовлетворяют базы данных `model` и `msdb`. А база данных `master` — нет.

```sql
SELECT name FROM sys.databases
WHERE name LIKE 'm_d%';
```   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-----
model
msdb
```   
Этому условию могут удовлетворять дополнительные базы данных.

Для представления нескольких символов можно использовать несколько символов подчеркивания. При изменении условия `LIKE` для включения двух символов подчеркивания `'m__%` в результат будет включена база данных master.

### <a name="b-more-complex-example"></a>Б. Более сложный пример
 В следующем примере используется оператор _ для поиска в таблице `Person` всех людей, у которых имя состоит из трех букв и заканчивается на `an`.  
  
```sql  
-- USE AdventureWorks2012
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE '_an'  
ORDER BY FirstName;  
```  
## <a name="c-escaping-the-underscore-character"></a>В. Экранирование символа подчеркивания   
В следующем примере возвращаются имена предопределенных ролей базы данных, например `db_owner` и `db_ddladmin`, но вместе с ними возвращается пользователь `dbo`. 

```sql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db_%';
```

Символ подчеркивания в третьей позиции рассматривается как подстановочный знак и не выполняет фильтрацию только участников, начинающихся с буквы `db_`. Чтоб экранировать символ подчеркивания, заключите его в скобки `[_]`. 

```sql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db[_]%';
```   
Теперь пользователь `dbo` исключен.   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-------------
db_owner
db_accessadmin
db_securityadmin
...
```

  
## <a name="see-also"></a>См. также:  
 [LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX (Transact-SQL)](../../t-sql/functions/patindex-transact-sql.md)   
  [% (подстановочный знак — символы для сопоставления)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [[ ] (подстановочный знак — символы для сопоставления)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [[^] (подстановочный знак — символы не для сопоставления)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
  
