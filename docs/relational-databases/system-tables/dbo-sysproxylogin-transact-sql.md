---
title: dbo.sysproxylogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fb62d70c1b0a41edf684a8216205fb43e070eea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984879"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Регистрирует текущее соответствие учетных записей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетным записям-посредникам агента SQL Server. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Идентификатор учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это значение соответствует **proxy_id** столбца в **sysproxies** таблицы.|  
|**ИД безопасности**|**varbinary(85)**|Microsoft Windows *security_identifier* для имени входа SQL Server.|  
|**principal_id**|**int**|Идентификатор пользователя или группы, которая имеет разрешение на использование учетной записи-посредника для указанного шага подсистемы.|  
|**flags**|**int**|Тип имени входа:<br /><br /> **0** = группы или пользователя Windows, и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа.<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Фиксированная системная роль<br /><br /> **2** = **msdb** роли базы данных|  
  
## <a name="remarks"></a>Примечания  
 Только члены **sysadmin** предопределенной роли сервера можно получить доступ к этой таблице.  
  
## <a name="see-also"></a>См. также  
 [dbo.sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
