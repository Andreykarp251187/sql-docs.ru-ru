---
title: sp_adduser (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_adduser
- sp_adduser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adduser
ms.assetid: 61a40eb4-573f-460c-9164-bd1bbfaf8b25
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a2984479c8a1be35f8ccfa63d14b3250939f56c3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68117902"
---
# <a name="spadduser-transact-sql"></a>sp_adduser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет нового пользователя в текущую базу данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [CREATE USER](../../t-sql/statements/create-user-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_adduser [ @loginame = ] 'login'   
    [ , [ @name_in_db = ] 'user' ]   
    [ , [ @grpname = ] 'role' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login'` Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или имя входа Windows. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* должен быть существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или имя входа Windows.  
  
`[ @name_in_db = ] 'user'` — Это имя для нового пользователя базы данных. *пользователь* — **sysname**, значение по умолчанию NULL. Если *пользователя* не указан, по умолчанию используется имя нового пользователя базы данных *входа* имя. Указание *пользователя* задает имя для нового пользователя в базе данных, отличное от имени входа уровня сервера.  
  
`[ @grpname = ] 'role'` Представляет роль базы данных, членом которой становится новый пользователь. *роль* — **sysname**, значение по умолчанию NULL. *роль* должна быть допустимая роль в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_adduser** также создается схема с именем пользователя.  
  
 После добавления пользователя следует определить разрешения, управляющие действиями, которые пользователь может выполнять, с помощью инструкций GRANT, DENY и REVOKE.  
  
 Используйте **sys.server_principals** чтобы отобразить список допустимых имен входа.  
  
 Используйте **sp_helprole** чтобы отобразить список допустимых имен ролей. При задании роли пользователь автоматически получает соответствующие этой роли разрешения. Если роль не указан, то пользователь получает разрешения, предоставленные по умолчанию **открытый** роли. Чтобы добавить пользователя в роль, значение для *имя пользователя* должен быть указан. (*username* может быть таким же, как *login_id*.)  
  
 Пользователь **гостевой** уже существует в каждой базе данных. При добавлении пользователя **гостевой** включит его, если оно было отключено. По умолчанию пользователь **гостевой** отключен в новых базах данных.  
  
 **sp_adduser** не может быть выполнена внутри пользовательской транзакции.  
  
 Не удается добавить **гостевой** пользователя поскольку **гостевой** пользователь уже существует в каждой базе данных. Чтобы включить **гостевой** пользователя, предоставление **гостевой** разрешение CONNECT следующим образом:  
  
```  
GRANT CONNECT TO guest;  
GO  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо, чтобы пользователь был владельцем базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-database-user"></a>A. Добавление пользователя базы данных  
 В следующем примере пользователь `Vidur` добавляется в существующую роль `Recruiting` текущей базы данных с помощью существующего имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Vidur`.  
  
```  
EXEC sp_adduser 'Vidur', 'Vidur', 'Recruiting';  
```  
  
### <a name="b-adding-a-database-user-with-the-same-login-id"></a>Б. Добавление пользователя базы данных с таким же идентификатором входа  
 В приведенном ниже примере пользователь `Arvind` добавляется в текущую базу данных для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Arvind`. Этот пользователь принадлежит значение по умолчанию **открытый** роли.  
  
```  
EXEC sp_adduser 'Arvind';  
```  
  
### <a name="c-adding-a-database-user-with-a-different-name-than-its-server-level-login"></a>В. Добавление пользователя базы данных с именем, отличным от имени входа уровня сервера  
 В приведенном ниже примере в текущую базу данных, в которой есть пользователь с именем `BjornR`, добавляется имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Bjorn`, а также пользователь `Bjorn` добавляется в роль `Production`.  
  
```  
EXEC sp_adduser 'BjornR', 'Bjorn', 'Production';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
