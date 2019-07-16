---
title: sp_help_notification (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_notification
- sp_help_notification_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_notification
ms.assetid: 0273457f-9d2a-4a6f-9a16-6a6bf281cba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 630c2f90085cedfbb5c59ba395c7d0d9ae9d9643
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906098"
---
# <a name="sphelpnotification-transact-sql"></a>sp_help_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит список предупреждений для заданного оператора или список операторов для заданного предупреждения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_notification  
     [ @object_type = ] 'object_type' ,  
     [ @name = ] 'name' ,  
     [ @enum_type = ] 'enum_type' ,   
     [ @notification_method = ] notification_method   
     [ , [ @target_name = ] 'target_name' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @object_type = ] 'object_type'` Тип возвращаемых данных. *object_type*— **char(9)** , не имеет значения по умолчанию. *object_type* может принимать значение ALERTS, перечисляя предупреждения, назначенные указанному имени оператора *,* или OPERATORS, перечисляя операторов, ответственных за указанное имя предупреждения *.*  
  
`[ @name = ] 'name'` Имя оператора (если *object_type* имеет значение OPERATORS) или имя предупреждения (если *object_type* имеет значение ALERTS). *имя* — **sysname**, не имеет значения по умолчанию.  
  
`[ @enum_type = ] 'enum_type'` *Object_type*сведений, возвращаемых. *enum_type* в большинстве случаев имеет значение ACTUAL. *enum_type*— **char(10)** , по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|ACTUAL|Перечисляет только *object_types* связанные с *имя*.|  
|ALL|Перечисляет все*object_types* включая те, которые не связаны с *имя*.|  
|TARGET|Перечисляет только *object_types* совпадающие с предоставленным *target_name*, независимо от ассоциации с*имя*.|  
  
`[ @notification_method = ] notification_method` Числовое значение, которое определяет метод уведомления для возврата столбцов. *notification_method* — **tinyint**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Электронная почта: возвращает только **use_email** столбца.|  
|**2**|Пейджер: возвращает только **use_pager** столбца.|  
|**4**|NetSend: возвращает только **use_netsend** столбца.|  
|**7**|Все: возвращает все столбцы.|  
  
`[ @target_name = ] 'target_name'` Имя искомого предупреждения (если *object_type* имеет значение ALERTS) или имя искомого оператора (если *object_type* имеет значение OPERATORS). *target_name* требуется только в том случае, если *enum_type* является целевым ОБЪЕКТОМ. *target_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-valves"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если *object_type* — **ОПОВЕЩЕНИЯ**, в результирующем наборе перечислены все предупреждения для данного оператора.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Идентификатор предупреждения.|  
|**alert_name**|**sysname**|Имя предупреждения.|  
|**use_email**|**int**|Уведомление оператора происходит по электронной почте.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**use_pager**|**int**|Уведомление оператора происходит по пейджеру.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**use_netsend**|**int**|Уведомление оператора происходит с помощью сетевого всплывающего окна.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**has_email**|**int**|Количество уведомлений, отправленных для данного предупреждения по электронной почте.|  
|**has_pager**|**int**|Количество уведомлений, отправленных для данного предупреждения по пейджеру.|  
|**has_netsend**|**int**|Число **команды net send** уведомлений, отправленных для данного предупреждения.|  
  
 Если **object_type** — **ОПЕРАТОРЫ**, в результирующем наборе перечислены все операторы для данного предупреждения.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**operator_id**|**int**|Идентификационный номер оператора.|  
|**имя_оператора**|**sysname**|Имя оператора.|  
|**use_email**|**int**|Уведомление оператора происходит по электронной почте.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**use_pager**|**int**|Уведомление оператора происходит по пейджеру.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**use_netsend**|**int**|Для уведомления оператора используется всплывающее сетевое сообщение.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**has_email**|**int**|У оператора есть адрес электронной почты.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**has_pager**|**int**|У оператора есть адрес пейджера.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**has_netsend**|**int**|Оператор имеет настроенное уведомление net send.<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
  
## <a name="remarks"></a>Примечания  
 Эта хранимая процедура должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-alerts-for-a-specific-operator"></a>A. Список предупреждений для указанного оператора  
 В следующем примере возвращаются все предупреждения, для которых оператор `François Ajenstat` получает уведомления любого вида.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_notification   
    @object_type = N'ALERTS',  
    @name = N'François Ajenstat',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
### <a name="b-listing-operators-for-a-specific-alert"></a>Б. Список операторов для указанного предупреждения  
 В следующем примере возвращаются все операторы, которые получают уведомления любого вида для предупреждения `Test Alert`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_notification  
    @object_type = N'OPERATORS',  
    @name = N'Test Alert',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
