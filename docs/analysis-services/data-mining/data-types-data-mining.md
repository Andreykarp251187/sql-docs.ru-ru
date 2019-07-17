---
title: Типы данных (интеллектуальный анализ данных) | Документация Майкрософт
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4b62c9a4ebc9caf9875a1e5b6aef987bf0b4fa8a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68183354"
---
# <a name="data-types-data-mining"></a>Типы данных (интеллектуальный анализ данных)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  При создании модели или структуры интеллектуального анализа данных в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]необходимо указать типы данных для каждого столбца в структуре интеллектуального анализа. Тип данных сообщает модулю анализа, является ли источник данных числовым или текстовым и каким образом следует обрабатывать данные. Например, если исходные данные числовые, можно указать, должны числа обрабатываться как целые или содержать десятичные разряды.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают следующие типы данных для столбцов структуры интеллектуального анализа данных.  
  
|Тип данных|Поддерживаемые типы содержимого|  
|---------------|-----------------------------|  
|**Text**|Cyclical, Discrete, Discretized, Key Sequence, Ordered, Sequence|  
|**Long**|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time<br /><br /> Classified|  
|**Boolean**|Cyclical, Discrete, Ordered|  
|**Double**|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time<br /><br /> Classified|  
|**Дата**|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered|  
  
> [!NOTE]  
>  Типы содержимого Time и Sequence поддерживаются только алгоритмами сторонних производителей. Типы содержимого Cyclical и Ordered поддерживаются, однако большинство алгоритмов обрабатывает их как дискретные величины и не производит их особой обработки.  
  
 В приведенной ниже таблице представлены *типы содержимого* , поддерживаемые для каждого типа данных.  
  
 Тип содержимого связан с интеллектуальным анализом данных и позволяет настроить способ обработки или вычисления данных в модели интеллектуального анализа. Например, даже если столбец содержит числа, при необходимости их можно смоделировать как дискретные значения. Если столбец содержит числа, можно настроить их сегментирование или дискретизацию либо указать, что система должна обрабатывать их как непрерывные значения. Таким образом, тип содержимого может существенно влиять на модель. Список всех типов содержимого см. в разделе [Типы содержимого (интеллектуальный анализ данных)](../../analysis-services/data-mining/content-types-data-mining.md).  
  
> [!NOTE]  
>  В других системах машинного обучения встречаются также термины *номинальные данные*, *факторы* или *категории*, *порядковые*или *последовательные данные*. Как правило, эти термины соответствуют типам содержимого. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]тип данных определяет тип значения только для хранения, а не для использования в модели.  
  
## <a name="specifying-a-data-type"></a>Указание типа данных  
 При создании модели интеллектуального анализа непосредственно с помощью расширений интеллектуального анализа данных можно определить тип данных для каждого столбца при определении модели, а службы Analysis Services в то же время создадут соответствующую структуру интеллектуального анализа с указанными типами данных. Если модель или структура интеллектуального анализа данных создается с помощью мастера, то службы Analysis Services предложат тип данных или же можно будет выбрать тип данных из списка.  
  
## <a name="changing-a-data-type"></a>Изменение типа данных  
 При изменении типа данных в столбце необходимо всегда снова обрабатывать структуру и модели интеллектуального анализа данных, основанные на этой структуре. Иногда при изменении типа данных столбец более не может использоваться в определенной модели. В этом случае службы Analysis Services либо вернут ошибку при повторной обработке модели, либо обработают модель, но пропустят определенный столбец.  
  
## <a name="see-also"></a>См. также  
 [Типы содержимого (интеллектуальный анализ данных)](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Типы содержимого (расширения интеллектуального анализа данных)](../../dmx/content-types-dmx.md)   
 [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Структуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Типы данных (расширения интеллектуального анализа данных)](../../dmx/data-types-dmx.md)   
 [Столбцы модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-columns.md)   
 [Столбцы структуры интеллектуального анализа данных](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
