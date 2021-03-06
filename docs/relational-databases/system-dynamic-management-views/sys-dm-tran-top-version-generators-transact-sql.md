---
description: sys.dm_tran_top_version_generators (Transact-SQL)
title: sys. dm_tran_top_version_generators (Transact-SQL) | Документация Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 54e3caeb50a0c6fd9f3a6b1523675eb482005384
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546526"
---
# <a name="sysdm_tran_top_version_generators-transact-sql"></a>sys.dm_tran_top_version_generators (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Возвращает виртуальную таблицу для объектов, формирующих большинство версий в хранилище версий. **sys. dm_tran_top_version_generators** возвращает первые 256 суммарных значений длины записей, сгруппированных по **database_id** и **rowset_id**. **sys. dm_tran_top_version_generators** извлекает данные путем запроса к виртуальной таблице **dm_tran_version_store** . представление **sys. dm_tran_top_version_generators** является неэффективным для выполнения, так как это представление запрашивает хранилище версий, а хранилище версий может быть очень большим. Эту функцию рекомендуется использовать для поиска самых крупных потребителей в хранилище версий.  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , используйте имя **sys. dm_pdw_nodes_tran_top_version_generators**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_tran_top_version_generators  
```  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных.|  
|**rowset_id**|**bigint**|Идентификатор набора строк.|  
|**aggregated_record_length_in_bytes**|**int**|Сумма значений длины записей для каждой пары **database_id** и **rowset_id** в хранилище версий.|  
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="permissions"></a>Разрешения

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется  **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   

## <a name="remarks"></a>Примечания  
 Поскольку **sys. dm_tran_top_version_generators** может потребоваться чтение большого количества страниц при сканировании всего хранилища версий, выполнение **sys. dm_tran_top_version_generators** может повлиять на производительность системы.  
  
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
  
 Выходные данные показывают, что все версии создаются с помощью `database_id``9` и что версии формируются из двух таблиц.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


