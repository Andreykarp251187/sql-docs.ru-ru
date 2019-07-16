---
title: sp_addremotelogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addremotelogin_TSQL
- sp_addremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addremotelogin
ms.assetid: 71b7cd36-a17d-4b12-b102-10aeb0f9268b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: eb45ce1c3e1786eb5a9a3cd630741dd4df773c40
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030959"
---
# <a name="spaddremotelogin-transact-sql"></a>sp_addremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет новый идентификатор удаленного имени входа на локальный сервер. Это позволяет удаленным серверам подключаться и выполнять удаленные вызовы процедуры (RPC).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Используйте вместо этого связанные серверы и хранимые процедуры связанных серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @remoteserver **=** ] **"** _remoteserver_ **"**  
 Имя удаленного сервера, к которому применяется удаленный вход. *удаленный сервер* — **sysname**, не имеет значения по умолчанию. Если только *remoteserver* указан, все пользователи на *remoteserver* сопоставляются существующие имена входа с тем же именем на локальном сервере. Сервер должен быть известен локальному серверу. Он добавляется с помощью sp_addserver. Когда пользователей на *remoteserver* подключиться к локальному серверу, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения удаленной хранимой процедуры осуществляется по локальным именам входа, совпадающим с их именами на *remoteserver* . *удаленный сервер* — это сервер, который инициирует удаленный вызов процедур.  
  
 [ @loginame **=** ] **"** _входа_ **"**  
 Идентификатор имени входа для пользователя локального экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. *Имя входа*должен уже существовать на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если *входа* указано, все пользователи в *remoteserver* сопоставляются, определенным локальным именем входа. Когда пользователей на *remoteserver* подключиться к локальному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения удаленной хранимой процедуры осуществляется по *входа*.  
  
 [ @remotename **=** ] **"** _remote_name_ **"**  
 Идентификатор имени входа пользователя на удаленном сервере. *remote_name* — **sysname**, значение по умолчанию NULL. *remote_name* должен существовать на *remoteserver*. Если *remote_name* указан, пользователь *remote_name* сопоставляется *входа* на локальном сервере. Когда *remote_name* на *remoteserver* подключается к локальному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения удаленной хранимой процедуры, она подключается как *входа*. Идентификатор входа *remote_name* может отличаться от идентификатора входа на удаленном сервере, *входа*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Для выполнения распределенных запросов, используйте sp_addlinkedsrvlogin.  
  
 sp_addremotelogin нельзя использовать внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Только члены sysadmin и предопределенной роли сервера securityadmin могут выполнять sp_addremotelogin.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-mapping-one-to-one"></a>A. Сопоставление «один к одному»  
 Следующий пример сопоставляет удаленные имена локальным, если имена входа пользователей на удаленном сервере `ACCOUNTS` и на локальном сервере совпадают.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-mapping-many-to-one"></a>Б. Сопоставление «многие к одному»  
 В следующем примере создается запись, которая сопоставляет всех пользователей удаленного сервера `ACCOUNTS` локальному идентификатору входа `Albert`.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-using-explicit-one-to-one-mapping"></a>В. Использование явного сопоставления «один к одному»  
 Следующий пример сопоставляет удаленное имя входа удаленного пользователя `Chris` на удаленном сервере `ACCOUNTS` локальному пользователю `salesmgr`.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>См. также  
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [Хранимая процедура sp_revokelogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
