---
title: Категория событий Database | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cf3fd2a6cd222320e55b7336272bf9f662b81694
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68009571"
---
# <a name="database-event-category"></a>Категория событий Database
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В категории событий **База данных** содержатся классы событий для контроля компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Класс событий Data File Auto Grow](../../relational-databases/event-classes/data-file-auto-grow-event-class.md)|Указывает на то, что размер файла данных увеличивается автоматически. Это событие не происходит при явном увеличении файла данных с помощью инструкции ALTER DATABASE.|  
|[Класс событий Data File Auto Shrink](../../relational-databases/event-classes/data-file-auto-shrink-event-class.md)|Указывает на то, что файл данных был сжат.|  
|[Класс событий Database Mirroring Connection](../../relational-databases/event-classes/database-mirroring-connection-event-class.md)|Событие, формируемое для уведомления о состоянии транспортного соединения для зеркального отображения базы данных.|  
|[Класс событий Database Mirroring State Change](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md)|Указывает, когда изменяется состояние зеркальной базы данных.|  
|[Класс событий Database Suspect Data Page](../../relational-databases/event-classes/database-suspect-data-page-event-class.md)|Указывает, что страница добавлена в таблицу **suspect_pages** базы данных **msdb** .|  
|[Класс событий Log File Auto Grow](../../relational-databases/event-classes/log-file-auto-grow-event-class.md)|Указывает на то, что размер файла журнала был сжат автоматически. Это событие не происходит при явном увеличении файла журнала с помощью инструкции ALTER DATABASE.|  
|[Класс событий Log File Auto Shrink](../../relational-databases/event-classes/log-file-auto-shrink-event-class.md)|Указывает на то, что размер файла журнала был сжат автоматически. Это событие не происходит при явном сжатии файла журнала с помощью инструкции ALTER DATABASE.|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
