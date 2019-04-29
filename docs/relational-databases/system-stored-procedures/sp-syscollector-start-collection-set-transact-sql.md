---
title: sp_syscollector_start_collection_set (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_start_collection_set_TSQL
- sp_syscollector_start_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_start_collection_set
ms.assetid: d8357180-f51e-4681-99f9-0596fe2d2b53
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e2806d42e58bbd60b962f83e8ab58fbe4511e44b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001741"
---
# <a name="spsyscollectorstartcollectionset-transact-sql"></a>sp_syscollector_start_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запускает набор элементов сбора в том случае, если сборщик данных уже включен, но набор сбора еще не работает. Если сборщик не включен, включите сборщик данных, выполнив [sp_syscollector_enable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md) и затем использовать эту хранимую процедуру для запуска набора сбора.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_start_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @collection_set_id = ] collection_set_id` — Это уникальный локальный идентификатор набора элементов сбора. *collection_set_id* — **int** со значением по умолчанию NULL. *collection_set_id* должен иметь значение, если *имя* имеет значение NULL.  
  
`[ @name = ] 'name'` — Имя набора элементов сбора. *имя* — **sysname** со значением по умолчанию NULL. *имя* должен иметь значение, если *collection_set_id* имеет значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Функция sp_syscollector_create_collection_set должна выполняться в контексте системной базы данных msdb, а агент SQL Server должен быть включен.  
  
 Эта процедура завершится с ошибкой при выполнении для набора элементов сбора, для которого нет расписания. Если набор сбора не имеет расписания (так как его установлен режим сбора без кэширования, например), используйте [sp_syscollector_run_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql.md) хранимую процедуру для запуска набора сбора.  
  
 Данная процедура включает задания сбора и передачи данных для заданного набора сбора, а также немедленно запускает задание агента сбора, если для этого набора сбора значение параметра равно 0 (режим сбора с кэшированием). Дополнительные сведения см. в разделе [sp_syscollector_create_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 Если набор сбора не содержит каких-либо элементов сбора, эта операция не действует. В качестве предупреждения возвращается ошибка 14685.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_operator. Если набор сбора не имеет учетной записи-посредника, требуется членство в предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 В следующем примере запуск набора элементов сбора осуществляется с помощью его идентификатора.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
