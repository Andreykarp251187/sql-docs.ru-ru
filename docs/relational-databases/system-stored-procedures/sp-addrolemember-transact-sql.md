---
title: Хранимая процедура sp_addrolemember (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addrolemember_TSQL
- sp_addrolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrolemember
ms.assetid: a583c087-bdb3-46d2-b9e5-3921b3e6d10b
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 18680069663b0979662b3288b5d02439fdf55297
ms.sourcegitcommit: c0e48b643385ce19c65ca6e348ce83b2d22b6514
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67492754"
---
# <a name="spaddrolemember-transact-sql"></a>Хранимая процедура sp_addrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Добавляет пользователя базы данных, роль базы данных, имя входа Windows или группу Windows к роли текущей базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```
sp_addrolemember [ @rolename = ] 'role', [ @membername = ] 'security_account'  

```    
  
## <a name="arguments"></a>Аргументы  
 [ @rolename=] '*роли*"  
 Имя роли базы данных в текущей базе данных. *роль* — **sysname**, не имеет значения по умолчанию.  
  
 [ @membername= ] '*security_account*'  
 Учетная запись безопасности, добавляемая к роли. *security_account* — **sysname**, не имеет значения по умолчанию. *security_account* может быть пользователем базы данных, роли базы данных, имя входа Windows или группы Windows.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Член роли, добавляемый с помощью процедуры sp_addrolemember, наследует разрешения этой роли. Если добавляемый член — участник уровня Windows, не имеющий соответствующего пользователя базы данных, этот пользователь будет создан, но может быть не полностью сопоставлен с именем входа. Всегда проверяйте, существует ли имя входа, и предоставлен ли ему доступ к базе данных.  
  
 Роль не может быть членом самой себя. Такие «циклические» определения недопустимы, даже если подразумевается только косвенное членство через несколько промежуточных ролей.  
  
 Хранимая процедура sp_addrolemember не может добавить предопределенной роли базы данных, предопределенной роли сервера или dbo роли.
  
 Процедура sp_addrolemember используется только для добавления нового члена к роли базы данных. Добавление члена к роли сервера, используйте [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Для добавления члена к гибким ролям базы данных необходимо выполнение одного из следующих условий.  
  
-   Членство в роли базы данных db_securityadmin или db_owner.  
  
-   Членство в роли, которой принадлежит эта роль.  
  
-   **Разрешение ALTER ANY ROLE** разрешение или **ALTER** разрешение для роли.  
  
 Для добавления членов в предопределенную роль базы данных необходимо быть членом предопределенной роли базы данных db_owner.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-windows-login"></a>A. Добавление имени входа Windows  
 В следующем примере добавляется имя входа Windows `Contoso\Mary5` для `AdventureWorks2012` базы данных как пользователь `Mary5`. Затем пользователь `Mary5` добавляется к роли `Production`.  
  
> [!NOTE]  
>  Так как `Contoso\Mary5` известен как пользователь базы данных `Mary5` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] , имя пользователя `Mary5` должно быть определено. Выражение будет завершаться с ошибкой `Contoso\Mary5` , пока существует имя для входа. Можно проверить, используя имя входа в домене.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE USER Mary5 FOR LOGIN [Contoso\Mary5] ;  
GO  
```  
  
### <a name="b-adding-a-database-user"></a>Б. Добавление пользователя базы данных  
 В следующем примере пользователь базы данных `Mary5` добавляется к роли базы данных `Production` текущей базы данных.  
  
```  
EXEC sp_addrolemember 'Production', 'Mary5';  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-adding-a-windows-login"></a>В. Добавление имени входа Windows  
 В следующем примере добавляется имя входа `LoginMary` для `AdventureWorks2008R2` базы данных как пользователь `UserMary`. Затем пользователь `UserMary` добавляется к роли `Production`.  
  
> [!NOTE]  
>  Так как имя входа `LoginMary` известен как пользователь `UserMary` в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных, имя пользователя `UserMary` должен быть указан. Выражение будет завершаться с ошибкой `Mary5` , пока существует имя для входа. Имена входа и пользователи обычно имеют тем же именем. В этом примере использует разные имена для различения действий, затрагивающих имени входа и пользователя.  
  
```  
-- Uses AdventureWorks  
  
CREATE USER UserMary FOR LOGIN LoginMary ;  
GO  
EXEC sp_addrolemember 'Production', 'UserMary'  
```  
  
### <a name="d-adding-a-database-user"></a>Г. Добавление пользователя базы данных  
 В следующем примере пользователь базы данных `UserMary` добавляется к роли базы данных `Production` текущей базы данных.  
  
```  
EXEC sp_addrolemember 'Production', 'UserMary'  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_grantdbaccess (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  
