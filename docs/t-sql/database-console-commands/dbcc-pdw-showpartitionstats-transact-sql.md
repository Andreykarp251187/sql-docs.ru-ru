---
description: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 03ef74fb824c39aee0045f378f6aaf5268052794
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88479843"
---
# <a name="dbcc-pdw_showpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)

[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

Отображает размер и число строк для каждой секции таблицы в базе данных [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  

## <a name="arguments"></a>Аргументы  
 `[ database_name . [ schema_name ] . | schema_name . ] table_name`  
 Имя отображаемой таблицы, состоящее из одной, двух или трех частей.  Если имя таблицы состоит из двух или трех частей, оно должно заключаться в двойные кавычки (""). Заключать однокомпонентное имя таблицы в кавычки необязательно.  
  
## <a name="permissions"></a>Разрешения
Необходимо разрешение **VIEW SERVER STATE**.
  
## <a name="result-sets"></a>Результирующие наборы  
Этот набор является результатом выполнения команды DBCC PDW_SHOWPARTITIONSTATS.
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|partition_number|INT|Номер секции.|  
|used_page_count|BIGINT|Число страниц, используемых для данных.|  
|reserved_page_count|BIGINT|Количество страниц, зарезервированных в секции.|  
|row_count|BIGINT|Число строк в секции.|  
|pdw_node_id|INT|Вычислительный узел для данных.|  
|distribution_id|INT|Идентификатор единицы распределения для данных.|  
  
## <a name="examples-sssdw-and-sspdw"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdw_showpartitionstats-basic-syntax-examples"></a>A. Примеры базового синтаксиса DBCC PDW_SHOWPARTITIONSTATS  
В приведенных ниже примерах отображается занимаемое пространство и число строк для каждой секции таблицы FactInternetSales в базе данных [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  

## <a name="see-also"></a>См. также раздел

- [DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)](dbcc-pdw-showexecutionplan-transact-sql.md)  
- [DBCC PDW_SHOWSPACEUSED (Transact-SQL)](dbcc-pdw-showspaceused-transact-sql.md)  
