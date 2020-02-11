---
title: Просмотр событий для зарегистрированных пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing events
- extended events [SQL Server], viewing events
ms.assetid: 9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1156a7272edc8ad1ecfb8e173f81bc678800c855
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089633"
---
# <a name="view-the-events-for-registered-packages"></a>просмотреть события для зарегистрированных пакетов
  Перед созданием сеанса расширенных событий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] рекомендуется выявить события, доступные в зарегистрированных пакетах. Дополнительные сведения см. в разделе [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).  
  
 Эта задача решается с помощью редактора запросов в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] для выполнения следующей процедуры.  
  
 После выполнения инструкций данной процедуры на вкладке **Результаты** редактора запросов будут отображены следующие столбцы.  
  
-   имя. Имя пакета.  
  
-   событие. Имя события.  
  
-   ключевое слово. Ключевое слово, полученное из внутренней числовой таблицы сопоставлений.  
  
-   канал. Аудитория события.  
  
-   описание. Описание события.  
  
## <a name="to-view-the-events-for-registered-packages-using-query-editor"></a>Просмотр событий для зарегистрированных пакетов с помощью редактора запросов  
  
-   В редакторе запросов выполните следующие инструкции.  
  
    ```  
    USE msdb  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
    (  
    SELECT event_package=o.package_guid, o.description,   
    event=c.object_name, channel=v.map_value  
    FROM sys.dm_xe_objects o  
    LEFT JOIN sys.dm_xe_object_columns c ON o.name=c.object_name  
    INNER JOIN sys.dm_xe_map_values v ON c.type_name=v.name   
    AND c.column_value=cast(v.map_key AS nvarchar)  
    WHERE object_type='event' AND (c.name='CHANNEL' or c.name IS NULL)  
  
    ) c LEFT JOIN   
    (  
    SELECT event_package=c.object_package_guid, event=c.object_name,   
    keyword=v.map_value  
    FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
    ON c.type_name=v.name AND c.column_value=v.map_key   
    AND c.type_package_guid=v.object_package_guid  
    INNER JOIN sys.dm_xe_objects o ON o.name=c.object_name   
    AND o.package_guid=c.object_package_guid  
    WHERE object_type='event' AND c.name='KEYWORD'   
    ) k  
    ON  
    k.event_package=c.event_package AND (k.event=c.event or k.event IS NULL)  
    INNER JOIN sys.dm_xe_packages p ON p.guid=c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server пакетов расширенных событий](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [sys. dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
