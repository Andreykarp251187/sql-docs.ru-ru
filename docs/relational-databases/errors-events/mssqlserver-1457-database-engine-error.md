---
title: MSSQLSERVER_1457 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1aed6c7df5a09d98d7fc5de90c5e3bf2add05fb1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62859778"
---
# <a name="mssqlserver1457"></a>MSSQLSERVER_1457
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1457|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_PAGE_UNDO_PENDING|  
|Текст сообщения|Синхронизация зеркальной базы данных «%.*ls» прервана, база данных осталась в несогласованном состоянии. Ошибка при выполнении команды ALTER DATABASE. Убедитесь, что создана резервная копия зеркальной базы данных и она находится в режиме «в сети», а затем подключите заново экземпляр зеркального сервера и дайте возможность зеркальной базе данных завершить синхронизацию.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение указывает на неуспешное завершение инструкции ALTER DATABASE *имя_базы_данных* SET PARTNER OFF. Неуспешная попытка удалить зеркальное отображение базы данных прервала синхронизацию зеркальной базы данных. База данных в несогласованном состоянии.  
  
## <a name="user-action"></a>Действие пользователя  
Для устранения этой ошибки можно предпринять одно из следующих действий.  
  
-   Восстановите связь между зеркальным и основным сервером, чтобы обеспечить синхронизацию зеркальной базы данных.  
  
-   Удалите зеркальную базу данных.  
  
    После удаления зеркальной базы данных можно создать новую базу данных из резервных копий.  
  
    > [!NOTE]  
    > Удалить зеркальную базу данных при включенном зеркальном отображении можно только после того, как инструкция SET PARTNER OFF завершается ошибкой.  
  
## <a name="see-also"></a>См. также:  
[Зеркальное отображение базы данных (SQL Server)](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[ALTER DATABASE (Transact-SQL)](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
[Настройка зеркального отображения базы данных (SQL Server)](~/database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)  
[Удаление зеркального отображения базы данных (SQL Server)](~/database-engine/database-mirroring/removing-database-mirroring-sql-server.md)  
[Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)](~/database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
