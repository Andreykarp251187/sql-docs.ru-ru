---
title: SystemGetClusterAccuracyResults (службы Analysis Services — Интеллектуальный анализ данных) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9521cfd6e2b9ec0d08f290c60167c682c98e46f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209651"
---
# <a name="systemgetclusteraccuracyresults-analysis-services---data-mining"></a>Метод SystemGetClusterAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Возвращает показатели точности перекрестной проверки для структуры интеллектуального анализа и связанных с ней моделей кластеризации.  
  
 Эта хранимая процедура возвращает показатели для всего набора данных как единой секции. Чтобы выполнить секционирование набора данных на перекрестные разделы и вернуть метрики для каждой секции, используйте [SystemGetClusterCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Эта хранимая процедура работает только с моделями кластеризации. Для некластеризованных моделей используется [SystemGetAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SystemGetClusterAccuracyResults(  
<mining structure>   
[,<mining model list>]  
,<data set>  
,<test list>])  
```  
  
## <a name="arguments"></a>Аргументы  
 *структура интеллектуального анализа данных*  
 Имя структуры интеллектуального анализа данных в текущей базе данных.  
  
 (обязательно)  
  
 *список моделей интеллектуального анализа данных*  
 Список моделей для проверки с разделителями-запятыми.  
  
 По умолчанию значение **null**, означающее, что используются все применимые модели. При использовании значения по умолчанию некластеризованные модели автоматически исключаются из списка обработки.  
  
 (необязательно)  
  
 *набор данных*  
 Целочисленное значение, указывающее, что секция в структуре интеллектуального анализа должна использоваться для тестирования. Это значение получается из битовой маски, которая представляет сумму следующих значений, каждое из которых в отдельности является необязательным:  
  
|||  
|-|-|  
|Обучающие варианты|0x0001|  
|Проверочные варианты|0x0002|  
|Фильтр модели|0x0004|  
  
 Полный список возможных значений см. в подразделе «Примечания» этого раздела.  
  
 (обязательно)  
  
 *список тестирования*  
 Строка, указывающая параметры тестирования. Этот параметр зарезервирован для использования в будущем.  
  
 (необязательно).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Таблица, содержащая оценки каждой отдельной секции и статистических функций для всех моделей.  
  
 Следующая таблица содержит список столбцов, возвращаемых методом **SystemGetClusterAccuracyResults**. Дополнительные сведения об интерпретации сведений, возвращаемых этой хранимой процедурой, см. в разделе [Меры в отчете перекрестной проверки](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|ModelName|Имя протестированной модели. Значение**Все** указывает, что результат представляет собой статистическое выражение, полученное для всех моделей.|  
|AttributeName|Неприменимо к моделям кластеризации.|  
|AttributeState|Неприменимо к моделям кластеризации.|  
|PartitionIndex|Число, указывающее секцию.<br /><br /> Для этой хранимой процедуры оно всегда будет равно 0.|  
|PartitionCases|Целое число, указывающее количество проверенных вариантов.|  
|Тест|Тип выполненного теста.|  
|Measure|Имя меры, возвращенной тестом. Меры для каждой модели зависят от типа модели и типа прогнозируемого значения.<br /><br /> Список мер, возвращаемых для каждого прогнозируемого типа, см. в разделе [Меры в отчете перекрестной проверки](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).<br /><br /> Определение каждой меры см. в разделе [Перекрестная проверка (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md).|  
|Значение|Оценка вероятности, указывающая вероятность кластерного варианта.|  
  
## <a name="remarks"></a>Примечания  
 В следующей таблице приводятся примеры значений, с помощью которых можно указать в структуре интеллектуального анализа данные, используемые для перекрестной проверки. Если для перекрестной проверки нужно использовать проверочные варианты, то структура интеллектуального анализа данных должна содержать набор проверочных данных. Сведения о том, как определить набор проверочных данных во время создания структуры интеллектуального анализа данных, см. в разделе [Обучающие и проверочные наборы данных](../../analysis-services/data-mining/training-and-testing-data-sets.md).  
  
|Целое значение|Описание|  
|-------------------|-----------------|  
|1|Используются только обучающие варианты.|  
|2|Используются только проверочные варианты.|  
|3|Используются и обучающие и проверочные варианты.|  
|4|Недопустимое сочетание.|  
|5|Используются только обучающие варианты, и применяется фильтр модели.|  
|6|Используются только проверочные варианты, и применяется фильтр модели.|  
|7|Используются и обучающие и проверочные варианты, и применяется фильтр модели.|  
  
 Дополнительные сведения о сценариях, в которых применяется перекрестная проверка, см. в разделе [Тестирование и проверка (интеллектуальный анализ данных)](../../analysis-services/data-mining/testing-and-validation-data-mining.md).  
  
## <a name="examples"></a>Примеры  
 Этот пример возвращает меры точности для двух моделей кластеризации, `Cluster 1` и `Cluster 2`, которые связаны со структурой интеллектуального анализа vTargetMail. Код в четвертой строке указывает, что результаты должны быть основаны только на проверке вариантов, без использования фильтров, которые могут быть связаны с каждой моделью.  
  
```  
CALL SystemGetClusterAccuracyResults (  
[vTargetMail],  
[Cluster 1], [Cluster 2],  
2  
)  
```  
  
 Образец результатов:  
  
|ModelName|AttributeName|AttributeState|PartitionIndex|PartitionSize|Тест|Measure|Значение|  
|---------------|-------------------|--------------------|--------------------|-------------------|----------|-------------|-----------|  
|Кластер 1|||0|5545|Кластеризация|Вероятность варианта|0.796514342249313|  
|Кластер 2|||0|5545|Кластеризация|Вероятность варианта|0.732122471228572|  
  
## <a name="requirements"></a>Требования  
 Перекрестная проверка доступна только в версиях [!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)] , начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>См. также  
 [SystemGetCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)   
 [SystemGetClusterCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)   
 [SystemClusterGetAccuracyResults](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
  
