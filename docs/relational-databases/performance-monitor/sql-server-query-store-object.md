---
title: SQL Server, объект хранилища запросов | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Query Store object
- SQL Server:Query Store
ms.assetid: b4a04acd-0b66-44a5-b72d-1a45b49e13e6
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 08cc5200801b99442c8973583f4ab7caa9ea9fb5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68140731"
---
# <a name="sql-server-query-store-object"></a>SQL Server, объект хранилища запросов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Объект хранилища запросов предоставляет счетчики, позволяющие отслеживать использование ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения текстов запросов, планов выполнения и статистики времени выполнения для таких объектов, как хранимые процедуры, динамические и подготовленные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и триггеры.  
  
 В таблице ниже описываются счетчики **SQL Server:хранилище запросов**.  
  
|Счетчики хранилища запросов SQL Server|Description|  
|-------------------------------------|-----------------|  
|**Счетчик использования ЦП для хранилища запросов**|Показывает использование ЦП для хранилища запросов.|  
|**Счетчик логических операций чтения хранилища запросов**|Показывает количество логических операций чтения, выполненных хранилищем запросов.|  
|**Счетчик логических операций записи хранилища запросов**|Показывает объем данных, которые помещаются в очередь для удаления из хранилища запросов. Частота и задержка добавления элементов в очередь (что представляет статистику времени выполнения) контролируются параметром интервала сброса данных.|  
|**Счетчик физических операций чтения хранилища запросов**|Показывает количество физических операций чтения, выполненных хранилищем запросов.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр хранилища запросов|Description|  
|--------------------------|-----------------|  
|**_Total**|Сведения о хранилище запросов для этого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|\<имя базы данных>|Сведения о хранилище запросов для этой базы данных.|  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Query Store Stored Procedures (Transact-SQL)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  (Хранимые процедуры хранилища запросов (Transact-SQL))  
 [Query Store Catalog Views (Transact-SQL) ](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  (Представления каталогов хранилища запросов (Transact-SQL))  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
