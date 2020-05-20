---
title: sys. Servers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- servers_TSQL
- sys.servers_TSQL
- servers
- sys.servers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.servers catalog view
ms.assetid: 4e774ed9-4e83-4726-9f1d-8efde8f9feff
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 7b9cb03b97660bedc9c8e86cc72ae2bf9ebdd56d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832756"
---
# <a name="sysservers-transact-sql"></a>sys.servers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Содержит строку для каждого зарегистрированного или удаленного сервера и строку для локального сервера, имеющего **server_id** = 0.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Локальный идентификатор связанного сервера.|  
|**name**|**sysname**|Если **server_id** = 0, возвращаемое значение является именем сервера.<br /><br /> Если **server_id** > 0, возвращаемое значение является локальным именем связанного сервера.|  
|**продукта**|**sysname**|Имя продукта связанного сервера. Значение "SQL Server" указывает на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**поставщики**|**sysname**|Имя поставщика OLE DB для соединения со связанным сервером.|  
|**data_source**|**nvarchar(4000)**|Свойство соединения источника данных OLE DB.|  
|**расположение**|**nvarchar(4000)**|Свойство соединения местоположения OLE DB. NULL — если нет.|  
|**provider_string**|**nvarchar(4000)**|Свойство соединения строки поставщика OLE DB.<br /><br /> Имеет значение NULL, если только вызывающий не обладает разрешением ALTER ANY LINKED SERVER.|  
|**каталога**|**sysname**|Свойство соединения каталога OLE DB. NULL — если нет.|  
|**connect_timeout**|**int**|Время ожидания соединения в секундах; 0 — не указано.|  
|**query_timeout**|**int**|Время ожидания запроса в секундах; 0 — не указано.|  
|**is_linked**|**bit**|0 = это сервер со старым стилем, добавленный с помощью **sp_addserver**, с различными поведениями RPC и распределенных транзакций.<br /><br /> 1 = стандартный связанный сервер.|  
|**is_remote_login_enabled**|**bit**|Параметр RPC установлен на включение входящих удаленных имен входа для этого сервера.|  
|**is_rpc_out_enabled**|**bit**|Исходящие (от этого сервера) RPC включены.|  
|**is_data_access_enabled**|**bit**|Сервер включен для распределенных запросов.|  
|**is_collation_compatible**|**bit**|Параметры сортировки удаленных данных рассматриваются как совместимые с локальными данными, если нет доступных сведений о параметрах сортировки.|  
|**uses_remote_collation**|**bit**|При значении 1 используйте параметры сортировки, переданные удаленным сервером; в ином случае используйте параметры сортировки, указанные следующим столбцом.|  
|**collation_name**|**sysname**|Имя параметров сортировки, которые должны быть использованы, или NULL, если следует использовать локальные параметры сортировки.|  
|**lazy_schema_validation**|**bit**|При значении 1 проверка правильности схемы при запуске запроса не производится.|  
|**is_system**|**bit**|Доступ на этот сервер может получить только внутренняя система.|  
|**is_publisher**|**bit**|Сервер является издателем репликации.|  
|**is_subscriber**|**bit**|Сервер является подписчиком репликации.|  
|**is_distributor**|**bit**|Сервер является распространителем репликации.|  
|**is_nonsql_subscriber**|**bit**|Сервер является подписчиком репликации, отличным от SQL Server.|  
|**is_remote_proc_transaction_promotion_enabled**|**bit**|Если 1, вызов удаленной хранимой процедуры приводит к запуску распределенной транзакции и привлекает к выполнению транзакции MS DTC. Дополнительные сведения см. в статье [sp_serveroption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md).|  
|**modify_date**|**datetime**|Дата последнего изменения сведений о сервере.|  
  
## <a name="permissions"></a>Разрешения  
 Значение в **provider_string** всегда равно null, если у вызывающего объекта нет разрешения ALTER ANY Linked Server.  
  
 Для просмотра локального сервера разрешения не требуются (**server_id** = 0).  
  
 При создании связанного или удаленного сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает сопоставление имени входа по умолчанию с ролью сервера **Public** . Сопоставление имен входа по умолчанию означает, что все имена входа могут просматривать все связанные и удаленные серверы. Чтобы ограничить видимость этих серверов, удалите сопоставление имен входа по умолчанию, выполнив [sp_droplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md) и УКАЗАВ значение NULL для параметра *локаллогин* .  
  
 Если сопоставление удалено, только те пользователи, которые добавлены явно со связанным или удаленным именем входа, могут просматривать связанные или удаленные сервера соответственно.  Следующие разрешения необходимы для просмотра всех связанных и удаленных серверов после сопоставления имени входа по умолчанию:  
  
- `ALTER ANY LINKED SERVER` или `ALTER ANY LOGIN ON SERVER`  
- Членство в предопределенных ролях сервера **setupadmin** или **sysadmin**  
  
## <a name="see-also"></a>См. также  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога связанных серверов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addremotelogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)  
  
  
