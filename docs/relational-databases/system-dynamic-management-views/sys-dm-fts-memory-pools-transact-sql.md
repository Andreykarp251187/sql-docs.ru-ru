---
description: sys.dm_fts_memory_pools (Transact-SQL)
title: sys. dm_fts_memory_pools (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_memory_pools_TSQL
- sys.dm_fts_memory_pools_TSQL
- sys.dm_fts_memory_pools
- dm_fts_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_pools dynamic management view
ms.assetid: 24747239-cd78-4d55-a00a-19233a457f42
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 720c3a3727f332c289b08480f6367babc0213ad4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489896"
---
# <a name="sysdm_fts_memory_pools-transact-sql"></a>sys.dm_fts_memory_pools (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает сведения о пулах общей памяти, доступных компоненту полнотекстового сборщика данных для полнотекстового сканирования или диапазона полнотекстового сканирования.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|Идентификатор выделенного пула памяти.<br /><br /> 0 = небольшие буферы<br /><br /> 1 = большие буферы|  
|**buffer_size**|**int**|Размер каждого распределенного буфера в пуле памяти.|  
|**min_buffer_limit**|**int**|Минимальное количество буферов, допустимых в пуле памяти.|  
|**max_buffer_limit**|**int**|Максимальное количество буферов, допустимых в пуле памяти.|  
|**buffer_count**|**int**|Текущее количество общих буферов памяти в пуле памяти.|  
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется  **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   
 
## <a name="physical-joins"></a>Физические соединения  
 ![Существенные соединения данного динамического административного представления](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-pools-1.gif "Существенные соединения данного динамического административного представления")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Кому|Связь|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|«многие к одному»|  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о суммарном объеме общей памяти, принадлежащей компоненту полнотекстового сборщика данных ([!INCLUDE[msCoName](../../includes/msconame-md.md)]) процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT SUM(buffer_size * buffer_count) AS "total memory"   
    FROM sys.dm_fts_memory_pools;  
```  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
