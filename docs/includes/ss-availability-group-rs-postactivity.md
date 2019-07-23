---
ms.openlocfilehash: bf755ccfe5a1a6816129173dcb6ad5050ea5e114
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68213329"
---

## <a name="add-a-database-to-the-availability-group"></a>Добавление базы данных в группу доступности

Убедитесь, что база данных, добавляемая в группу доступности, находится в режиме полного восстановления и имеет действительную резервную копию журналов. Если база данных тестовая или только что создана, сделайте ее резервную копию. Чтобы создать базу данных с именем `db1` и ее резервную копию, в основном экземпляре SQL Server выполните следующий скрипт Transact-SQL:

```sql
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1]
   TO DISK = N'c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Backup\db1.bak';
```

Чтобы добавить базу данных с именем `db1` в группу доступности с именем `ag1`, в первичной реплике SQL Server выполните следующий скрипт Transact-SQL:

```sql
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Убедитесь, что база данных создана на вторичных серверах.

Чтобы убедиться в том, что база данных `db1` создана и синхронизирована, в каждой вторичной реплике SQL Server выполните следующий запрос:

```sql
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
