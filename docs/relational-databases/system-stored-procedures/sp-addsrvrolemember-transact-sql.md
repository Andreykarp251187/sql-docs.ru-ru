---
title: sp_addsrvrolemember (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addsrvrolemember
- sp_addsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addsrvrolemember
ms.assetid: 777f0e09-8ee5-4cb2-a3ac-939d02c3cd22
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2c927bdff462922d1846188366fbb92ce0d3663c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022424"
---
# <a name="spaddsrvrolemember-transact-sql"></a>sp_addsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет имя входа в качестве члена предопределенной роли сервера.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addsrvrolemember [ @loginame= ] 'login'   
    , [ @rolename = ] 'role'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @loginame **=** ] **"** _входа_ **"**  
 Имя входа, добавляемое к предопределенной роли сервера. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* может быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или имя входа Windows. Если имени входа Windows еще не был предоставлен доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], он предоставляется автоматически.  
  
 [ @rolename **=** ] **"** _роли_ **"**  
 Имя предопределенной роли сервера, к которой добавляется имя входа. *роль* — **sysname**, значение по умолчанию NULL, и должен иметь одно из следующих значений:  
  
-   sysadmin  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin  

## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 При добавлении имени входа к предопределенной роли сервера, оно получает разрешения, связанные с этой ролью.  
  
 Нельзя изменить членство в роли имени входа sa и общедоступных.  
  
 Процедура sp_addrolemember используется для добавления члена к предопределенной или определяемой пользователем роли.  
  
 sp_addsrvrolemember не может быть выполнена в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в роли, к которой добавляется новый элемент.  
  
## <a name="examples"></a>Примеры  
 В следующем примере добавляется имя входа Windows `Corporate\HelenS` для `sysadmin` предопределенной роли сервера.  
  
```  
EXEC sp_addsrvrolemember 'Corporate\HelenS', 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)   
 [CREATE SERVER ROLE (Transact-SQL)](../../t-sql/statements/create-server-role-transact-sql.md)   
 [DROP SERVER ROLE (Transact-SQL)](../../t-sql/statements/drop-server-role-transact-sql.md)  
  
  
