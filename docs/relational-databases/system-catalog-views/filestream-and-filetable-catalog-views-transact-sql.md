---
title: FileStream и представления каталога FileTable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
author: stevestein
ms.author: sstein
ms.openlocfilehash: 04fc26296d7c499982c75296089decfb57bd9ab4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016606"
---
# <a name="filestream-and-filetable-catalog-views-transact-sql"></a>Представления каталога Filestream и FileTable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются представления каталога, связанные с таблицами FileTable.  
  
## <a name="filestream-and-filetable-catalog-views-transact-sql"></a>FileStream и filetable представления каталога (Transact-SQL)
 [sys.database_filestream_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)  
 Отображает сведения об уровне нетранзакционного доступа к данным FILESTREAM в каждой из включенных таблиц FileTable. Содержит по одной строке для каждой базы данных в экземпляре SQL Server.  
  
 [sys.filetable_system_defined_objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md)  
 Отображает список системных объектов, связанных с таблицами FileTable. Содержит по одной строке для каждого системного объекта.  
  
 [sys.filetables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)  
 Возвращает по одной строке для каждой таблицы FileTable. Наследует от **sys.tables**.  

## <a name="see-also"></a>См. также
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Таблицы Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Динамические административные представления Filestream и FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Системные хранимые процедуры Filestream и FileTable (Transact-SQL)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)
  
  
