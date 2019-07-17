---
title: sp_delete_targetserver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_targetserver
- sp_delete_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_targetserver
ms.assetid: cc438701-ad91-419d-9f23-ebc4c548c700
author: stevestein
ms.author: sstein
ms.openlocfilehash: 487d88a7580432bf947893920d307e2f0adffd18
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111993"
---
# <a name="spdeletetargetserver-transact-sql"></a>sp_delete_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет указанный сервер из списка доступных целевых серверов.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_targetserver [ @server_name = ] 'server'   
     [ , [ @clear_downloadlist = ] clear_downloadlist ]  
     [ , [ @post_defection = ] post_defection ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @server_name = ] 'server'` Имя сервера, необходимо удалить в качестве доступного целевого сервера. *сервер* — **nvarchar(30)** , не имеет значения по умолчанию.  
  
`[ @clear_downloadlist = ] clear_downloadlist` Указывает, очистить ли список загрузки для целевого сервера. *clear_downloadlist* является типом **бит**, значение по умолчанию **1**. Когда *clear_downloadlist* — **1**, процедура очищает список загрузки для сервера перед удалением сервера. Когда *clear_downloadlist* — **0**, список загрузки не очищается.  
  
`[ @post_defection = ] post_defection` Указывает, следует ли отправлять инструкцию отключения на целевой сервер. *post_defection* является типом **бит**, значение по умолчанию 1. Когда *post_defection* — **1**, процедура посылает инструкцию отключения на целевой сервер перед удалением сервера. Когда *post_defection* — **0**, процедура не отправлять инструкцию отключения на целевой сервер.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Обычным способом удаления целевого сервера является вызов **sp_msx_defect** на целевом сервере. Используйте **sp_delete_targetserver** только при необходимости ручное исключение.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы выполнить эту хранимую процедуру, пользователям необходимо предоставить **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере сервер `LONDON1` удаляется из списка доступных серверов заданий.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_targetserver  
  @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_help_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)   
 [sp_msx_defect &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-defect-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
