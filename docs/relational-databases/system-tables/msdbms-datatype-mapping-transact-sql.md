---
title: MSdbms_datatype_mapping (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_datatype_mapping_TSQL
- MSdbms_datatype_mapping
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype_mapping system table
ms.assetid: 13289a0b-dfb0-4771-ad80-4c5f83cded99
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6d513da9588b8ae8fb4f20ece11390c29d71bcf9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817054"
---
# <a name="msdbmsdatatypemapping-transact-sql"></a>MSdbms_datatype_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_datatype_mapping** таблица содержит допустимые сопоставления типов данных из типа данных в системы управления базами данных (СУБД) для одного или нескольких конкретных типов данных в целевой СУБД. Эта таблица хранится в **msdb** базы данных и используется для разнородной репликации базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**datatype_mapping_id**|**int**|Идентифицирует каждое уникальное сопоставление типа данных.|  
|**map_id**|**int**|Идентифицирует исходный тип данных.|  
|**dest_datatype_id**|**int**|Идентифицирует целевой тип данных.|  
|**dest_precision**|**bigint**|Определяет точность целевого типа данных, где значение NULL обозначает, что точность не используется, и значение **-1** означает, что используется точность исходного типа данных.|  
|**dest_scale**|**int**|Определяет масштаб целевого типа данных, где значение NULL обозначает, что масштаб не используется, и значение **-1** означает, что используется масштаб исходного типа данных.|  
|**dest_length**|**bigint**|Определяет длину целевого типа данных, где значение NULL обозначает, что длина не используется, и значение **-1** означает, что используется длина исходного типа данных.|  
|**dest_nullable**|**bit**|Показывает, допускает ли целевой столбец в данном сопоставлении значения NULL; причем NULL означает, что это определение не требуется.|  
|**dest_createparams**|**int**|Битовая карта, описывающая, какое сочетание длины, точности и масштаба применимо для каждого типа данных:<br /><br /> **0x1** = точность.<br /><br /> **0x2** = масштаб.<br /><br /> **0x4** = длина.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
