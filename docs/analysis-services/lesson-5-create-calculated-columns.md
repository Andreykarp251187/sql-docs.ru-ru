---
title: 'Занятие 5.: Создание вычисляемых столбцов | Документация Майкрософт'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e5e23ca8ccf344ec9f250eac032946ac074a735d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62752533"
---
# <a name="lesson-5-create-calculated-columns"></a>Занятие 5.: Создание вычисляемых столбцов
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии мы создадим новые данные в модели путем добавления вычисляемых столбцов. Вычисляемый столбец основывается на данных, которые уже существуют в модели. Дополнительные сведения см. в разделе [Calculated Columns](../analysis-services/tabular-models/ssas-calculated-columns.md).  
  
Мы создадим пять новых вычисляемых столбцов в трех разных таблицах. Шаги выполнения для каждой задачи могут немного отличаться друг от друга. Это сделано для того, чтобы продемонстрировать разные способы создания новых столбцов, переименовывания и размещения в разных местах в таблице.  
  
Предполагаемое время для выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [Занятие 4. Создание связей](../analysis-services/lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Создание вычисляемых столбцов  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Создание вычисляемого столбца MonthCalendar в таблице DimDate  
  
1.  Нажмите кнопку **модели** меню > **представление модели** > **представление данных**.  
  
    Вычисляемые столбцы можно создавать только с помощью конструктора моделей в представлении данных.  
  
2.  В конструкторе моделей щелкните **DimDate** таблицу (вкладку).  
  
3.  Щелкните правой кнопкой мыши **CalendarQuarter** заголовок столбца, а затем щелкните **вставить столбец**.  
  
    Новый столбец с именем **Вычисляемый столбец 1** будет вставлен слева от столбца **Календарный квартал** .  
  
4.  В строке формул над таблицей введите следующую формулу. Автозаполнение помогает вводить полные имена столбцов и таблиц, а также выводит список доступных функций.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    Все строки вычисляемого столбца будут заполнены значениями. При прокрутке таблицы вниз будет видно, что строки могут содержать различные значения для данного столбца, на основе данных, которые содержатся в каждой строке.    
  
5.  Переименуйте этот столбец в **MonthCalendar**. 

    ![как табличных lesson5-newcolumn](../analysis-services/media/as-tabular-lesson5-newcolumn.png) 
  
MonthCalendar вычисляемый столбец содержит поддерживающее сортировку имя для месяца.  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>Создание вычисляемого столбца DayOfWeek в таблице DimDate  
  
1.  С помощью **DimDate** активной таблице, щелкните **столбец** меню, а затем щелкните **добавить столбец**.  
  
2.  В строке формул введите следующую формулу:  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    Завершив построение формулы, нажмите клавишу ВВОД. Новый столбец будет добавлен на самой правой стороне таблицы.  
  
3.  Переименуйте столбец в **DayOfWeek**.  
  
4.  Щелкните заголовок столбца, а затем перетащите столбец между столбцами **EnglishDayNameOfWeek** столбца и **DayNumberOfMonth** столбца.  
  
    > [!TIP]  
    > Перемещение столбцов в таблице облегчает навигацию.  
  
DayOfWeek вычисляемый столбец содержит сортируемое имя дня недели.  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>Создание вычисляемого столбца ProductSubcategoryName в таблице DimProduct  
  
  
1.  В **DimProduct** таблицы, прокрутите до правого края таблицы. Обратите внимание на то, что крайний правый столбец имеет имя **Добавление столбца** (курсивом), и щелкните заголовок столбца.  
  
2.  В строке формул введите следующую формулу:  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  Переименуйте столбец в **ProductSubcategoryName**.  
  
Вычисляемый столбец ProductSubcategoryName используется для создания иерархии в таблице DimProduct, которая включает данные из столбца EnglishProductSubcategoryName таблицы DimProductSubcategory. Иерархии не могут охватывать более одной таблицы. Вы создадите иерархии позднее в занятии 9.  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>Создание вычисляемого столбца ProductCategoryName в таблице DimProduct  
  
1.  С помощью **DimProduct** активна, откройте таблицу **столбец** меню, а затем щелкните **добавить столбец**.  
  
2.  В строке формул введите следующую формулу:  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  Переименуйте столбец в **ProductCategoryName**.  
  
Вычисляемый столбец ProductCategoryName используется для создания иерархии в таблице DimProduct, которая включает данные из столбца EnglishProductCategoryName таблицы DimProductCategory. Иерархии не могут охватывать более одной таблицы.  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>Создание вычисляемого столбца Margin в таблице FactInternetSales  
  
1.  В конструкторе моделей выберите **FactInternetSales** таблицы.  
  
2.  Добавление нового столбца.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Переименуйте столбец в **Маржа**.  
  
5.  Перетащите столбец между столбцами **SalesAmount** столбца и **TaxAmt** столбца. 
 
      ![как табличных lesson5-newmargin](../analysis-services/media/as-tabular-lesson5-newmargin.png)
      
    Вычисляемый столбец Margin используется для анализа маржи для каждой продажи.  
  
## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [Занятие 6. Создание мер](../analysis-services/lesson-6-create-measures.md).
  
  
  
