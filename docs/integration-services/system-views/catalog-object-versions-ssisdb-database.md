---
title: catalog.object_versions (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b68fcc0cffada1ac895548a0c6858f0bde76fe6c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65714490"
---
# <a name="catalogobjectversions-ssisdb-database"></a>catalog.object_versions (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает версии объектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом выпуске в данном представлении поддерживаются только версии проектов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|Уникальный идентификатор версии объекта. Не гарантируется, что это число будет последовательным.|  
|object_id|**bigint**|Уникальный идентификатор объекта.|  
|object_type|**smallint**|Тип объекта. Для проектов отображается значение `20`.|  
|object_name|**sysname(nvarchar(128))**|Имя объекта.|  
|description|**nvarchar(1024)**|Описание проекта.|  
|created_by|**nvarchar(128)**|Имя пользователя, который добавил объект в каталог.|  
|created_time|**datetimeoffset**|Дата и время добавления объекта в каталог.|  
|restored_by|**nvarchar(128)**|Имя пользователя, который восстановил объект.|  
|last_restored_time|**datetimeoffset**|Дата и время последнего восстановления объекта.|  
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображается по одной строке для каждой из версий объекта в каталоге.  
  
## <a name="permissions"></a>Разрешения  
 Для просмотра строк в этом представлении необходимо иметь одно из следующих разрешений:  
  
-   разрешение READ на объект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**.  
  
> [!NOTE]  
>  Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
