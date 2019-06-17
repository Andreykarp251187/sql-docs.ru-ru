---
title: Доступ к таблицам FileTable с помощью Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with T-SQL
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9a01f23b598e6a8a81122c8a670fadc9f00b6009
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089010"
---
# <a name="access-filetables-with-transact-sql"></a>Доступ к таблицам FileTable с помощью Transact-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Описывает, как команды языка обработки данных DML [!INCLUDE[tsql](../../includes/tsql-md.md)] работают c таблицами FileTable.  
  
##  <a name="BasicsInsert"></a> Операции INSERT в таблицах FileTable  
 С операциями **INSERT** в таблицах FileTable связаны следующие моменты:  
  
-   Все столбцы атрибутов файла имеют ограничения NO NULL. Если значения не заданы явным образом, предоставляются соответствующие значения по умолчанию.  
  
-   Если инструкция INSERT задает значения для параметров **name**, **path_locator**, **parent_path_locator** или атрибуты файлов, то применяются системные ограничения.  
  
-   Приложение может получить **path_locator** для файла или каталога, указав путь файловой системы для функции [GetPathLocator (Transact-SQL)](../../relational-databases/system-functions/getpathlocator-transact-sql.md).  
  
##  <a name="BasicsUpdate"></a> Операции UPDATE в таблицах FileTable  
 С операциями UPDATE в таблицах **FileTable** связаны следующие моменты:  
  
-   Разрешается обновлять любые данные, определяемые пользователем.  
  
-   Если инструкция INSERT задает значения для параметров **name**, **path_locator**, **parent_path_locator**или атрибуты файлов, то применяются системные ограничения.  
  
-   Обновления данных FILESTREAM в столбце **file_stream** не влияют ни на какие другие столбцы, включая отметки времени.  
  
##  <a name="BasicsDelete"></a> Операции DELETE в таблицах FileTable  
 С операциями **DELETE** в таблицах FileTable связаны следующие моменты.  
  
-   При удалении строки удаляется соответствующий файл или каталог из файловой системы.  
  
-   Невозможно удалить строку, если она относится к каталогу, который содержит другие файлы или каталоги.  
  
##  <a name="BasicsConstraints"></a> Ограничения, необходимые для операций DML в таблицах FileTable  
 Определяемые системой ограничения обеспечивают сохранение целостности иерархии пространства имен файлов во время операций DML. Принудительно применяются следующие ограничения.  
  
-   При установке или изменении **name** файла или каталога:  
  
    -   Поддерживаются обозначения имен файлов и каталогов Windows.  
  
    -   Обеспечивается уникальность имени в родительском каталоге.  
  
-   При установке или изменении расположения файла или каталога путем назначения или редактирования **path_locator** или **parent_path_locator**:  
  
    -   Обеспечивается уникальность.  
  
    -   Обеспечивается согласованность иерархического дерева каталогов и файлов, включая согласованность значений **path_locator** и **parent_path_locator** .  
  
-   Значение **is_directory** не может быть задано как true для ненулевого столбца **file_stream** . Данные в столбце **file_stream** показывают, что строка соответствует файлу, а не каталогу.  
  
-   Столбцы атрибутов файлов не могут иметь значение NULL. Ограничения NOT NULL применяются со значениями по умолчанию.  
  
-   Значение **last_access_time** не может быть меньше (раньше), чем **last_write_time** и **creation_time**.  
  
## <a name="see-also"></a>См. также:  
 [выполнить загрузку файлов в таблицу FileTables](../../relational-databases/blob/load-files-into-filetables.md)   
 [Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)   
 [Доступ к таблицам FileTable с помощью API-интерфейсов ввода-вывода файлов](../../relational-databases/blob/access-filetables-with-file-input-output-apis.md)   
 [Инструкции FileTable языка DDL, функции, хранимые процедуры и представления](../../relational-databases/blob/filetable-ddl-functions-stored-procedures-and-views.md)  
  
  
