---
title: sp_setreplfailovermode (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ae89e606633fc3555745dd56fc7703ef50685468
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028652"
---
# <a name="spsetreplfailovermode-transact-sql"></a>Хранимая процедура sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Позволяет установить режим отработки отказа для подписок, включенных для немедленного обновления с отработкой отказа с обновлением посредством очередей. Эта хранимая процедура выполняется на подписчике в базе данных подписки. Дополнительные сведения о режимах отработки отказа см. в разделе [обновляемые подписки для репликации транзакций](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_setreplfailovermode [ @publisher= ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication= ] 'publication' ]  
    [ , [ @failover_mode= ] 'failover_mode' ]  
    [ , [ @override = ] override ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию. Публикация уже должна существовать.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация*— **sysname**, не имеет значения по умолчанию.  
  
 [**@failover_mode=**] **'***failover_mode***'**  
 Режим отработки отказа для подписок. *failover_mode* — **nvarchar(10)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**немедленное** или **синхронизации**|Изменения данных на подписчике массово копируются на издатель по мере их возникновения.|  
|**в очереди**|Изменения данных сохраняются в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очереди.|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Служба Message Queuing устарел и больше не поддерживается.  
  
`[ @override = ] override` Только для внутреннего использования.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_setreplfailovermode** используется в репликации моментальных снимков или репликации транзакций для которых подписки включены, либо обновления с переходом на немедленное обновление посредством очередей или немедленного обновления с отработкой отказа в очередь обновление.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_setreplfailovermode**.  
  
## <a name="see-also"></a>См. также  
 [Переключение между режимами обновления для обновляемой подписки на публикацию транзакций](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
