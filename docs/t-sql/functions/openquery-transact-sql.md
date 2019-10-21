---
title: OPENQUERY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OPENQUERY_TSQL
- OPENQUERY
dev_langs:
- TSQL
helpviewer_keywords:
- DELETE statement [SQL Server], OPENQUERY function
- OPENQUERY function
- FROM clause, OPENQUERY function
- UPDATE statement [SQL Server], OPENQUERY function
- pass-through queries [SQL Server]
- INSERT statement [SQL Server], OPENQUERY function
ms.assetid: b805e976-f025-4be1-bcb0-3a57b0c57717
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1276b80c4a668173f5a0b7055e789ab3f521dd9e
ms.sourcegitcommit: c7a202af70fd16467a498688d59637d7d0b3d1f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72313734"
---
# <a name="openquery-transact-sql"></a>OPENQUERY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Выполняет указанный передаваемый запрос к указанному связанному серверу. Этот сервер является источником данных OLE DB. Из предложения FROM запроса можно ссылаться на функцию OPENQUERY как на имя таблицы. На функцию OPENQUERY можно также ссылаться как на целевую таблицу инструкции INSERT, UPDATE или DELETE. Это зависит от возможностей поставщика OLE DB. Запрос может возвратить несколько результирующих наборов, но функция OPENQUERY возвращает только первый.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
OPENQUERY ( linked_server ,'query' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *linked_server*  
 Идентификатор, представляющий имя связанного сервера.  
  
 **'** *query* **'**  
 Строка запроса, выполненного в связанном сервере. Максимальная длина строки 8 КБ.  
  
## <a name="remarks"></a>Remarks  
 В качестве аргументов в функции OPENQUERY нельзя использовать переменные.  
  
 Функцию OPENQUERY нельзя использовать для выполнения расширенных хранимых процедур на связанном сервере. Однако расширенную хранимую процедуру можно выполнить на связанном сервере с помощью четырехкомпонентного имени. Пример:  
  
```sql  
EXEC SeattleSales.master.dbo.xp_msver  
```  
  
 Любой вызов функции OPENDATASOURCE, OPENQUERY или OPENROWSET в предложении FROM вычисляется отдельно и независимо от любого вызова этих функций, используемого как назначение при обновлении, даже если в двух таких вызовах будут заданы идентичные аргументы. В частности, условия фильтра или соединения, применяемые к результатам одного из таких вызовов, никак не влияют на результаты другого.  
  
## <a name="permissions"></a>Разрешения  
 Функцию OPENQUERY может выполнить любой пользователь. Разрешения, используемые для подключения к удаленному серверу, извлекаются из настроек, определенных для связанного сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-executing-an-update-pass-through-query"></a>A. Выполнение передаваемого запроса UPDATE  
 В следующем примере используется передаваемый запрос `UPDATE` к связанному серверу, созданному в примере А.  
  
```sql  
UPDATE OPENQUERY (OracleSvr, 'SELECT name FROM joe.titles WHERE id = 101')   
SET name = 'ADifferentName';  
```  
  
### <a name="b-executing-an-insert-pass-through-query"></a>Б. Выполнение передаваемого запроса INSERT  
 В следующем примере используется передаваемый запрос `INSERT` к связанному серверу, созданному в примере А.  
  
```sql  
INSERT OPENQUERY (OracleSvr, 'SELECT name FROM joe.titles')  
VALUES ('NewTitle');  
```  
  
### <a name="c-executing-a-delete-pass-through-query"></a>В. Выполнение передаваемого запроса DELETE  
 В следующем примере используется передаваемый запрос `DELETE` для удаления строки, созданной в примере В.  
  
```sql  
DELETE OPENQUERY (OracleSvr, 'SELECT name FROM joe.titles WHERE name = ''NewTitle''');  
```  
  
### <a name="d-executing-a-select-pass-through-query"></a>Г. Выполнение передаваемого запроса SELECT  
 В приведенном ниже примере используется передаваемый запрос `SELECT` для выбора строки, вставленной в примере В.  
  
```sql  
SELECT * FROM OPENQUERY (OracleSvr, 'SELECT name FROM joe.titles WHERE name = ''NewTitle''');  
```  
    
## <a name="see-also"></a>См. также:  
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [OPENDATASOURCE (Transact-SQL)](../../t-sql/functions/opendatasource-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [Функции наборов строк (Transact-SQL)](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_serveroption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)  
  
  
