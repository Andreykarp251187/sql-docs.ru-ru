---
title: log_shipping_monitor_error_detail (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_error_detail_TSQL
- log_shipping_monitor_error_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_error_detail system table
ms.assetid: 0c38a625-60d2-4ee2-bcf3-2ba367914220
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e441e5165262a4455e34cb9a0adb55b9679578f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67990052"
---
# <a name="logshippingmonitorerrordetail-transact-sql"></a>log_shipping_monitor_error_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сохраняет подробное описание ошибок для заданий доставки журналов. Эта таблица хранится в **msdb** базы данных.  
  
 Таблицы, связанные с ведением журналов и мониторингом, также используются на сервере-источнике и серверах-получателях.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|Первичный идентификатор для резервирования или вторичный идентификатор для копирования или восстановления.|  
|**agent_type**|**tinyint**|Тип задания доставки журналов:<br /><br /> 0 = резервирование;<br /><br /> 1 = копирование;<br /><br /> 2 = восстановление.|  
|**session_id**|**int**|Идентификатор сеанса для задания резервирования/копирования/восстановления.|  
|**database_name**|**sysname**|Имя базы данных, связанной с данной записью об ошибке. База данных-источник для резервирования, база данных-получатель для восстановления или пустая для копирования.|  
|**sequence_number**|**int**|Добавочное число, указывающее правильный порядок сведений для ошибок, описываемых несколькими записями.|  
|**log_time**|**datetime**|Дата и время создания записи.|  
|**log_time_utc**|**datetime**|Дата и время создания записи по Гринвичу.|  
|**message**|**nvarchar**|Текст сообщения.|  
|**источник**|**nvarchar**|Источник сообщения об ошибке или событии.|  
|**help_url**|**nvarchar**|URL-адрес, по которому в случае доступности могут быть найдены дополнительные сведения о данной ошибке.|  
  
## <a name="remarks"></a>Примечания  
 Эта таблица содержит подробные сведения об ошибках для агентов доставки журнала. Каждая ошибка регистрируется как последовательность исключений. Может быть несколько ошибок (последовательности) для каждого сеанса агента.  
  
 Помимо хранения на удаленном сервере мониторинга, сведения, относящиеся к серверу-источнику хранится на сервере-источнике в его **log_shipping_monitor_error_detail** таблицы и сведения, связанные с сервером-получателем также хранится на сервере-получателе в его **log_shipping_monitor_error_detail** таблицы.  
  
 Чтобы идентифицировать сеанс агента, используйте столбцы **agent_id**, **agent_type**, и **session_id**. Сортировать по **log_time** информацию об ошибках, в том порядке, в котором они были зарегистрированы.  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [log_shipping_monitor_history_detail &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql.md)   
 [sp_cleanup_log_shipping_history (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
