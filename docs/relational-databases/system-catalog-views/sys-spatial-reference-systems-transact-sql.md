---
title: sys. spatial_reference_systems (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7beb40f3810a4e9793eaadd912a501edacfa222e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833988"
---
# <a name="sysspatial_reference_systems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Список систем пространственной ссылки (SRID), поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|Идентификаторы SRID, поддерживаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|authority_name|**nvarchar(128)**|Центр сертификации SRID.|  
|authorized_spatial_reference_id|**int**|SRID, заданный в центре **authority_name**.|  
|well_known_text|**nvarchar(4000)**|Представление SRID в формате WKT.|  
|unit_of_measure|**nvarchar(128)**|Имя единицы измерения.|  
|unit_conversion_factor|**float**|Длина единицы измерения в метрах.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
