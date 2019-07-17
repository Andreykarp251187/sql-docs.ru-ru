---
title: sp_addmergepullsubscription_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_agent
- sp_addmergepullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addmergepullsubscription_agent
ms.assetid: a2f4b086-078d-49b5-8971-8a1e3f6a6feb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8bfa9ff0683f67a1d38aeb17bccd0cfc1443d6d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68117958"
---
# <a name="spaddmergepullsubscriptionagent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет новое задание агента для планирования синхронизации подписки по запросу на публикацию слиянием. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergepullsubscription_agent [ [ @name = ] 'name' ]   
        , [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication =] 'publication'   
    [ , [ @publisher_security_mod e= ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher_encrypted_password = ] publisher_encrypted_password ]   
    [ , [ @subscriber = ] 'subscriber' ]   
    [ , [ @subscriber_db = ] 'subscriber_db' ]   
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]   
    [ , [ @subscriber_login = ] 'subscriber_login' ]   
    [ , [ @subscriber_password= ] 'subscriber_password' ]   
    [ , [ @distributor = ] 'distributor' ]   
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @encrypted_password = ] encrypted_password ]   
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
    [ , [ @optional_command_line = ] 'optional_command_line' ]   
    [ , [ @merge_jobid = ] merge_jobid ]   
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]    
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @working_directory = ] 'working_directory' ]   
    [ , [ @use_ftp = ] 'use_ftp' ]   
    [ , [ @reserved = ] 'reserved' ]   
    [ , [ @use_interactive_resolver = ] 'use_interactive_resolver' ]   
    [ , [ @offloadagent = ] 'remote_agent_activation' ]   
    [ , [ @offloadserver = ] 'remote_agent_server_name']   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]  
    [ , [ @use_web_sync = ] use_web_sync ]  
        [ , [ @internet_url = ] 'internet_url' ]  
    [ , [ @internet_login = ] 'internet_login' ]  
        [ , [ @internet_password = ] 'internet_password' ]  
    [ , [ @internet_security_mode = ] internet_security_mode ]  
        [ , [ @internet_timeout = ] internet_timeout ]  
    [ , [ @hostname = ] 'hostname' ]  
        [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] 'name'` — Имя агента. *имя* — **sysname**, значение по умолчанию NULL.  
  
`[ @publisher = ] 'publisher'` — Имя сервера издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя базы данных издателя. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_security_mode = ] publisher_security_mode` — Режим безопасности для использования при подключении к издателю при синхронизации. *publisher_security_mode* — **int**, значение по умолчанию 1. Если **0**, указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Если **1**, задает проверку подлинности Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` — Это имя для использования при подключении к издателю при синхронизации. *publisher_login* — **sysname**, значение по умолчанию NULL.  
  
`[ @publisher_password = ] 'publisher_password'` Пароль, используемый при соединении с издателем. *publisher_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] При возможности предлагать пользователю ввод учетных данных безопасности во время выполнения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password` Установка *publisher_encrypted_password* больше не поддерживается. Попытка присвоить этому **бит** параметр **1** приведет к ошибке.  
  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` — Имя базы данных подписки. *subscriber_db* — **sysname**, значение по умолчанию NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` — Режим безопасности для использования при подключении к подписчику при синхронизации. *subscriber_security_mode* — **int**, значение по умолчанию 1. Если **0**, указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Если **1**, задает проверку подлинности Windows.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Агент слияния всегда подключается к локальному подписчику с использованием проверки подлинности Windows. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @subscriber_login = ] 'subscriber_login'` — Это имя входа подписчика, используемое при подключении к подписчику при синхронизации. *subscriber_login* является обязательным, если *subscriber_security_mode* присваивается **0**. *subscriber_login* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @subscriber_password = ] 'subscriber_password'` Пароль подписчика для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. *subscriber_password* является обязательным, если *subscriber_security_mode* присваивается **0**. *subscriber_password* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если для этого аргумента указано значение, оно не будет учитываться и будет возвращено предупреждающее сообщение.  
  
`[ @distributor = ] 'distributor'` — Имя распространителя. *распространитель* — **sysname**, значение по умолчанию *издателя*; то есть издатель является и распространителем.  
  
