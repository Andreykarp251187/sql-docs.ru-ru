---
title: MSSQL_ENG014150 | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d41e532936b29d7824c27da57653bafe0a304408
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100191"
---
# <a name="mssqleng014150"></a>MSSQL_ENG014150
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14150|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Репликация-%s: агент %s выполнен успешно. %s|  
  
## <a name="explanation"></a>Объяснение  
 Это сообщение указывает, что агент репликации успешно завершил работу. Для репликации применяются следующие агенты.  
  
-   Агент моментальных снимков. Используется всеми публикациями.  
  
-   Агент чтения журнала. Используется всеми публикациями транзакций.  
  
-   Агент чтения очереди. Используется публикациями транзакций, для которых включены обновляемые посредством очередей подписки.  
  
-   Агент распространителя. Синхронизирует подписки на публикации транзакций и публикации моментальных снимков.  
  
-   Агент слияния. Синхронизирует подписки на публикации слиянием.  
  
-   Задания по обслуживанию репликации.  
  
## <a name="user-action"></a>Действие пользователя  
 Агент чтения журнала, агент чтения очереди и агент распространителя обычно выполняются постоянно, тогда как другие агенты чаще всего выполняются по запросу или по расписанию. Если агент неожиданно завершил работу, проверьте состояние агента. Дополнительные сведения см. в статье [Monitor Replication Agents](../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
## <a name="see-also"></a>См. также:  
 [Администрирование агента репликации](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Агент распространения репликации](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Агент слияния репликации](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Агент моментальных снимков репликации](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
