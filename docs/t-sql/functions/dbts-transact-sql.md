---
title: '@@DBTS (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@DBTS_TSQL'
- '@@DBTS'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@DBTS function'
- timestamp data type
ms.assetid: 91842ddd-91c0-4445-a03f-116f6bc991d0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f9fca5c54451d13a8496d20e453d0bd89bf27fed
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65945622"
---
# <a name="x40x40dbts-transact-sql"></a>&#x40;&#x40;DBTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция возвращает значение текущего типа данных **timestamp** для текущей базы данных. У текущей базы данных будет гарантированно уникальное значение отметки времени.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```
@@DBTS  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных
**varbinary**
  
## <a name="remarks"></a>Remarks  
@@DBTS возвращает последнее использованное значение отметки времени для текущей базы данных. Новое значение отметки времени формируется при вставке или обновлении строки со столбцом **timestamp**.
  
Функция @@DBTS не затрагивается изменениями на уровнях изоляции транзакции.
  
## <a name="examples"></a>Примеры  
В этом примере возвращается текущее значение **timestamp** из базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@DBTS;  
```  
  
## <a name="see-also"></a>См. также раздел
[Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)  
[Параллелизм курсоров (ODBC)](../../relational-databases/native-client-odbc-cursors/properties/cursor-concurrency-odbc.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION (Transact-SQL)](../../t-sql/functions/min-active-rowversion-transact-sql.md)
  
  
