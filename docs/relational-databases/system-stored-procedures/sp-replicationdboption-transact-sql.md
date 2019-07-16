---
title: sp_replicationdboption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replicationdboption_TSQL
- sp_replicationdboption
helpviewer_keywords:
- sp_replicationdboption
ms.assetid: d021864e-3f21-4d1a-89df-6c1086f753bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8285713df1fb17b2e82dcfa6edac0fd6db5500a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950665"
---
# <a name="spreplicationdboption-transact-sql"></a>sp_replicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Устанавливает аргументы репликации указанной базы данных. Эта хранимая процедура выполняется на издателе или подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replicationdboption [ @dbname= ] 'db_name'   
        , [ @optname= ] 'optname'   
        , [ @value= ] 'value'   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
    [ , [ @from_scripting = ] from_scripting ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@dbname=** ] **"***dbname***"**  
 База данных, для которой устанавливаются параметры репликации. *db_name* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@optname=** ] **"***optname***"**  
 Параметр репликации базы данных, который должен быть включен или выключен. *optname* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**публикации слиянием**|База данных может использоваться для публикации слиянием.|  
|**Публикация**|База данных может использоваться для других типов публикаций.|  
|**подписаться**|База данных является базой данных подписки.|  
|**Синхронизация с резервной копией**|База данных доступна для скоординированного создания резервных копий. Дополнительные сведения см. в разделе [Включение скоординированного резервного копирования для репликации транзакций &#40;программирование репликации Transact-SQL&#41;](../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md).|  
  
`[ @value = ] 'value'` Это, следует ли включить или отключить параметр данной репликации базы данных. *значение* — **sysname**и может быть **true** или **false**. Если это значение равно **false** и *optname* — **публикации слиянием**, подписки слиянием опубликованной базы данных также удаляются.  
  
`[ @ignore_distributor = ] ignore_distributor` Указывает, выполняется ли данная хранимая процедура без подключения к распространителю. *ignore_distributor* — **бит**, значение по умолчанию **0**, это означает распространителя должны подключения и обновления состояния публикуемой базы данных. Значение **1** должно указываться, только если распространитель недоступен и **sp_replicationdboption** , используется для отключения публикации.  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_replicationdboption** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 Эта процедура создает или удаляет определенные системные таблицы репликации, учетные записи безопасности и так далее в зависимости от указанного аргумента. Наборы, соответствующий бит категории в **master.sysdatabases** системной таблицы и создает необходимые системные таблицы.  
  
 Для отключения публикации база данных публикации должна находиться в режиме «в сети». Если для базы данных публикации существует моментальный снимок, он должен быть удален перед отключением публикации. Моментальный снимок базы данных доступен только для чтения в виде копии базы данных вне сети и не относится к моментальному снимку репликации. Дополнительные сведения см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_replicationdboption**.  
  
## <a name="see-also"></a>См. также  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Удаление публикации](../../relational-databases/replication/publish/delete-a-publication.md)   
 [Disable Publishing and Distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)  (Отключение публикации и распространения)  
 [sys.sysdatabases &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
