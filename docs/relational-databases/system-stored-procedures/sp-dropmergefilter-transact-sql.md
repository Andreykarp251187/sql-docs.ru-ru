---
title: sp_dropmergefilter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergefilter_TSQL
- sp_dropmergefilter
helpviewer_keywords:
- sp_dropmergefilter
ms.assetid: 798586d7-05f3-4a5e-bea8-a34b7b52d0fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b952fcd8145a2cf5392308b21d593e8c377761f3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933966"
---
# <a name="spdropmergefilter-transact-sql"></a>sp_dropmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет фильтр слияния. **sp_dropmergefilter** удаляет все столбцы фильтра слияния, определенные в фильтре слияния, подлежащем удалению. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmergefilter [ @publication= ] 'publication', [ @article= ] 'article'     , [ @filtername= ] 'filtername'  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя статьи. *статья* — **sysname**, не имеет значения по умолчанию.  
  
`[ @filtername = ] 'filtername'` — Имя фильтра для удаления. *FilterName* — **sysname**, не имеет значения по умолчанию.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Включает или отключает возможность наличия недействительных моментальных снимков. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приводят к недействительности моментального снимка.  
  
 **1** означает, что изменения статьи слияния могут привести к недействительности моментального снимка. Если это так, значение **1** дает разрешение нового моментального снимка.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Включает или отключает возможность отметки подписки как не является допустимым. *Этот* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения в фильтре статьи слияния не приводят к недействительности подписок.  
  
 **1** обозначает, что изменения в фильтре статьи слияния приведут к недействительности подписок.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropmergefilter** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_dropmergefilter**.  
  
## <a name="see-also"></a>См. также  
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
