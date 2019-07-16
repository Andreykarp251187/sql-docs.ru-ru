---
title: Хранимая процедура sp_helpreplicationoption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationoption
- sp_helpreplicationoption_TSQL
helpviewer_keywords:
- sp_helpreplicationoption
ms.assetid: ef988dbc-dd0b-4132-80ab-81eebec1cffe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9852aaaf0b719bfa03736997959d76110dff4d6e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997504"
---
# <a name="sphelpreplicationoption-transact-sql"></a>Хранимая процедура sp_helpreplicationoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Показывает типы параметров репликации, включенных на сервере. Эта хранимая процедура выполняется на любом сервере в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpreplicationoption [ [ @optname =] 'option_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @optname = ] 'option_name'` — Имя параметра репликации для запроса. *option_name* — **sysname**, значение по умолчанию NULL.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Транзакций**|Результирующий набор возвращается, если включена репликация транзакций.|  
|**Слияние**|Результирующий набор возвращается, если включена репликация слиянием.|  
|NULL (по умолчанию)|Результирующий набор не возвращается.|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|Имя параметра репликации, может быть одним из следующих:<br /><br /> **Транзакций**<br /><br /> **Слияние**|  
|**value**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**основная_версия**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**вспомогательная_версия**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**редакция**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**install_failures**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **Хранимая процедура sp_helpreplicationoption** используется для получения сведений о параметрах репликации, включенных на конкретном сервере. Чтобы получить сведения о конкретной базы данных, используйте **sp_helpreplicationdboption**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение по умолчанию принадлежат роли **public** .  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
