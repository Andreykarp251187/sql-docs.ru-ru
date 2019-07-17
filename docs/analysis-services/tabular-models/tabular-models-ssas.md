---
title: Табличные модели в службах Analysis Services | Документация Майкрософт
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae7dfd78e71c41ab5b826a27742923445117417d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162435"
---
# <a name="tabular-models"></a>Табличные модели
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Табличные модели в службах Analysis Services являются баз данных, выполняющихся в памяти или в режиме DirectQuery, подключение к данным непосредственно из реляционных данных серверной части источников. С помощью алгоритмов состояние art сжатия и многопоточного обработчика запросов, также Vertipaq служб Analysis Services модуль аналитики предоставляет быстрый доступ к объектам табличной модели и данным через информативные клиентские приложения Power BI и Excel.  
  
 Хотя в моделях в памяти используются по умолчанию, DirectQuery — это альтернативный режим запроса для моделей, которые могут быть слишком велик для обработки в памяти или изменчивость данных исключает разумной стратегии обработки. DirectQuery достигает четности с помощью моделей в памяти, благодаря поддержке широкого спектра источников данных, возможность обрабатывать вычисляемые таблицы и столбцы в модели DirectQuery, защите уровня строк посредством выражений DAX, которые охватывают серверной базы данных и запрос оптимизации, которые обеспечивают большую пропускную способность.
  
 Табличные модели создаются в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] с помощью шаблона проекта табличной модели. Шаблон проекта предоставляет рабочую область конструирования для создания семантической модели объектов, таких как таблицы, секции, связей, иерархий, меры и ключевые показатели эффективности. 
  
 Табличные модели могут развертываться для служб Azure Analysis Services или экземпляр SQL Server Analysis Services, работающем в режиме табличного сервера. Можно управлять развернутых табличных моделей в SQL Server Management Studio. 

Документация по табличного моделирования, в этой статье применяется в большинстве случаев для SQL Server Analysis Services и служб Azure Analysis Services. Статьи, относящиеся к службам Azure Analysis Services публикуются вместе с другой документацией Azure. Дополнительные сведения см. в разделе [документации по Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).
  
