---
title: Воспроизведение одного события за раз (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 91db80cd80b5e69bd9dee2c72c99eae6c76f166b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67732951"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a>воспроизвести одиночное событие за раз (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается, как с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]воспроизвести одно событие за раз в файл трассировки воспроизведения или таблицу.  
  
### <a name="to-replay-a-single-event-at-a-time"></a>Вспроизведение одиночное события за раз  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в разделе [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  В меню **Воспроизведение** выберите **Шаг**и подключитесь к экземпляру сервера, на котором предстоит воспроизвести трассировку.  
  
3.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**. Дополнительные сведения о задании параметров в диалоговом окне **Конфигурация воспроизведения** см. в разделе [Воспроизведение файла трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) или [Воспроизведение таблицы трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md).  
  
4.  Чтобы воспроизвести первое событие, нажмите кнопку **OK** в диалоговом окне **Конфигурация воспроизведения** .  
  
5.  Чтобы воспроизвести следующие события, в меню **Воспроизведение** выберите **Шаг**или нажмите клавишу F10. Повторно нажимайте **Шаг** или клавишу F10 для каждого события.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
