---
title: Объекты (службы Analysis Services — многомерные данные) базы данных | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c7b9bab0da5b00e77696217974dee5eb5d1d522
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165640"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a>Объекты баз данных (службы Analysis Services — многомерные данные)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Объект [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр содержит объекты базы данных и сборки для использования с оперативной аналитической обработки (OLAP) и интеллектуального анализа данных.  
  
-   В базах данных содержатся объекты OLAP и интеллектуального анализа данных, такие как источники данных, представления источников данных, кубы, меры, группы мер, атрибуты, иерархии, структуры и модели интеллектуального анализа данных, а также роли.  
  
-   В сборках содержатся пользовательские функции, расширяющие функциональность внутренних функций, обеспечиваемых языками многомерных выражений и расширениями интеллектуального анализа данных.  
  
 Объект <xref:Microsoft.AnalysisServices.Database> представляет собой контейнер для всех объектов данных, которые требуются для проектов бизнес-аналитики (таких как кубы OLAP, измерения и структуры интеллектуального анализа данных), а также для поддерживающих их объектов (таких как <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account> и <xref:Microsoft.AnalysisServices.Role>).  
  
 Объект <xref:Microsoft.AnalysisServices.Database> предоставляет доступ ко всем объектам и атрибутам, которые включают следующее.  
  
-   Все кубы, к которым может быть получен доступ, в виде коллекции.  
  
-   Все измерения, к которым может быть получен доступ, в виде коллекции.  
  
-   Все структуры интеллектуального анализа данных, к которым может быть получен доступ, в виде коллекции.  
  
-   Все источники данных и представления источников данных, в виде двух коллекций.  
  
-   Все роли и разрешения базы данных, в виде двух коллекций.  
  
-   Значение параметра сортировки для базы данных.  
  
-   Предполагаемый размер базы данных.  
  
-   Значение языка базы данных.  
  
-   Параметр, определяющий, является ли база данных видимой.  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих подразделах описываются объекты, совместно используемые как OLAP, так и функциями интеллектуального анализа данных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Источники данных в многомерных моделях](../../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)|Содержит описание источника данных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Представления источников данных в многомерных моделях](../../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)|Содержит описание моделей логических данных, основанных на одном или более источниках данных в службе[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Кубы в многомерных моделях](../../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)|Содержит описание кубов и объектов кубов, включая меры, группы мер, связи использования измерений, вычисления, ключевые показатели эффективности, действия, переводы, секции и перспективы.|  
|[Измерения (службы Analysis Services — многомерные данные)](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|Содержит описание измерений и объектов измерений, включая атрибуты, связи атрибутов, иерархии, уровни и элементы.|  
|[Структуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)|Содержит описание структур и объектов интеллектуального анализа данных, включая модели интеллектуального анализа данных.|  
|[Роли безопасности (службы Analysis Services — многомерные данные)](../../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)|Содержит описание роли, механизма безопасности, используемого для управления доступом к объектам в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Управление сборками многомерной модели](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)|Содержит описание сборки, коллекции пользовательских функций, используемой для расширения языков многомерных выражений и для расширений интеллектуального анализа данных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые источники данных (службы SSAS — многомерные базы данных)](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)   
 [Решения многомерной модели](../../../analysis-services/multidimensional-models/multidimensional-model-solutions-ssas.md)   
 [Решения для интеллектуального анализа данных](../../../analysis-services/data-mining/data-mining-solutions.md)  
  
  
