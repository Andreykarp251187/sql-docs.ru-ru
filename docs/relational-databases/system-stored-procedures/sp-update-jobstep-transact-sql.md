---
title: sp_update_jobstep (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_jobstep
- sp_update_jobstep_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobstep
ms.assetid: e158802c-c347-4a5d-bf75-c03e5ae56e6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7914e3b56dd02d96c02835bf6b4dcc5eb90e8f4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084880"
---
# <a name="spupdatejobstep-transact-sql"></a>sp_update_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет настройку шага задания, которое используется для выполнения автоматических действий.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_jobstep   
     {   [@job_id =] job_id   
       | [@job_name =] 'job_name' } ,  
     [@step_id =] step_id  
     [ , [@step_name =] 'step_name' ]  
     [ , [@subsystem =] 'subsystem' ]   
     [ , [@command =] 'command' ]  
     [ , [@additional_parameters =] 'parameters' ]  
     [ , [@cmdexec_success_code =] success_code ]  
     [ , [@on_success_action =] success_action ]   
     [ , [@on_success_step_id =] success_step_id ]  
     [ , [@on_fail_action =] fail_action ]   
     [ , [@on_fail_step_id =] fail_step_id ]  
     [ , [@server =] 'server' ]   
     [ , [@database_name =] 'database' ]  
     [ , [@database_user_name =] 'user' ]   
     [ , [@retry_attempts =] retry_attempts ]  
     [ , [@retry_interval =] retry_interval ]   
     [ , [@os_run_priority =] run_priority ]  
     [ , [@output_file_name =] 'file_name' ]   
     [ , [@flags =] flags ]  
     [ ,  {   [ @proxy_id = ] proxy_id   
            | [ @proxy_name = ] 'proxy_name' }   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id` Идентификационный номер задания, к которому принадлежит шаг. *job_id*— **uniqueidentifier**, значение по умолчанию NULL. Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
`[ @job_name = ] 'job_name'` Имя задания, к которому принадлежит шаг. *имя_задания*— **sysname**, значение по умолчанию NULL. Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
`[ @step_id = ] step_id` Идентификационный номер для шага задания изменить. Этот номер не может быть изменен. *step_id*— **int**, не имеет значения по умолчанию.  
  
`[ @step_name = ] 'step_name'` — Это новое имя для шага. *step_name*— **sysname**, значение по умолчанию NULL.  
  
`[ @subsystem = ] 'subsystem'` Подсистема, используемая агентом Microsoft SQL Server для выполнения *команда*. *Подсистема* — **nvarchar(40)** , значение по умолчанию NULL.  
  
`[ @command = ] 'command'` Выполнение команд для выполнения с помощью *подсистемы*. *команда* — **nvarchar(max)** , значение по умолчанию NULL.  
  
`[ @additional_parameters = ] 'parameters'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @cmdexec_success_code = ] success_code` Значение, возвращенное **CmdExec** командой подсистемы, чтобы указать, что *команда* выполнена успешно. *success_code* — **int**, значение по умолчанию NULL.  
  
`[ @on_success_action = ] success_action` Действие, выполняемое, если шаг завершился успешно. *success_action* — **tinyint**, значение по умолчанию NULL, и может принимать одно из следующих значений.  
  
|Значение|Описание (действие)|  
|-----------|----------------------------|  
|**1**|Завершить с успешным выполнением.|  
|**2**|Завершить с ошибкой.|  
|**3**|Перейти к следующему шагу.|  
|**4**|Перейдите к шагу *success_step_id.*|  
  
`[ @on_success_step_id = ] success_step_id` Идентификационный номер шага данного задания, для выполнения, если шаг завершился успешно и *success_action* — **4**. *success_step_id* — **int**, значение по умолчанию NULL.  
  
`[ @on_fail_action = ] fail_action` Действие, выполняемое, если шаг завершился с ошибкой. *fail_action* — **tinyint**, значение по умолчанию NULL и может иметь одно из следующих значений.  
  
|Значение|Описание (действие)|  
|-----------|----------------------------|  
|**1**|Завершить с успешным выполнением.|  
|**2**|Завершить с ошибкой.|  
|**3**|Перейти к следующему шагу.|  
|**4**|Перейдите к шагу *fail_step_id **.*|  
  
`[ @on_fail_step_id = ] fail_step_id` Идентификационный номер шага данного задания, для выполнения, если шаг завершился с ошибкой и *fail_action* — **4**. *fail_step_id* — **int**, значение по умолчанию NULL.  
  
`[ @server = ] 'server'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *сервер* — **nvarchar(128)** , значение по умолчанию NULL.  
  
`[ @database_name = ] 'database'` Имя базы данных, в которой выполняется [!INCLUDE[tsql](../../includes/tsql-md.md)] шаг. *База данных*— **sysname**. Символы, заключенные в квадратные скобки ([ ]), являются недопустимыми. Значение по умолчанию — NULL.  
  
`[ @database_user_name = ] 'user'` Имя учетной записи пользователя, которая используется при выполнении [!INCLUDE[tsql](../../includes/tsql-md.md)] шаг. *пользователь*— **sysname**, значение по умолчанию NULL.  
  
`[ @retry_attempts = ] retry_attempts` Число повторных попыток для использования, если этот шаг завершается ошибкой. *retry_attempts*— **int**, значение по умолчанию NULL.  
  
`[ @retry_interval = ] retry_interval` Количество времени в минутах между попытками повтора. *интервал_повтора* — **int**, значение по умолчанию NULL.  
  
`[ @os_run_priority = ] run_priority` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @output_file_name = ] 'file_name'` Имя файла, в котором будет сохранен выход данного шага. *File_name* — **nvarchar(200)** , значение по умолчанию NULL. Данный аргумент действителен только с командами, запущенными в подсистемах [!INCLUDE[tsql](../../includes/tsql-md.md)] или CmdExec.  
  
 Чтобы вернуть аргументу output_file_name значение NULL, необходимо задать *аргументу output_file_name* пустую строку ("") или в строку из пробелов, но вы не можете использовать **CHAR(32)** функции. Например, установление данного аргумента равным пустой строке производится следующим образом:  
  
 **@output_file_name = ' '**  
  
`[ @flags = ] flags` Параметр, контролирующий поведение. *флаги* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0** (по умолчанию)|Переписать выходной файл.|  
|**2**|Добавить к выходному файлу.|  
|**4**|Записать вывод шага задания Transact-SQL в журнал шагов.|  
|**8**|Записать журнал в таблицу (переписать существующий журнал).|  
|**16**|Записать журнал в таблицу (добавить к существующему журналу).|  
  
`[ @proxy_id = ] proxy_id` Идентификационный номер, шаг задания выполняется как прокси-сервер. *proxy_id* является типом **int**, значение по умолчанию NULL. Если не *proxy_id* указан, не *proxy_name* указано и не *user_name* указан, шаг задания выполняется как учетная запись службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента.  
  
`[ @proxy_name = ] 'proxy_name'` Имя прокси-сервера, который выполняется шаг задания. *proxy_name* является типом **sysname**, значение по умолчанию NULL. Если не *proxy_id* указан, не *proxy_name* указано и не *user_name* указан, шаг задания выполняется как учетная запись службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_update_jobstep** должна запускаться из **msdb** базы данных.  
  
 Обновление шага задания увеличивает номер версии задания.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены **sysadmin** можно обновить шаг задания, которыми владеют другие пользователи.  
  
 Если шаг задания требует доступа к учетной записи-посреднику, создатель шага задания должен обеспечить ему доступ к такой записи. Все подсистемы, за исключением Transact-SQL, требуют учетную запись-посредник. Членами **sysadmin** имеют доступ для всех учетных записей-посредников и можно использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы агента прокси-сервера.  
  
## <a name="examples"></a>Примеры  
 Следующий пример изменяет количество повторных попыток для первого шага задания `Weekly Sales Data Backup`. После выполнения данного примера количество повторных попыток будет равно `10`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1,  
    @retry_attempts = 10 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Просмотр или изменение заданий](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
