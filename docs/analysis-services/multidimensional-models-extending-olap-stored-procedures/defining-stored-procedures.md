---
title: Определение хранимых процедур | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 54b14cd5ee54edab4508c06c55e5815bfeab934f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209377"
---
# <a name="defining-stored-procedures"></a>Определение хранимых процедур
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Хранимые процедуры можно использовать для вызова внешних подпрограмм из [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Для написания внешней подпрограммы, вызываемой хранимой процедурой, можно использовать любой язык среды CLR, например C, C++, C#, Visual Basic или Visual Basic .NET. Хранимую процедуру можно создать один раз и затем вызывать из множества контекстов, например из других хранимых процедур, вычисляемых мер или клиентских приложений. Хранимые процедуры упрощают разработку и реализацию базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] благодаря тому, что общий код создается один раз и сохраняется в одном месте. Хранимые процедуры можно использовать для расширения функциональности приложений за счет добавления дополнительных функций к собственной функциональности многомерных выражений.  
  
 В данном разделе приводятся сведения, необходимые для понимания, проектирования и реализации хранимых процедур.  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Конструирование хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Содержит описание проектирования сборок для использования со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Создание хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md)|Содержит описание создания сборок для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Вызов хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)|Предоставляет сведения об использовании сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Доступ к контексту запросов в хранимых процедурах](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/accessing-query-context-in-stored-procedures.md)|Содержит описание получения доступа к данным области и контекстным данным при помощи сборок.|  
|[Настройка безопасности для хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md)|Содержит описание настройки безопасности для сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Отладка хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)|Содержит описание отладки сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Управление сборками многомерной модели](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
