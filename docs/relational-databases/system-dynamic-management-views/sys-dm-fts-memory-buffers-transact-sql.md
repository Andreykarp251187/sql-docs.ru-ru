---
title: sys.dm_fts_memory_buffers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_memory_buffers
- dm_fts_memory_buffers_TSQL
- dm_fts_memory_buffers
- sys.dm_fts_memory_buffers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_buffers dynamic management view
ms.assetid: 56895fe5-e8df-4d75-9adc-c1f7757cdef8
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cfca7379336d07b9e5a7099c6c8075c0f959b7ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900924"
---
# <a name="sysdmftsmemorybuffers-transact-sql"></a>sys.dm_fts_memory_buffers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает данные о буферах памяти, принадлежащих конкретному пулу памяти, используемому в качестве части полнотекстового сканирования или диапазона полнотекстового сканирования.  
  
> [!NOTE]
> Следующий столбец будет удален в одном из будущих выпусков [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **row_count**. Не пользуйтесь ими в новых разработках и запланируйте изменение приложений, которые сейчас их используют.  

  
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|Идентификатор выделенного пула памяти.<br /><br /> 0 = небольшие буферы<br /><br /> 1 = большие буферы|  
|**адрес_памяти**|**varbinary(8)**|Адрес выделенного буфера памяти.|  
|**name**|**nvarchar(4000)**|Имя общего буфера памяти, для которого было произведено данное выделение.|  
|**is_free**|**bit**|Текущее состояние буфера памяти.<br /><br /> 0 = свободен<br /><br /> 1 = занят|  
|**row_count**|**int**|Число строк, обрабатываемое в данный момент буфером.|  
|**bytes_used**|**int**|Объем памяти, используемой данным буфером, в байтах.|  
|**percent_used**|**int**|Процент использования выделенной памяти.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
В [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] необходимо разрешение `VIEW DATABASE STATE` для базы данных.   
  
## <a name="physical-joins"></a>Физические соединения  
 ![Существенные соединения данного динамического административного представления](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "существенные соединения данного динамического административного представления")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

