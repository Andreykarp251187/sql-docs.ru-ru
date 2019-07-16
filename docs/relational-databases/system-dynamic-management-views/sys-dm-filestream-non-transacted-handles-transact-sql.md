---
title: sys.dm_filestream_non_transacted_handles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_filestream_non_transacted_handles_TSQL
- dm_filestream_non_transacted_handles
- dm_filestream_non_transacted_handles_TSQL
- sys.dm_filestream_non_transacted_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_non_transacted_handles dynamic management view
ms.assetid: 507ec125-67dc-450a-9081-94cde5444a92
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dda607ace977be539dbed096a3d83ac5f220ea0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950981"
---
# <a name="sysdmfilestreamnontransactedhandles-transact-sql"></a>sys.dm_filestream_non_transacted_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Показывает открытые в настоящее время нетранзакционные дескрипторы файлов, связанные с данными FileTable.  
  
 Это представление содержит по одной строке на каждый открытый дескриптор файла. Поскольку данные этого представления соответствуют активному внутреннему состоянию сервера, они постоянно изменяются по мере открытия и закрытия дескрипторов. Это представление не содержит данных предыстории.  
  
 Дополнительные сведения см. в статье [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md).  
  
|**Столбец**|**Тип**|**Описание**|  
|----------------|--------------|---------------------|  
|database_id|ssNoversion|Идентификатор базы данных, связанной с дескриптором.|  
|object_id|ssNoversion|Идентификатор объекта таблицы FileTable, с которой связан дескриптор.|  
|handle_id|ssNoversion|Уникальный идентификатор контекста дескриптора. Используемые [sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md) хранимой процедуры для уничтожения определенного дескриптора.|  
|file_object_type|ssNoversion|Тип дескриптора. Он указывает уровень иерархии, для которого был открыт дескриптор, такой как база данных или элемент.|  
|file_object_type_desc|nvarchar(120)|«НЕ ОПРЕДЕЛЕНО»,<br />«SERVER_ROOT»,<br />«DATABASE_ROOT»,<br />«TABLE_ROOT»,<br />«TABLE_ITEM»|  
|correlation_process_id|varbinary(8)|Содержит уникальный идентификатор для процесса, отправившего запрос.|  
|correlation_thread_id|varbinary(8)|Содержит уникальный идентификатор для потока, отправившего запрос.|  
|file_context|varbinary(8)|Указатель на файловый объект, используемый данным дескриптором.|  
|state|ssNoversion|Текущее состояние дескриптора. Может быть активным, закрытым или уничтоженным.|  
|state_desc|nvarchar(120)|«АКТИВНО»,<br />«ЗАКРЫТО»<br />«ЗАВЕРШИТЬ»|  
|current_workitem_type|ssNoversion|Состояние, в котором этот дескриптор обрабатывается в данный момент.|  
|current_workitem_type_desc|nvarchar(120)|«NoSetWorkItemType»,<br />«FFtPreCreateWorkitem»,<br />«FFtGetPhysicalFileNameWorkitem»,<br />«FFtPostCreateWorkitem»,<br />«FFtPreCleanupWorkitem»,<br />«FFtPostCleanupWorkitem»,<br />«FFtPreCloseWorkitem»,<br />«FFtQueryDirectoryWorkItem»,<br />«FFtQueryInfoWorkItem»,<br />«FFtQueryVolumeInfoWorkItem»,<br />«FFtSetInfoWorkitem»,<br />«FFtWriteCompletionWorkitem»|  
|fcb_id|BIGINT|Идентификатор блока управления файлами FileTable.|  
|item_id|varbinary(892)|Идентификатор элемента для файла или каталога. Может быть NULL для корневых дескрипторов сервера.|  
|is_directory|bit|Представляет ли собой каталог.|  
|item_name|nvarchar(512)|Имя элемента.|  
|opened_file_name|nvarchar(512)|Первоначально запрошенный путь для открытия.|  
|database_directory_name|nvarchar(512)|Часть opened_file_name, которая представляет имя каталога базы данных.|  
|table_directory_name|nvarchar(512)|Часть opened_file_name, которая представляет имя каталога таблицы.|  
|remaining_file_name|nvarchar(512)|Часть opened_file_name, которая представляет остальную часть имени каталога.|  
|open_time|datetime|Время открытия дескриптора.|  
|flags|ssNoversion|ShareFlagsUpdatedToFcb = 0x1,<br />DeleteOnClose = 0x2,<br />NewFile = 0x4,<br />PostCreateDoneForNewFile = 0x8,<br />StreamFileOverwritten = 0x10,<br />RequestCancelled = 0x20,<br />NewFileCreationRolledBack = 0x40|  
|login_id|ssNoversion|Идентификатор участника, открывшего дескриптор.|  
|login_name|nvarchar(512)|Имя участника, открывшего дескриптор.|  
|login_sid|значение типа varbinary(85)|Идентификатор безопасности участника, открывшего дескриптор.|  
|read_access|bit|Открыто для чтения.|  
|write_access|bit|Открыто для записи.|  
|delete_access|bit|Открыто для удаления.|  
|share_read|bit|Открыто с разрешением share_read.|  
|share_write|bit|Открыто с разрешением share_write.|  
|share_delete|bit|Открыто с разрешением share_delete.|  
  
## <a name="see-also"></a>См. также  
 [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
