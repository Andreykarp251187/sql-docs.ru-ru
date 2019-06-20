---
title: sys.spatial_reference_systems (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c2ab77dbaf90edf1421a0d15073258c370de4c7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62856959"
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Список систем пространственной ссылки (SRID), поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|Идентификаторы SRID, поддерживаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|authority_name|**nvarchar(128)**|Центр сертификации SRID.|  
|authorized_spatial_reference_id|**int**|Идентификатор SRID, заданный центром сертификации, в **authority_name**.|  
|well_known_text|**nvarchar(4000)**|Представление SRID в формате WKT.|  
|unit_of_measure|**nvarchar(128)**|Имя единицы измерения.|  
|unit_conversion_factor|**float**|Длина единицы измерения в метрах.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
