---
description: sp_trace_setstatus (Transact-SQL)
title: sp_trace_setstatus (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_setstatus_TSQL
- sp_trace_setstatus
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setstatus
ms.assetid: 29e7a7d7-b9c1-414a-968a-fc247769750d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 23d74214176d70ef2d71e04b1d758b4e40fac808
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543046"
---
# <a name="sp_trace_setstatus-transact-sql"></a>sp_trace_setstatus (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет текущее состояние указанной трассировки.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте расширенные события.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_trace_setstatus [ @traceid = ] trace_id , [ @status = ] status  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @traceid = ] trace_id` Идентификатор изменяемой трассировки. *trace_id* имеет **тип int**и не имеет значения по умолчанию. Пользователь использует это *trace_id* значение для выявления, изменения и управления трассировкой. Дополнительные сведения о получении *trace_id*см. в разделе [sys. Fn_trace_getinfo &#40;&#41;Transact-SQL ](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md).  
  
`[ @status = ] status` Указывает действие, реализуемое для трассировки. *состояние* имеет **тип int**и не имеет значения по умолчанию.  
  
 В следующей таблице приведены состояния, которые могут быть заданы.  
  
|Состояние|Описание|  
|------------|-----------------|  
|**0**|Останавливает указанную трассировку.|  
|**1**|Начинает указанную трассировку.|  
|**2**|Закрывает указанную трассировку и удаляет ее определение из сервера.|  
  
> [!NOTE]  
>  Перед закрытием трассировка должна быть остановлена. Перед просмотром трассировка должна быть остановлена и закрыта.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 В следующей таблице описаны значения кодов, которые могут быть возвращены пользователю при завершении хранимой процедуры.  
  
|Код возврата|Описание|  
|-----------------|-----------------|  
|**0**|Нет ошибки.|  
|**1**|Неизвестная ошибка.|  
|**8**|Указано недопустимое состояние.|  
|**9**|Указан недопустимый дескриптор трассировки.|  
|**13**|Недостаточно памяти. Возвращается, когда для выполнения указанного действия недостаточно памяти.|  
  
 Если трассировка уже находится в указанном состоянии, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] то возвращает **0**.  
  
## <a name="remarks"></a>Примечания  
 Параметры всех хранимых процедур трассировки SQL (**sp_trace_xx**) строго типизированы. Если эти аргументы указываются с неправильными типами данных входных параметров, как указано в описании их аргументов, хранимая процедура возвратит ошибку.  
  
 Пример использования хранимых процедур трассировки см. в разделе [Создание трассировки (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен иметь разрешение ALTER TRACE.  
  
## <a name="see-also"></a>См. также:  
 [sys. fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_getfilterinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Трассировка SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
