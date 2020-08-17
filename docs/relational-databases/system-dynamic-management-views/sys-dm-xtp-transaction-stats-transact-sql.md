---
description: sys.dm_xtp_transaction_stats (Transact-SQL)
title: sys. dm_xtp_transaction_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_transaction_stats_TSQL
- dm_xtp_transaction_stats
- sys.dm_xtp_transaction_stats_TSQL
- sys.dm_xtp_transaction_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_transaction_stats dynamic management view
ms.assetid: 9389f48d-0de5-47bd-9821-4db8f04504e4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c26dfd447806c3ffcf7d4a105255aad87aaa9787
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88322570"
---
# <a name="sysdm_xtp_transaction_stats-transact-sql"></a>sys.dm_xtp_transaction_stats (Transact-SQL)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Предоставляет статистические данные о транзакциях, выполненных с момента запуска сервера.  
  
 Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|total_count|**bigint**|Общее число транзакций, которые были запущены в компоненте In-Memory OLTP.|  
|read_only_count|**bigint**|Число транзакций в режиме только для чтения.|  
|total_aborts|**bigint**|Общее число транзакций, которые были прерваны пользователем или системой.|  
|user_aborts|**bigint**|Количество прерываний, инициированных системой. Эти прерывания могут быть вызваны конфликтами операции записи, ошибками проверки и зависимости.|  
|validation_failures|**bigint**|Количество раз, когда транзакция была прервана вследствие ошибки проверки.|  
|dependencies_taken|**bigint**|Только для внутреннего применения.|  
|dependencies_failed|**bigint**|Количество раз, когда транзакция была прервана, поскольку транзакция, от которой она зависела, была прервана.|  
|savepoint_create|**bigint**|Количество созданных точек сохранения. Новая точка сохранения создается для каждого атомарного блока.|  
|savepoint_rollbacks|**bigint**|Количество откатов к предыдущей точке сохранения.|  
|savepoint_refreshes|**bigint**|Только для внутреннего применения.|  
|log_bytes_written|**bigint**|Общее число байтов, записанных в записи журнала компонента In-Memory OLTP.|  
|log_IO_count|**bigint**|Общее число транзакций, для которых требуется ввести журнал операций ввода-вывода. Учитываются только транзакции в долговечных таблицах.|  
|phantom_scans_started|**bigint**|Только для внутреннего применения.|  
|phatom_scans_retries|**bigint**|Только для внутреннего применения.|  
|phantom_rows_touched|**bigint**|Только для внутреннего применения.|  
|phantom_rows_expiring|**bigint**|Только для внутреннего применения.|  
|phantom_rows_expired|**bigint**|Только для внутреннего применения.|  
|phantom_rows_expired_removed|**bigint**|Только для внутреннего применения.|  
|scans_started|**bigint**|Только для внутреннего применения.|  
|scans_retried|**bigint**|Только для внутреннего применения.|  
|rows_returned|**bigint**|Только для внутреннего применения.|  
|rows_touched|**bigint**|Только для внутреннего применения.|  
|rows_expiring|**bigint**|Только для внутреннего применения.|  
|rows_expired|**bigint**|Только для внутреннего применения.|  
|rows_expired_removed|**bigint**|Только для внутреннего применения.|  
|rows_inserted|**bigint**|Только для внутреннего применения.|  
|rows_updated|**bigint**|Только для внутреннего применения.|  
|rows_deleted|**bigint**|Только для внутреннего применения.|  
|write_conflicts|**bigint**|Только для внутреннего применения.|  
|unique_constraint_violations|**bigint**|Общее число нарушений ограничений уникальности.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Оптимизированные для памяти динамические административные представления таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
