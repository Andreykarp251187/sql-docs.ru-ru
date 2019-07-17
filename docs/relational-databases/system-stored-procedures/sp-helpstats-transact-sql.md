---
title: sp_helpstats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpstats
- sp_helpstats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpstats
ms.assetid: 00ab3cfd-2736-4fc0-b1b2-16dd49fb2fe5
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fba09255204b796a5134e8b8098e650430b7de63
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048406"
---
# <a name="sphelpstats-transact-sql"></a>sp_helpstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает статистические сведения о столбцах и индексах указанной таблицы.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] Чтобы получить сведения о статистике, запрос [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) и [sys.stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md) представления каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpstats[ @objname = ] 'object_name'   
     [ , [ @results = ] 'value' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @objname = ] 'object_name'` Указывает таблицу, для которой необходимо получить статистические сведения. *object_name* — **nvarchar(520)** и не может иметь значение null. Можно указать одно- или двухкомпонентное имя таблицы.  
  
`[ @results = ] 'value'` Определяет экстент предоставляемых сведений. Допустимыми значениями являются **все** и **STATS**. **ВСЕ** Статистика предоставляется для всех индексов, а также столбцов, для которых создана статистика **STATS** только статистика, не связанная с индексом. *значение* — **nvarchar(5)** значение по умолчанию STATS.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 В следующей таблице отображены столбцы результирующего набора.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**statistics_name**|Название статистики. Возвращает **sysname** и не может иметь значение null.|  
|**statistics_keys**|Ключи, на которых основаны статистические сведения. Возвращает **nvarchar(2078)** и не может иметь значение null.|  
  
## <a name="remarks"></a>Примечания  
 Для отображения подробных статистических сведений об определенном индексе или статистике воспользуйтесь инструкцией DBCC SHOW_STATISTICS. Дополнительные сведения см. в разделе [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41; ](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md) и [sp_helpindex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере с помощью процедуры `sp_createstats` создаются статистики, состоящие из одного столбца, для всех подходящих столбцов всех таблиц пользователя в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Затем, чтобы найти полученные статистики, созданные для таблицы `sp_helpstats`, запускается процедура `Customer`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_createstats;  
GO  
EXEC sp_helpstats   
@objname = 'Sales.Customer',  
@results = 'ALL';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `statistics_name               statistics_keys`  
  
 `----------------------------  ----------------`  
  
 `_WA_Sys_00000003_22AA2996     AccountNumber`  
  
 `AK_Customer_AccountNumber     AccountNumber`  
  
 `AK_Customer_rowguid           rowguid`  
  
 `CustomerType                  CustomerType`  
  
 `IX_Customer_TerritoryID       TerritoryID`  
  
 `ModifiedDate                  ModifiedDate`  
  
 `PK_Customer_CustomerID        CustomerID`  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
