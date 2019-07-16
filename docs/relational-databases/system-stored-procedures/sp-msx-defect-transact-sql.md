---
title: sp_msx_defect (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_defect
- sp_msx_defect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_defect
ms.assetid: 0dfd963a-3bc5-4b58-94f7-aec976da2883
author: stevestein
ms.author: sstein
ms.openlocfilehash: c8f2e34d15f7cca4443680b2d8b8a9fa2c7c6199
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952311"
---
# <a name="spmsxdefect-transact-sql"></a>sp_msx_defect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет текущий сервер из многосерверных операций.  
  
> [!CAUTION]  
>  **sp_msx_defect** вносит изменения в реестр. Редактировать реестр вручную не рекомендуется, так как неуместные или неверные изменения могут серьезно нарушить конфигурацию системы. Пользоваться программой редактирования реестра должны только опытные пользователи. Дополнительные сведения см. в документации по Microsoft Windows.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_msx_defect [@forced_defection =] forced_defection  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @forced_defection = ] forced_defection` Указывает, следует ли выполнять принудительное исключение в случае, если главный SQLServerAgent постоянно потерян по причине невосстановимого **msdb** базы данных, или нет, **msdb** резервной копии базы данных. *forced_defection*— **бит**, значение по умолчанию **0**, которое указывает, что принудительное исключение не должно выполняться. Значение **1** включает принудительное исключение.  
  
 После принудительного исключения, выполнив **sp_msx_defect**, является членом **sysadmin** предопределенной роли сервера на главном SQLServerAgent необходимо запустить следующую команду, чтобы завершить исключение:  
  
```  
EXECUTE msdb.dbo.sp_delete_targetserver @server_name = 'tsx-server', @post_defection =  0;  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Когда **sp_msx_defect** завершается должным образом, выдается сообщение.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также  
 [sp_msx_enlist &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
