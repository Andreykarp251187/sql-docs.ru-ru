---
title: sys.resource_governor_workload_groups (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_workload_groups
- resource_governor_workload_groups_TSQL
- sys.resource_governor_workload_groups_TSQL
- resource_governor_workload_groups
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_workload_groups catalog view
ms.assetid: 619ba4b7-868f-4784-b527-ec1dfd703c4f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0f80d9ba8f5b5a1e81949d0fb2ea4b1d9bca59d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904448"
---
# <a name="sysresourcegovernorworkloadgroups-transact-sql"></a>sys.resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает хранимую в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] конфигурацию группы рабочей нагрузки. Каждая группа рабочей нагрузки может иметь подписку только на один и только один пул ресурсов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|group_id|**int**|Уникальный идентификатор группы рабочей нагрузки. Не допускает значение NULL.|  
|name|**sysname**|Имя группы рабочей нагрузки. Не допускает значение NULL.|  
|importance|**sysname**|**Примечание.** Важность применима только к группам рабочей нагрузки в одном пуле ресурсов.<br /><br /> Относительная важность запроса в данной группе рабочей нагрузки. Важность представлена одним из следующих значений, причем значением по умолчанию является MEDIUM. НИЗКИЙ, СРЕДНИЙ, ВЫСОКИЙ.<br /><br /> Не допускает значение NULL.|  
|request_max_memory_grant_percent|**int**|Максимальный объем предоставляемой памяти, в процентах, для отдельного запроса. Значение по умолчанию — 25. Не допускает значение NULL.<br /><br /> **Примечание.** Если этот параметр имеет более 50 процентов, большие запросы будут выполняться по одному. Поэтому повышается риск возникновения ошибки нехватки памяти при выполнении запроса.|  
|request_max_cpu_time_sec|**int**|Максимально допустимое использование ЦП, в секундах, для отдельного запроса. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.<br /><br /> **Примечание.** Дополнительные сведения см. в разделе [Класс событий CPU Threshold Exceeded](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).|  
|request_memory_grant_timeout_sec|**int**|Время ожидания предоставления памяти, в секундах, для отдельного запроса. Для значения по умолчанию 0 используется внутреннее вычисление, основанное на стоимости запроса. Не допускает значение NULL.|  
|max_dop|**int**|Максимальная степень параллелизма для группы рабочей нагрузки. Для значения по умолчанию 0 используются глобальные параметры. Не допускает значение NULL.<br /><br /> **Узел:** Этот параметр переопределяет параметр запроса **maxdop**.|  
|group_max_requests|**int**|Максимальное число параллельных запросов. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.|  
|pool_id|**int**|Идентификатор пула ресурсов, используемого данной группой рабочей нагрузки.|  
|external_pool_id|**int**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор внешнего пула ресурсов, использующий данной группе рабочей нагрузки.|  
  
## <a name="remarks"></a>Примечания  
 Представление каталога отображает хранимые метаданные. Чтобы увидеть конфигурации, хранимой в памяти, используйте соответствующее динамическое административное представление [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md).  
  
 Сохраненная конфигурация и конфигурация, хранимая в памяти, могут различаться, если конфигурация регулятора ресурсов была изменена, но инструкция ALTER RESOURCE GOVERNOR RECONFIGURE не применялась.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешение VIEW ANY DEFINITION для просмотра содержимого и разрешение CONTROL SERVER для изменения содержимого.  
  
## <a name="see-also"></a>См. также  
 [sys.dm_resource_governor_workload_groups (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога регулятора ресурсов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)  
  
  
