---
title: Выбор строк, не соответствующих значению
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 56038b9497f60c2a3275c9216d5c2252d65d81f3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86010608"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Выбор строк, не соответствующих заданному значению (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Чтобы найти строки, которые не соответствуют значению, используется оператор NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Поиск строк, не соответствующих значению  
  
1.  Если это еще не сделано, нужно добавить на [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)столбцы или выражения, которые необходимо использовать в условиях поиска.  
  
2.  Найдите строку, содержащую столбец данных или выражение поиска, и в столбце сетки **Фильтр** введите оператор NOT и затем значение поиска.  
  
Например, чтобы найти строки в таблице `products` , в которой значения в столбце кода продукта начинаются с символа, отличного от «A», можно ввести такое условие поиска:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>См. также:  
[Правила ввода значений для поиска](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Определение критериев поиска](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
