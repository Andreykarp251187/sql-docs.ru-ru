---
title: PredictHistogram (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e7129985eac09d741ea9d00c551a9507ee92c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659178"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает таблицу, представляющую гистограмму прогноза данного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>Объект применения  
  Скалярный или кластерный столбец.  Может использоваться со всеми типами алгоритмов, за исключением алгоритма взаимосвязей ([!INCLUDE[msCoName](../includes/msconame-md.md)]).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Таблица.  
  
## <a name="remarks"></a>Примечания  
 Гистограмма формирует статистические столбцы. Структура столбца возвращенной гистограммы зависит от типа ссылки столбца, который используется с **PredictHistogram** функции.  
  
## <a name="scalar-columns"></a>Скалярные столбцы  
 Для \<ссылка на скалярный столбец >, гистограмма, **PredictHistogram** функция возвращает состоит из следующих столбцов:  
  
-   Прогнозируемое значение  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмы интеллектуального анализа данных не поддерживают **$ProbabilityVariance**. Этот столбец всегда содержит значение 0 для алгоритмов [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмы интеллектуального анализа данных не поддерживают **$ProbabilityStdev**. Этот столбец всегда содержит значение 0 для алгоритмов [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$AdjustedProbability**  
  
     **$AdjustedProbability** столбец [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] расширение [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB для интеллектуального анализа данных.  
  
## <a name="cluster-columns"></a>Кластерные столбцы  
 Гистограмма, **PredictHistogram** функция возвращает для \<ссылка на столбец кластера > состоит из следующих столбцов:  
  
-   **$Cluster** (представляет имя кластера)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает спрогнозированное состояние столбца Bike Buyer в одноэлементном запросе. Этот запрос также возвращает два верхних наиболее вероятных состояния атрибута «Покупатель велосипеда», в зависимости от настроенной вероятности, полученной с помощью **PredictHistogram** функции.  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  TopCount(PredictHistogram([Bike Buyer]),$AdjustedProbability,3)  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>См. также  
 [Кластер &#40;расширений интеллектуального анализа данных&#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40;расширений интеллектуального анализа данных&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictvariance-dmx.md)   
 [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
