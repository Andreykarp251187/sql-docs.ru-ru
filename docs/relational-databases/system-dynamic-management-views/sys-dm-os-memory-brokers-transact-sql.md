---
title: sys.dm_os_memory_brokers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_brokers
- dm_os_memory_brokers_TSQL
- sys.dm_os_memory_brokers_TSQL
- dm_os_memory_brokers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_brokers dynamic management view
ms.assetid: 48dd6ad9-0d36-4370-8a12-4921d0df4b86
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8e131e2550ffa5078df5e284898ffe936128b7e
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265868"
---
# <a name="sysdmosmemorybrokers-transact-sql"></a>sys.dm_os_memory_brokers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Внутреннее распределение памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляется с помощью диспетчера памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Разности между счетчиков памяти из **sys.dm_os_process_memory** и внутренних счетчиков можно указать использование памяти внешними компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пространство памяти.  
  
 Брокеры памяти должным образом распределяют выделяемые объемы памяти между различными компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], основываясь на текущем и прогнозируемом использовании. Брокеры памяти не осуществляют выделение памяти. Ими выполняется только отслеживание операций выделения памяти с целью вычисления необходимого распределения.  
  
 Сведения о брокерах памяти приведены в следующей таблице.  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_memory_brokers**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|Идентификатор пула ресурсов, если он связан с пулом регулятора ресурсов.|  
|**memory_broker_type**|**nvarchar(60)**|Тип брокера памяти. В настоящее время существует три типа брокеров памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], перечисленных ниже, с их компонентами.<br /><br /> **MEMORYBROKER_FOR_CACHE** : Объем памяти, выделенной для использования с кэшированными объектами (не буферный пул кэша).<br /><br /> **MEMORYBROKER_FOR_STEAL** : Память, заимствованная из буферного пула. Эта память недоступна для повторного использования другими компонентами до тех пор, пока она не будет освобождена текущим владельцем.<br /><br /> **MEMORYBROKER_FOR_RESERVE** : Памяти, зарезервированной для использования в будущем, в данный момент запросы.|  
|**allocations_kb**|**bigint**|Объем памяти, в килобайтах (КБ), выделенный для этого типа брокера.|  
|**allocations_kb_per_sec**|**bigint**|Интенсивность операций выделения памяти, в килобайтах (КБ) в секунду. Это значение может быть отрицательным для операций освобождения выделенной памяти.|  
|**predicted_allocations_kb**|**bigint**|Прогнозируемый объем выделенной памяти для брокера. Основывается на закономерности использования памяти.|  
|**target_allocations_kb**|**bigint**|Рекомендуемый объем выделенной памяти, в килобайтах (КБ), основанный на текущих параметрах и закономерностях использования памяти. Этот брокер должен быть приведен к указанному объему путем сокращения или увеличения используемого им объема выделенной памяти.|  
|**future_allocations_kb**|**bigint**|Прогнозируемое количество памяти, в килобайтах (КБ), которое будет выделено в течение следующих нескольких секунд.|  
|**overall_limit_kb**|**bigint**|Максимальный объем памяти в килобайтах (КБ), может быть выделен брокером.|  
|**last_notification**|**nvarchar(60)**|Рекомендация по использованию памяти, основанная на текущих параметрах и закономерностях использования памяти. Допустимы следующие значения:<br /><br /> grow<br /><br /> shrink<br /><br /> stable|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   
  
## <a name="see-also"></a>См. также  

  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


