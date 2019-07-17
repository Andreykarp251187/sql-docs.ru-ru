---
title: Изменение шаблонов трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 34d3b69a345a9d7575cc850d4416695206b11a5e
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733067"
---
# <a name="modify-trace-templates"></a>Изменение шаблонов трассировки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Можно изменить шаблоны, сохраняемые в файле на локальном компьютере, на котором выполняется [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Можно также изменить шаблоны, производные от этих файлов. При изменении существующих шаблонов выполняется редактирование таких свойств шаблонов, как классы событий и столбцы данных в том же порядке, в котором эти свойства были установлены первоначально, на вкладке **Выбор событий** диалогового окна **Свойства трассировки** . Классы событий и столбцы данных можно добавлять и удалять, а фильтры изменять. После изменения шаблона создается пользовательский шаблон и исходный системный шаблон остается без изменений. Дополнительные сведения см. в разделе [Сохранение трассировок и шаблонов трассировок](../../tools/sql-server-profiler/save-traces-and-trace-templates.md).  
  
 Может потребоваться производный шаблон от существующего файла трассировки, если пользователь не помнит (или не сохранил) исходный шаблон, использованный при создании трассировки, или если нужно выполнить ту же трассировку в последующий день. При работе с существующими трассировками можно просматривать свойства, но нельзя изменять их. Чтобы изменить свойства, необходимо остановить или приостановить трассировку. Дополнительные сведения см. в разделах [Создать шаблон на основе файла трассировки или таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) и [Создать шаблон на основе выполняемой трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
## <a name="to-modify-a-trace-template"></a>Изменение шаблона трассировки  
  
1.  В меню **Файл** выберите **Шаблоны**и затем выберите **Изменить шаблон**.  
  
2.  В диалоговом окне **Свойства шаблона трассировки** на вкладке **Общие** можно изменить тип сервера и имя шаблона или выбрать использование шаблона по умолчанию для типа сервера.  
  
3.  На вкладке **Выбор событий** используйте сетку для добавления или удаления событий и столбцов данных в файле трассировки следующим образом.  
  
    -   Чтобы добавить событие, разверните соответствующую категорию событий в столбце **События** и выберите имя события.  
  
    -   При добавлении события все относящиеся к нему столбцы данных включаются автоматически. Чтобы удалить столбец данных для события из трассировки, снимите флажок в столбце данных для этого события.  
  
    -   Чтобы добавить фильтры, щелкните имя столбца данных и определите критерии фильтра в диалоговом окне **Изменение фильтра** . Также можно щелкнуть имя столбца данных правой кнопкой мыши и выбрать пункт **Изменить фильтр столбца** , чтобы открыть диалоговое окно **Изменение фильтра** . Нажмите кнопку **ОК** , чтобы добавить фильтр.  
  
4.  Нажмите кнопку **Сохранить** или кнопку **Сохранить как** для сохранения шаблона трассировки под другим именем.  
  
## <a name="next-steps"></a>Следующие шаги  
[Запуск трассировки](../../tools/sql-server-profiler/start-a-trace.md)  
[Создание трассировки](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
[Изменение существующей трассировки с помощью Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
[Указание столбцов событий и данных для файла трассировки с помощью SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
[sp-trace-setevent-transact-sql](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
