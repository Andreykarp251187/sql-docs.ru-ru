---
title: sp_addapprole (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addapprole_TSQL
- sp_addapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addapprole
ms.assetid: 24200295-9a54-4cab-9922-fb2e88632721
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 74860a8f4c8dee263ea7ee0eea75679c721d1fa5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032978"
---
# <a name="spaddapprole-transact-sql"></a>sp_addapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет роль приложения к текущей базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addapprole [ @rolename = ] 'role' , [ @password = ] 'password'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'` — Имя новой роли приложения. *роль* — **sysname**, не имеет значения по умолчанию. *роль* должен быть допустимым идентификатором и не может уже существовать в текущей базе данных.  
  
 Имена ролей приложения могут содержать от 1 до 128 символов, включая любые буквы, специальные символы и цифры. Имена ролей, не может содержать обратную косую черту (\\) не может иметь значение NULL или пустая строка ("«).  
  
`[ @password = ] 'password'` — Пароль, необходимый для активации роли приложения. *пароль* — **sysname**, не имеет значения по умолчанию. *пароль* не может иметь значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 В ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователи (и роли) не полностью отличались от схем. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], схемы полностью отличаются от ролей. Эта новая архитектура отражена в поведении CREATE APPLICATION ROLE. Эта инструкция заменяет **sp_addapprole**.  
  
 Для обеспечения обратной совместимости с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **sp_addapprole** сделает следующее:  
  
-   если схема с таким же именем, как и имя роли приложения, еще не существует, то такая схема будет создана. Владельцем новой схемы будет роль приложения, и она же будет схемой по умолчанию в роли приложения;  
  
-   если схема с таким же именем, как и имя роли приложения, уже существует, то процедура завершится неудачно;  
  
-   Сложность пароля не будет проверена **sp_addapprole**. Но сложность пароля проверяется с помощью CREATE APPLICATION ROLE.  
  
 Параметр *пароль* хранится в виде одностороннего хэша.  
  
 **Sp_addapprole** хранимая процедура не может выполняться внутри пользовательской транзакции.  
  
> [!IMPORTANT]  
>  Microsoft ODBC **шифрования** параметр не поддерживается **SqlClient**. По возможности всегда запрашивайте пользователя ввести учетные данные роли приложения во время исполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранить учетные данные, то зашифруйте их с использованием функций CryptoAPI.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо наличие разрешения ALTER ANY APPLICATION ROLE для этой базы данных. Если схема с таким же самым именем и владельцем, как и имя и владелец новой роли, еще не существует, то также требуется разрешение CREATE SCHEMA на базу данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере добавляется новой роли приложения `SalesApp` с паролем `x97898jLJfcooFUYLKm387gf3` в текущей базе данных.  
  
```  
EXEC sp_addapprole 'SalesApp', 'x97898jLJfcooFUYLKm387gf3' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)  
  
  
