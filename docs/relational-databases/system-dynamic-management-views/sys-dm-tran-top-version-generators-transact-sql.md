---
title: sys.dm_tran_top_version_generators (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_tran_top_version_generators
- sys.dm_tran_top_version_generators
- dm_tran_top_version_generators_TSQL
- sys.dm_tran_top_version_generators_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_top_version_generators dynamic management view
ms.assetid: cec7809b-ba8a-4df9-b5bb-d4f651ff1a86
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 61bbef9d64ad204b1e7c747559c20d99d8811507
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090477"
---
# <a name="sysdmtrantopversiongenerators-transact-sql"></a>sys.dm_tran_top_version_generators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает виртуальную таблицу для объектов, формирующих большинство версий в хранилище версий. **sys.dm_tran_top_version_generators** возвращает первые 256 значений длины записей, сгруппированных по **database_id** и **rowset_id**. **sys.dm_tran_top_version_generators** извлекает данные, запросив **dm_tran_version_store** виртуальной таблицы. **sys.dm_tran_top_version_generators** является неэффективным, так как в этом представлении запросов в хранилище версий и хранилище версий может быть очень большим. Эту функцию рекомендуется использовать для поиска самых крупных потребителей в хранилище версий.  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_tran_top_version_generators**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_tran_top_version_generators  
```  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных.|  
|**rowset_id**|**bigint**|Идентификатор набора строк.|  
|**aggregated_record_length_in_bytes**|**int**|Сумма длин записей для каждого **database_id** и **rowset_id pair** в хранилище версий.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
В [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] необходимо разрешение `VIEW DATABASE STATE` для базы данных.   

## <a name="remarks"></a>Примечания  
 Так как **sys.dm_tran_top_version_generators** может потребоваться считать много страниц, так как он проверяет все хранилище версий, под управлением **sys.dm_tran_top_version_generators** могут мешать работе системы производительность.  
  
## <a name="examples"></a>Примеры  
 Следующий пример использует тестовый сценарий, содержащий четыре параллельные транзакции, идентифицированные порядковыми номерами (XSN), который выполняется в базе данных с параметрами ALLOW_SNAPSHOT_ISOLATION и READ_COMMITTED_SNAPSHOT, установленными в значение ON. Следующие транзакции запущены:  
  
-   XSN-57 является операцией обновления с сериализуемой изоляцией.  
  
-   XSN-58 аналогична XSN-57.  
  
-   XSN-59 является операцией выбора с изоляцией моментального снимка.  
  
-   XSN-60 аналогична XSN-59.  
  
 Выполнен следующий запрос.  
  
```  
SELECT  
    database_id,  
    rowset_id,  
    aggregated_record_length_in_bytes  
  FROM sys.dm_tran_top_version_generators;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
database_id rowset_id            aggregated_record_length_in_bytes  
----------- -------------------- ---------------------------------  
9           72057594038321152    87  
9           72057594038386688    33  
```  
  
 Выходные данные показывают, что все версии созданы с помощью `database_id``9` и версии, создаваемый из двух таблиц.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


