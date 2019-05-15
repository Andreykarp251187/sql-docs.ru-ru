---
title: Задание условий для групп (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8fbf1ea1a9793ae8d0aad56ee6f524e2e225d26a
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65098958"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a>Задание условий для групп (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Группы, возвращаемые запросом, можно ограничить, задав условие для групп в целом с помощью предложения HAVING. Условие в приложении HAVING применяется после группировки и статистической обработки данных. Запрос возвращает только те группы, которые удовлетворяют условию.  
  
Допустим, требуется посмотреть среднюю цену на все книги каждого издателя в таблице `titles` , если средняя цена превышает $10.00. В этом случае в предложении HAVING можно указать следующее условие: `AVG(price) > 10`.  
  
> [!NOTE]  
> Иногда требуется исключить из групп отдельные строки перед применением условия на всю группу. Дополнительные сведения см. в разделе [Использование предложения HAVING и WHERE в одном запросе (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/use-having-and-where-clauses-in-the-same-query-visual-database-tools.md).  
  
Предложение HAVING может содержать сложные условия, соединенные операторами AND и OR. Дополнительные сведения об использовании операторов AND и OR в условиях поиска см. в разделе [Указание нескольких условий поиска для одного столбца (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-multiple-search-conditions-for-one-column-visual-database-tools.md).  
  
### <a name="to-specify-a-condition-for-a-group"></a>Указание условия для группы  
  
1.  Укажите группы для запроса. Дополнительные сведения см. в разделе [Группирование строк в результатах запроса (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/group-rows-in-query-results-visual-database-tools.md).  
  
2.  Если она уже находится на [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md), добавьте столбец, лежащий в основе условия. (Чаще всего условие содержит столбец, который является столбцом группы или суммарным столбцом.) Столбец, который отсутствует в агрегатной функции или предложении GROUP BY, использовать нельзя.  
  
3.  В столбце **Фильтр** укажите условие, которое требуется применить к группе.  
  
    [конструктор запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) автоматически добавит предложение HAVING в инструкцию на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md), как показано в следующем примере:  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
    ```  
  
4.  Повторите шаги 2 и 3 для каждого дополнительного условия.  
  
## <a name="see-also"></a>См. также:  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
