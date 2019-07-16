---
title: sp_addpullsubscription_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpullsubscription_agent
- sp_addpullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addpullsubscription_agent
ms.assetid: b9c2eaed-6d2d-4b78-ae9b-73633133180b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 220e21713935409d7d85ecd156524883dbbace08
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022463"
---
# <a name="spaddpullsubscriptionagent-transact-sql"></a>sp_addpullsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
 
  Добавляет новое запланированное задание агента, используемое для синхронизации подписки по запросу с публикацией транзакций. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addpullsubscription_agent [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]          , [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor = ] 'distributor' ]  
    [ , [ @distribution_db = ] 'distribution_db' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]  
    [ , [ @distributor_login = ] 'distributor_login' ]  
    [ , [ @distributor_password = ] 'distributor_password' ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @distribution_jobid = ] distribution_jobid OUTPUT ]  
    [ , [ @encrypted_distributor_password = ] encrypted_distributor_password ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port = ] ftp_port ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]  
    [ , [ @working_directory = ] 'working_directory' ]  
    [ , [ @use_ftp = ] 'use_ftp' ]  
    [ , [ @publication_type = ] publication_type ]  
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @offloadagent = ] 'remote_agent_activation' ]  
    [ , [ @offloadserver = ] 'remote_agent_server_name']  
    [ , [ @job_name = ] 'job_name' ]  
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` — Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'_` — Имя базы данных издателя. *publisher_db* — **sysname**, со значением по умолчанию NULL. *publisher_db* обрабатывается издателями Oracle.  
  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов.  
  
`[ @subscriber_db = ] 'subscriber_db'` — Имя базы данных подписки. *subscriber_db* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` — Режим безопасности для использования при подключении к подписчику при синхронизации. *subscriber_security_mode* — **int,** значение по умолчанию NULL. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. **1** задает проверку подлинности Windows.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Агент распространителя всегда подключается к локальному подписчику с использованием проверки подлинности Windows. Если значение, отличное от NULL или **1** указан для данного параметра, выдается предупреждающее сообщение.  
  
`[ @subscriber_login = ] 'subscriber_login'` — Это имя входа подписчика, используемое при подключении к подписчику при синхронизации. *subscriber_login* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если для этого аргумента указывается значение, то выдается предупреждающее сообщение, а значение не обрабатывается.  
  
`[ @subscriber_password = ] 'subscriber_password'` — Пароль подписчика. *subscriber_password* является обязательным, если *subscriber_security_mode* присваивается **0**. *subscriber_password* — **sysname**, значение по умолчанию NULL. Если пароль подписчика используется, он автоматически шифруется.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если для этого аргумента указывается значение, то выдается предупреждающее сообщение, а значение не обрабатывается.  
  
`[ @distributor = ] 'distributor'` — Имя распространителя. *распространитель* — **sysname**, значение по умолчанию значение, заданное параметром *издателя*.  
  
`[ @distribution_db = ] 'distribution_db'` — Имя базы данных распространителя. *distribution_db* — **sysname**, со значением по умолчанию NULL.  
  
`[ @distributor_security_mode = ] distributor_security_mode` — Режим безопасности для использования при подключении к распространителю при синхронизации. *distributor_security_mode* — **int**, значение по умолчанию **1**. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. **1** задает проверку подлинности Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` — Это имя входа распространителя для использования при подключении к распространителю при синхронизации. *distributor_login* является обязательным, если *distributor_security_mode* присваивается **0**. *distributor_login* — **sysname**, значение по умолчанию NULL.  
  
`[ @distributor_password = ] 'distributor_password'` — Пароль распространителя. *distributor_password* является обязательным, если *distributor_security_mode* присваивается **0**. *distributor_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @optional_command_line = ] 'optional_command_line'` Предоставляется ли дополнительная Командная строка агента распространителя. Например **- DefinitionFile** C:\Distdef.txt или **- CommitBatchSize** 10. *optional_command_line* — **nvarchar(4000)** , значение по умолчанию пустая строка.  
  
`[ @frequency_type = ] frequency_type` Это частота запуска агента распространителя. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2** (по умолчанию)|по запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторяющееся задание|  
  
> [!NOTE]  
>  Указав значение **64** агент распространителя запускается в непрерывном режиме. Это соответствует вводу параметра **-непрерывной** параметром для агента. Дополнительные сведения см. в статье [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
`[ @frequency_interval = ] frequency_interval` — Это значение, которое применяется к частоте, задаваемой аргументом *frequency_type*. *frequency_interval* — **int**, значение по умолчанию 1.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` — Дата агента распространителя. Этот параметр используется при *frequency_type* присваивается **32** (относительно ежемесячно). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию **1**.  
  
