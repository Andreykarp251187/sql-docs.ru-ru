---
title: Воспроизведение до точки останова (SQL Server Profiler) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4cb776b84c68c5903b5c7204109d2d56eb1cbed7
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67732128"
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a>воспроизвести нагрузку до точки останова (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом подразделе описывается, как создавать точки останова в файле или таблице трассировки, воспроизводимой в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Определение точек останова перед запуском воспроизведения трассировки позволяет останавливать ее по определенным событиям. Точки останова позволяют отлаживать воспроизведение трассировки, разбивая длинный скрипт трассировки на короткие сегменты, которые могут быть подвергнуты последовательному анализу.  
  
### <a name="to-replay-to-a-breakpoint"></a>Воспроизведение до точки останова  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в статье [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  В окне трассировки щелкните событие, по которому устанавливается точка останова. Точку останова можно назначить одним из следующих трех способов:  
  
    -   Нажмите клавишу F9.  
  
    -   В меню **Воспроизведение** выбрав пункт **Переключить точку останова**.  
  
    -   Щелкнув событие правой кнопкой мыши, а затем выбрав пункт **Переключить точку останова**.  
  
     Справа от выбранного события трассировки появляется красный маркер, указывающий на наличие точки останова.  
  
     Повторите этот шаг для установки нескольких точек останова.  
  
3.  В меню **Воспроизведение** выберите **Начать**и подключитесь к серверу, на котором будет воспроизводиться трассировка.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
     Воспроизведение начинается, приостанавливаясь при достижении точки останова.  
  
5.  Нажмите F5 для возобновления воспроизведения до следующей точки останова.  
  
6.  Повторяйте шаг 5 до завершения трассировки.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизвести нагрузку до курсора (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)   
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
