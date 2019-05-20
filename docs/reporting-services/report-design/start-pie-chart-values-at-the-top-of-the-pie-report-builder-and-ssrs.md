---
title: Вывод значений круговой диаграммы в верхней части диаграммы (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7f2e174d9f08e22f57375703093ed44ab57be83e
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65578466"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>Вывод значений круговой диаграммы в верхней части диаграммы (построитель отчетов и службы SSRS)
По умолчанию в круговых диаграммах отчетов с разбиением на страницы [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] первое значение набора данных отстоит от верхней части диаграммы на 90 градусов. 

![report-builder-pie-chart-start-at-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*Значения диаграммы начинаются с 90 градусов.*

Можно указать, чтобы первое значение отсчитывалось от верхней части диаграммы. 

![report-builder-pie-chart-start-at-top](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*Значения диаграммы начинаются с верхней части диаграммы.*
  
## <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>Отсчет значений круговой диаграммы от верхней части диаграммы  
  
1.  Щелкните круговую диаграмму.  
  
2.  Если панель **Свойства** не отображается, выберите на вкладке **Вид** пункт **Свойства**.  
  
3.  На панели **Свойства** в области **Настраиваемые атрибуты**измените значение **Начальный угол круговой диаграммы** с **0** на **270**.  
  
4.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Теперь первое значение круговой диаграммы отсчитывается от верхней части диаграммы.  
  
## <a name="see-also"></a>См. также:  
 [Форматирование диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  
