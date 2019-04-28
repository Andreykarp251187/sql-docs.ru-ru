---
title: sys.dm_pdw_exec_requests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 72c449ee83798a99109029fc2d0b91e2b8c1e2b6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62691325"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех запросов в настоящее время или недавно active в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. В ней перечислены одну строку для каждого запроса или запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|Уникально для всех запросов в системе.|  
|session_id|**nvarchar(32)**|Уникальный числовой идентификатор, связанный с сеансом, в котором был запущен этот запрос. См. в разделе [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Текущее состояние запроса.|«Выполняется», «Приостановлено», «Завершено», «Отменено», «Сбой».|  
|submit_time|**datetime**|Время отправки запроса для выполнения.|Допустимые **datetime** меньше или равна start_time и текущего времени.|  
|start_time|**datetime**|Время начала выполнения запроса.|Значение NULL для запросов в очереди; в противном случае допустимый **datetime** меньше или равна текущее время.|  
|end_compile_time|**datetime**|Время, обработчик завершения компиляции запроса.|Значение NULL для запросов, которые еще не были скомпилированы еще; в противном случае допустимый **datetime** меньше, чем start_time и меньше или равно текущее время.|
|end_time|**datetime**|Время, по которому выполнения запроса, не удалось, была завершена или отменена.|Значение NULL для запросов в очереди, либо active; в противном случае допустимый **datetime** меньше или равна текущее время.|  
|total_elapsed_time|**int**|Время затраченное на выполнение с момента запуска запроса, в миллисекундах.|Между 0 и разница между start_time и end_time.</br></br> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будут продолжать максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»</br></br> Максимальное значение в миллисекундах совпадает 24,8 дня.|  
|Метка|**nvarchar(255)**|Строку необязательную метку, связанную с некоторые операторы запроса SELECT.|Любая строка, содержащая «a – z», «A – Z», "0-9", «_».|  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибку, связанную с запросом, если таковые имеются.|См. в разделе [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); значение NULL, если не возникло ошибок.|  
|database_id|**int**|Идентификатор базы данных, используемой явный контекст (например, используйте DB_X).|См. в разделе с кодом в [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Содержит полный текст запроса, предоставленных пользователю.|Любой допустимый текст, запроса или запроса. Запросы, в которых превышает 4 000 байт, усекаются.|  
|resource_class|**nvarchar(20)**|Класс ресурсов для данного запроса. См. связанные **concurrency_slots_used** в [sys.dm_pdw_resource_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).  Дополнительные сведения о классах ресурсов см. в разделе [ресурсов классов и управление рабочими нагрузками](https://docs.microsoft.com/azure/sql-data-warehouse/resource-classes-for-workload-management) |Статические классы ресурсов</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Динамические классы ресурсов</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|важность (классификации рабочей нагрузки доступна в предварительной версии для Gen2 хранилище данных SQL. Предварительные версии таких функций, как управленческая классификация рабочих нагрузок и приоритет рабочих нагрузок доступны в сборках, выпущенных после 9 апреля 2019 г.  Чтобы протестировать функцию управления рабочими нагрузками, следует использовать сборки, выпущенные после этой даты.  Чтобы определить, если построение является возможность управления рабочими нагрузками, выполните select @@version при подключении к экземпляру хранилища данных SQL.)|**nvarchar(32)**|Отправлено важность запроса. Запросы с низким важности останется в очереди в приостановленном состоянии, если выше важности запросы отправляются.  Запросы с высокой важностью будет выполняться до нижней важность запросов, отправленных ранее.  Дополнительные сведения о важности, см. в разделе [важность рабочих нагрузок](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-workload-importance).  |NULL</br>Низкий</br>below_normal</br>Обычный (по умолчанию)</br>above_normal</br>Высокий уровень|
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе метаданных в [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) раздела.   
  
## <a name="permissions"></a>Разрешения

 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="security"></a>безопасность

 sys.dm_pdw_exec_requests не фильтрует результаты запроса в соответствии с конкретной базы данных разрешения. Имена входа с разрешением VIEW SERVER STATE можно получить результаты запроса результаты для всех баз данных  
  
>[!WARNING]  
>Злоумышленник может использовать sys.dm_pdw_exec_requests для получения сведений о конкретных объектов базы данных, путем простого наличия разрешения VIEW SERVER STATE и при отсутствии разрешений для базы данных.  
  
## <a name="see-also"></a>См. также

 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md) 
