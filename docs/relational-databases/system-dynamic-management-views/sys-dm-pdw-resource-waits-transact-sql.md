---
title: sys.dm_pdw_resource_waits (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a43ce9a2-5261-41e3-97f0-555ba05ebed9
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 35868774efc7083b835bb6f44b6c71cbffc7ae2c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899218"
---
# <a name="sysdmpdwresourcewaits-transact-sql"></a>sys.dm_pdw_resource_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Отображает ожидания сведения для всех типов ресурсов в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Позиция в списке ожидания запроса.|Отсчитываемый от нуля порядковый номер. Это не является уникальным во всех записях ожидания.|  
|session_id|**nvarchar(32)**|Идентификатор сеанса, в котором возникло состояние ожидания.|См. в разделе session_id в [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|type|**nvarchar(255)**|Тип ожидания, которые представляет эта запись.|Возможные значения:<br /><br /> Соединение<br /><br /> Локальные запросы параллелизма<br /><br /> Распределенные запросы параллелизма<br /><br /> DMS параллелизма<br /><br /> Резервного копирования параллелизма|  
|object_type|**nvarchar(255)**|Тип объекта, который зависит от ожидания.|Возможные значения:<br /><br /> **ОБЪЕКТ**<br /><br /> **DATABASE**<br /><br /> **SYSTEM**<br /><br /> **SCHEMA**<br /><br /> **ПРИЛОЖЕНИЯ**|  
|object_name|**nvarchar(386)**|Имя или идентификатор GUID для указанного объекта, который был подвергнут ожидания.|Таблицы и представления отображаются имена из трех частей.<br /><br /> Индексы и статистику отображаются четырехкомпонентные имена.<br /><br /> Имена субъектов и баз данных являются строковыми именами.|  
|request_id|**nvarchar(32)**|Идентификатор запроса, в котором произошло состояния ожидания.|Идентификатор QID запроса.<br /><br /> Идентификатор GUID для запросов на загрузку.|  
|request_time|**datetime**|Время, с которого была запрошена блокировка или ресурса.||  
|acquire_time|**datetime**|Время, с которого была получена блокировка или ресурса.||  
|state|**nvarchar(50)**|Состояние из состояния ожидания.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Приоритет элемента ожидания.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|concurrency_slots_used|**int**|Число слотов (32 max), зарезервированный для данного запроса.|1 — для SmallRC<br /><br /> 3 — для MediumRC<br /><br /> 7 для LargeRC<br /><br /> 22 - для XLargeRC|  
|resource_class|**nvarchar(20)**|Класс ресурсов для данного запроса.|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
