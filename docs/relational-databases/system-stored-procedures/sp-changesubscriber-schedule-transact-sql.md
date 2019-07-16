---
title: sp_changesubscriber_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber_schedule
- sp_changesubscriber_schedule_TSQL
helpviewer_keywords:
- sp_changesubscriber_schedule
ms.assetid: ff84e8e2-d496-482c-b23e-38a6626596e6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a61dfd60dbde554ba3db24a4740b6220f9d68a99
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091334"
---
# <a name="spchangesubscriberschedule-transact-sql"></a>sp_changesubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет расписание агента распространителя или агента слияния для подписчика. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changesubscriber_schedule [ @subscriber = ] 'subscriber', [ @agent_type = ] type  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* — **sysname**. Имя подписчика должно быть уникальным в базе данных, не должно использоваться до этого и не может иметь значения NULL.  
  
`[ @agent_type = ] type` — Тип агента. *Тип* — **smallint**, значение по умолчанию **0**. **0** указывает на агент распространителя. **1** указывает на агент слияния.  
  
`[ @frequency_type = ] frequency_type` Это частота, с которой необходимо планировать задачу распространения. *frequency_type* — **int**, значение по умолчанию **64**. Существует 10 столбцов расписания.  
  
`[ @frequency_interval = ] frequency_interval` Значение, применяемое к частоте, задаваемой аргументом *frequency_type*. *frequency_interval* — **int**, значение по умолчанию **1**.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` — Дата задачи распределения. *frequency_relative_interval* — **int**, значение по умолчанию **1**.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию **0**.  
  
`[ @frequency_subday = ] frequency_subday` — Как часто, в минутах, производится изменение расписания в течение определенного периода. *frequency_subday* — **int**, значение по умолчанию **4**.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Интервал для *frequency_subday*. *frequency_subday_interval* — **int**, значение по умолчанию **5**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` — Время суток, когда запланирован первый запуск задачи распространения. *active_start_time_of_day* — **int**, значение по умолчанию **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` — Время суток, когда задачи распространения был удален из расписания. *active_end_time_of_day* — **int**, значение по умолчанию **235959**, означающее 23:59:59. в 24-часовом формате времени.  
  
`[ @active_start_date = ] active_start_date` Дата первого запуска задачи распространения запланирована, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию **0**.  
  
`[ @active_end_date = ] active_end_date` Дата, когда запуск задачи распространения, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию **99991231**, что соответствует 31 декабря 9999 года.  
  
`[ @publisher = ] 'publisher'` Указывает, отличный от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при изменении свойств статьи на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_changesubscriber_schedule** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_changesubscriber_schedule**.  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_addsubscriber_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-schedule-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
