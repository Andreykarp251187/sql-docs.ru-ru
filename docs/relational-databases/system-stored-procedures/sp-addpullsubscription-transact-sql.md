---
title: sp_addpullsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpullsubscription
- sp_addpullsubscription_TSQL
helpviewer_keywords:
- sp_addpullsubscription
ms.assetid: 0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea87c5e83b5be3945469ddb0e32c9f8158a5e116
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022446"
---
# <a name="spaddpullsubscription-transact-sql"></a>sp_addpullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет подписку по запросу к моментальному снимку или публикации транзакций. Эта хранимая процедура выполняется на подписчике в базе данных, в которой создается подписка по запросу.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addpullsubscription [ @publisher= ] 'publisher'  
    [ , [ @publisher_db= ] 'publisher_db' ]  
        , [ @publication= ] 'publication'  
    [ , [ @independent_agent= ] 'independent_agent' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @update_mode= ] 'update_mode' ]  
    [ , [ @immediate_sync = ] immediate_sync ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` — Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию NULL. *publisher_db* обрабатывается издателями Oracle.  
  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @independent_agent = ] 'independent_agent'` Указывает, имеется ли для этой публикации изолированный агент распространителя. *independent_agent* — **nvarchar(5)** , значение по умолчанию TRUE. Если **true**, имеется изолированный агент распространителя для этой публикации. Если **false**, имеется один агент распространителя для каждой пары издатель базы данных подписчик базы данных. *independent_agent* является свойством публикации и должен иметь то же значение что и на издателе.  
  
`[ @subscription_type = ] 'subscription_type'` — Тип подписки. *subscription_type* — **nvarchar(9)** , значение по умолчанию **анонимный**. Необходимо указать значение **по запросу** для *subscription_type*, только если вы хотите создать подписку без регистрации подписки на издателе. В этом случае необходимо указать значение **анонимный**. Это необходимо в тех случаях, когда невозможно установить соединение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с издателем в момент настройки подписки.  
  
`[ @description = ] 'description'` Представляет собой описание публикации. *Описание* — **nvarchar(100)** , значение по умолчанию NULL.  
  
`[ @update_mode = ] 'update_mode'` — Это тип обновления. *update_mode* — **nvarchar(30)** , и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**только для чтения** (по умолчанию)|Подписка только для чтения. Никакие изменения на подписчике не передаются на издатель. Используется в том случае, когда данные на подписчике изменяться не будут.|  
|**synctran**|Включает поддержку немедленно обновляемых подписок.|  
|**в очереди tran**|Обеспечивает подписку обновляемую посредством очередей. Изменение данных можно выполнять у подписчика, сохранять в очереди и после этого передавать издателю.|  
|**отработка отказа**|Включает для подписки немедленное обновление с обновлением по очереди при переходе на другой ресурс в случае отработки отказа. Изменение данных можно выполнять на подписчике и немедленно передавать издателю. Если пропало соединение между издателем и подписчиком, изменения данных, выполненные на подписчике, сохраняются в очереди, пока связь не будет восстановлена.|  
|**в очереди отработки отказа**|Включает подписку с обновлением по очереди в качестве обновляемой посредством очередей подписки, при этом поддерживает возможность переключения в режим немедленного обновления. Изменение данных можно выполнять у подписчика и сохранять в очереди до установления соединения между подписчиком и издателем. При установлении постоянного соединения можно переключиться в режим немедленного обновления. *Не поддерживается для издателей Oracle*.|  
  
`[ @immediate_sync = ] immediate_sync` Является ли файлы синхронизации создаются или повторно создаются каждый раз при выполнении агента моментальных снимков. *immediate_sync* — **бит** значение по умолчанию 1 и должно быть присвоено то же значение, что *immediate_sync* в **sp_addpublication**. *immediate_sync* является свойством публикации и должен иметь то же значение что и на издателе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addpullsubscription** используется в репликации моментальных снимков и репликации транзакций.  
  
> [!IMPORTANT]  
>  Для обновляемых посредством очередей подписок при соединении с подписчиками используйте проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указывая для каждого из подписчиков различные учетные записи. При создании подписки по запросу, поддерживающей обновление посредством очередей, репликация всегда устанавливает соединение с использованием проверки подлинности Windows (так как для подписок по запросу репликация не сможет получить доступ к метаданным на подписчике, необходимым для выполнения проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). В этом случае следует выполнить [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) изменить подключение для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, после настройки подписки.  
  
 Если [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) таблица не существует на подписчике, **sp_addpullsubscription** создает ее. Он также добавляет строку к [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) таблицы. Для подписок по запросу [sp_addsubscription &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) должен вызываться сначала на издателе.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-t_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addpullsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Создание обновляемой подписки на публикацию транзакций](../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md) [подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
