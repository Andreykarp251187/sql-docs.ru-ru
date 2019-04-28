---
title: sys.dm_pdw_exec_sessions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/22/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 331bb44faa2938241de98a6bff08f1e660583c4e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689831"
---
# <a name="sysdmpdwexecsessions-transact-sql"></a>sys.dm_pdw_exec_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех сеансах в настоящее время или недавно открытые на устройстве. Он содержит одну строку для каждого сеанса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|Идентификатор текущего запроса или запроса последнего выполнения (если сеанс ЗАВЕРШЕН и выполнении запроса во время завершения). Ключ для этого представления.|Уникальный во всех сеансах в системе.|  
|status|**nvarchar(10)**|Для текущих сеансов определяет ли сеанс в настоящий момент активно или простоя. Для прошедших сеансах работы может отображаться состояние сеанса закрытым или уничтоженным, (если сеанс было принудительно закрыто).|«АКТИВНО», «ЗАКРЫТО», «ПРОСТАИВАЕТ», «ЗАВЕРШЕНО»|  
|request_id|**nvarchar(32)**|Идентификатор текущего запроса или выполнения последнего запроса.|Уникально для всех запросов в системе. Значение NULL, если не будет выполнено.|  
|security_id|**varbinary(85)**|Идентификатор безопасности участника, для запуска сеанса.||  
|login_name|**nvarchar(128)**|Имя входа участника, для запуска сеанса.|Любая строка, соответствующие соглашениям об именах пользователей.|  
|login_time|**datetime**|Дата и время, в которой пользователь вошел в систему, и этот сеанс был создан.|Допустимые **datetime** до текущего времени.|  
|query_count|**int**|Число запросов/requeststhis сеанса запускался с момента создания снимков.|Больше или равно 0.|  
|is_transactional|**bit**|Фиксирует сеанс находится ли в рамках транзакции или нет.|0 для автоматической фиксации, 1 для транзакций.|  
|client_id|**nvarchar(255)**|Записывает сведения о клиенте для сеанса.|Любая допустимая строка.|  
|APP_NAME|**nvarchar(255)**|Записывает сведения об имени приложения, при необходимости задать как часть процесса соединения.|Любая допустимая строка.|  
|sql_spid|**int**|Идентификатор SPID. Используйте `session_id` этого сеанса. Используйте `sql_spid` столбца для присоединения к **sys.dm_pdw_nodes_exec_sessions**.<br /><br /> **\*\* Предупреждение \* \***  этот столбец содержит закрытые SPID.||  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе метаданных в [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) раздела.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение `VIEW SERVER STATE`.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
