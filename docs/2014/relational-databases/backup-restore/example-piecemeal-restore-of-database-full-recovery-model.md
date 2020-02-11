---
title: Пример. Поэтапное восстановление базы данных (модель полного восстановления) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- piecemeal restores [SQL Server], full recovery model
- restore sequences [SQL Server], piecemeal
ms.assetid: 0a84892d-2f7a-4e77-b2d0-d68b95595210
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 157541fe3792ba082d9b1ec84c3ab45ca0617060
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62875826"
---
# <a name="example-piecemeal-restore-of-database-full-recovery-model"></a>Пример. Поэтапное восстановление базы данных (модель полного восстановления)
  При поэтапной последовательности восстановления база данных восстанавливается в течение нескольких этапов на уровне файловой группы, начиная с первичной и всех вторичных файловых групп, доступных для чтения и записи.  
  
 В данном примере база данных `adb` восстанавливается после сбоя на новом компьютере. Используется полная модель восстановления базы данных, поэтому перед началом восстановления необходимо сделать резервную копию заключительного фрагмента журнала базы данных. До сбоя все файловые группы работали в режиме «в сети». Файловая группа `B` доступна только для чтения. Необходимо восстановить все вторичные файловые группы, но они восстанавливаются в порядке важности: `A` (наивысшая), `C`и `B`. В этом примере существует четыре резервные копии журнала, включая резервную копию заключительного фрагмента журнала.  
  
## <a name="tail-log-backup"></a>Резервная копия заключительного фрагмента журнала  
 Перед тем как восстановить базу данных из копии, администратор этой базы данных должен создать резервную копию заключительного фрагмента журнала. Поскольку база данных повреждена, для создания резервной копии заключительного фрагмента журнала требуется применение параметра NO_TRUNCATE:  
  
```  
BACKUP LOG adb TO tailLogBackup WITH NORECOVERY, NO_TRUNCATE  
```  
  
 Резервная копия заключительного фрагмента журнала — это последняя резервная копия, используемая в следующих последовательностях восстановления.  
  
## <a name="restore-sequences"></a>Последовательности восстановления  
  
> [!NOTE]  
>  Синтаксис последовательности восстановления в сети тот же самый, что и в случае последовательности восстановления вне сети.  
  
1.  Частичное восстановление первичной и вторичной файловой группы `A`:  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
       WITH PARTIAL, NORECOVERY  
    RESTORE DATABASE adb FILEGROUP='A' FROM backup2   
       WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
2.  Восстановление файловой группы `C`«в сети».  
  
     На этом этапе первичная файловая группа и вторичная файловая группа `A` находятся в режиме «в сети». Все файлы в файловых группах `B` и `C` ожидают восстановления, а сами файловые группы находятся в режиме «вне сети».  
  
     Сообщения от последней инструкции `RESTORE LOG` в шаге 1 указывают, что откат транзакций, задействовавших файловую группу `C` , был отложен из-за недоступности этой файловой группы. Нормальная работа может продолжаться, но этими транзакциями удерживаются блокировки, поэтому до завершения отката усечение журнала выполнено не будет.  
  
     Во второй последовательности восстановления администратор базы данных восстанавливает файловую группу `C`:  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' FROM backup2a WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     На этом этапе первичная файловая группа и файловые группы `A` и `C` находятся в режиме в сети. Файлы в файловой группе `B` ожидают восстановления, при этом она находится в режиме «вне сети». Отложенные транзакции разрешены, и выполняется усечение журнала.  
  
3.  Восстановление файловой группы `B`«в сети».  
  
     В третьей последовательности восстановления администратор базы данных восстанавливает файловую группу `B`. После того как файловая группа `B` стала доступна только для чтения, используется ее резервная копия, чтобы не нужно было осуществлять накат во время восстановления.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup2b WITH RECOVERY  
    ```  
  
     Теперь все файловые группы находятся в режиме «в сети».  
  
## <a name="additional-examples"></a>Дополнительные примеры  
  
-   [Пример. Поэтапное восстановление базы данных (простая модель восстановления)](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление отдельных файловых групп (простая модель восстановления)](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Пример. Оперативное восстановление доступного только для чтения файла (простая модель восстановления)](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление только некоторых файловых групп (модель полного восстановления)](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного для чтения и записи (модель полного восстановления)](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного только для чтения (модель полного восстановления)](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [Восстановление в сети (SQL Server)](online-restore-sql-server.md)   
 [Применение резервных копий журналов транзакций (SQL Server)](transaction-log-backups-sql-server.md)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Поэтапное восстановление (SQL Server)](piecemeal-restores-sql-server.md)  
  
  