`[ @frequency_subday = ] frequency_subday` Том, как часто следует запланировать повторное выполнение в течение определенного периода. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию **1**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Время суток, когда агент распространителя впервые запланировано, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Время суток, когда прекращается выполнение агента распространителя, в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию **0**.  
  
`[ @active_start_date = ] active_start_date` Дата первого запуска агента распространителя запланирована, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию **0**.  
  
`[ @active_end_date = ] active_end_date` Дата плановой остановки агента распространителя, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию **0**.  
  
`[ @distribution_jobid = ] _distribution_jobidOUTPUT` — Идентификатор агента распространителя для этого задания. *distribution_jobid* — **binary(16)** , значение по умолчанию NULL и является ВЫХОДНЫМ параметром.  
  
`[ @encrypted_distributor_password = ] encrypted_distributor_password` Установка *encrypted_distributor_password* больше не поддерживается. Попытка присвоить этому **бит** параметр **1** приведет к ошибке.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Является ли подписку можно синхронизировать через [!INCLUDE[msCoName](../../includes/msconame-md.md)] диспетчер синхронизации. *enabled_for_syncmgr* — **nvarchar(5)** , значение по умолчанию FALSE. Если **false**, подписка не зарегистрирована диспетчером синхронизации. Если **true**, подписка регистрируется диспетчером синхронизации и может быть синхронизирована без запуска [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @ftp_address = ] 'ftp_address'` Только для обратной совместимости.  
  
`[ @ftp_port = ] ftp_port` Только для обратной совместимости.  
  
`[ @ftp_login = ] 'ftp_login'` Только для обратной совместимости.  
  
`[ @ftp_password = ] 'ftp_password'` Только для обратной совместимости.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'_` Указывает расположение альтернативной папки для моментального снимка. *alternate_snapshot_folder* — **nvarchar(255)** , значение по умолчанию NULL.  
  
`[ @working_directory = ] 'working_director'` Это имя рабочего каталога, используемого для хранения файлов данных и схем для публикации. *working_directory* — **nvarchar(255)** , значение по умолчанию NULL. Имя должно быть задано в формате UNC.  
  
`[ @use_ftp = ] 'use_ftp'` Указывает использование протокола FTP вместо обычного протокола для получения моментальных снимков. *use_ftp* — **nvarchar(5)** , значение по умолчанию FALSE.  
  
`[ @publication_type = ] publication_type` Указывает тип репликации публикации. *publication_type* — **tinyint** значение по умолчанию **0**. Если **0**, публикация является публикацией транзакций. Если **1**, публикация является публикацией моментальных снимков. Если **2**, публикация является публикацией слиянием.  
  
`[ @dts_package_name = ] 'dts_package_name'` Указывает имя пакета служб DTS. *dts_package_name* — **sysname** значение по умолчанию NULL. Например, для задания пакета `DTSPub_Package` параметр должен быть равен `@dts_package_name = N'DTSPub_Package'`.  
  
`[ @dts_package_password = ] 'dts_package_password'` Указывает пароль для пакета, если таковой имеется. *dts_package_password* — **sysname** значение по умолчанию NULL, означающее пароль не входит в пакет.  
  
> [!NOTE]  
>  Необходимо указать пароль, если *dts_package_name* указан.  
  
`[ @dts_package_location = ] 'dts_package_location'` Указывает местоположение пакета. *dts_package_location* — **nvarchar(12)** , значение по умолчанию **подписчика**. Расположение пакета может быть **распространителя** или **подписчика**.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка *remote_agent_activation* на значение, отличное от **false** приведет к ошибке.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка *remote_agent_server_name* любое значение, отличное от NULL, будут вызывать ошибку.  
  
`[ @job_name = ] 'job_name'` — Имя существующего задания агента. *имя_задания* — **sysname**, со значением по умолчанию NULL. Этот аргумент указывается только тогда, когда подписка будет синхронизироваться с использованием существующего задания, а не вновь создаваемого задания (выбор по умолчанию). Если вы не являетесь членом **sysadmin** предопределенной роли сервера, необходимо указать *job_login* и *job_password* при указании *имя_задания*.  
  
`[ @job_login = ] 'job_login'` — Это имя для учетной записи Windows, под которой запускается агент. *job_login* — **nvarchar(257)** , не имеет значения по умолчанию. Для соединений агента с подписчиком всегда используется эта учетная запись Windows.  
  
`[ @job_password = ] 'job_password'` — Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addpullsubscription_agent** используется в репликации моментальных снимков и репликации транзакций.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addpullsubscription_agent**.  
  
## <a name="see-also"></a>См. также  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
