---
description: MSrepl_errors (Transact-SQL)
title: MSrepl_errors (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_errors
- MSrepl_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_errors system table
ms.assetid: c6e023c1-2c32-4269-8d76-e442ea309e4b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5afa86de5a33eab4f7e77da1c825619a738381de
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540294"
---
# <a name="msrepl_errors-transact-sql"></a>MSrepl_errors (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSrepl_errors** содержит строки со сведениями об ошибках расширенных агент распространения и агент слияния. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор ошибки.|  
|**time**|**datetime**|Время возникновения ошибки.|  
|**error_type_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**source_type_id**|**int**|Идентификатор типа источника ошибки.|  
|**source_name**|**nvarchar (100)**|Имя источника ошибки.|  
|**error_code**|**sysname**|Код ошибки.|  
|**error_text**|**ntext**|Сообщение об ошибке.|  
|**xact_seqno**|**varbinary (16)**|Порядковый номер транзакции в журнале начальной транзакции для пакета, завершенного с ошибкой. Это последовательный номер журнала транзакций, содержащего первую транзакцию в пакете, выполненном с ошибкой. Он используется только агентами распространителя.|  
|**command_id**|**int**|Идентификатор команды пакета, завершенного с ошибкой. Это идентификатор первой команды в пакете, завершенном с ошибкой, используемый только агентами распространителя.|  
|**session_id**|**int**|Идентификатор сеанса агента, в котором возникла ошибка.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
