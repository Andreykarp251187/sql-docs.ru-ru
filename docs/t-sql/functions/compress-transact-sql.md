---
title: COMPRESS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e42349b93666071e389e080e200591f70a2517e9
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87111061"
---
# <a name="compress-transact-sql"></a>COMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Эта функция сжимает входное выражение с использованием алгоритма GZIP. Она возвращает массив байтов типа **varbinary(max)** .
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COMPRESS ( expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
*expression*  
Объект

* **binary(***n***)**
* **char(***n***)**
* **nchar(***n***)**
* **nvarchar(max)**
* **nvarchar(***n***)**
* **varbinary(max)**
* **varbinary(***n***)**
* **varchar(max)**

или диспетчер конфигурации служб

* **varchar(***n***)**

. Дополнительные сведения см. в статье [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="return-types"></a>Типы возвращаемых данных
**varbinary(max)** , представляющие сжатое содержимое входного выражения.
  
## <a name="remarks"></a>Remarks  
Сжатые данные невозможно индексировать.
  
Функция `COMPRESS` сжимает данные, предоставленные во входном выражении. Ее необходимо вызывать для каждого раздела сжимаемых данных. Дополнительные сведения об автоматическом сжатии хранимых данных на уровне строк или страниц см. в статье [Сжатие данных](../../relational-databases/data-compression/data-compression.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. Сжатие данных во время вставки в таблицу  
В этом примере показано, как сжать данные, вставляемые в таблицу.
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>Б. Архивация сжатой версии удаленных строк  
Приведенная ниже инструкция сначала удаляет старые записи игроков из таблицы `player`. Затем для экономии места она сохраняет их в сжатом виде в таблице `inactivePlayer`.
  
```sql
DELETE FROM player  
OUTPUT deleted.id, deleted.name, deleted.surname, deleted.datemodifier, COMPRESS(deleted.info)   
INTO dbo.inactivePlayers
WHERE datemodified < @startOfYear; 
```  
  
## <a name="see-also"></a>См. также раздел
[Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[DECOMPRESS (Transact-SQL)](../../t-sql/functions/decompress-transact-sql.md)
  
  
