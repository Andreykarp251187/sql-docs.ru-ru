---
description: sys. sp_cleanup_temporal_history (Transact-SQL)
title: sys. sp_cleanup_temporal_history | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 3b47fd6b0ee5a06ae1ce585f583a699a530e350b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545802"
---
# <a name="syssp_cleanup_temporal_history-transact-sql"></a>sys. sp_cleanup_temporal_history (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

Удаляет все строки из темпоральной таблицы журнала, которые соответствуют настроенному HISTORY_RETENTION ПЕРИОДу в рамках одной транзакции.

## <a name="syntax"></a>Синтаксис

```
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```

## <a name="arguments"></a>Аргументы

*\@table_name*

Имя темпоральной таблицы, для которой вызывается очистка хранения.

*schema_name*

Имя схемы, которой принадлежит текущая Темпоральная таблица

*row_count_var* [выходные данные]

Выходной параметр, возвращающий число удаленных строк. Если таблица журнала имеет кластеризованный индекс columnstore, этот параметр возвратит значение всегда 0.

## <a name="remarks"></a>Примечания

Эта хранимая процедура может использоваться только с временными таблицами, для которых указан конечный срок хранения.
Используйте эту хранимую процедуру только в том случае, если необходимо немедленно очистить все устаревшие строки из таблицы журнала. Следует иметь в курсе, что он может оказать значительное влияние на журнал базы данных и подсистему ввода-вывода, так как он удаляет все подходящие строки в рамках одной транзакции.

Всегда рекомендуется полагаться на внутреннюю фоновую задачу для очистки, которая удаляет устаревшие строки с минимальным влиянием на обычные рабочие нагрузки и базу данных в целом.

## <a name="permissions"></a>Разрешения

Требуются db_owner разрешения.

## <a name="example"></a>Пример

```sql
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="next-steps"></a>Дальнейшие действия

[Политика хранения временных таблиц](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
