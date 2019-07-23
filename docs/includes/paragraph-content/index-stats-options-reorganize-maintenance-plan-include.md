---
ms.openlocfilehash: 78b372942de6ec62823dddecd08fdb7221cbe7a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68219679"
---


### <a name="index-stats-options"></a>Параметры статистики индексов

<!--
This includes/paragraph-content/ file was created when processing vsts sqlbuvsts01 2999014 (5589131).  genemi  2017-07-21

Initially used in:
- relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md
- relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md
-->


В более ранних версиях Microsoft SQL Server операции реорганизации или повторного создания больших индексов могли снижать производительность системы. В SQL Server 2016 реализован ряд улучшений для существенного повышения производительности таких операций.

Кроме того, в более ранних версиях было доступно меньше возможностей управления. Из-за этого операции реорганизации или повторного создания выполнялись даже для индексов с низкой фрагментацией, что было слишком затратно. Новые элементы управления в пользовательском интерфейсе для плана обслуживания позволяют исключать индексы, которые не нужно обновлять, руководствуясь критериями статистики индексов. При этом для внутренних целей используются следующие динамические административные представления (DMV) Transact-SQL:


- [sys.dm_db_index_usage_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md);
- [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).


 **Тип просмотра**  
 Система должна использовать ресурсы для сбора статистики индексов. Вы можете выбрать объем используемых ресурсов, исходя из того, какой уровень точности, по вашему мнению, требуется для статистики индексов. В пользовательском интерфейсе доступны следующие уровни точности:


- быстрый;
- с выборкой;
- подробный.


 **Оптимизация индекса только в определенных случаях**  
 В пользовательском интерфейсе доступны следующие настраиваемые фильтры, благодаря которым можно избежать обновления индексов, для которых это не требуется:


- фрагментация &gt; *(%)* ;
- число страниц &gt;;
- использовано за последние *(дни)* .

