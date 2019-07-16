---
title: sys.trace_events (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_events_TSQL
- trace_events
- sys.trace_events
- sys.trace_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_events catalog view
ms.assetid: e7d2c5df-0e17-4e94-9d41-d36c7ee60662
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 17bf8ff345e2869d6189491cbf09df49312e1f75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106663"
---
# <a name="systraceevents-transact-sql"></a>sys.trace_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sys.trace_events** представление каталога содержит список всех событий трассировки SQL. Эти события трассировки не изменились в данной версии компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
> **ВАЖНО!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте представления каталога расширенных событий.  
  
 Дополнительные сведения об этих событиях трассировки см. в разделе [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**trace_event_id**|**smallint**|Уникальный идентификатор события. Этот столбец присутствует также в **sys.trace_event_bindings** и **sys.trace_subclass_values** представления каталога.|  
|**category_id**|**smallint**|Идентификатор категории события. Этот столбец присутствует также в **sys.trace_categories** представления каталога.|  
|**name**|**nvarchar(128)**|Уникальное имя события. Этот аргумент не локализуется.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys.trace_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys.trace_event_bindings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys.trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
