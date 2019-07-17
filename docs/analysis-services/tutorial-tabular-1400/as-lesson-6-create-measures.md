---
title: 'Analysis Services занятие для учебника по 6: Создание мер | Документация Майкрософт'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 715fe6144cc430e545feb3c484d148531cff6ec9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207343"
---
# <a name="create-measures"></a>Создание мер

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии вы создадите меры для включения в модель. Как и вычисляемые столбцы, которые вы создали, мера представляет собой вычисление, созданное с помощью формулы DAX. Тем не менее, в отличие от вычисляемых столбцов меры вычисляются на основе выбранного пользователем *фильтра*. Например определенного столбца или среза, добавленного в поле метки строк в сводной таблице. Значение для каждой ячейки в фильтре вычисляется с помощью меры. Меры — это мощные гибкие вычисления, которые вы хотите включить в почти в любых табличных моделях для динамических расчетов с числовыми данными. Дополнительные сведения см. в разделе [меры](../tabular-models/measures-ssas-tabular.md).
  
Чтобы создать меры, используйте *сетку мер*. По умолчанию каждая таблица имеет пустая сетка мер; Тем не менее обычно не создают меры для каждой таблицы. Сетка мер появляется внизу таблицы в конструкторе моделей, когда открыто представление данных. Чтобы скрыть или отобразить сетку мер таблицы, в меню **Таблица** выберите команду **Показать сетку мер**.  
  
Можно создать меру, щелкнув пустую ячейку в сетке мер и введите формулу DAX в строке формул. При нажатии клавиши ВВОД для завершения формулы мера затем отображается в ячейке. Вы также можете создать меры с помощью стандартной статистической функции, щелкнув столбец, а затем нажать кнопку "Автосумма" (**∑**) на панели инструментов. Меры, созданные с помощью функции "Автосумма" отображаются в сетке мер под столбцом, но их можно перемещать.  
  
На этом занятии вы создадите меры путем ввода формулы DAX в строке формул и с помощью функции "Автосумма".  
  
Предполагаемое время для выполнения этого занятия: **30 минут**  
  
## <a name="prerequisites"></a>предварительные требования  

Эта статья входит в учебник по табличному моделированию, который следует изучать в порядке. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [Занятие 5. Создание вычисляемых столбцов](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Создание мер  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Создание меры DaysCurrentQuarterToDate в таблице DimDate  
  
1.  В конструкторе моделей щелкните **DimDate** таблицы.  
  
2.  В сетке мер щелкните верхнюю левую пустую ячейку.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Обратите внимание, что верхняя левая ячейка теперь содержит имя меры, **DaysCurrentQuarterToDate**, а затем результат **92**. Результат не относится к этому моменту поскольку применен ни один фильтр пользователя.
    
      ![как newmeasure lesson6](../tutorial-tabular-1400/media/as-lesson6-newmeasure.png) 
    
    В отличие от вычисляемых столбцов формул мер можно ввести имя меры, за которым следует двоеточие, а затем выражение формулы.

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>Создание меры DaysInCurrentQuarter в таблице DimDate  
  
1.  С помощью **DimDate** таблицы все еще активна в конструкторе моделей в сетке мер щелкните пустую ячейку под созданной мерой.  
  
2.  В строке формул введите следующую формулу:  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    При расчете коэффициента сопоставления между текущим неполным периодом и предыдущим периодом. Формула должна вычислить пропорцию периода, который истек и сравните его с такой же пропорцией в предыдущем периоде. В этом случае [DaysCurrentQuarterToDate] / [DaysInCurrentQuarter] дает пропорцию, прошедшую в текущем периоде.  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>Создание меры InternetDistinctCountSalesOrder в таблице FactInternetSales  
  
1.  Нажмите кнопку **FactInternetSales** таблицы.   
  
2.  Нажмите кнопку **SalesOrderNumber** заголовок столбца.  
  
3.  Щелкните стрелку вниз рядом с кнопкой автосуммирования (**∑**) на панели инструментов и выберите формулу **DistinctCount**.  
  
    Функция автосуммирования автоматически создаст меру для выбранного столбца, используя стандартную статистическую формулу DistinctCount.  
    
       ![как newmeasure2 lesson6](../tutorial-tabular-1400/media/as-lesson6-newmeasure2.png)
  
4.  В сетке мер щелкните новую меру, а затем в **свойства** окно в **имя меры**, переименуйте эту меру в **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Создание дополнительных мер в таблице FactInternetSales  
  
1.  Создайте и назовите следующие меры, используя функцию автосуммирования.  

    |Столбец|Имя меры|Автосуммирование (∑)|Формула|  
    |----------------|----------|-----------------|-----------|  
    |SalesOrderLineNumber|InternetOrderLinesCount|Count|=COUNTA([SalesOrderLineNumber])|  
    |OrderQuantity|InternetTotalUnits|Sum|=SUM([OrderQuantity])|  
    |DiscountAmount|InternetTotalDiscountAmount|Sum|=SUM([DiscountAmount])|  
    |TotalProductCost|InternetTotalProductCost|Sum|=SUM([TotalProductCost])|  
    |SalesAmount|InternetTotalSales|Sum|=SUM([SalesAmount])|  
    |Маржа|InternetTotalMargin|Sum|=SUM([маржа])|  
    |TaxAmt|InternetTotalTaxAmt|Sum|=SUM([TaxAmt])|  
    |Freight|InternetTotalFreight|Sum|=SUM([фрахт])|  
  
2.  Щелкнув пустую ячейку в сетке мер или с помощью строки формул создайте, следующие пользовательские меры в указанном порядке:  
  
      ```
      InternetPreviousQuarterMargin:=CALCULATE([InternetTotalMargin],PREVIOUSQUARTER('DimDate'[Date]))
      ```
      
      ```
      InternetCurrentQuarterMargin:=TOTALQTD([InternetTotalMargin],'DimDate'[Date])
      ```
  
      ```
      InternetPreviousQuarterMarginProportionToQTD:=[InternetPreviousQuarterMargin]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
      ```
      InternetPreviousQuarterSales:=CALCULATE([InternetTotalSales],PREVIOUSQUARTER('DimDate'[Date]))
      ```
  
      ```
      InternetCurrentQuarterSales:=TOTALQTD([InternetTotalSales],'DimDate'[Date])
      ```
      
      ```
      InternetPreviousQuarterSalesProportionToQTD:=[InternetPreviousQuarterSales]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
Меры, созданные для таблицы FactInternetSales может использоваться для анализа критических финансовых данных, таких как продажи, затраты и прибыли для элементов, определенных с помощью выбранного пользователем фильтра.  
  
## <a name="whats-next"></a>Дальнейшие действия

[Занятие 7. Создание ключевых показателей эффективности](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  

  
