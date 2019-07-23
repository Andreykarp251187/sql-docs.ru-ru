---
title: Фильтрация идентификаторов процессов сервера (SPID) в трассировке (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 172ba4b6cb2ed5bee84d920f8b7e0c73de3b8e90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075016"
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a>отфильтровать идентификаторы процессов сервера (SPID) в трассировке (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Данный подраздел описывает, как отфильтровать идентификаторы процессов сервера (SPID) в трассировке при использовании приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-system-ids-in-a-trace"></a>Фильтрация системных идентификаторов в трассировке  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру SQL Server.  
  
     отображается диалоговое окно **Свойства трассировки** .  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки** не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис** выберите пункт **Параметры** и снимите флажок **Начать трассировку немедленно после установления соединения**.  
  
2.  В поле **Имя трассировки** введите имя трассировки.  
  
3.  В списке имен **Использовать шаблон** выберите шаблон трассировки.  
  
4.  Можно также задать целевой файл или таблицу, в которых будут сохраняться результаты трассировки.  
  
5.  На вкладке **Выбор событий** щелкните заголовок столбца **SPID**, чтобы открыть диалоговое окно **Изменение фильтра**. Можно также правой кнопкой мыши щелкнуть заголовок столбца и выбрать пункт **Изменить фильтр столбца**. Если столбец **SPID** не отображается, установите флажок **Показать все столбцы** .  
  
6.  В диалоговом окне **Изменение фильтра** раскройте соответствующий оператор сравнения и введите SPID как значение для сравнения.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
