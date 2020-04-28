---
title: sys. dm_db_mirroring_auto_page_repair (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_mirroring_auto_page_repair_TSQL
- sys.dm_db_mirroring_auto_page_repair_TSQL
- sys.dm_db_mirroring_auto_page_repair
- dm_db_mirroring_auto_page_repair
dev_langs:
- TSQL
helpviewer_keywords:
- automatic page repair
- database mirroring [SQL Server], automatic page repair
- sys.dm_db_mirroring_auto_page_repair dynamic management view
ms.assetid: 49f0fc2a-e25e-47e1-a135-563adb509af1
author: stevestein
ms.author: sstein
ms.openlocfilehash: e08aa031af0bd8c9d5c5ad012d11c534281f92f3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017915"
---
# <a name="database-mirroring---sysdm_db_mirroring_auto_page_repair"></a>Зеркальное отображение базы данных — sys. dm_db_mirroring_auto_page_repair
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждой попытки автоматического восстановления страниц во всех зеркально отображаемых баз данных на экземпляре сервера. Представление содержит строки, связанные с последними попытками автоматического восстановления страниц в определенной зеркальной базе данных, с максимальным количеством 100 строк на каждую базу данных. По достижении максимального значения строка для следующей попытки автоматического восстановления страниц заменяет одну из существующих записей. В следующей таблице дается определение значения столбцов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, которой принадлежит строка.|  
|**file_id**|**int**|Идентификатор файла, в котором находится страница.|  
|**page_id**|**bigint**|Идентификатор страницы в файле.|  
|**error_type**|**int**|Тип ошибки. Допустимые значения:<br /><br /> **-** 1 = все ошибки оборудования 823<br /><br /> 1 = ошибки 824, кроме неверной контрольной суммы или разрыва страницы (например, неверный идентификатор страницы);<br /><br /> 2 = неверная контрольная сумма;<br /><br /> 3 = разрыв страницы.|  
|**page_status**|**int**|Состояние попытки восстановления страниц:<br /><br /> 2 = в очереди на запрос к участнику;<br /><br /> 3 = запрос отправлен участнику;<br /><br /> 4 = в очереди на автоматическое восстановление страниц (от участника получен ответ);<br /><br /> 5 = автоматическое восстановление страниц успешно завершено, и страница должна быть готова к использованию;<br /><br /> 6 = непоправимо повреждена. Во время попытки восстановления страниц произошла ошибка, например потому, что страница также повреждена на участнике, или участник не подключен, или возникли проблемы с сетью. Это состояние не окончательное: если на странице вновь встретится повреждение, она будет запрошена у участника.|  
|**modification_time**|**datetime**|Время последнего изменения состояния страницы.|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Автоматическое восстановление страниц &#40;группы доступности:&#41;зеркального отображения базы данных](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [suspect_pages &#40;Transact-SQL&#41;](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [Управление таблицей suspect_pages (SQL Server)](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  


