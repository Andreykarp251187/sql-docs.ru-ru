---
title: MSSQL_ENG014165 | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014165 error
ms.assetid: 7bb07672-310c-4f51-ae76-c55e7c8d51ea
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: c7c4dde3b5c82816932521b81d8ede0d7654d0f9
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68765812"
---
# <a name="mssqleng014165"></a>MSSQL_ENG014165
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14165|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Задан порог [%s:%s] для публикации [%s]. Убедитесь в том, что агент слияния запущен и соответствует предъявляемому требованию.|  
  
## <a name="explanation"></a>Объяснение  
 При репликации можно включить предупреждения для ряда условий. Сюда входит неуспешное завершение обработки большого числа строк при синхронизации изменений между издателем и подписчиком слияния. Для соединений по локальной сети и коммутируемых соединений можно указать разные значения времени.  
  
 Когда предупреждение включается при помощи монитора репликации или процедуры [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), необходимо указать пороговое значение, определяющее, в какой момент выдается предупреждение. При достижении или превышении порогового значения предупреждение отображается в мониторе репликации, а в журнал событий Windows записывается событие. Достижение порогового значения также может приводить к выдаче предупреждения агента SQL Server. Дополнительные сведения см. в статьях [Настройка пороговых значений и предупреждений в мониторе репликации](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md). и [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Если подписка не отвечает пороговому значению для обработки строк, необходимо определить, является это проблемой производительности системы или свидетельствует о необходимости скорректировать пороговое значение. После настройки репликации разработайте базовый уровень производительности, позволяющий определить работу репликации при рабочей нагрузке, типичной для ваших приложений и топологии. Включите в базовый уровень количество строк, чтобы правильно выбрать подходящее пороговое значение.  
  
 Если пороговое значение выбрано верно, но превышение порогового значения все же наблюдается, то нужно определить, где в системе находится узкое место по производительности. Дополнительные сведения о мониторинге и устранении неполадок, влияющих на производительность репликации, см. в следующих разделах:  
  
-   [Наблюдение за производительностью с помощью монитора репликации](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) (в частности, раздел "Просмотр подробных сведений о производительности синхронизации для репликации слиянием").  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
