---
title: MSSQLSERVER_2527 | | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26dfce968215f01ea1e3451bf879f41ecc1b9962
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045383"
---
# <a name="mssqlserver2527"></a>MSSQLSERVER_2527
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2527|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_INDEX_FILEGROUP_IS_OFFLINE|  
|Текст сообщения|Невозможно обработать индекс I_NAME таблицы O_NAME, так как файловая группа F_NAME находится в режиме «вне сети».|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение указывает, что индекс невозможно проверить, поскольку одна из файловых групп, в которой хранятся данные индекса, находится в режиме «вне сети». Состояние файлов в файловой группе определяет доступность всей файловой группы. Чтобы файловая группа была доступна, необходимо, чтобы все файлы в файловой группе находились в режиме в сети. Если других проблем нет, будут проверяться все остальные индексы того же объекта.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы просмотреть текущее состояние файлов указанной файловой группы, выполните запрос к представлению каталога **sys.database_files** или**sys.master_files**.  
  
Восстановите автономный файл из резервной копии.  
  
## <a name="see-also"></a>См. также:  
[sys.database_files (Transact-SQL)](~/relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[sys.master_files &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
[RESTORE (Transact-SQL)](~/t-sql/statements/restore-statements-transact-sql.md)  
  
