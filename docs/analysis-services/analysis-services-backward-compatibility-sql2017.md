---
title: Обратная совместимость служб SQL Server 2017 Analysis Services | Документация Майкрософт
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 3ad5bed93bf69f004276fd751f7f2fdef1ea9997
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210277"
---
# <a name="analysis-services-backward-compatibility-sql-2017"></a>Обратная совместимость служб анализа (SQL 2017 г.)
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

В этой статье описаны изменения в доступности функций и поведении между текущим выпуском и предыдущего выпуска.

## <a name="deprecated-features"></a>Устаревшие функции
Объект *нерекомендуемая функция* будет прекращена из продукта в будущем выпуске, но по-прежнему поддерживается и включен в текущем выпуске для обеспечения обратной совместимости. Рекомендуется прекратить использование устаревшие функции в новых и существующих проектов для обеспечения совместимости в будущих выпусках. Документация не обновляется для устаревших компонентов.

В этом выпуске устарели следующие функции:
  
|||  
|-|-|  
|**Режим/категории**|**Возможность**|
|Multidimensional|Интеллектуальный анализ данных|
|Multidimensional|Удаленные связанные группы мер|
|Табличный|Модели с уровнем совместимости 1100 и 1103|
|Табличный|Свойства табличной объектной модели: Column.IsDefaultImage Column.TableDetailPosition Column.IsDefaultLabel,|
|Инструменты|Приложение SQL Server Profiler для перехвата трассировки<br /><br /> В качестве замены можно использовать профилировщик расширенных событий, встроенный в SQL Server Management Studio.  <br /> См. раздел [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Инструменты|Воспроизведение трассировки с помощью приложения SQL Server Profiler <br />Замена. Замена отсутствует.|  
|Объекты управления трассировкой и интерфейсы API трассировки|Объекты Microsoft.AnalysisServices.Trace (содержат интерфейсы API для объектов трассировки и воспроизведения Analysis Services). Замена состоит из нескольких частей:<br /><br /> — Настройка трассировки: Microsoft.SqlServer.Management.XEvent<br />-Чтение трассировки: Microsoft.SqlServer.XEvent.Linq<br />— Воспроизведение трассировки: None|  


## <a name="discontinued-features"></a>Неподдерживаемые функции
Объект *неподдерживаемой* был объявлен устаревшим в более раннем выпуске. Он может по-прежнему должны быть включены в текущем выпуске, но больше не поддерживается. Неподдерживаемые функции могут быть удалены полностью в будущем выпуске или обновить.

Следующие функции стали нерекомендуемыми в более раннем выпуске и больше не поддерживаются в этом выпуске.
  
|||  
|-|-|  
|**Режим/категории**|**Возможность**|  
|Табличный|Значение свойства VertipaqPagingPolicy памяти (2), разрешите разбиение на страницы на диск с использованием памяти сопоставлены файлы.|
|Multidimensional|Удаленные секции|  
|Multidimensional|Удаленные связанные группы мер|  
|Multidimensional|Многомерная обратная запись|  
|Multidimensional|Связанные измерения|


## <a name="breaking-changes"></a>Критические изменения
Объект *критическое изменение* вызывает функцию, модель данных, код приложения или сценария к прекращению работы после обновления до текущего выпуска.

Отсутствуют критические изменения в этом выпуске.

## <a name="behavior-changes"></a>Изменения в поведении
Объект *изменение поведения* влияет на том, как же работает в текущей версии по сравнению с предыдущим выпуском. Описываются только существенных изменений в поведении. Изменения в пользовательском интерфейсе, не включаются.

Изменения MDSCHEMA_MEASUREGROUP_DIMENSIONS и DISCOVER_CALC_DEPENDENCY, подробно описаны в [новые возможности в SQL Server 2017 CTP 2.1 для служб Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/05/18/whats-new-in-sql-server-2017-ctp-2-1-for-analysis-services/) объявления.


## <a name="see-also"></a>См. также
[Обратная совместимость служб анализа (SQL Server 2016)](analysis-services-backward-compatibility.md)
