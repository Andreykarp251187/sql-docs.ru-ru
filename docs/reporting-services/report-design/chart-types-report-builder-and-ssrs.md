---
title: Типы диаграмм (построитель отчетов) | Документация Майкрософт
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
f1_keywords:
- "10423"
ms.assetid: 57b00017-69ae-4e71-8d78-44744e208ac7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b2d1d58a5a37078021e8ef6c30ed387fe1f2c406
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081735"
---
# <a name="chart-types-report-builder-and-ssrs"></a>Типы диаграмм (построитель отчетов и службы SSRS)

Важно выбрать тип диаграммы, подходящий для типа представляемых данных. От этого зависит, насколько успешно можно будет интерпретировать данные после их вывода на диаграмме. Например, если набор данных содержит количество точек данных, сравнимое с размером диаграммы, то может оказаться более успешным представление данных с использованием диаграммы с областями, графика или точечной диаграммы. Обсуждение темы, касающейся подготовки данных в зависимости от выбранного типа диаграммы, см. в разделе [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="choosing-a-chart-type"></a>Выбор типа диаграммы  
 Диаграмма каждого типа обладает уникальными характеристиками, позволяющими наилучшим образом представить визуально конкретный набор данных. Для отображения данных можно использовать диаграммы любого типа, но удобство чтения данных повышается, если применяется тип диаграммы, подходящий для конкретных данных, учитывая то, что должно быть показано в отчете. В следующей таблице собраны характеристики диаграммы, от которых зависит применимость диаграммы для конкретного набора данных.  
  
 Тип диаграммы можно изменить после ее создания. Дополнительные сведения см. в статье [Изменение типа диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/change-a-chart-type-report-builder-and-ssrs.md).  
  
 Примеры многих из этих типов диаграмм доступны в качестве образцов отчетов. Дополнительные сведения о скачивании образцов отчетов см. в статье [(Примеры отчетов построителя отчетов и конструктора отчетов)](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
|Тип диаграммы|Отображение данных отношений|Отображение данных об акциях|Отображение линейных данных|Отображение многозначных данных|  
|----------------|------------------------|------------------------|-------------------------|-------------------------------|  
|[Диаграммы с областями (построитель отчетов и службы SSRS)](../../reporting-services/report-design/area-charts-report-builder-and-ssrs.md)|||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||  
|[Линейчатые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)|||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||  
|[Гистограммы](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)|||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||  
|[Гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)|||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||  
|[Графики (построитель отчетов и службы SSRS)](../../reporting-services/report-design/line-charts-report-builder-and-ssrs.md)|||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||  
|[Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||||  
|[Полярные диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/polar-charts-report-builder-and-ssrs.md)|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||||  
|[Диаграммы диапазонов (построитель отчетов и службы SSRS)](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md)|||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|  
|[Точечные диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/scatter-charts-report-builder-and-ssrs.md)|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||  
|[Фигурные диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/shape-charts-report-builder-and-ssrs.md)|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||||  
|[Спарклайны](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|  
|[Биржевые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/stock-charts-report-builder-and-ssrs.md)||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|  

## <a name="next-steps"></a>Дальнейшие действия

[Диаграммы](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Точки данных со значением NULL и пустые точки в графиках](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
[Добавление диаграммы в отчет](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
