---
description: sys. dm_pdw_hadoop_operations (Transact-SQL)
title: sys. dm_pdw_hadoop_operations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6665a23aa3b3a30aee3c80cfbd8ed139d6784d3e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481882"
---
# <a name="sysdm_pdw_hadoop_operations-transact-sql"></a>sys. dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит по одной строке для каждого задания Map-reduce, которое передается в Hadoop в ходе выполнения [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] запроса к внешней таблице Hadoop. Каждое задание Map-reduce представляет один из предикатов в запросе. Используется, только если предикат включение включен для запросов к внешним таблицам Hadoop.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Идентификатор для этой внешней операции Hadoop.|То же, что и идентификатор в [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Индекс шага запроса, который ссылается на эту операцию Hadoop.|То же, что и step_index в [sys. dm_pdw_request_steps &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Описывает тип внешней операции.|"Внешняя операция Hadoop"|  
|operation_name|**nvarchar(4000)**|Идентификатор задания для задания Map-reduce. Это значение возвращается службой Hadoop после [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] отправки задания.||  
|map_progress|**float**|Процент входных данных, которые были использованы заданием Map до сих пор.|Число с плавающей запятой между, включая, 0 и 100.|  
|reduce_progress|**int**|Процент завершенного задания сокращения.|Число с плавающей запятой между, включая, 0 и 100.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;&#41;Transact-SQL ](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