`[ @distributor_security_mode = ] distributor_security_mode` — Режим безопасности для использования при подключении к распространителю при синхронизации. *distributor_security_mode* — **int**, значение по умолчанию 0. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. **1** задает проверку подлинности Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` — Это имя входа распространителя для использования при подключении к распространителю при синхронизации. *distributor_login* является обязательным, если *distributor_security_mode* присваивается **0**. *distributor_login* — **sysname**, значение по умолчанию NULL.  
  
`[ @distributor_password = ] 'distributor_password'` — Пароль распространителя. *distributor_password* является обязательным, если *distributor_security_mode* присваивается **0**. *distributor_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] При возможности предлагать пользователю ввод учетных данных безопасности во время выполнения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @encrypted_password = ] encrypted_password` Установка *encrypted_password* больше не поддерживается. Попытка присвоить этому **бит** параметр **1** приведет к ошибке.  
  
`[ @frequency_type = ] frequency_type` Это частота запуска агента слияния. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|по запросу|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторяющееся задание|  
|NULL (по умолчанию)||  
  
> [!NOTE]  
>  Указав значение **64** агент слияния запускается в непрерывном режиме. Это соответствует вводу параметра **-непрерывной** параметром для агента. Дополнительные сведения см. в статье [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
`[ @frequency_interval = ] frequency_interval` День или дни запуска агента слияния. *frequency_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Воскресенье|  
|**2**|Понедельник|  
|**3**|Вторник|  
|**4**|Среда|  
|**5**|Четверг|  
|**6**|Пятница|  
|**7**|Суббота|  
|**8**|День|  
|**9**|По рабочим дням|  
|**10**|По выходным дням|  
|NULL (по умолчанию)||  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` — Дата агента слияния. Этот параметр используется при *frequency_type* присваивается **32** (относительно ежемесячно). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
|NULL (по умолчанию)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию NULL.  
  
`[ @frequency_subday = ] frequency_subday` Том, как часто следует запланировать повторное выполнение в течение определенного периода. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4**|Минута|  
|**8**|Час|  
|NULL (по умолчанию)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Время суток, когда агент слияния впервые запланировано, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Время остановки агента слияния, в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию NULL.  
  
`[ @active_start_date = ] active_start_date` Дата первого запуска агента слияния запланирована, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date` Дата плановой остановки агента слияния, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'` — Это дополнительная Командная строка, предоставляемая для агента слияния. *optional_command_line* — **nvarchar(255)** , значение по умолчанию "". Может использоваться для передачи агенту слияния дополнительных параметров. Следующий пример иллюстрирует увеличение времени ожидания выполнения запроса по умолчанию до `600` секунд.  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid` — Это выходной параметр идентификатора задания. *merge_jobid* — **binary(16)** , значение по умолчанию NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Указывает, может ли подписка быть синхронизирована посредством диспетчера синхронизации Windows. *enabled_for_syncmgr* — **nvarchar(5)** , значение по умолчанию FALSE. Если **false**, подписка не зарегистрирована диспетчером синхронизации. Если **true**, подписка регистрируется диспетчером синхронизации и может быть синхронизирована без запуска [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @ftp_address = ] 'ftp_address'` Только для обратной совместимости.  
  
`[ @ftp_port = ] ftp_port` Только для обратной совместимости.  
  
`[ @ftp_login = ] 'ftp_login'` Только для обратной совместимости.  
  
`[ @ftp_password = ] 'ftp_password'` Только для обратной совместимости.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'` Указывает расположение, откуда извлекаются файлы моментальных снимков. *alternate_snapshot_folder* — **nvarchar(255)** , значение по умолчанию NULL. При значении NULL файлы моментальных снимков считываются из местонахождения по умолчанию, определяемого издателем.  
  
`[ @working_directory = ] 'working_directory'` Это имя рабочего каталога, используемого для временного хранения файлов данных и схем публикации при использовании протокола FTP для передачи файлов моментальных снимков. *working_directory* — **nvarchar(255)** , значение по умолчанию NULL.  
  
`[ @use_ftp = ] 'use_ftp'` Указывает использование протокола FTP вместо обычного протокола для получения моментальных снимков. *use_ftp* — **nvarchar(5)** , значение по умолчанию FALSE.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]` Использует интерактивный арбитр конфликтов для всех статей, которые допускают интерактивное разрешение. *use_interactive_resolver* — **nvarchar(5)** , значение по умолчанию FALSE.  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка *remote_agent_activation* на значение, отличное от **false** приведет к ошибке.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Удаленная активация агента является устаревшей и больше не поддерживается. Этот аргумент поддерживается только для обратной совместимости скриптов. Установка *remote_agent_server_name* любое значение, отличное от NULL, будут вызывать ошибку.  
  
`[ @job_name = ] 'job_name' ]` — Имя существующего задания агента. *имя_задания* — **sysname**, со значением по умолчанию NULL. Этот аргумент указывается только тогда, когда подписка будет синхронизироваться с использованием существующего задания, а не вновь создаваемого задания (выбор по умолчанию). Если вы не являетесь членом **sysadmin** предопределенной роли сервера, необходимо указать *job_login* и *job_password* при указании *имя_задания*.  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]` Путь к папке, в которой файлы моментальных снимков будут считываться из Если моментального снимка отфильтрованных данных будет использоваться. *dynamic_snapshot_location* — **nvarchar(260)** , значение по умолчанию NULL. Дополнительные сведения см. в разделе [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @use_web_sync = ] use_web_sync` Указывает, что веб-синхронизация разрешена. *use_web_sync* — **бит**, значение по умолчанию 0. **1** указывает, что подписки по запросу могут синхронизироваться через Интернет по протоколу HTTP.  
  
`[ @internet_url = ] 'internet_url'` — Это расположение средства прослушивания репликации (REPLISAPI. Библиотека DLL) для веб-синхронизации. *internet_url* — **nvarchar(260)** , значение по умолчанию NULL. *internet_url* — это полный URL-адрес в формате `http://server.domain.com/directory/replisapi.dll`. Если сервер настроен для прослушивания порта, отличного от 80-го, необходимо также задать номер порта в формате `http://server.domain.com:portnumber/directory/replisapi.dll`, где `portnumber` указывает номер порта.  
  
