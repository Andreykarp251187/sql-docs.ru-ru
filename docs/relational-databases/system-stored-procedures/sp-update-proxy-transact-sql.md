---
title: sp_update_proxy (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_proxy
- sp_update_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PROXY statement
- sp_update_proxy
ms.assetid: 864fd0e6-9d61-4f07-92ef-145318d2f881
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 632df5807e1e857c852807d0088219dee4448b6f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946709"
---
# <a name="spupdateproxy-transact-sql"></a>sp_update_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства существующей учетной записи-посредника.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @new_name = ] 'new_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @proxy_id = ] id` Идентификационный номер изменяемой. *Proxy_id* — **int**, значение по умолчанию NULL.  
  
`[ @proxy_name = ] 'proxy_name'` Имя прокси-сервера для изменения. *Proxy_name* — **sysname**, значение по умолчанию NULL.  
  
`[ @credential_name = ] 'credential_name'` Имя новых учетных данных прокси-сервера. *Credential_name* — **sysname**, значение по умолчанию NULL. Либо *credential_name* или *credential_id* может быть указан.  
  
`[ @credential_id = ] credential_id` Идентификационный номер новых учетных данных прокси-сервера. *Credential_id* — **int**, значение по умолчанию NULL. Либо *credential_name* или *credential_id* может быть указан.  
  
`[ @new_name = ] 'new_name'` Новое имя прокси-сервера. *Новое_имя* — **sysname**, значение по умолчанию NULL. Если указано, процедура изменяет имя прокси-сервера, *новое_имя*. Если этот аргумент равен NULL, имя учетной записи-посредника остается неизменным.  
  
`[ @enabled = ] is_enabled` Определяет, активна ли прокси-сервер. *Is_enabled* установлен флаг **tinyint**, значение по умолчанию NULL. Когда *is_enabled* — **0**, прокси-сервер не включен и не может использоваться шагом задания. Если этот аргумент равен NULL, состояние учетной записи-посредника остается неизменным.  
  
`[ @description = ] 'description'` Новое описание прокси-сервера. *Описание* — **nvarchar(512)** , значение по умолчанию NULL. Если этот аргумент равен NULL, описание учетной записи-посредника остается неизменным.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Либо **@proxy_name** или **@proxy_id** должен быть указан. Если указаны оба аргумента, они должны ссылаться на одну и ту же учетную запись-посредник, в противном случае хранимая процедура завершается ошибкой.  
  
 Либо **@credential_name** или **@credential_id** должен быть указан для изменения учетных данных прокси-сервер. Если указаны оба аргумента, они должны ссылаться на одни и те же учетные данные, в противном случае хранимая процедура завершается ошибкой.  
  
 Эта процедура вносит изменения в учетную запись-посредник, но не меняет порядок доступа к нему. Изменение доступа к учетной записи-посредника, использовать **sp_grant_login_to_proxy** и **sp_revoke_login_from_proxy**.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** фиксированной роли безопасности могут выполнить эту процедуру.  
  
## <a name="examples"></a>Примеры  
 В следующем примере значение «enabled» для учетной записи-посредника `Catalog application proxy` устанавливается в `0`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 0;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md)   
 [Хранимая процедура sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
