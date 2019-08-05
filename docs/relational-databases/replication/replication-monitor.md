---
title: Монитор репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.beta2.f1
helpviewer_keywords:
- Replication Monitor, help
ms.assetid: 39b92198-c3f6-4f25-8560-095848ad652d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 89f992afc1a419f5d2fa5aa172d9e5e930a8a21b
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769682"
---
# <a name="replication-monitor"></a>монитор репликации
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  В данном разделе документации содержатся сведения о мониторе репликации. Страницы и диалоговые окна, отображаемые в мониторе, различаются в зависимости от типа репликации и версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , мониторинг которой осуществляется.  
  
-   [Replication Monitor, Main Page](../../relational-databases/replication/replication-monitor-main-page.md) (Монитор репликации, страница "Общие")  
  
-   [Добавление издателя](../../relational-databases/replication/add-publisher.md)  
  
-   [Параметры распространителя](../../relational-databases/replication/distributor-settings.md)  
  
-   [Сведения о распространителе, вкладка "Публикации"](../../relational-databases/replication/distributor-information-publications.md)  
  
-   [Настройки издателя](../../relational-databases/replication/publisher-settings.md)  
  
-   [Publisher Information, Publications](../../relational-databases/replication/publisher-information-publications.md) (Данные об издателе, вкладка "Публикации")  
  
-   [Publisher Information, Subscription Watch List (Transactional Publication, SQL Server 2005 and Later)](../../relational-databases/replication/publisher-information-subscription-watch-list-transactional.md) (Сведения об издателе, вкладка "Список наблюдения за подписками" (публикация транзакций, SQL Server 2005 и более поздние версии))  
  
-   [Publisher Information, Subscription Watch List (Merge Publication, SQL Server 2005 and Later)](../../relational-databases/replication/publisher-information-subscription-watch-list-merge-publication.md) (Сведения об издателе, вкладка "Список наблюдения за подписками" (публикация слиянием, SQL Server 2005 и более поздние версии))  
  
-   [Publisher Information, Subscription Watch List (Snapshot Publication, SQL Server 2005 and Later)](../../relational-databases/replication/publisher-information-subscription-watch-list-snapshot.md) Сведения об издателе, вкладка "Список наблюдения за подписками" (публикация моментальных снимков, SQL Server 2005 и более поздние версии)  
  
-   [Publisher Information, Agents](../../relational-databases/replication/publisher-information-agents.md) (Данные об издателе, вкладка "Агенты")  
  
-   [Publication Information, All Subscriptions (Transactional Publication)](../../relational-databases/replication/publication-information-all-subscriptions-transactional-publication.md) (Сведения о публикации, вкладка "Все подписки" (публикация транзакций))  
  
-   [Publication Information, All Subscriptions (Merge Publication)](../../relational-databases/replication/publication-information-all-subscriptions-merge-publication.md) (Сведения о публикации, вкладка "Все подписки" (публикация слиянием))  
  
-   [Publication Information, All Subscriptions (Snapshot Publication)](../../relational-databases/replication/publication-information-all-subscriptions-snapshot-publication.md) (Сведения о публикации, вкладка "Все подписки" (публикация моментальных снимков))  
  
-   [Publication Information, Warnings (Transactional Publication, SQL Server 2005 and Later)](../../relational-databases/replication/publication-information-warnings-transactional-publication.md) (Сведения о публикации, вкладка "Предупреждения" (публикация транзакций, SQL Server 2005 и более поздние версии))  
  
-   [Publication Information, Warnings (Merge Publication, SQL Server 2005 and Later)](../../relational-databases/replication/publication-information-warnings-merge-publication-sql-server-2005-and-later.md) (Сведения о публикации, вкладка "Предупреждения" (публикации слиянием, SQL Server 2005 и более поздние версии))  
  
-   [Сведения о публикации, вкладка "Предупреждения" (публикация моментальных снимков, SQL Server 2005 и более поздние версии)](../../relational-databases/replication/publication-information-warnings-snapshot-publication-sql-server-2005-and-later.md)  
  
-   [Publication Information, Agents (Transactional Publication)](../../relational-databases/replication/publication-information-agents-transactional-publication.md) (Сведения о публикации, вкладка "Агенты" (публикация транзакций))  
  
-   [Publication Information, Agents (Merge Publication)](../../relational-databases/replication/publication-information-agents-merge-publication.md) (Сведения о публикации, вкладка "Агенты" (публикация слиянием))    
-   [Publication Information, Agents (Snapshot Publication)](../../relational-databases/replication/publication-information-agents-snapshot-publication.md) (Сведения о публикации, вкладка "Агенты" (публикация моментальных снимков))  
  
-   [Publication Information, Tracer Tokens (Transactional Publication, SQL Server 2005 and Later)](../../relational-databases/replication/publication-information-tracer-tokens-sql-server-2005-and-later.md) (Сведения о публикации, вкладка "Трассировочные токены" (публикация транзакций, SQL Server 2005 и более поздние версии))  
  
-   [Subscription, Undistributed Commands (Transactional Subscription, SQL Server 2005 and Later)](../../relational-databases/replication/subscription-undistributed-commands-transactional-subscription.md) (Подписка, вкладка "Нераспространенные команды" (подписка на публикацию транзакций, SQL Server 2005 и более поздние версии))  
  
-   [Subscription, Publisher to Distributor History (Transactional Subscription)](../../relational-databases/replication/subscription-publisher-to-distributor-history-transactional-subscription.md) (Подписка, вкладка "Журнал издателя для распространителя" (подписка на публикацию транзакций))  
  
-   [Subscription, Distributor to Subscriber History (Transactional Subscription)](../../relational-databases/replication/subscription-distributor-to-subscriber-history-transactional-subscription.md) (Подписка, вкладка "Журнал операций от распространителя к подписчику" (подписка на публикацию транзакций))  
  
-   [Subscription, Synchronization History (Merge Subscription, SQL Server 2005 and Later)](../../relational-databases/replication/subscription-synchronization-history.md) (Подписка, вкладка "Журнал синхронизации" (подписка на публикацию слиянием, SQL Server 2005 и более поздние версии))  
  
-   [Subscription, Distributor to Subscriber History (Snapshot Subscription)](../../relational-databases/replication/subscription-distributor-to-subscriber-history-snapshot-subscription.md) (Подписка, вкладка "Журнал операций от распространителя к подписчику" (подписка на моментальные снимки))  
  
-   [Log Reader Agent](../../relational-databases/replication/log-reader-agent.md) (Диалоговое окно "Агент чтения журнала")  
  
-   [Агент чтения очереди](../../relational-databases/replication/queue-reader-agent.md)  
  
-   [Агент моментальных снимков](../../relational-databases/replication/snapshot-agent.md)  
  
-   [Настройки фильтра](../../relational-databases/replication/filter-settings.md)  
  
-   [Sort Columns](../../relational-databases/replication/sort-columns.md) (Диалоговое окно "Сортировка столбцов")  
  
## <a name="see-also"></a>См. также:  
 [Запуск монитора репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   

  
  
