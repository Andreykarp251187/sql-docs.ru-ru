---
title: sp_add_category (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_category
- sp_add_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_category
ms.assetid: 6cca32cd-d941-4378-aed6-a7c90cb7520a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b29f3e348800c300698533fb8aad47066bd0b46a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941761"
---
# <a name="spaddcategory-transact-sql"></a>sp_add_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет указанную категорию заданий, предупреждений или операторов на сервер.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_category   
     [ [ @class = ] 'class', ]   
     [ [ @type = ] 'type', ]   
     { [ @name = ] 'name' }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @class = ] 'class'` Класс добавляемой категории. *Класс* — **varchar(8)** со значением по умолчанию задания, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|JOB|Добавление категории заданий.|  
|ALERT|Добавление категории предупреждений.|  
|OPERATOR|Добавление категории операторов.|  
  
`[ @type = ] 'type'` Тип добавляемой категории. *Тип* — **varchar(12)** , со значением по умолчанию **ЛОКАЛЬНОГО**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|LOCAL|Локальная категория заданий.|  
|НЕСКОЛЬКИМИ СЕРВЕРАМИ|Многосерверная категория заданий.|  
|None|Категория для класса, отличного от задания **.**|  
  
`[ @name = ] 'name'` Имя добавляемой категории. Имя должно быть уникальным в указанном классе. *имя* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **sp_add_category** должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_add_category**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается локальная категория заданий с именем `AdminJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_category  
    @class=N'JOB',  
    @type=N'LOCAL',  
    @name=N'AdminJobs' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [dbo.sysjobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md)   
 [dbo.sysjobservers &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
