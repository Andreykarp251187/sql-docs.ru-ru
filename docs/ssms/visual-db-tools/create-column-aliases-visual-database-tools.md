---
title: Создание псевдонимов столбцов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8bae23cd9ddd9221dd9084d0a6b273b57650e38d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105219"
---
# <a name="create-column-aliases-visual-database-tools"></a>Создание псевдонимов столбцов (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Для имен столбцов можно создать псевдонимы, чтобы облегчить работу с ними, подсчеты и суммирования значений. Например, можно создать псевдоним столбца для:  
  
-   создания именованного столбца, например «Общий итог», для выражения типа `(quantity * unit_price)` или агрегатной функции.  
  
-   создания сокращенной формы имени столбца, например `"d_id"` для `"discounts.stor_id."`  
  
После того, как псевдоним столбца определен, можно использовать его в запросе, чтобы указать данные, выбираемые запросом.  
  
### <a name="to-create-a-column-alias"></a>Создание псевдонима столбца  
  
1.  На **панели критериев**укажите строку, содержащую столбец данных, для которого нужно создать псевдоним и, если необходимо, пометьте ее как выходные данные. Если столбца данных нет в сетке, добавьте его.  
  
2.  В столбце **Псевдоним** для этой строки введите псевдоним. Этот псевдоним должен соответствовать всем соглашениям об именах для SQL. Если введенное имя псевдонима содержит пробелы, конструктор запросов и представлений автоматически ставит вокруг них разделители.  
  
## <a name="see-also"></a>См. также:  
[Добавление столбцов в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
