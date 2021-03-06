---
description: sys.dm_os_job_object (база данных SQL Azure)
title: sys. dm_os_job_object (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 06/03/2020
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 3ed298216393b59d723eb58cac783f9836ce93d0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489881"
---
# <a name="sysdm_os_job_object-azure-sql-database"></a>sys.dm_os_job_object (база данных SQL Azure)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

Возвращает одну строку, описывающую конфигурацию объекта задания, управляющего SQL Server процессом, а также определенную статистику потребления ресурсов на уровне объектов задания. Возвращает пустой набор, если SQL Server не выполняется в объекте задания.

Объект задания — это конструкция Windows, которая реализует управление ресурсами ЦП, памяти и ввода-вывода на уровне операционной системы. Дополнительные сведения об объектах заданий см. в разделе [объекты задания](/windows/desktop/ProcThread/job-objects).
  
|Столбцы|Тип данных|Описание|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|Указывает часть циклов процессора, которые SQL Server потоки могут использовать во время каждого интервала планирования. Значение указывается как процент доступных циклов в пределах интервала планирования в 10000 циклов, умноженный на число логических процессоров. Например, значение 800 в экземпляре SQL Server с 8 логическими ЦП означает, что потоки могут использовать процессоры с полной емкостью.|
|cpu_affinity_mask|**bigint**|Битовая маска, описывающая логические процессоры, которые процесс SQL Server может использовать в группе процессоров. Например, cpu_affinity_mask 255 (1111 1111 в двоичном формате) означает, что можно использовать первые восемь логических процессоров. <br /><br />Этот столбец предоставляется для обеспечения обратной совместимости. Он не сообщает о группе процессоров, а Сообщаемое значение может быть неправильным, если группа процессоров содержит более 64 логических процессоров. Используйте `process_physical_affinity` столбец, чтобы определить сходство процессоров.|
|cpu_affinity_group|**int**|Номер группы процессоров, используемой SQL Server.|
|memory_limit_mb|**bigint**|Максимальный объем зафиксированной памяти (в МБ), в течение которого все процессы в объекте задания, включая SQL Server, могут использоваться кумулятивно.| 
|process_memory_limit_mb |**bigint**|Максимальный объем зафиксированной памяти (в МБ), который может использовать один процесс в объекте задания, например SQL Server.|
|workingset_limit_mb |**bigint**|Максимальный объем памяти (в МБ), который может использовать SQL Server рабочий набор.|
|non_sos_mem_gap_mb|**bigint**|Объем памяти (в МБ), заданный для стеков потоков, библиотек DLL и других операций выделения памяти, не относящихся к SOS. Целевая память SOS — это разница между `process_memory_limit_mb` и `non_sos_mem_gap_mb` .| 
|low_mem_signal_threshold_mb|**bigint**|Пороговое значение памяти в МБ. Когда объем доступной памяти для объекта задания ниже этого порога, в процесс SQL Server отправляется сигнал о нехватке памяти. |
|total_user_time|**bigint**|Общее число 100 единиц записи NS, которые потоки в объекте задания тратили в пользовательском режиме, так как был создан объект задания. |
|total_kernel_time |**bigint**|Общее число 100 единиц записи NS, которые потоки в объекте задания тратили в режиме ядра, так как был создан объект задания. |
|write_operation_count |**bigint**|Общее число операций записи ввода-вывода на локальных дисках, выданных SQL Server с момента создания объекта задания. |
|read_operation_count |**bigint**|Общее число операций чтения ввода-вывода на локальных дисках, выданных SQL Server с момента создания объекта задания. |
|peak_process_memory_used_mb|**bigint**|Пиковый объем памяти (в МБ), в течение которого один процесс в объекте задания, например SQL Server, использовался с момента создания объекта задания.| 
|peak_job_memory_used_mb|**bigint**|Пиковый объем памяти (в МБ), в течение которого все процессы в объекте задания использовались кумулятивно с момента создания объекта задания.|
|process_physical_affinity|**nvarchar (3072)**|Битовые маски, описывающие логические процессоры, которые процесс SQL Server может использовать в каждой группе процессоров. Значение в этом столбце формируется одной или несколькими парами значений, каждое из которых заключено в фигурные скобки. В каждой паре первое значение — номер группы процессоров, а второе — битовая маска сходства для этой группы процессоров. Например, значение `{{0,a}{1,2}}` означает, что маска сходства для группы процессоров `0` `a` ( `1010` в двоичном коде, указывающая, что используются процессоры 2 и 4), а маска сходства для группы процессоров `1` — `2` ( `10` в двоичном формате, указывающий, что используется процессор 2).|
  
## <a name="permissions"></a>Разрешения  
Для Управляемый экземпляр SQL требуется `VIEW SERVER STATE` разрешение. В Базе данных SQL требуется соответствующее разрешение `VIEW DATABASE STATE`.  
 
## <a name="see-also"></a>См. также  

Дополнительные сведения об управляемых экземплярах см. в разделе [SQL управляемый экземпляр](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
