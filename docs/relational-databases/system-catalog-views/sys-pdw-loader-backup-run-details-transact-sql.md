---
title: sys.pdw_loader_backup_run_details (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: dead5962987f7fb132f21bb4e3517f7cc9249601
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127650"
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Дополнительно содержит подробные сведения, помимо сведения в [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), о текущих и выполненных операциях backup и restore в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и о текущих и завершения резервного копирования, восстановления и операций загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Эта информация сохраняется и после перезапуска системы.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Уникальный идентификатор для определенной резервной копии или восстановления выполнения.<br /><br /> run_id и pdw_node_id формируют ключ для этого представления.||  
|pdw_node_id|**int**|Уникальный идентификатор узла устройства, для которого эта запись содержит сведения.<br /><br /> run_id и pdw_node_id формируют ключ для этого представления.|См. в разделе node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16) в формате**|Текущее состояние выполнения.|«ОТМЕНЕНО», «ЗАВЕРШЕНО», «СБОЙ», «QUEUED», «РАБОТАЕТ»|  
|start_time|**datetime**|Время начала операции на данный узел.||  
|end_time|**datetime**|Время операции окончания на данный узел, если таковые имеются.||  
|total_elapsed_time|**int**|Общее время выполнения операции на данный узел.|Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дня в миллисекундах), он вызывает ошибку материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
|Ход выполнения|**int**|Ход выполнения операции, выраженное в процентах.|0 до 100|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
