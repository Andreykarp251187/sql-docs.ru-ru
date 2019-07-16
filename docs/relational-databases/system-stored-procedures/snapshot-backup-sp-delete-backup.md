---
title: sp_delete_backup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 808e50ae-ff6e-4520-9ce2-530591d3d59b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49eb0906a9a5af1fec2abfeec3ef58845b605e69
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941824"
---
# <a name="spdeletebackup-transact-sql"></a>sp_delete_backup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Удаление всех моментальных снимков и файл резервной копии, составляющие моментальный снимок резервного набора данных из указанной базы данных. Этой системной хранимой процедуры рекомендуется только для управления наборами данных резервного копирования моментальных снимков. Дополнительные сведения см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_delete_backup   
    [ @backup_url = ] backup_metadata_file_url  
    ,[ [ @db_name = ] database_name | NULL ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *[ @backup_url = ] backup_meta_file_url*  
 URL-адрес резервного копирования для удаления, который удаляет все моментальные снимки, составляющие указанный резервный набор, включая файл резервной копии.  
  
 *[ @db_name =] имя_базы_данных*  
 Имя базы данных, содержащей ждет удаления снимка. Если имя базы данных предоставляется, система проверяет, что URL-адрес архива предоставленные резервного копирования URL-адрес для указанной базы данных и использует [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) для удаления каждого моментального снимка. Если имя базы данных не указано, эта проверка базы данных не выполняется.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY DATABASE или разрешение ALTER для указанной базы данных.  
  
## <a name="see-also"></a>См. также  
 [sys.fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup_file_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
