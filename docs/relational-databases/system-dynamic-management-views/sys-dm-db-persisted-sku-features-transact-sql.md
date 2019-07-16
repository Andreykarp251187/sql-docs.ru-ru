---
title: sys.dm_db_persisted_sku_features (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_persisted_sku_features_TSQL
- sys.dm_db_persisted_sku_features
- dm_db_persisted_sku_features_TSQL
- dm_db_persisted_sku_features
dev_langs:
- TSQL
helpviewer_keywords:
- editions [SQL Server], feature restrictions
- sys.dm_db_persisted_sku_features dynamic management view
ms.assetid: b4b29e97-b523-41b9-9528-6d4e84b89e09
author: stevestein
ms.author: sstein
ms.openlocfilehash: f59d96f9a1aa6598c5acb4fe9a88ea57965ede5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096274"
---
# <a name="sysdmdbpersistedskufeatures-transact-sql"></a>sys.dm_db_persisted_sku_features (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Некоторые функции компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] изменяют способ, с помощью которого [!INCLUDE[ssDE](../../includes/ssde-md.md)] хранит информацию в файлах базы данных. Эти функции зависят от конкретных выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. База данных, содержащая данные функции, не может быть перемещена в выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который их не поддерживает. Используйте динамическое административное представление sys.dm_db_persisted_sku_features Чтобы получить список зависящих от выпуска функций, включенных в текущей базе данных.
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|feature_name|**sysname**|Внешнее имя функции, включенной в базе данных, но не поддерживаемой всеми выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы обеспечить возможность переноса базы данных на все доступные выпуски [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], эту функцию необходимо удалить.|  
|feature_id|**int**|Связанный с функцией идентификатор. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)].|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на базу данных.  
  
## <a name="remarks"></a>Примечания  
 Если нет функций, которые может быть ограничен с помощью определенной версии используются в базе данных, представление не возвращает строк.  
  
 представление sys.dm_db_persisted_sku_features может содержать следующие функции изменения баз данных, как только к определенным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выпуски:  
  
-   **ChangeCapture**: Указывает, что базы данных имеет включить сбор данных изменений. Чтобы удалить измененных данных, используйте [sys.sp_cdc_disable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md) хранимой процедуры. Дополнительные сведения см. в статье [О системе отслеживания измененных данных (SQL Server)](../../relational-databases/track-changes/about-change-data-capture-sql-server.md).  
  
-   **ColumnStoreIndex**: Указывает, что, хотя бы одна таблица имеет индекс columnstore. Чтобы включить базу данных для перемещения в выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который не поддерживает эту функцию, используйте [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md) или [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) инструкцию, чтобы удалить индекс columnstore. Дополнительные сведения см. в разделе [индексы Columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md).  
  
    **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
-   **Сжатие**: Указывает, что по крайней мере одну таблицу или индекс используют сжатие данных или формат хранения vardecimal. Чтобы включить базу данных для перемещения в выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который не поддерживает эту функцию, используйте [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) инструкцию, чтобы отключить сжатие данных. Чтобы удалить формат хранения vardecimal, используйте инструкцию sp_tableoption. Дополнительные сведения см. в разделе [Data Compression](../../relational-databases/data-compression/data-compression.md).  
  
-   **MultipleFSContainers**: Указывает, что база данных использует несколько контейнеров файлового ПОТОКА. База данных имеет файловую группу FILESTREAM с несколькими контейнерами (файлы). Дополнительные сведения см. в разделе [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md).  
  
-   **InMemoryOLTP**: Указывает, что база данных использует In-Memory OLTP. База данных имеет файловую группу MEMORY_OPTIMIZED_DATA. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
  **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]). 
  
-   **Секционирование.** Указывает, что база данных содержит секционированные таблицы или индексы, схемы или функции секционирования. Чтобы обеспечить возможность перемещения базы данных в выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], отличный от Enterprise или Developer, недостаточно просто изменить таблицу, поместив ее в одну секцию. Необходимо удалить секционированную таблицу. Если таблица содержит данные, конвертировать каждую секцию в несекционированную таблицу можно с помощью инструкции SWITCH PARTITION. Затем необходимо удалить секционированную таблицу, схему секционирования и функцию секционирования.  
  
-   **TransparentDataEncryption.** Указывает, что база данных зашифрована с помощью прозрачного шифрования данных. Чтобы удалить прозрачное шифрование данных, используйте инструкцию ALTER DATABASE. Дополнительные сведения см. в статье [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md).  

> [!NOTE]
> Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1, эти функции доступны в нескольких [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выпуски и не ограничен Enterprise или Developer Edition только.

 Чтобы определить, используются ли в базе данных функции, ограниченные конкретными выпусками, выполните следующую инструкцию:  
  
```sql  
SELECT feature_name FROM sys.dm_db_persisted_sku_features;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [Выпуски и поддерживаемые функции SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Выпуски и поддерживаемых функций SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)  
  
