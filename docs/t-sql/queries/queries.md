---
title: Запросы | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5ff02a32-e8d3-479c-ae8b-07581e41f5f8
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 79afe251de0561bbf9dda840eb9ce578efa94b80
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68141303"
---
# <a name="queries"></a>Запросы

[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Язык обработки данных DML представляет словарь, используемый для получения данных и работы с ними в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и базе данных SQL. Большая часть инструкций также работает с хранилищем данных SQL и PDW (подробные сведения см. в описании каждой отдельной инструкции). Эти инструкции предназначены для добавления данных, изменения данных, запроса данных и удаления данных из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующей таблице перечислены инструкции DML, используемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|||  
|-|-|  
|[BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)|[SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)|  
|[DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)|[UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)|  
|[INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)|[UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)|  
|[MERGE (Transact-SQL)](../../t-sql/statements/merge-transact-sql.md)|[WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)|  
|[READTEXT (Transact-SQL)](../../t-sql/queries/readtext-transact-sql.md)| &nbsp; |  
| &nbsp; | &nbsp; |

 В следующей таблице перечислены предложения, используемые в нескольких инструкциях или предложениях DML.  
  
|Предложение|Может использоваться в следующих инструкциях|  
|------------|-------------------------------------|  
|[FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)|DELETE, SELECT, UPDATE|  
|[Указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql.md)|DELETE, INSERT, SELECT, UPDATE|  
|[Предложение OPTION (Transact-SQL)](../../t-sql/queries/option-clause-transact-sql.md)|DELETE, SELECT, UPDATE|  
|[Предложение OUTPUT (Transact-SQL)](../../t-sql/queries/output-clause-transact-sql.md)|DELETE, INSERT, MERGE, UPDATE|  
|[Условие поиска (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md)|DELETE, MERGE, SELECT, UPDATE|  
|[Конструктор табличных значений (Transact-SQL)](../../t-sql/queries/table-value-constructor-transact-sql.md)|FROM, INSERT, MERGE|  
|[TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md)|DELETE, INSERT, MERGE, SELECT, UPDATE|  
|[WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)|DELETE, SELECT, UPDATE, MATCH|  
|[WITH common_table_expression (Transact-SQL)](../../t-sql/queries/with-common-table-expression-transact-sql.md)|DELETE, INSERT, MERGE, SELECT, UPDATE|  
| &nbsp; | &nbsp; |
