---
title: sys.pdw_distributions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7deddb57cdc02410fe161728f45190492ac18a16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127554"
---
# <a name="syspdwdistributions-transact-sql"></a>sys.pdw_distributions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о распределениях на устройстве. В ней перечислены одну строку для каждого устройства распространения.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|Уникальный числовой идентификатор, связанная с распределением.<br /><br /> Ключ для этого представления.|от 1 до количество вычислительных узлов в устройстве, умноженное на количество распределений на каждом вычислительном узле.|  
|pdw_node_id|**int**|Идентификатор узла, в которой находится этот дистрибутив.|См. в разделе pdw_node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|name|**nvarchar(32)**|Строковый идентификатор, связанная с распределением, используемый в качестве суффикса для распределенных таблиц.|Строка, состоящая из «A – Z», «a – z», "0-9", «_», "-".|  
|position|**int**|Позиция распространения в узле соответствующего для других дистрибутивов на этом узле.|от 1 до количество распределений на узел.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
