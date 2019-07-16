---
title: sys.sp_xtp_control_proc_exec_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_proc_exec_stats
- sys.sp_xtp_control_proc_exec_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_proc_exec_stats
ms.assetid: f5119808-76a1-4522-8529-9e02ee39adcb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 14c45f5ba725ef8d9cc498b1049c5a71c80a6d7a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67909226"
---
# <a name="sysspxtpcontrolprocexecstats-transact-sql"></a>sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Включает сбор статистики для скомпилированных в собственном коде хранимых процедур экземпляра.  
  
 Чтобы включить сбор статистики на уровне запроса для скомпилированных хранимых процедурах, см. в разделе [sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_xtp_control_proc_exec_stats [ [ @new_collection_value = ] collection_value ], [ @old_collection_value]  
```  
  
## <a name="arguments"></a>Аргументы  
 @new_collection_value = *значение*  
 Определяет, включен (1) или выключен (0) сбор статистики на уровне процедуры.  
  
 @new_collection_value имеет значение ноль Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или запуске базы данных.  
  
 @old_collection_value = *значение*  
 Возвращает текущее состояние.  
  
## <a name="return-code"></a>Код возврата  
 0 — успешное завершение. Ненулевое значение — ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли sysadmin.  
  
## <a name="code-samples"></a>Образцы кода  
 Чтобы задать @new_collection_value и запросить значение @new_collection_value:  
  
```  
exec [sys].[sp_xtp_control_proc_exec_stats] @new_collection_value = 1  
declare @c bit  
exec sp_xtp_control_proc_exec_stats @old_collection_value=@c output  
select @c as 'collection status'  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
