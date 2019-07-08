---
title: Сортировка столбцов | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.sortcolumns.f1
ms.assetid: 66b44b6c-10a5-4e3f-a97b-7568609c88ac
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a5fb78f4d7ab510f9b7dde3eb8f9d4d43ca157aa
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586438"
---
# <a name="sort-columns"></a>Сортировка столбцов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Сортировка столбцов** позволяет сортировать сетки в мониторе репликации по значению одного или нескольких столбцов. (Отсортировать по одному столбцу можно, щелкнув его заголовок в сетке монитора репликации). Например, чтобы отсортировать подписки на вкладке **Все подписки** по состоянию, а затем по типу соединения, выполните следующие действия.  
  
1.  В первой строке сетки выберите **Состояние** в столбце **Имя столбца** и значение в столбце **Порядок сортировки** .  
  
2.  Во второй строке сетки выберите **Тип соединения** в столбце **Имя столбца** и значение в столбце **Порядок сортировки** .  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="options"></a>Параметры  
 **Имя столбца**  
 Имя столбца, по которому нужно выполнить сортировку. Можно выполнить сортировку по одному или нескольким столбцам. Нельзя выполнить сортировку по столбцам **Текущая средняя производительность** и **Худшая производительность в данный момент** на вкладке **Публикации** из-за способа вычисления значений в этих столбцах.  
  
 **Порядок сортировки**  
 Укажите значение **По возрастанию** или **По убыванию**.  
  
 **Очистить все**  
 Удалите все строки из сетки сортировки. Для удаления одной строки выделите строку и нажмите клавишу «DELETE».  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
