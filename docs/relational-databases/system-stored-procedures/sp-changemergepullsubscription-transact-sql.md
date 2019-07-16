---
title: sp_changemergepullsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergepullsubscription
- sp_changemergepullsubscription_TSQL
helpviewer_keywords:
- sp_changemergepullsubscription
ms.assetid: 5e0d04f2-6175-44a2-ad96-a8e2986ce4c9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8771d7c821a82733b0664f09c5dadf2128baf877
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090852"
---
# <a name="spchangemergepullsubscription-transact-sql"></a>sp_changemergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства подписки слиянием по запросу. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changemergepullsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @publisher= ] 'publisher' ]  
    [ , [ @publisher_db= ] 'publisher_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, значение по умолчанию %.  
  
`[ @publisher = ] 'publisher'` — Имя издателя. *издатель*— **sysname**, значение по умолчанию %.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя базы данных издателя. *publisher_db*— **sysname**, значение по умолчанию %.  
  
`[ @property = ] 'property'` — Имя свойства, которое необходимо изменить. *Свойство* — **sysname**, и может принимать одно из значений в таблице.  
  
`[ @value = ] 'value'` — Это новое значение для указанного свойства. *значение*— **nvarchar(255)** , и может принимать одно из значений в таблице.  
  
|Свойство|Значение|Описание|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||Местоположение папки моментальных снимков, если оно отлично от местоположения по умолчанию или дополняет его.|  
|**description**||Описание подписки слиянием по запросу.|  
|**распространитель**||Имя распространителя.|  
|**distributor_login**||Идентификатор входа, используемый на стороне распространителя для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_password**||Пароль (шифрованный), используемый на распространителе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows.|  
||**0**|При подключении к подписчику используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**dynamic_snapshot_location**||Путь к папке, в которой сохраняются файлы моментальных снимков.|  
|**ftp_address**||Приводится только для обратной совместимости. Сетевой адрес службы FTP распространителя.|  
|**ftp_login**||Приводится только для обратной совместимости. Имя пользователя, используемое для подключения к службе FTP.|  
|**ftp_password**||Приводится только для обратной совместимости. Пароль пользователя, используемый для подключения к службе FTP.|  
|**ftp_port**||Приводится только для обратной совместимости. Номер порта службы FTP распространителя.|  
|**Имя узла**||Указывает значение HOST_NAME(), когда эта функция используется в предложении WHERE фильтра соединения или отношения логических записей.|  
|**internet_login**||Имя входа, используемое агентом слияния для подключения к веб-серверу, на котором доступна веб-синхронизация с обычной проверкой подлинности.|  
|**internet_password**||Пароль для имени входа, используемого агентом слияния при подключении к веб-серверу, на котором доступна веб-синхронизация с использованием обычной проверки подлинности.|  
|**internet_security_mode**|**1**|Использование системы проверки подлинности Windows при подключении к веб-серверу, который поддерживает веб-синхронизацию.|  
||**0**|Использование обычной системы проверки подлинности при подключении к веб-серверу, который поддерживает веб-синхронизацию.|  
|**internet_timeout**||Время (в секундах) перед отменой запроса на веб-синхронизацию.|  
|**internet_url**||UR-адрес, который представляет собой адрес средства прослушивания репликации для веб-синхронизации.|  
|**merge_job_login**||Имя входа учетной записи Windows, от имени которой выполняется агент.|  
|**merge_job_password**||Пароль учетной записи Windows, от имени которой выполняется агент.|  
|**priority**||Для обратной совместимости. Запустите [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md) на издателе вместо Чтобы изменить приоритет подписки.|  
|**publisher_login**||Идентификатор входа, используемый на издателе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_password**||Пароль (шифрованный), используемый на издателе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_security_mode**|**0**|При подключении к издателю используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
||**1**|При подключении к подписчику используется проверка подлинности Windows.|  
||**2**|Триггеры синхронизации используют статическую **sysservers** для выполнения удаленного вызова процедур (RPC), а издатель должен быть определен в **sysservers** таблицу как удаленный сервер или связанный сервер.|  
|**sync_type**|**Автоматически**|Схема и начальные данные для опубликованных таблиц вначале передаются подписчику.|  
||**Нет**|Подписчик уже имеет схему и начальные данные для опубликованных таблиц; системные таблицы и данные передаются всегда.|  
|**use_ftp**|**true**|Для получения моментальных снимков используется FTP вместо обычного протокола.|  
||**false**|Получение моментальных снимков с помощью обычного протокола.|  
|**use_web_sync**|**true**|Подписку можно синхронизировать через HTTP.|  
||**false**|Подписку нельзя синхронизировать через HTTP.|  
|**use_interactive_resolver**|**true**|При проверке используется интерактивный сопоставитель.|  
||**false**|Интерактивный сопоставитель не используется.|  
|**working_directory**||Полный путь к каталогу, куда передаются файлы моментальных снимков по протоколу FTP, если указан соответствующий параметр.|  
|NULL (по умолчанию)||Возвращает список поддерживаемых значений для *свойство*.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_changemergepullsubscription** используется в репликации слиянием.  
  
 Подразумевается, что текущий сервер и текущая база данных являются соответственно подписчиком и базой данных подписчика.  
  
 После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_changemergepullsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
