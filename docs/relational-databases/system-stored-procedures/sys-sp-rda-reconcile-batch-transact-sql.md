---
title: sys.sp_rda_reconcile_batch (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 54bdac5237ff190f3620bb29dabbf684868c0b75
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982930"
---
# <a name="syssprdareconcilebatch-transact-sql"></a>sys.sp_rda_reconcile_batch (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Согласовывает идентификатор пакета, хранящиеся в таблице с включенным Stretch SQL Server с Идентификатором пакета, хранимой в удаленной таблице Azure.  
  
 Обычно достаточно для запуска **sp_rda_reconcile_batch** Если вы вручную удалили наиболее недавно перенесенных данных из удаленной таблицы. При удалении вручную удаленных данных, включающий последние пакета, идентификаторы пакетной службы не синхронизированы и миграции останавливается.  
 
 Чтобы удалить данные, которые уже была перенесена в Azure, см. в разделе "Примечания" на этой странице.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 \@objname = "*\@objname*"  
 Имя таблицы SQL Server с поддержкой Stretch.  
  
## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  
  
## <a name="remarks"></a>Примечания  
 Если вы хотите удалить данные, которые уже была перенесена в Azure, выполните указанные ниже действия.  
  
1.  Приостановить перенос данных. Дополнительные сведения см. в разделе [Приостановка и возобновление переноса данных (Stretch Database)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
2.  Удалите данные из промежуточной таблицы SQL Server, выполнив команду удаления с подсказку STAGE_ONLY. Дополнительные сведения см. в разделе [выполнение административных обновлений и удалений](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints).
  
3.  Удаление тех же данных из удаленной таблицы Azure, выполнив команду удаления с указанием REMOTE_ONLY.  
  
4.  Запустите **sp_rda_reconcile_batch**.  
  
5.  Возобновление переноса данных. Дополнительные сведения см. в разделе [Приостановка и возобновление переноса данных (Stretch Database)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
## <a name="example"></a>Пример  
 Для выверки идентификаторов пакетов, выполните следующую инструкцию.  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
