---
title: MSSQL_ENG014150 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fc4e2ecd81b6bf0a6c24aff8e89dc31c95e04625
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63191437"
---
# <a name="mssql_eng014150"></a>MSSQL_ENG014150
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
 Агент чтения журнала, агент чтения очереди и агент распространителя обычно выполняются постоянно, тогда как другие агенты чаще всего выполняются по запросу или по расписанию. Если агент неожиданно завершил работу, проверьте состояние агента. Дополнительные сведения см. в статье [Monitor Replication Agents](agents/replication-agents-overview.md).  
  
## <a name="see-also"></a>См. также:  
 [Администрирование агента репликации](agents/replication-agent-administration.md)   
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)   
 [Replication Distribution Agent](agents/replication-distribution-agent.md)   
 [Replication Log Reader Agent](agents/replication-log-reader-agent.md)   
 [Replication Merge Agent](agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  
