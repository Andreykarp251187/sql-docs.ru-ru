---
title: sp_helpmergearticlecolumn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticlecolumn
- sp_helpmergearticlecolumn_TSQL
helpviewer_keywords:
- sp_helpmergearticlecolumn
ms.assetid: 651c017b-9e9a-48f2-a0bd-6fc896eab334
author: stevestein
ms.author: sstein
ms.openlocfilehash: da2eec998176dfd46ab261fa405ecaa4b6e90044
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126440"
---
# <a name="sphelpmergearticlecolumn-transact-sql"></a>sp_helpmergearticlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список столбцов в статье указанной таблицы или представления для публикации слиянием. Поскольку хранимые процедуры не имеют столбцов, эта хранимая процедура возвращает ошибку, если в качестве статьи указана хранимая процедура. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergearticlecolumn [ @publication = ] 'publication' ]  
        , [ @article= ] 'article' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *публикации* — **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя таблицы или представления, являющейся статьей необходимо получить сведения. *статье* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**column_id**|**sysname**|Идентификатор столбца.|  
|**column_name**|**sysname**|Имя столбца для таблицы или представления.|  
|**Опубликованные**|**bit**|Указывает, опубликовано ли имя столбца.<br /><br /> **1** указывает, что столбец опубликован.<br /><br /> **0** указывает, что он не опубликован.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergearticlecolumn** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **replmonitor** предопределенной роли базы данных в базе данных распространителя или в списке доступа к публикации для публикации могут выполнять процедуру **sp_helpmergearticlecolumn**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
