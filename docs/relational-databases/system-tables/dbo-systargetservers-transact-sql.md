---
description: dbo.systargetservers (Transact-SQL)
title: dbo.sysтаржетсерверс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6ecf738591688ba3ad25c58f6b77dabec5df73b2
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538321"
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Записи, занесенные целевыми серверами в этот многосерверный операционный домен.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификатор сервера.|  
|**server_name**|**sysname**|Имя сервера.|  
|**расположение**|**nvarchar(200)**|Расположение указанного целевого сервера.|  
|**time_zone_adjustment**|**int**|Интервал смещения времени, в часах, от среднего времени по Гринвичу (GMT).|  
|**enlist_date**|**datetime**|Дата и время, когда указанный сервер был занесен в список.|  
|**last_poll_date**|**datetime**|Дата и время последнего опроса **sysdownloadlist** системной таблицы многосерверной системы для выполнения заданий.|  
|**status**|**int**|Состояние целевого сервера:<br /><br /> **1** = обычная<br /><br /> **2** = ожидается повторная синхронизация<br /><br /> **4** = предположительно вне сети|  
|**local_time_at_last_poll**|**datetime**|Дата и время последнего обращения к целевому серверу за операциями заданий.|  
|**enlisted_by_nt_user**|**nvarchar (100)**|Имя пользователя, выполняющего **sp_msx_enlist** на целевом сервере.|  
|**poll_internal**|**int**|Количество секунд, которое должно пройти, прежде чем целевой сервер обратится к главному серверу за новыми инструкциями по загрузке.|  
  
  
