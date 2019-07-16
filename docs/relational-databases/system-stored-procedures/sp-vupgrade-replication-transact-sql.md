---
title: sp_vupgrade_replication (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_replication_TSQL
- sp_vupgrade_replication
helpviewer_keywords:
- sp_vupgrade_replication
ms.assetid: d2c0ed66-07d1-4adc-82e5-a654376879bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66ee4819e8830fd718334d4a094ec22c01bf069d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67927806"
---
# <a name="spvupgradereplication-transact-sql"></a>sp_vupgrade_replication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Активируется программой установки при обновлении сервера репликации. Производит необходимое обновление схемы и системных данных для поддержки репликации на текущем уровне продукта. Создает новые системные объекты репликации в системных и пользовательских базах данных. Эта хранимая процедура выполняется на машине, на которой должно производиться обновление репликации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_vupgrade_replication [ [@login=] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @ver_old= ] 'old_version' ]  
    [ , [ @force_remove= ] 'force_removal' ]  
    [ , [ @security_mode= ] security_mode ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @login = ] 'login'` — Это имя входа администратора системы, используемый при создании новых системных объектов в базе данных распространителя. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. Этот параметр не является обязательным, если *security_mode* присваивается **1**, что означает проверку подлинности Windows.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и поздних версий этот аргумент не используется.  
  
`[ @password = ] 'password'` — Пароль администратора системы, используемый при создании новых системных объектов в базе данных распространителя. *пароль* — **sysname**, значение по умолчанию **''** (пустая строка). Этот параметр не является обязательным, если *security_mode* присваивается **1**, что означает проверку подлинности Windows.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий этот параметр не обрабатывается.  
  
`[ @ver_old = ] 'old_version'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 Данная хранимая процедура является устаревшей и в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет удалена.  
  
`[ @force_remove = ] 'force_removal'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @security_mode = ] 'security_mode'` — Это режим безопасности имени входа, используемый при создании новых системных объектов в базе данных распространителя. *security_mode* — **бит** со значением по умолчанию **0**. Если **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использоваться проверка подлинности. Если **1**, будет использоваться проверка подлинности Windows.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и поздних версий этот аргумент не используется.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_vupgrade_replication** используется при обновлении всех типов репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_vupgrade_replication**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
