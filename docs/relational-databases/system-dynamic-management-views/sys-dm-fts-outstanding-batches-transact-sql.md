---
title: sys.dm_fts_outstanding_batches (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_outstanding_batches
- dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches
dev_langs:
- TSQL
helpviewer_keywords:
- troubleshooting [SQL Server], full-text search
- sys.dm_fts_outstanding_batches dynamic management view
ms.assetid: c4d697ed-c906-4c28-b137-036a25e13c84
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3644e809910b2a7b54e1acc89c6dc667deb7c7cc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947251"
---
# <a name="sysdmftsoutstandingbatches-transact-sql"></a>sys.dm_fts_outstanding_batches (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает данные о каждом пакете полнотекстового индексирования.  
  
  |Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|  
|catalog_id|**int**|Идентификатор полнотекстового каталога.|  
|table_id|**int**|Идентификатор идентификатора таблицы, в которой содержится полнотекстовый индекс.|  
|batch_id|**int**|Идентификатор пакета|  
|memory_address|**varbinary(8)**|Адрес памяти пакетного объекта.|  
|crawl_memory_address|**varbinary(8)**|Адрес памяти объекта сканирования (родительского объекта).|  
|memregion_memory_address|**varbinary(8)**|Адрес области памяти исходящей общей памяти узла управляющей программы фильтрации (fdhost.exe).|  
|hr_batch|**int**|Самый последний код ошибки для пакета.|  
|is_retry_batch|**bit**|Обозначает, является ли пакет повторно передаваемым:<br /><br /> 0 = нет<br /><br /> 1 = да|  
|retry_hints|**int**|Тип повторной попытки, нужный для пакета:<br /><br /> 0 = нет повторения;<br /><br /> 1 = многопоточное повторение;<br /><br /> 2 = однопоточное повторение;<br /><br /> 3 = однопоточное и многопоточное повторение;<br /><br /> 5 = многопоточное окончательное повторение;<br /><br /> 6 = однопоточное окончательное повторение;<br /><br /> 7 = однопоточное и многопоточное окончательное повторение.|  
|retry_hints_description|**nvarchar(120)**|Описание типа необходимой повторной попытки:<br /><br /> НЕТ ПОВТОРЕНИЯ;<br /><br /> МНОГОПОТОЧНОЕ ПОВТОРЕНИЕ;<br /><br /> ОДНОПОТОЧНОЕ ПОВТОРЕНИЕ;<br /><br /> ОДНОПОТОЧНОЕ И МНОГОПОТОЧНОЕ ПОВТОРЕНИЕ;<br /><br /> МНОГОПОТОЧНОЕ ОКОНЧАТЕЛЬНОЕ ПОВТОРЕНИЕ;<br /><br /> ОДНОПОТОЧНОЕ ОКОНЧАТЕЛЬНОЕ ПОВТОРЕНИЕ;<br /><br /> ОДНОПОТОЧНОЕ И МНОГОПОТОЧНОЕ ОКОНЧАТЕЛЬНОЕ ПОВТОРЕНИЕ.|  
|doc_failed|**bigint**|Количество отказавших документов в пакете.|  
|batch_timestamp|**timestamp**|Значение timestamp, полученное при создании пакета.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
  
## <a name="examples"></a>Примеры  
 В следующем примере выясняется, сколько пакетов обрабатывается в данный момент для каждой таблицы для экземпляра сервера.  
  
```  
SELECT database_id, table_id, COUNT(*) AS batch_count FROM sys.dm_fts_outstanding_batches GROUP BY database_id, table_id ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
