---
title: sys.dm_os_memory_pools (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dbd5ce36c9d83eb6347bcba71c26c3fd71c4513d
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265741"
---
# <a name="sysdmosmemorypools-transact-sql"></a>sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строку для каждого хранилища объектов в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это представление можно использовать для наблюдения за использованием кэша и для выявления случаев ненадлежащего кэширования.  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_memory_pools**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary(8)**|Адрес памяти записи, представляющей пул памяти. Не допускает значение NULL.|  
|**pool_id**|**int**|Идентификатор конкретного пула внутри набора пулов. Не допускает значение NULL.|  
|**type**|**nvarchar(60)**|Тип пула объектов. Не допускает значение NULL. Дополнительные сведения см. в разделе [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**name**|**nvarchar(256)**|Присвоенное системой имя данного объекта памяти. Не допускает значение NULL.|  
|**max_free_entries_count**|**bigint**|Максимальное число свободных записей, допустимое для одного пула. Не допускает значение NULL.|  
|**free_entries_count**|**bigint**|Число свободных записей, имеющихся в пуле в данное время. Не допускает значение NULL.|  
|**removed_in_all_rounds_count**|**bigint**|Число записей, удаленных из пула за время, прошедшее с момента запуска экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значение NULL.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   

## <a name="remarks"></a>Примечания  
 Компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] иногда используют общую среду пула для кэширования однородных типов данных без сохранения состояния. Среда пула организована проще, чем среда кэша. Все записи в пулах рассматриваются как равные. Пулы с точки зрения внутренней структуры представляют собой клерки памяти и могут использоваться там, где используются клерки памяти.  
  
## <a name="see-also"></a>См. также  
 
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


