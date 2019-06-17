---
title: Распределения столбцов (интеллектуальный анализ данных) | Документация Майкрософт
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83da6c1ba0a278d2d6b80f309a7bc7f6a1688ba4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62724992"
---
# <a name="column-distributions-data-mining"></a>Распределения столбцов (интеллектуальный анализ данных)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]можно определить распределения столбцов в структуре интеллектуального анализа данных, чтобы влиять на то, как алгоритмы обрабатывают данные в этих столбцах при создании моделей интеллектуального анализа данных. В некоторых алгоритмах лучше задавать распределение для всех столбцов, содержащих непрерывные данные, до начала обработки модели в случае, если указанные столбцы содержат общие распределения значений. Если распределения не заданы, создаваемые модели интеллектуального анализа данных могут работать менее точно, чем модели с заданными распределениями, так как на вход алгоритмов будет подаваться меньшее количество данных для анализа.  
  
 Алгоритмы, доступные в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , поддерживают следующие типы распределения.  
  
 **Нормальный**  
 Значения для непрерывного столбца формируют гистограмму с нормальным распределением.  
  
 ![Гистограмма с нормальным распределением](../../analysis-services/data-mining/media/normal-distribution.gif "гистограмма с нормальным распределением")  
  
 **Логарифмическое нормальное**  
 Значения для непрерывного столбца формируют гистограмму, вытянутую в верхнем конце и скошенную в нижнем конце.  
  
 ![Гистограмма с логарифмически нормальным распределением](../../analysis-services/data-mining/media/log-normal-distribution.gif "гистограмма с логарифмически нормальным распределением")  
  
 **Равномерное**  
 На основе значений столбца непрерывных данных может быть сформирована плоская кривая, на которой все значения являются равновероятными.  
  
 ![Гистограмма с равномерным распределением](../../analysis-services/data-mining/media/uniform-distribution.gif "гистограмма с равномерным распределением")  
  
 Дополнительные сведения об алгоритмах в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>См. также  
 [Типы содержимого (интеллектуальный анализ данных)](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Структуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Методы дискретизации (интеллектуальный анализ данных)](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [Распределения (расширения интеллектуального анализа данных)](../../dmx/distributions-dmx.md)   
 [Столбцы структуры интеллектуального анализа данных](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
