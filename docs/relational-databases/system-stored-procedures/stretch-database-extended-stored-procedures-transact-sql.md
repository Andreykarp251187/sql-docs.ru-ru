---
title: Stretch Database, расширенные хранимые процедуры (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Stretch Database, stored procedures
ms.assetid: bda29952-4b8b-4295-ab78-f24dcb0b03c6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5acbd4a14de04df412d71fb4ec8fd7d40e8fb7a8
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65979986"
---
# <a name="stretch-database-extended-stored-procedures-transact-sql"></a>Stretch Database, расширенные хранимые процедуры (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 В этом разделе описываются расширенные хранимые процедуры, которые связаны с Stretch Database.  
  
## <a name="in-this-section"></a>в этом разделе  
[sys.sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md) удаляет соединения между локальной базы данных с поддержкой Stretch и удаленной базе данных Azure с проверкой подлинности.

[sys.sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md) возвращает количество часов перенесенных данных, хранящихся на сервере SQL в промежуточной таблице, чтобы обеспечить полное восстановление удаленной базы данных Azure, при необходимости восстановления.
  
 [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) восстанавливает соединения с проверкой подлинности между локальной базой данных включена для Stretch и удаленной базе данных.
  
 [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)  
 Согласовывает идентификатор пакета, хранящиеся в таблице с включенным Stretch SQL Server для наиболее недавно перенесенных данных с Идентификатором пакета, хранимой в удаленной таблице Azure. 
 
[sys.sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md) согласовывает столбцы в удаленной таблице Azure со столбцами в таблице с включенным Stretch SQL Server.
 
 [sys.sp_rda_reconcile_indexes](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-indexes-transact-sql.md) помещает в очередь задачи схемы для сверить индексы в удаленной таблице.
 
 [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) указывает, возвращают ли запросы к текущей базе данных с поддержкой Stretch и его таблиц локальных и удаленных данных (по умолчанию) или только локальные данные.
 
 [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) задает количество часов перенесенных данных, хранящихся на сервере SQL в промежуточной таблице, чтобы обеспечить полное восстановление удаленной базы данных Azure, при необходимости восстановления.
 
 [sys.sp_rda_test_connection](../../relational-databases/system-stored-procedures/sys-sp-rda-test-connection-transact-sql.md) проверяет соединение с SQL Server с удаленным сервером Azure и сообщает о проблемах, которые могут помешать миграции данных.
 
## <a name="see-also"></a>См. также  
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)  
  
  
