---
title: Восстановление базы данных без восстановления данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], recovery-only
- recovery-only scenario [SQL Server]
- restoring databases [SQL Server], recovery-only
- recovery [SQL Server], recovery-only
- database recovery [SQL Server]
- database restores [SQL Server], recovery-only
- recovery [SQL Server], without restoring data
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2109346c60ca807dcc818941f9baff862a211247
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62921819"
---
# <a name="recover-a-database-without-restoring-data-transact-sql"></a>Восстановление базы данных без восстановления данных (Transact-SQL)
  Обычно все данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] восстанавливаются перед восстановлением базы данных. Однако операция восстановления может восстановить базу данных без использования резервной копии, например, при восстановлении согласованных с базой данных файлов, доступных только для чтения. Это называется *восстановлением только по журналу транзакций*. Восстановление только по журналу транзакций выполняется в тех случаях, когда данные уже согласованы с базой данных и остается только сделать их доступными.  
  
 Восстановление только по журналу транзакций может выполняться для одного или нескольких файлов или файловых групп базы данных.  
  
## <a name="recovery-only-database-restore"></a>Восстановление базы данных только по журналу транзакций  
 Восстановление базы данных только по журналу транзакций может применяться в следующей ситуации.  
  
-   При восстановлении из последней резервной копии в последовательности восстановления база данных, которую в настоящее время нужно перевести в оперативный режим, не была восстановлена по журналу.  
  
-   База данных находится в режиме ожидания, поэтому необходимо сделать ее доступной для обновлений без применения еще одной резервной копии журналов.  
  
 Синтаксис инструкции [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) для восстановления базы данных только по журналу транзакций:  
  
 RESTORE DATABASE *имя_базы_данных* WITH RECOVERY  
  
> [!NOTE]  
>  Предложение FROM **=** \<*устройство_резервного_копирования>* не используется для восстановления базы данных только по журналу транзакций, так как резервная копия не требуется.  
  
 **Пример**  
  
 В следующем примере выполняется восстановление базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] в ходе операции восстановления без восстановления данных.  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## <a name="recovery-only-file-restore"></a>Восстановление файлов только по журналу транзакций  
 Восстановление файлов только по журналу транзакций может применяться в следующей ситуации.  
  
 База данных поэтапно восстановлена из резервной копии. После восстановления первичной файловой группы один или несколько еще не восстановленных файлов согласованы с новым состоянием базы данных, потому что, например, в течение некоторого времени они были доступны только для чтения. Эти файлы достаточно восстановить по журналу транзакций. Копировать данные не нужно.  
  
 Операция восстановления только по журналу транзакций переводит файловую группу «вне сети» в режим «в сети», при этом не выполняется ни копирование, ни повтор, ни стадия отката. Сведения об этапах восстановления см. в статье [Обзор процессов восстановления (SQL Server)](restore-and-recovery-overview-sql-server.md).  
  
 Синтаксис инструкции [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) для восстановления файлов только по журналу транзакций:  
  
 RESTORE DATABASE *database_name* { FILE **=** _логическое_имя_файла_ | FILEGROUP **=** _логическое_имя_файловой_группы_ }[ **,** ...*n* ] WITH RECOVERY  
  
 **Пример**  
  
 В следующем примере показано восстановление по журналу транзакций для файлов вторичной файловой группы `SalesGroup2`в базе данных `Sales` . Первичная файловая группа уже восстановлена в качестве первого шага поэтапного восстановления, поэтому группа `SalesGroup2` согласована с первичной файловой группой. Восстановление файловой группы и ее перевод в режим «в сети» требует только одной инструкции.  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## <a name="examples-of-completing-a-piecemeal-restore-scenario-with-a-recovery-only-restore"></a>Примеры завершения сценария поэтапного восстановления восстановлением только по журналу транзакций  
 **Простая модель восстановления**  
  
-   [Пример. Поэтапное восстановление базы данных &#40;простая модель восстановления&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление отдельных файловых групп &#40;простая модель восстановления&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 **Модель полного восстановления**  
  
-   [Пример. Поэтапное восстановление базы данных &#40;модель полного восстановления&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление только некоторых файловых групп &#40;модель полного восстановления&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## <a name="see-also"></a>См. также  
 [Восстановление в сети (SQL Server)](online-restore-sql-server.md)   
 [Поэтапное восстановление (SQL Server)](piecemeal-restores-sql-server.md)   
 [Восстановление файлов (простая модель восстановления)](file-restores-simple-recovery-model.md)   
 [Восстановления файлов (модель полного восстановления)](file-restores-full-recovery-model.md)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
