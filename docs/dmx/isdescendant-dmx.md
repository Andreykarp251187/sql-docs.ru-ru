---
title: IsDescendant (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c33a607587ee19de0f47942cd2c1e5b350229a88
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62503805"
---
# <a name="isdescendant-dmx"></a>IsDescendant (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Указывает, является ли текущий узел потомком заданного узла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Тип Boolean.  
  
## <a name="remarks"></a>Примечания  
 **IsDescendant** используется только в [SELECT FROM &#60;модели&#62;. СОДЕРЖИМОГО &#40;расширений интеллектуального анализа данных&#41; ](../dmx/select-from-model-content-dmx.md) и [SELECT FROM &#60;модели&#62;. DIMENSION_CONTENT &#40;расширений интеллектуального анализа данных&#41; ](../dmx/select-from-model-dimension-content-dmx.md) запросов.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере выдаются все объекты, которые являются потомками узла, заданного в функции IsDescendant.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
