---
title: sys.dm_db_missing_index_details (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_details
- dm_db_missing_index_details
- sys.dm_db_missing_index_details_TSQL
- dm_db_missing_index_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- missing indexes feature [SQL Server], sys.dm_db_missing_index_details dynamic management view
- sys.dm_db_missing_index_details dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1fc72e290bf1aa495493eb09d5e0db8cf305202e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62508255"
---
# <a name="sysdmdbmissingindexdetails-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает подробные сведения об отсутствующих индексах, за исключением пространственных индексов.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать раскрытия этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**index_handle**|**int**|Идентифицирует специфический отсутствующий индекс. Этот идентификатор уникален для сервера. **index_handle** является ключевым для данной таблицы.|  
|**database_id**|**smallint**|Идентифицирует базу данных, в которой находится таблица с отсутствующим индексом.|  
|**object_id**|**int**|Идентифицирует таблицу, в которой отсутствует индекс.|  
|**equality_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, соответствующих предикатам равенства в форме:<br /><br /> *table.column* =*constant_value*|  
|**inequality_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, который соответствует предикатам неравенства, например предикатам в форме:<br /><br /> *table.column* > *constant_value*<br /><br /> Любой оператор сравнения, кроме «=», выражает неравенство.|  
|**included_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, необходимых в качестве столбцов для запроса. Дополнительные сведения о включенных столбцах см. в разделе [создание индексов с включенными столбцами](../../relational-databases/indexes/create-indexes-with-included-columns.md).<br /><br /> Для индексов, оптимизированных для памяти (оба хэширования и оптимизированных для памяти некластеризованный), игнорировать **included_columns**. Все столбцы таблицы включаются в каждый индекс с оптимизацией для памяти.|  
|**инструкция**|**nvarchar(4000)**|Имя таблицы, в которой отсутствует индекс.|  
  
## <a name="remarks"></a>Примечания  
 Сведения, возвращаемые функцией **sys.dm_db_missing_index_details** обновляется, когда запрос оптимизирован оптимизатором запросов и не сохраняется. Сведения об отсутствующих индексах хранятся только до перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Администраторы базы данных должны периодически делать резервные копии сведений об отсутствующих индексах, чтобы сохранить их после перезагрузки сервера.  
  
 Чтобы определить, какие группы входит отсутствующий индекс является частью, вы можете запросить **sys.dm_db_missing_index_groups** динамическому административному представлению, объединив ее с **sys.dm_db_missing_index_details**  на основе **index_handle** столбца.  

  >[!NOTE]
  >Результирующий набор для этого динамического административного Представления может использовать до 600 строк. Каждая строка содержит один отсутствующий индекс. При наличии более чем 600 отсутствующих индексов, следует устранить существующие отсутствующие индексы, после чего можно просмотреть более новые. 
  
## <a name="using-missing-index-information-in-create-index-statements"></a>Использование сведений об отсутствующих индексах в инструкциях CREATE INDEX  
 Чтобы преобразовать данные, возвращаемые командлетом **sys.dm_db_missing_index_details** инструкцию CREATE INDEX для индексов на диске и оптимизированных для памяти, столбцы равенства должны быть помещены перед столбцами неравенства, а вместе они должны образовать индекс ключа. Включенные столбцы должны быть добавлены в инструкцию CREATE INDEX с помощью предложения INCLUDE. Чтобы определить эффективный порядок столбцов равенства, расположите их на основе их выборности, перечисляя наиболее выбираемые столбцы первыми (крайние левые в списке столбцов).  
  
 Дополнительные сведения об индексах оптимизированных для памяти, см. в разделе [индексы для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
## <a name="transaction-consistency"></a>Согласованность транзакций  
 Если транзакция создает или удаляет таблицу, то строки, содержащие сведения отсутствующих индексов об удаленных объектах, удаляются из данного объекта DMO, сохраняя согласованность транзакций.  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
