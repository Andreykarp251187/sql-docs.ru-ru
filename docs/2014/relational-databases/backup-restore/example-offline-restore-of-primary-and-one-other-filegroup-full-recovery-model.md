---
title: Пример Автономное восстановление основной и еще одной файловой группы (модель полного восстановления) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- offline restores [SQL Server]
- restore sequences [SQL Server], offline
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fec409bf6f391e14dd5e1a2b8b102df2fd00cfd4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62921759"
---
# <a name="example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model"></a>Пример Автономное восстановление основной и еще одной файловой группы (модель полного восстановления)
  Данный раздел относится только к базам данных с моделью полного восстановления, содержащим несколько файловых групп.  
  
 В данном примере база данных `adb` содержит три файловые группы. Файловые группы `A` и `C` предназначены для считывания и записи, а файловые группы `B` предназначены только для чтения. Первичная файловая группа и файловая группа `B` повреждены, но файловые группы `A` и `C` не затронуты. До аварии все файловые группы находились в режиме «в сети».  
  
 Администратор базы данных принял решение восстановить первичную файловую группу и файловую группу `B`. Используется полная модель восстановления базы данных, поэтому перед началом восстановления необходимо сделать резервную копию заключительного фрагмента журнала базы данных. Когда база данных переходит в режим «в сети», файловые группы `A` и `C` автоматически переходят в режим «в сети».  
  
> [!NOTE]  
>  В последовательности восстановления вне сети предусмотрено меньше шагов, чем для восстановления файлов в сети только для чтения. Например, см. в разделе [пример: Оперативное восстановление файла только для чтения &#40;модель полного восстановления&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md). Однако в процессе выполнения последовательности в режиме «вне сети» находится вся база данных.  
  
## <a name="tail-log-backup"></a>Резервная копия заключительного фрагмента журнала  
 Перед тем как восстановить базу данных из копии, администратор этой базы данных должен создать резервную копию заключительного фрагмента журнала. Поскольку база данных повреждена, для создания резервной копии заключительного фрагмента журнала требуется применение параметра NO_TRUNCATE:  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 Резервная копия заключительного фрагмента журнала — это последняя резервная копия, используемая в следующих последовательностях восстановления.  
  
## <a name="restore-sequence"></a>Последовательность восстановления  
 Чтобы восстановить первичную файловую группу и файловую группу `B`, администратор базы данных использует последовательность восстановления без параметра PARTIAL, как указано ниже:  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 Файлы, которые не затрагивает процесс восстановления, автоматически переводятся в режим «в сети». Сейчас все файловые группы переведены в режим «в сети».  
  
## <a name="see-also"></a>См. также  
 [Восстановление в сети (SQL Server)](online-restore-sql-server.md)   
 [Поэтапное восстановление (SQL Server)](piecemeal-restores-sql-server.md)   
 [Восстановление файлов (модель полного восстановления)](file-restores-full-recovery-model.md)   
 [Применение резервных копий журналов транзакций (SQL Server)](transaction-log-backups-sql-server.md)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
