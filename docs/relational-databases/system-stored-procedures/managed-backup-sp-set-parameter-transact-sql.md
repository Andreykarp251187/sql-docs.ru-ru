---
title: managed_backup.sp_set_parameter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_parameter_TSQL
- sp_set_parameter
- smart_admin.sp_set_parameter
- smart_admin.sp_set_parameter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_parameter
- smart_admin.sp_set_parameter
ms.assetid: bd8ae5fd-1337-4b7f-b0a4-153cbca9fa5f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 838a8b0d998476a37b0dd4d30cab5041ad4276a0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942037"
---
# <a name="managedbackupspsetparameter-transact-sql"></a>managed_backup.sp_set_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Задает значение указанного системного параметра Smart Admin.  
  
 Доступные параметры связаны с [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Эти параметры используются для задания уведомлений по электронной почте, включения определенных расширенных событий и предоставления разрешения пользователю задавать политики управления на основе политик. Необходимо указать пары имени параметра и значения параметра.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
EXEC managed_backup.sp_set_parameter   
    [@parameter_name = ] {'SSMBackup2WANotificationEmailIds' | 'SSMBackup2WAEnableUserDefinedPolicy' | 'SSMBackup2WADebugXevent' | 'FileRetentionDebugXevent' | 'StorageOperationDebugXevent'}  
    ,[@parameter_value = ] 'parameter_value'  
```  
  
##  <a name="Arguments"></a> Аргументы  
 @parameter_name  
 Имя параметра, для которого требуется установить значение. @parameter_name — Это NVARCHAR(128). Доступные имена параметров — **SSMBackup2WANotificationEmailIds**, **SSMBackup2WADebugXevent**, **SSMBackup2WAEnableUserDefinedPolicy**, **FileRetentionDebugXevent**, и **StorageOperationDebugXevent**.  
  
 @parameter_value  
 Задаваемое значение параметра. @parameter Value — это NVARCHAR(128).  Ниже приведены разрешенные пары имен и значений параметров.  
  
-   @parameter_name = 'SSMBackup2WANotificationEmailIds': @parameter_value = «email»  
  
-   @parameter_name = 'SSMBackup2WAEnableUserDefinedPolicy': @parameter_value = {'true' | 'false'}  
  
-   @parameter_name = «SSMBackup2WADebugXevent»: @parameter_value = {'true' | 'false'}  
  
-   @parameter_name = «FileRetentionDebugXevent»: @parameter_value = {'true' | 'false'}  
  
-   @parameter_name = «StorageOperationDebugXevent» = {'true' | 'false'}  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="best-practices"></a>Рекомендации  
 Необязательный раздел, описывающий рекомендации по выполнению инструкции или процедуры.  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется **EXECUTE** разрешения на **managed_backup.sp_set_parameter** хранимой процедуры.  
  
## <a name="examples"></a>Примеры  
 Следующие примеры включают оперативные и отладочные расширенные события.  
  
```  
-- to enable operational events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionOperationalXevent', 'True'  
--  to enable debug events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
```  
  
 Следующий пример включает уведомления об ошибках и предупреждения по электронной почте, а также устанавливает emailID для отправки уведомлений.  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
```  
  
  
