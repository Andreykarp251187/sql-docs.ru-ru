---
title: sys.dm_hadr_instance_node_map (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sys.dm_hadr_instance_node_map_TSQL
- sys.sys.dm_hadr_instance_node_map
- sys.dm_hadr_instance_node_map_TSQL
- sys.dm_hadr_instance_node_map
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC
- sys.sys.dm_hadr_instance_node_map dynamic management view
ms.assetid: ccfaf62c-9f87-43cf-a5e7-8942e91dd041
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: edd2ea7a215f01c25539753dff4bd170cf9d422f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900422"
---
# <a name="sysdmhadrinstancenodemap-transact-sql"></a>sys.dm_hadr_instance_node_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Для каждого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором размещена реплика доступности, которая соединяется с соответствующей группы доступности Always On, то возвращается имя узла отказоустойчивого кластера Windows Server (WSFC), на котором размещена на экземпляре сервера. Это динамическое административное представление может использоваться следующим образом.  
  
-   Динамическое административное представление может оказаться полезным для обнаружения группы доступности с несколькими репликами доступности, размещенными на одном узле WSFC, поскольку такая конфигурация, которая может возникнуть после отработки отказа FCI в том случае, если группа доступности сконфигурирована неверно, не поддерживается. Дополнительные сведения см. в разделе [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).  
  
-   Когда несколько экземпляров SQL Server размещаются на одном узле WSFC, DLL-библиотека ресурсов через это динамическое административное представление определяет экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], к которому следует подключаться.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ag_resource_id**|**nvarchar(256)**|Уникальный идентификатор группы доступности в качестве ресурса в кластере WSFC.|  
|**instance_name**|**nvarchar(256)**|Имя -*server*/*экземпляр*-экземпляра сервера, на котором размещена реплика группы доступности.|  
|**node_name**|**nvarchar(256)**|Имя узла WSFC.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические представления управления и функции, связанные с группами доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Представления каталога групп доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
