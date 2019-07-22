---
title: Поиск объектов, на которые наложено наибольшее число блокировок | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
helpviewer_keywords:
- objects [SQL Server], extended events
- xe
- extended events [SQL Server], locks
- objects [SQL Server], locks
ms.assetid: fcbadbda-c91c-43f0-a1b5-601e40110e07
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fac3a2a73e9701cde3420dc617fefc71ca46670d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074232"
---
# <a name="find-the-objects-that-have-the-most-locks-taken-on-them"></a>найти объекты, на которые наложено наибольшее число блокировок

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Администраторам баз данных часто нужно определить источник блокировок, приводящих к ухудшению производительности базы данных.  
  
 Например, наблюдение за рабочим сервером осуществляется с целью выявления возможных узких мест. Имеется предположение о наличии высоко востребованных ресурсов, поэтому требуется определить количество блокировок этих объектов. Как только объекты с наибольшим количеством блокировок будут определены, можно будет предпринять действия по оптимизации доступа к этим востребованным объектам.  
  
 Для этого воспользуйтесь редактором запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### <a name="to-find-the-objects-that-have-the-most-locks"></a>Поиск объектов с наибольшим количеством блокировок  
  
1.  В редакторе запросов выполните следующие инструкции.  
  
    ```  
    -- Find objects in a particular database that have the most  
    -- lock acquired. This sample uses AdventureWorksDW2012.  
    -- Create the session and add an event and target.  
    --   
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='LockCounts')  
    DROP EVENT session LockCounts ON SERVER  
    GO  
    DECLARE @dbid int  
  
    SELECT @dbid = db_id('AdventureWorksDW2012')  
  
    DECLARE @sql nvarchar(1024)  
    SET @sql = '  
    CREATE event session LockCounts ON SERVER  
    ADD EVENT sqlserver.lock_acquired (WHERE database_id =' + CAST(@dbid AS nvarchar) +')  
    ADD TARGET package0.histogram(   
    SET filtering_event_name=''sqlserver.lock_acquired'', source_type=0, source=''resource_0'')'  
  
    EXEC (@sql)  
    GO  
    ALTER EVENT session LockCounts ON SERVER   
    STATE=start  
    GO  
    --   
    -- Create a simple workload that takes locks.  
    --   
    USE AdventureWorksDW2012  
    GO  
    SELECT TOP 1 * FROM dbo.vAssocSeqLineItems  
    GO  
    -- The histogram target output is available from the   
    -- sys.dm_xe_session_targets dynamic management view in  
    -- XML format.  
    -- The following query joins the bucketizing target output with  
    -- sys.objects to obtain the object names.  
    --  
    SELECT name, object_id, lock_count FROM   
    (SELECT objstats.value('.','bigint') AS lobject_id,   
    objstats.value('@count', 'bigint') AS lock_count  
    FROM (  
    SELECT CAST(xest.target_data AS XML)  
    LockData  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'LockCounts'  
    ) Locks  
    CROSS APPLY LockData.nodes('//HistogramTarget/Slot') AS T(objstats)  
     ) LockedObjects   
    INNER JOIN sys.objects o  
    ON LockedObjects.lobject_id = o.object_id  
    WHERE o.type != 'S' AND o.type = 'U'  
    ORDER BY lock_count desc  
    GO  
    --   
    -- Stop the event session.  
    --   
    ALTER EVENT SESSION LockCounts ON SERVER  
    state=stop  
    GO  
  
    ```  
  
 После выполнения инструкций данной процедуры на вкладке **Результаты** редактора запросов будут отображены следующие столбцы.  
  
-   name  
  
-   object_id  
  
-   lock_count  
  
## <a name="see-also"></a>См. также:  
 [CREATE EVENT SESSION (Transact-SQL)](../../t-sql/statements/create-event-session-transact-sql.md)   
 [ALTER EVENT SESSION (Transact-SQL)](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [sys.dm_xe_session_targets (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql.md)   
 [sys.dm_xe_sessions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql.md)   
 [sys.server_event_sessions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)  
  
  
