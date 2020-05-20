---
title: sys. dm_io_cluster_shared_drives (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_cluster_shared_drives_TSQL
- sys.dm_io_cluster_shared_drives
- dm_io_cluster_shared_drives_TSQL
- dm_io_cluster_shared_drives
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_cluster_shared_drives dynamic management view
ms.assetid: c8fcced8-c780-49dc-99bd-6beb3ca532c4
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e89252effd6e8fbb14d800837328c9ff8042e0d3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827955"
---
# <a name="sysdm_io_cluster_shared_drives-transact-sql"></a>sys.dm_io_cluster_shared_drives (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Это представление возвращает имя каждого из общих устройств, если текущий экземпляр сервера является кластерным сервером. Если текущий экземпляр сервера некластеризованный, возвращает пустой набор строк.  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , используйте имя **sys. dm_pdw_nodes_io_cluster_shared_drives**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**DriveName**|**nchar(2)**|Тип устройства (буква диска), которое представляет отдельный диск, являющийся частью общего кластерного дискового массива. Столбец не может содержать значение NULL.|  
|**pdw_node_id**|**int**|**Применимо к**: сспдв<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="remarks"></a>Примечания  
 Если включена кластеризация, экземпляру отказоустойчивого кластера требуются файлы данных и журналов, расположенные на общих дисках, к которым можно получить доступ при переходе экземпляра на другой узел. Каждая строка представления соответствует одному общему диску, который используется кластеризованным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для хранения данных или файлов журнала для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут использоваться только диски, отображаемые в этом представлении. Диски, перечисленные в данном представлении, являются дисками в группе кластерных ресурсов, связанной с этим экземпляром.  
  
> [!NOTE]  
>  В следующей версии это представление будет упразднено. Вместо этого рекомендуется использовать [sys. dm_io_cluster_valid_path_names &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md) .  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен иметь на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешение VIEW SERVER STATE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано применение функции sys.dm_io_cluster_shared_drives для определения общих дисков на экземпляре кластеризованного сервера:  
  
```  
SELECT * FROM sys.dm_io_cluster_shared_drives;  
```  
  
 Результирующий набор:  
  
 DriveName  
  
 --------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>См. также  
 [sys. dm_io_cluster_valid_path_names &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [sys. dm_os_cluster_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys. fn_servershareddrives &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  
