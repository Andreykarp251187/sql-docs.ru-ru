---
title: Группы доступности AlwaysOn Взаимодействие (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3f6123f66d687327ba56601419328e44fd920a2a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62815755"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Группы доступности AlwaysOn Взаимодействие (SQL Server)
  В этом разделе описывается совместимость [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] с другими функциями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  

  
##  <a name="Interop"></a> Функции, совместимые с группами доступности AlwaysOn  
 В следующей таблице перечислены функции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , совместимые с [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Ссылка в столбце **Дополнительные сведения** указывает, что имеются замечания по совместимости данной функции.  
  
|Компонент|Дополнительные сведения|  
|-------------|----------------------|  
|система отслеживания измененных данных|[Репликация, отслеживание изменений, измененных данных и групп доступности AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|отслеживание изменений|[Репликация, отслеживание изменений, измененных данных и групп доступности AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Автономные базы данных|[Автономные базы данных с группами доступности AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)|  
|Шифрование базы данных|[Зашифрованные базы данных с группами доступности AlwaysOn &#40;SQL Server&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|Моментальные снимки базы данных|[Моментальные снимки с группами доступности AlwaysOn для баз данных &#40;SQL Server&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM и FileTable|[FILESTREAM и FileTable с группами доступности AlwaysOn &#40;SQL Server&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|Полнотекстовый поиск|Примечание. Полнотекстовые индексы синхронизируются с базами данных-получателя AlwaysOn.|  
|доставка журналов;|[Необходимые условия для перехода от использования доставки журналов для групп доступности AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|Удаленное хранилище больших двоичных объектов|[Remote Blob Store &#40;RBS&#41; и группы доступности AlwaysOn &#40;SQL Server&#41;](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|Репликация[Настройка репликации для групп доступности AlwaysOn (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [Обслуживание базы данных публикации AlwaysOn &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [Репликация, отслеживание изменений, измененных данных и групп доступности AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [Подписчики репликации и группы доступности AlwaysOn &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Службы Analysis Services|[Службы Analysis Services с группами доступности AlwaysOn](analysis-services-with-always-on-availability-groups.md)|  
|Службы Reporting Services|Используйте вторичные реплики, доступные только для чтения, в качестве источника данных для отчетов для снижения нагрузки на первичную реплику, доступную для чтения и записи.<br /><br /> [Службы Reporting Services с группами доступности AlwaysOn &#40;SQL Server&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Компонент Service Broker|[Компонент Service Broker с группами доступности AlwaysOn &#40;SQL Server&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|Агент SQL Server||  
  
##  <a name="NoInterop"></a> Компоненты, несовместимые с группами доступности AlwaysOn  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] не работает в сочетании со следующими функциями.  
  
-   Транзакции между разными базами данных или распределенные транзакции  
  
     Сведения о том, почему не поддерживаются такие транзакции, см. в разделе [Транзакции между базами данных не поддерживаются при зеркальном отображении баз данных или в группах доступности AlwaysOn (SQL Server)](transactions-always-on-availability-and-database-mirroring.md).  
  
-   Зеркальное отображение базы данных  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [Руководство по миграции. Миграция на SQL Server 2012 отказоустойчивая кластеризация и группы доступности, с предшествующих кластеров и зеркальных отображений](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [Блоги группы AlwaysOn SQL Server: Официальный блог по SQL Server AlwaysOn Team](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги инженеров CSS SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Технические документы**  
  
     [Руководство по миграции. Переход на группы доступности AlwaysOn с предыдущих развертываний, сочетающих зеркальное отображение базы данных и доставка журналов](https://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft SQL Server AlwaysOn Solutions Guide for высокий уровень доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
