---
title: sys.dm_db_partition_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_partition_stats
- dm_db_partition_stats_TSQL
- sys.dm_db_partition_stats_TSQL
- sys.dm_db_partition_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_partition_stats dynamic management view
ms.assetid: 9db9d184-b3a2-421e-a804-b18ebcb099b7
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cb9ab9e3cbf5948e5e832171c179d6daa2c0bc28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096286"
---
# <a name="sysdmdbpartitionstats-transact-sql"></a>sys.dm_db_partition_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает страницу и сведения о количестве строк для всех секций текущей базы данных.  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_db_partition_stats**. Partition_id в sys.dm_pdw_nodes_db_partition_stats отличается от partition_id в представлении каталога sys.partitions для хранилища данных SQL Azure.
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Идентификатор секции. Является уникальным в пределах базы данных. Это то же значение, что **partition_id** в **sys.partitions** каталога представление, за исключением хранилище данных SQL Azure.|  
|**object_id**|**int**|Идентификатор таблицы или индексированного представления, в которое входит данная секция.|  
|**index_id**|**int**|Идентификатор кучи или индекса, в который входит данная секция.<br /><br /> 0 = куча;<br /><br /> 1 = Кластеризованный индекс.<br /><br /> > 1 = некластеризованный индекс|  
|**partition_number**|**int**|Номер секции внутри индекса или кучи (нумерация начинается с 1).|  
|**in_row_data_page_count**|**bigint**|Количество страниц, используемых для хранения данных, содержащихся в строках данной секции. Если секция является частью кучи, то данное значение отображает количество страниц данных в куче. Если секция является частью индекса, то данное значение отображает количество страниц на конечном уровне. (Неконечные страницы сбалансированного дерева не включаются в счетчик.) (Карты распределения индекса) IAM-страницы не включаются в любом случае. Всегда 0 для оптимизированного для памяти xVelocity индекса columnstore.|  
|**in_row_used_page_count**|**bigint**|Количество страниц, используемых для хранения и управления данными, содержащимися в строках данной секции. Данный счетчик учитывает страницы неконечные сбалансированного дерева, IAM-страниц и все страницы, включенные в **in_row_data_page_count** столбца. Всегда равно 0 для индекса columnstore.|  
|**in_row_reserved_page_count**|**bigint**|Общее количество страниц, зарезервированных для хранения и управления данными в данной секции (учитываются как используемые, так и не используемые страницы). Всегда равно 0 для индекса columnstore.|  
|**lob_used_page_count**|**bigint**|Количество страниц, используемых для хранения и управления out of row **текст**, **ntext**, **изображение**, **varchar(max)** , **nvarchar (max)** , **varbinary(max)** , и **xml** столбцов в пределах секции. IAM-страницы учитываются.<br /><br /> Количество больших объектов (LOB), используемых для хранения и управления данными индекса columnstore в секции.|  
|**lob_reserved_page_count**|**bigint**|Общее число страниц, зарезервированных для хранения и управления ими out of row **текст**, **ntext**, **изображение**, **varchar(max)** ,  **nvarchar(max)** , **varbinary(max)** , и **xml** столбцов в пределах секции, учитываются ли используемые страницы используется или нет. IAM-страницы учитываются.<br /><br /> Общее количество больших объектов (LOB), зарезервированных для хранения и управления индексом columnstore в секции.|  
|**row_overflow_used_page_count**|**bigint**|Количество страниц, используемых для хранения и управления строки, превышающие **varchar**, **nvarchar**, **varbinary**, и **sql_variant** столбцы в разделе. IAM-страницы учитываются.<br /><br /> Всегда равно 0 для индекса columnstore.|  
|**row_overflow_reserved_page_count**|**bigint**|Общее число страниц, зарезервированных для хранения и управления ими строки, превышающие **varchar**, **nvarchar**, **varbinary**, и **sql_variant** столбцы в пределах секции, учитываются ли используемые страницы используется или нет. IAM-страницы учитываются.<br /><br /> Всегда равно 0 для индекса columnstore.|  
|**used_page_count**|**bigint**|Общее число страниц, используемых в секции. Вычисляется как **in_row_used_page_count** + **lob_used_page_count** + **row_overflow_used_page_count**.|  
|**reserved_page_count**|**bigint**|Общее число страниц, зарезервированных в секции. Вычисляется как **in_row_reserved_page_count** + **lob_reserved_page_count** + **row_overflow_reserved_page_count**.|  
|**row_count**|**bigint**|Приблизительное количество строк в секции.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
|**distribution_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Уникальный числовой идентификатор, связанная с распределением.|  
  
## <a name="remarks"></a>Примечания  
 **sys.dm_db_partition_stats** отображаются сведения о пространстве, используемом для хранения и управления внутристрочные данные LOB, а данные строки, превышающие для всех секций в базе данных. Для каждой секции отображается одна строка.  
  
 Результаты подсчетов, на которых основаны выходные данные, хранятся в оперативной памяти или записываются в различные таблицы на жестком диске.  
  
 Данные в строках, данные LOB, а также данные строки, превышающие размер страницы, представляют собой три типа единиц распределения, из которых состоит секция. [Sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) запрос к представлению каталога метаданные по каждой единицы распределения в базе данных.  
  
 Если куча или индекс не имеют делений, то они состоят из одной секции (с номером 1); поэтому для каждой такой кучи или индекса возвращается только одна строка. [Sys.partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md) запрос к представлению каталога метаданные по каждой секции всех таблиц и индексов в базе данных.  
  
 Общее количество секций таблицы или индекса может быть получено путем суммирования результатов для всех секций.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW DATABASE STATE **sys.dm_db_partition_stats** динамическое административное представление. Дополнительные сведения о разрешениях на динамические административные представления, см. в разделе [динамические административные представления и функции &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-all-counts-for-all-partitions-of-all-indexes-and-heaps-in-a-database"></a>A. Возврат результатов подсчета для всех секций во всех индексах и кучах базы данных  
 В следующем примере выводятся результаты подсчета для всех секций во всех индексах и кучах базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats;  
GO  
```  
  
### <a name="b-returning-all-counts-for-all-partitions-of-a-table-and-its-indexes"></a>Б. Возврат результатов подсчета для всех секций таблицы и ее индексов  
 В следующем примере выводятся результаты подсчета для всех секций таблицы `HumanResources.Employee` и ее индексов.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats   
WHERE object_id = OBJECT_ID('HumanResources.Employee');  
GO  
```  
  
### <a name="c-returning-total-used-pages-and-total-number-of-rows-for-a-heap-or-clustered-index"></a>В. Возврат общего количества используемых страниц и общего количества строк для кучи или кластеризованного индекса  
 В следующем примере выводится общее количество используемых страниц и общее количество строк для кучи или кластеризованного индекса таблицы `HumanResources.Employee`. Сумма состоит из единственной секции, так как таблица `Employee` не секционирована по умолчанию.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT SUM(used_page_count) AS total_number_of_used_pages,   
    SUM (row_count) AS total_number_of_rows   
FROM sys.dm_db_partition_stats  
WHERE object_id=OBJECT_ID('HumanResources.Employee')    AND (index_id=0 or index_id=1);  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  


