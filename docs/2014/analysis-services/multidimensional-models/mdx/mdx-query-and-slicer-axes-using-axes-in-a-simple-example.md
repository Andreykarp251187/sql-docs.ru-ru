---
title: С помощью осей запроса и среза в простой пример (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 53f48d8f23ef8809f9392b1a2c7ede65239e4985
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074028"
---
# <a name="using-query-and-slicer-axes-in-a-simple-example-mdx"></a>Оси запроса и среза. Простой пример (многомерные выражения)
  Пример в этом разделе демонстрирует простейший метод указания и использования осей запроса и среза.  
  
## <a name="the-cube"></a>Куб  
 Куб TestCube имеет два измерения: Route и Time. Каждому из них соответствует только одна пользовательская иерархия (Route и Time соответственно). Поскольку меры куба относятся к измерению Measures, куб имеет всего три измерения.  
  
## <a name="the-query"></a>Запрос  
 Запрос должен возвращать матрицу, в которой меру «Пакеты» можно сравнивать по маршрутам и времени.  
  
 В следующем примере запроса многомерных выражений иерархии Route и Time являются осями запроса, а измерение Measures — осью среза. Функция [Members](/sql/mdx/members-set-mdx) указывает, что в многомерном запросе для формирования набора будут использоваться элементы иерархии или уровня. Благодаря функции `Members` в многомерном запросе не нужно явно указывать каждый элемент каждой конкретной иерархии или уровня.  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a>Результаты  
 Запрос возвращает таблицу значений меры Packages для каждого пересечения осей измерений COLUMNS и ROWS. Таблица должна выглядеть следующим образом.  
  
||по воздуху|по морю|  
|-|---------|---------|  
|Первый квартал|60|50|  
|Второй квартал|45|45|  
  
## <a name="see-also"></a>См. также  
 [Определение содержимого оси запроса (многомерные выражения)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)   
 [Определение содержимого оси среза (многомерные выражения)](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
