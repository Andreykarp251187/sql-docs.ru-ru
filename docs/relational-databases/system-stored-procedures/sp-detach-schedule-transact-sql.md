---
title: процедуру sp_detach_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_detach_schedule
- sp_detach_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_detach_schedule
ms.assetid: 9a1fc335-1bef-4638-a33a-771c54a5dd19
author: stevestein
ms.author: sstein
ms.openlocfilehash: aed989cc09922b7b480a7dd7b3ca6820d6b77ab2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936745"
---
# <a name="spdetachschedule-transact-sql"></a>sp_detach_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет ассоциативную связь между расписанием и заданием.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_detach_schedule   
     { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
       { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @delete_unused_schedule = ] delete_unused_schedule   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id` Идентификационный номер задания, чтобы удалить расписание из задания. *job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'` Имя, чтобы удалить расписание из задания. *имя_задания* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
`[ @schedule_id = ] schedule_id` Идентификационный номер расписания, которое удаляется из задания. *schedule_id* — **int**, значение по умолчанию NULL.  
  
`[ @schedule_name = ] 'schedule_name'` Имя расписания, которое удаляется из задания. *schedule_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *schedule_id* или *schedule_name* должен быть указан, но не оба аргумента одновременно.  
  
`[ @delete_unused_schedule = ] delete_unused_schedule` Указывает, следует ли удалять неиспользуемые расписания заданий. *delete_unused_schedule* — **бит**, значение по умолчанию **0**, означающее, что все расписания будут сохранены, даже если задания не ссылаться на них. Если значение **1**, неиспользуемые расписания заданий удаляются в том случае, если в них нет заданий.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Заметьте, что владелец задания может присоединять его к расписанию и отсоединять от расписания, не являясь владельцем расписания. Однако расписание нельзя удалить, если в результате отсоединения в нем не останется ни одного задания и вызов выполняется не владельцем расписания.  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет, является ли пользователь владельцем расписания. Только члены **sysadmin** предопределенной роли сервера могут удалять расписания из заданий, которыми владеют другие пользователи.  
  
## <a name="examples"></a>Примеры  
 Следующий пример удаляет ассоциативную связь между расписанием `'NightlyJobs'` и заданием `'BackupDatabase'`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_detach_schedule  
    @job_name = 'BackupDatabase',  
    @schedule_name = 'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)  
  
  
