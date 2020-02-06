---
title: Разнородная репликация базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/28/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, about heterogeneous database replication
- replication [SQL Server], heterogeneous database replication
- heterogeneous database replication
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6c7393b7cad97c613bf288d2f9e49e5922842e0b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67900980"
---
# <a name="heterogeneous-database-replication"></a>разнородная репликация базы данных  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает следующие разнородные сценарии для репликации транзакций и репликации моментальных снимков.  
  
-   Публикация данных с подписчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на подписчики, отличные от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  

-   Публикация данных в Oracle и из Oracle имеет следующие ограничения:  

  | |2016 или более ранние версии |2017 или более поздние версии |
  |-------|-------|--------|
  |Репликация из Oracle |Поддержка только Oracle 10g или более ранних версий |Поддержка только Oracle 10g или более ранних версий |
  |Репликация в Oracle |Версии до Oracle 12c |Не поддерживается |


 Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Публикация Oracle устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="publishing-data-from-oracle"></a>Публикация данных из Oracle  
 Для публикации данных из Oracle можно использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , причем большинство функций и простота их использования такие же, как и в случае репликации моментальных снимков и репликации транзакций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Для этой функции требуется Oracle 10G или более ранней версии. Публикация данных из Oracle идеально подходит для следующих сценариев:  
  
|Сценарий|Description|  
|--------------|-----------------|  
|Развертывание приложений на платформе[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Ведите разработку с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при работе с данными, реплицируемыми из базы данных, отличной от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Серверы промежуточного хранения данных|Поддерживайте синхронизацию промежуточных баз данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с базой данных, отличной от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Переход на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Протестируйте приложения в реальном времени совместно с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при репликации изменений исходной системы. Переключение на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при успешном испытании миграции.|  
  
 Дополнительные сведения см. в статье [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="publishing-data-to-non-sql-server-subscribers"></a>Публикация данных на подписчиках, отличных от подписчиков SQL Server  
 Следующие базы данных, отличные от баз данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], поддерживаются в качестве подписчиков для публикации моментальных снимков и публикации транзакций.  
  
-   Oracle для всех платформ с поддержкой Oracle.  
  
-   IBM DB2 для AS400, MVS, Unix, Linux и Windows.  
  
 Дополнительные сведения см. в статье [Non-SQL Server Subscribers](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
  
