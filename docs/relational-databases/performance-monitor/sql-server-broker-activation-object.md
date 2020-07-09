---
title: Объект активации брокера (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 0f2b877899a425397e7431d7b615c61356fb9d5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787335"
---
# <a name="sql-server-broker-activation-object"></a>SQL Server, объект Broker Activation
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Объект производительности **SQLServer:BrokerActivation** содержит счетчики производительности, возвращающие сведения об активации хранимых процедур. В следующей таблице перечислены счетчики этого объекта.  
  
|Счетчики SQL Server Broker Activation|Description|  
|-------------------------------------------|-----------------|  
|**Количество вызовов хранимых процедур/сек**|Этот счетчик возвращает общее количество хранимых процедур активации, вызываемых мониторами очереди в этом экземпляре за секунду.|  
|**Достигнут предел задач**|Этот счетчик возвращает общее число раз, когда монитор очереди должен был запустить новую задачу, но не сделал этого, так как уже выполнялось максимальное число задач для очереди.|  
|**Достигнут предел задач/сек**|Этот счетчик сообщает, сколько раз в секунду монитор очереди должен был запустить новую задачу, но не сделал этого, так как уже выполнялось максимальное число задач для очереди.|  
|**Прервано задач/сек**|Этот счетчик возвращает число задач хранимых процедур активации, завершившихся с ошибкой, либо тех, которые были прерваны монитором очереди из-за невозможности получать сообщения.|  
|**Задач работает**|Этот счетчик возвращает число хранимых процедур активации, работающих в настоящий момент.|  
|**Задач запущено/сек**|Этот счетчик возвращает число хранимых процедур активации, запущенных за секунду всеми мониторами очереди в этом экземпляре.|  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_broker_activated_tasks (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql.md)   
 [sys.dm_broker_queue_monitors (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
