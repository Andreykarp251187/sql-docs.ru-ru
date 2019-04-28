---
title: sysdbmaintplans (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplans_TSQL
- sysdbmaintplans
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplans system table
ms.assetid: 0363296a-3082-48a9-9eb5-a1020b2f541a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0525a50b30036470336dafe10c78a42218486c63
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62686240"
---
# <a name="sysdbmaintplans-transact-sql"></a>sysdbmaintplans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта таблица включена в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] чтобы сохранить существующие сведения по экземплярам, обновленным с предыдущей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет содержимое этой таблицы. Эта таблица хранится в **msdb** базы данных.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|Идентификатор плана обслуживания базы данных.|  
|**plan_name**|**sysname**|Имя плана обслуживания базы данных.|  
|**date_created**|**datetime**|Дата создания плана обслуживания базы данных.|  
|**Владелец**|**sysname**|Владелец плана обслуживания базы данных.|  
|**max_history_rows**|**int**|Максимальное число строк, выделенных для записи журнала плана обслуживания базы данных в системной таблице.|  
|**remote_history_server**|**sysname**|Имя удаленного сервера, на котором может быть сохранен отчет журнала.|  
|**max_remote_history_rows**|**int**|Максимальное количество строк, выделенных в системной таблице на удаленном сервере, в которые может быть записан отчет журнала.|  
|**user_defined_1**|**int**|Значение по умолчанию — NULL.|  
|**user_defined_2**|**nvarchar(100)**|Значение по умолчанию — NULL.|  
|**user_defined_3**|**datetime**|Значение по умолчанию — NULL.|  
|**user_defined_4**|**uniqueidentifier**|Значение по умолчанию — NULL.|  
|**log_shipping**|**bit**|Статус доставки журналов:<br /><br /> **0** = отключено **1** = включено|  
  
  
