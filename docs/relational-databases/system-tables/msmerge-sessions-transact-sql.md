---
title: MSmerge_sessions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_sessions
- MSmerge_sessions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_sessions system table
ms.assetid: 09ada8fc-c148-4379-9524-7826b1b0216c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4290f3d41cf4e5210a7fde98132db533f8336810
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903708"
---
# <a name="msmergesessions-transact-sql"></a>MSmerge_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_sessions** таблица содержит строки журнала с результатами предыдущих сеансов заданий агента слияния. При каждом запуске агента слияния к указанной таблице добавляется новая строка. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор сеанса задания агента слияния.|  
|**agent_id**|**int**|Идентификатор агента слияния.|  
|**start_time**|**datetime**|Время выполнения текущего задания.|  
|**end_time**|**datetime**|Время выполнения завершенного задания.|  
|**duration**|**int**|Общая продолжительность сеанса задания в секундах.|  
|**delivery_time**|**int**|Время, затраченное на применение пакета изменений, в секундах.|  
|**upload_time**|**int**|Время, затраченное на передачу изменений издателю, в секундах.|  
|**download_time**|**int**|Время, затраченное на загрузку изменений подписчиком, в секундах.|  
|**delivery_rate**|**float**|Среднее число команд, передаваемых в секунду.|  
|**time_remaining**|**int**|Предполагаемое время до окончания текущего сеанса в секундах.|  
|**percent_complete**|**decimal**|Предполагаемый процент уже примененных в течение данного сеанса всех изменений.|  
|**upload_inserts**|**int**|Количество изменений, примененных на издателе.|  
|**upload_updates**|**int**|Количество обновлений, примененных на издателе.|  
|**upload_deletes**|**int**|Количество объектов, удаленных с издателя.|  
|**upload_conflicts**|**int**|Количество неполадок, возникших во время применения изменений на издателе.|  
|**upload_conflicts_resolved**|**int**|Количество успешно разрешенных неполадок, возникших во время применения изменений на издателе.|  
|**upload_rows_retried**|**int**|Количество строк, повторно передаваемых издателю.|  
|**download_inserts**|**int**|Количество изменений, примененных на подписчике.|  
|**download_updates**|**int**|Количество обновлений, примененных на подписчике.|  
|**download_deletes**|**int**|Количество объектов, удаленных с подписчика.|  
|**download_conflicts**|**int**|Количество неполадок, возникших во время применения изменений на подписчике.|  
|**download_conflicts_resolved**|**int**|Количество успешно разрешенных неполадок, возникших во время применения изменений на подписчике.|  
|**download_rows_retried**|**int**|Количество строк, повторно передаваемых подписчику.|  
|**schema_changes**|**int**|Количество изменений, примененных в схеме в течение сеанса.|  
|**metadata_rows_cleanedup**|**int**|Количество строк метаданных, очищенных за сеанс.|  
|**runstatus**|**int**|Состояние выполнения:<br /><br /> **1** = start.<br /><br /> **2** = успешно.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействует.<br /><br /> **5** = повторных попыток.<br /><br /> **6** = неуспешное завершение.|  
|**estimated_upload_changes**|**int**|Предполагаемое количество изменений, которые необходимо применить на издателе.|  
|**estimated_download_changes**|**int**|Предполагаемое количество изменений, которые необходимо применить на подписчике.|  
|**connection_type**|**int**|Тип подключения, используемого для загрузки:<br /><br /> **1** = локальная сеть (LAN).<br /><br /> **2** = коммутируемое сетевое соединение.<br /><br /> **3** = веб-синхронизации.|  
|**timestamp**|**timestamp**|Столбец отметок времени этой таблицы.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
