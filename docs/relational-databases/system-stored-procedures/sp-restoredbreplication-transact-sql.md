---
title: sp_restoredbreplication (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_restoredbreplication
- sp_restoredbreplication_TSQL
helpviewer_keywords:
- sp_restoredbreplication
ms.assetid: a2c5ee32-e6d9-46e9-8031-8ff13c20acf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: d868ea9ce585dece65653cb010d0ed73b1b0cf51
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129640"
---
# <a name="sprestoredbreplication-transact-sql"></a>sp_restoredbreplication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет настройки репликации при восстановлении базы данных на сервер в базу данных, не являющиеся ее источниками, или на системе, не способной по какой-либо причине выполнять процессы репликации. При восстановлении реплицированной базы данных на сервер или в базу данных, отличающиеся от источника, с которого была создана резервная копия, сохранить настройки репликации невозможно. При восстановлении сервер вызывает **sp_restoredbreplication** напрямую, чтобы автоматически удалить метаданные репликации из восстановленной базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_restoredbreplication [ @srv_orig = ] 'original_server_name'  
        , [ @db_orig = ] 'original_database_name'  
    [ , [ @keep_replication = ] keep_replication ]  
    [ , [ @perform_upgrade = ] perform_upgrade ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @srv_orig = ] 'original_server_name'` Имя сервера, где было создано резервного копирования. *original_server_name* — **sysname**, не имеет значения по умолчанию.  
  
`[ @db_orig = ] 'original_database_name'` Имя базы данных, резервная копия. *original_database_name* — **sysname**, не имеет значения по умолчанию.  
  
`[ @keep_replication = ] keep_replication` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @perform_upgrade = ] perform_upgrade` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_restoredbreplication** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** или **dbcreator** предопределенной роли сервера или **dbo** схемы базы данных могут выполнять процедуру **sp_restoredbreplication**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