`[ @internet_login = ] 'internet_login'` Имя входа, используемое агентом слияния при подключении к веб-сервера, на котором размещается веб-синхронизации используется обычная проверка подлинности HTTP. *internet_login* — **sysname**, значение по умолчанию NULL.  
  
`[ @internet_password = ] 'internet_password'` Пароль, используемое агентом слияния при подключении к веб-сервера, на котором размещается веб-синхронизации используется обычная проверка подлинности HTTP. *internet_password* — **nvarchar(524)** , со значением по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode` Метод проверки подлинности, используемый агентом слияния при подключении к веб-сервер во время веб-синхронизации с помощью HTTPS. *internet_security_mode* — **int** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Используется обычная проверка подлинности (проверка пароля и имени входа, входящая в протокол HTTP).|  
|**1** (по умолчанию)|Используется встроенная проверка подлинности Windows.|  
  
> [!NOTE]  
>  При веб-синхронизации рекомендуется использовать обычную проверку подлинности. Для использования веб-синхронизации необходимо подключиться к веб-серверу с использованием шифруемого соединения SSL. Дополнительные сведения см. в разделе [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
`[ @internet_timeout = ] internet_timeout` — Это продолжительность времени в секундах до истечения срока действия запроса синхронизации веб-узла. *internet_timeout* — **int**, значение по умолчанию **300** секунд.  
  
`[ @hostname = ] 'hostname'` Переопределяет значение, возвращаемое функцией HOST_NAME() при использовании этой функции в предложении WHERE параметризованного фильтра. *Имя узла* — **sysname**, значение по умолчанию NULL.  
  
`[ @job_login = ] 'job_login'` — Это имя для учетной записи Windows, под которой запускается агент. *job_login* — **nvarchar(257)** , не имеет значения по умолчанию. Эта учетная запись Windows всегда используется при соединениях агента с подписчиком и соединениях с распространителем и издателем, когда применяется встроенная проверка подлинности Windows.  
  
`[ @job_password = ] 'job_password'` — Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, не имеет значения по умолчанию.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. Для обеспечения лучшей защиты имена входа и пароли должны вводиться в ходе выполнения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergepullsubscription_agent** используется в репликации слиянием и располагает функциональностью, аналогичной [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
 Пример правильного указания настроек безопасности при выполнении **sp_addmergepullsubscription_agent**, см. в разделе [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addmergepullsubscription_agent**.  
  
## <a name="see-also"></a>См. также  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
