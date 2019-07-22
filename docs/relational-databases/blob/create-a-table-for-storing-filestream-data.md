---
title: Создание таблицы для хранения данных FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], table storage
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54c3acef29036c8178b9103e31c7e01e7a02595b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085407"
---
# <a name="create-a-table-for-storing-filestream-data"></a>Создание таблицы для хранения данных FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе приводятся сведения о создании таблицы для хранения данных FILESTREAM.  
  
 Если в базе данных имеется файловая группа FILESTREAM, можно создавать или изменять таблицы для хранения данных FILESTREAM. Чтобы указать, что в столбце будут содержаться данные типа FILESTREAM, необходимо создать столбец с типом данных **varbinary(max)** и добавить атрибут FILESTREAM.  
  
### <a name="to-create-a-table-to-store-filestream-data"></a>Создание таблицы для хранения данных FILESTREAM  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]нажмите кнопку **Создать запрос** , чтобы открыть редактор запросов.  
  
2.  Скопируйте следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] и вставьте его в редактор запросов. Этот код [!INCLUDE[tsql](../../includes/tsql-md.md)] создает таблицу с поддержкой FILESTREAM, именуемую Records.  
  
3.  Чтобы создать таблицу, нажмите кнопку **Выполнить**.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как создать таблицу с именем `Records`. Столбец `Id` является столбцом типа `ROWGUIDCOL` и необходим для использования данных FILESTREAM с API Win32. Столбец `SerialNumber` имеет тип `UNIQUE INTEGER`. Столбец `Chart` является столбцом типа `FILESTREAM` и используется для хранения данных `Chart` в файловой системе.  
  
> [!NOTE]  
>  Этот пример ссылается на базу данных Archive, созданную в разделе [Создание базы данных с поддержкой FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
 [!code-sql[FILESTREAM#FS_CreateTable](../../relational-databases/blob/codesnippet/tsql/create-a-table-for-stori_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
