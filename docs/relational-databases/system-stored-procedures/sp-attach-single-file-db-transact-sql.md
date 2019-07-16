---
title: sp_attach_single_file_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_attach_single_file_db
- sp_attach_single_file_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_single_file_db
ms.assetid: 13bd1044-9497-4293-8390-1f12e6b8e952
author: stevestein
ms.author: sstein
ms.openlocfilehash: b285b5032c1ccde03ef8bd3f287d6b7f60eb0ffc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046168"
---
# <a name="spattachsinglefiledb-transact-sql"></a>sp_attach_single_file_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Присоединяет базу данных, которая имеет только один файл данных, к текущему серверу. **sp_attach_single_file_db** не может использоваться с несколькими файлами данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Мы рекомендуем использовать инструкцию CREATE DATABASE *имя_базы_данных* FOR ATTACH вместо этого. Дополнительные сведения см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md). Не используйте эту процедуру на реплицированной базе данных.  
  
> [!IMPORTANT]  
>  Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_attach_single_file_db [ @dbname= ] 'dbname'  
    , [ @physname= ] 'physical_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbname'` — Имя базы данных, подключенные к серверу. Имя должно быть уникальным. *DBName* — **sysname**, значение по умолчанию NULL.  
  
`[ @physname = ] 'physical_name'` Это физическое имя, включая путь файла базы данных. *physical_name* — **nvarchar(260)** , значение по умолчанию NULL.  
  
> [!NOTE]  
>  Этот аргумент сопоставляется с параметром FILENAME инструкции CREATE DATABASE. Дополнительные сведения см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
 Когда базу данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с файлами полнотекстовых каталогов присоединяют к экземпляру сервера [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , то присоединение файлов каталогов выполняется из их предыдущего расположения вместе с другими файлами баз данных, как и в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения см. в разделе [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Используйте **sp_attach_single_file_db** только на базах данных, которые были предварительно отсоединены от сервера с помощью явной **sp_detach_db** операции или на скопированных базах данных.  
  
 **sp_attach_single_file_db** применим только к базам данных, содержащим один файл журнала. Когда **sp_attach_single_file_db** присоединяет базу данных на сервере, он создает новый файл журнала. Если база данных находится в режиме «только для чтения», файл журнала будет создан в ее предыдущем местоположении.  
  
> [!NOTE]  
>  Невозможно отсоединить или присоединить моментальный снимок базы данных.  
  
 Не используйте эту процедуру на реплицированной базе данных.  
  
## <a name="permissions"></a>Разрешения  
 Сведения об управлении разрешениями при присоединении базы данных, см. в разделе [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 Следующий пример отсоединяет [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и затем присоединяет один файл из [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] к текущему серверу.  
  
```  
USE master;  
GO  
EXEC sp_detach_db @dbname = 'AdventureWorks2012';  
EXEC sp_attach_single_file_db @dbname = 'AdventureWorks2012',   
    @physname =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_Data.mdf';  
```  
  
## <a name="see-also"></a>См. также  
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
