---
title: MSpeer_response (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_response
- MSpeer_response_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_response system table
ms.assetid: 510e24cf-0292-47a9-b1d9-71a30fef030f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c930a5eeae8bfdb7d952610fadc0b7d779033435
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026669"
---
# <a name="mspeerresponse-transact-sql"></a>MSpeer_response (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpeer_response** таблица используется в репликации Peer-to-Peer для хранения ответа каждого узла с запросом состояния публикации. Эта таблица хранится в базе данных публикации.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|Идентифицирует запись запроса статуса в [MSpeer_request](../../relational-databases/system-tables/mspeer-request-transact-sql.md) таблицы.|  
|**однорангового узла**|**sysname**|Одноранговый узел, сформировавший ответ.|  
|**peer_db**|**sysname**|База данных подписки однорангового узла, сформировавшего ответ.|  
|**received_date**|**datetime**|Дата и время получения однорангового запроса.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
