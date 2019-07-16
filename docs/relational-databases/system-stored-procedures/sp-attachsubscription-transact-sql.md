---
title: sp_attachsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_attachsubscription
- sp_attachsubscription_TSQL
helpviewer_keywords:
- sp_attachsubscription
ms.assetid: b9bbda36-a46a-4327-a01e-9cd632e4791b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d9f144d9d896fb75af5f59850c249b9044d1b781
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046151"
---
# <a name="spattachsubscription-transact-sql"></a>sp_attachsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Присоединяет существующую базу данных подписки к любому подписчику. Эта хранимая процедура выполняется в базе данных master на новом подписчике.  
  
> [!IMPORTANT]  
>  Данная функция является устаревшей и в следующей версии будет удалена. Использовать эту функцию для новых разработок не рекомендуется. Для публикаций слиянием, секционированных с помощью параметризованных фильтров, рекомендуется использовать новые возможности секционированных снимков, которые упрощают инициализацию большого числа подписок. Дополнительные сведения см. в статье [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). Для несекционированных публикаций можно инициализировать подписку с помощью резервной копии. Дополнительные сведения см. в статье [Инициализация подписки на публикацию транзакций без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_attachsubscription [ @dbname = ] 'dbname'  
        , [ @filename = ] 'filename'  
    [ , [ @subscriber_security_mode = ] 'subscriber_security_mode' ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @db_master_key_password = ] 'db_master_key_password' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbname'` — Строка, которая указывает целевую базу данных подписки по имени. *DBName* — **sysname**, не имеет значения по умолчанию.  
  
`[ @filename = ] 'filename'` Имя и физическое расположение первичного файла MDF (**master** файла данных). *Имя файла* — **nvarchar(260)** , не имеет значения по умолчанию.  
  
`[ @subscriber_security_mode = ] 'subscriber_security_mode'` — Режим безопасности подписчика для использования при подключении к подписчику при синхронизации. *subscriber_security_mode* — **int**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо использовать проверку подлинности Windows. Если *subscriber_security_mode* не **1** (проверка подлинности Windows), будет возвращена ошибка.  
  
`[ @subscriber_login = ] 'subscriber_login'` — Это имя входа подписчика, используемое при подключении к подписчику при синхронизации. *subscriber_login* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если *subscriber_security_mode* не **1** и *subscriber_login* будет указано, будет возвращена ошибка.  
  
`[ @subscriber_password = ] 'subscriber_password'` — Пароль подписчика. *subscriber_password* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если *subscriber_security_mode* не **1** и *subscriber_password* будет указано, будет возвращена ошибка.  
  
`[ @distributor_security_mode = ] distributor_security_mode` — Режим безопасности для использования при подключении к распространителю при синхронизации. *distributor_security_mode* — **int**, значение по умолчанию **0**. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. **1** задает проверку подлинности Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` — Это имя входа распространителя для использования при подключении к распространителю при синхронизации. *distributor_login* является обязательным, если *distributor_security_mode* присваивается **0**. *distributor_login* — **sysname**, значение по умолчанию NULL.  
  
`[ @distributor_password = ] 'distributor_password'` — Пароль распространителя. *distributor_password* является обязательным, если *distributor_security_mode* присваивается **0**. *distributor_password* — **sysname**, значение по умолчанию NULL. Значение *distributor_password* должно содержать менее 120 символов Юникода.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher_security_mode = ] publisher_security_mode` — Режим безопасности для использования при подключении к издателю при синхронизации. *publisher_security_mode* — **int**, значение по умолчанию **1**. Если **0**, указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Если **1**, задает проверку подлинности Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` — Это имя для использования при подключении к издателю при синхронизации. *publisher_login* — **sysname**, значение по умолчанию NULL.  
  
`[ @publisher_password = ] 'publisher_password'` Пароль, используемый при соединении с издателем. *publisher_password* — **sysname**, значение по умолчанию NULL. Значение *publisher_password* должно содержать менее 120 символов Юникода.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @job_login = ] 'job_login'` — Это имя для учетной записи Windows, под которой запускается агент. *job_login* — **nvarchar(257)** , не имеет значения по умолчанию. Для соединения агента с распространителем всегда используется эта учетная запись Windows.  
  
`[ @job_password = ] 'job_password'` — Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, не имеет значения по умолчанию. Значение *job_password* должно содержать менее 120 символов Юникода.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @db_master_key_password = ] 'db_master_key_password'` — Пароль для определяемого пользователем главного ключа базы данных. *db_master_key_password* — **nvarchar(524)** , со значением по умолчанию NULL. Если *db_master_key_password* не указан, существующий главный ключ базы данных будет удалена и создана заново.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_attachsubscription** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 Подписка не может быть присоединена к публикации, если срок хранения публикации истек. При указании подписки с истекшим сроком хранения публикации возникает ошибка при присоединении или первой синхронизации подписки. Публикации со сроком хранения **0** (никогда не истекает) учитываются.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_attachsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
