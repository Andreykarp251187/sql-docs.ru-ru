---
title: Управление семантическим поиском и наблюдение за ним | Документация Майкрософт
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: c5e5c8256c117ebd3fbb57b5a7c291b539c5a428
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68132246"
---
# <a name="manage-and-monitor-semantic-search"></a>Управление и наблюдение за семантическим поиском
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Описывается процесс семантического индексирования и задачи, связанные с наблюдением за индексами и управлением ими.  
  
##  <a name="check-the-status-of-semantic-indexing"></a><a name="HowToMonitorStatus"></a> Проверка состояния семантической индексации  
### <a name="is-the-first-phase-of-semantic-indexing-complete"></a>Завершен ли первый этап семантического индексирования?
 Запросите динамическое административное представление [sys.dm_fts_index_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md) и проверьте столбцы **status** и **status_description**.  
  
 Первый этап индексирования включает заполнение полнотекстового индекса ключевых слов и семантического индекса ключевых фраз, а также извлечение данных о подобии документов.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
### <a name="is-the-second-phase-of-semantic-indexing-complete"></a>Завершен ли второй этап семантического индексирования?
 Запросите динамическое административное представление [sys.dm_fts_semantic_similarity_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md) и проверьте столбцы **status** и **status_description**.  
  
 Второй этап индексирования включает заполнение семантического индекса подобия документов.  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="check-the-size-of-the-semantic-indexes"></a><a name="HowToCheckSize"></a> Проверка размера семантических индексов  
### <a name="what-is-the-logical-size-of-a-semantic-key-phrase-index-or-a-semantic-document-similarity-index"></a>Каков логический размер семантического индекса ключевых фраз или семантического индекса подобия документов?
 Запросите динамическое административное представление [sys.dm_db_fts_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md).  
  
 Логический размер отображается в количестве страниц индекса.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
### <a name="what-is-the-total-size-of-the-full-text-and-semantic-indexes-for-a-full-text-catalog"></a>Каков общий размер полнотекстового и семантического индексов для полнотекстового каталога?  
 Запросите свойство **IndexSize** функции метаданных [FULLTEXTCATALOGPROPERTY (Transact-SQL)](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md).  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
### <a name="how-many-items-are-indexed-in-the-full-text-and-semantic-indexes-for-a-full-text-catalog"></a>Сколько элементов проиндексированы в полнотекстовом и семантическом индексах для полнотекстового каталога?  
 Запросите свойство **ItemCount** функции метаданных [FULLTEXTCATALOGPROPERTY (Transact-SQL)](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md).  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="force-the-population-of-the-semantic-indexes"></a><a name="HowToForcePopulation"></a> Принудительное заполнение семантических индексов  
 Можно принудительно выполнить заполнение полнотекстового и семантического индексов с помощью предложений START/STOP/PAUSE или RESUME POPULATION с таким же синтаксисом и поведением, как описано для полнотекстовых индексов. Дополнительные сведения см. в разделах [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md) и [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md).  
  
 Поскольку семантическое индексирование зависит от полнотекстового индексирования, семантические индексы заполняются только после заполнения связанных полнотекстовых индексов.  
  
 **Пример. Запуск полного заполнения полнотекстового и семантического индексов**  
  
 В следующем примере запускается заполнение полнотекстового и семантического индексов путем изменения существующего полнотекстового индекса таблицы **Production.Document** в образце базы данных AdventureWorks2012.  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="disable-or-re-enable-semantic-indexing"></a><a name="HowToDisableIndexing"></a> Отключение и повторное включение семантической индексации  
 Можно включить или отключить полнотекстовое или семантическое индексирование с помощью предложений ENABLE/DISABLE с таким же синтаксисом и поведением, как описано для полнотекстовых индексов. Дополнительные сведения см. в статье [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md).  
  
 Если семантическое индексирование отключено и приостановлено, запросы к семантическим данным продолжают успешно выполняться и возвращать ранее проиндексированные данные. Такое поведение не согласуется с поведением полнотекстового поиска.  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="about-the-phases-of-semantic-indexing"></a><a name="SemanticIndexing"></a> Этапы семантической индексации  
 Для семантического поиска индексируются два типа данных для каждого столбца, по которому он включен.  
  
1.  **Ключевые фразы**  
  
2.  **Подобие документов**  
  
 Семантическое индексирование выполняется в два этапа совместно с полнотекстовым индексированием.  
  
1.  **Этап 1**. Полнотекстовый индекс ключевых слов и семантический индекс ключевых фраз заполняются параллельно и одновременно. Одновременно извлекаются данные, необходимые для индексирования подобия документов.  
  
2.  **Этап 2**. Затем заполняется семантический индекс подобия документов. Этот индекс зависит от обоих индексов, заполненных на предыдущем этапе.  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="issue-semantic-indexes-are-not-populated"></a><a name="ProblemNotPopulated"></a> Проблема: семантические индексы не заполнены  
### <a name="are-the-associated-full-text-indexes-populated"></a>Заполнены ли связанные полнотекстовые индексы?  
 Поскольку семантическое индексирование зависит от полнотекстового индексирования, семантические индексы заполняются только после заполнения связанных полнотекстовых индексов.  
  
### <a name="are-full-text-search-and-semantic-search-properly-installed-and-configured"></a>Правильно ли установлены и настроены компоненты полнотекстового поиска и семантического поиска?  
 Дополнительные сведения см. в разделе [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
### <a name="is-the-fdhost-service-not-available-or-is-there-another-condition-that-would-cause-full-text-indexing-to-fail"></a>Не находится ли служба FDHOST в состоянии «недоступна» и нет ли других проблем, которые могли бы вызвать сбой полнотекстового индексирования?  
 Дополнительные сведения см. в разделе [Устранение неполадок полнотекстового индексирования](../../relational-databases/search/troubleshoot-full-text-indexing.md).  
  
  
