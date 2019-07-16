---
title: sp_dropmergepublication (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepublication
- sp_dropmergepublication_TSQL
helpviewer_keywords:
- sp_dropmergepublication
ms.assetid: 9e1cb96e-5889-4f97-88cd-f60cf313ce68
author: stevestein
ms.author: sstein
ms.openlocfilehash: b675b07466464f706b6503f3d017acd34822b2c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933904"
---
# <a name="spdropmergepublication-transact-sql"></a>sp_dropmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет публикацию слиянием и ассоциированный с ней агент моментальных снимков. Прежде чем удалять публикацию слиянием, необходимо удалить все подписки. Статьи в публикации удаляются автоматически. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmergepublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
    [ , [ @ignore_merge_metadata = ] ignore_merge_metadata ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, для удаления. *Публикация* — **sysname**, не имеет значения по умолчанию. Если **все**, а также задание агента моментальных снимков, связанных с ними удаляются все существующие публикации слиянием. Если указать определенное значение для *публикации*, удаляется только указанная публикация и его связанное задание агента моментальных снимков.  
  
`[ @ignore_distributor = ] ignore_distributor` Используется для удаления публикации без выполнения задач очистки на распространителе. *ignore_distributor* — **бит**, значение по умолчанию **0**. Данный аргумент также используется при переустановке распространителя.  
  
`[ @reserved = ] reserved` Зарезервировано для использования в будущем. *зарезервированные* — **бит**, значение по умолчанию **0**.  
  
`[ @ignore_merge_metadata = ] ignore_merge_metadata` Только для внутреннего использования.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropmergepublication** используется в репликации слиянием.  
  
 **sp_dropmergepublication** рекурсивно сбрасывает все статьи, связанные с публикацией, а затем удаляет саму публикацию. Публикацию нельзя удалить, если у нее есть хотя бы одна подписка. Сведения об удалении подписок см. в разделе [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md) и [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 Выполнение **sp_dropmergepublication** для удаления публикации не удаляет опубликованные объекты из базы данных публикации или соответствующие объекты из базы данных подписки. Используйте DROP \<объект > для удаления этих объектов вручную, при необходимости.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_dropmergepublication](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepublication-_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_dropmergepublication**.  
  
## <a name="see-also"></a>См. также  
 [Удаление публикации](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_helpmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
